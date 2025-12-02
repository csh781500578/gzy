# 广之优茶几工厂网站 - GitHub Pages部署指南

本文档详细说明如何将"广之优"茶几工厂网站部署到GitHub Pages。

## 📋 前置要求

- ✅ GitHub账号
- ✅ Git已安装
- ✅ Node.js 20.19.5或更高版本
- ✅ npm包管理器

## 🚀 快速部署步骤

### 方法一：使用GitHub Actions自动部署（推荐）

#### 1. 创建GitHub仓库

```bash
# 在GitHub网站上创建新仓库，例如命名为 'guangzhiyou-website'
# 不要初始化README、.gitignore或license
```

#### 2. 推送代码到GitHub

```bash
# 进入项目目录
cd /autocode/web

# 初始化Git仓库（如果还没有）
git init

# 添加所有文件
git add .

# 提交
git commit -m "Initial commit: 广之优茶几工厂网站"

# 添加远程仓库（替换YOUR_USERNAME为你的GitHub用户名）
git remote add origin https://github.com/YOUR_USERNAME/guangzhiyou-website.git

# 推送到main分支
git branch -M main
git push -u origin main
```

#### 3. 配置GitHub Pages

1. 进入GitHub仓库页面
2. 点击 **Settings** > **Pages**
3. 在 **Source** 下拉菜单中选择 **GitHub Actions**
4. GitHub Actions会自动构建和部署

#### 4. 配置base路径（重要）

如果你的仓库名不是你的用户名.github.io，需要修改base路径：

**编辑 `.github/workflows/deploy.yml`：**

```yaml
- name: Build
  run: npm run build
  env:
    NODE_OPTIONS: '--max_old_space_size=4096'
    VITE_BASE_PATH: '/guangzhiyou-website/'  # 添加这行，替换为你的仓库名
```

或者在本地开发时设置环境变量：

```bash
# Linux/Mac
export VITE_BASE_PATH=/guangzhiyou-website/
npm run build

# Windows
set VITE_BASE_PATH=/guangzhiyou-website/
npm run build
```

#### 5. 访问网站

部署完成后，访问：
```
https://YOUR_USERNAME.github.io/guangzhiyou-website/
```

### 方法二：手动部署

#### 1. 安装gh-pages工具

```bash
npm install -D gh-pages
```

#### 2. 构建项目

```bash
npm run build
```

#### 3. 部署到GitHub Pages

```bash
npm run deploy
```

## 🔧 配置说明

### Vite配置（vite.config.js）

```javascript
export default defineConfig({
  // GitHub Pages base路径配置
  base: process.env.VITE_BASE_PATH || '/',
  
  build: {
    outDir: 'dist',
    assetsDir: 'assets',
    // 代码分割优化
    rollupOptions: {
      output: {
        manualChunks: {
          'react-vendor': ['react', 'react-dom'],
          'antd-vendor': ['antd'],
          'router-vendor': ['react-router-dom']
        }
      }
    }
  }
})
```

### package.json脚本

```json
{
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "build:prod": "vite build --mode production",
    "predeploy": "npm run build",
    "deploy": "gh-pages -d dist",
    "preview": "vite preview"
  }
}
```

## 🌐 自定义域名配置（可选）

### 1. 创建CNAME文件

在 `/autocode/web/public/` 目录下创建 `CNAME` 文件：

```
www.guangzhiyou.com
```

### 2. 配置DNS

在域名提供商处添加DNS记录：

**A记录：**
```
@ -> 185.199.108.153
@ -> 185.199.109.153
@ -> 185.199.110.153
@ -> 185.199.111.153
```

**CNAME记录：**
```
www -> YOUR_USERNAME.github.io
```

### 3. GitHub Pages配置

1. 进入 Settings > Pages
2. 在 Custom domain 输入你的域名
3. 勾选 Enforce HTTPS

### 4. 更新base配置

使用自定义域名时，设置 `base: '/'`：

```javascript
// vite.config.js
export default defineConfig({
  base: '/',  // 使用自定义域名时
  // ...
})
```

## 🔒 HTTPS配置

GitHub Pages自动提供免费的HTTPS证书（Let's Encrypt）：

1. 确保DNS配置正确
2. 等待证书颁发（可能需要几分钟到几小时）
3. 在GitHub Pages设置中勾选 **Enforce HTTPS**

## 📊 性能优化建议

### 1. 图片优化

```bash
# 压缩图片（推荐使用TinyPNG或ImageOptim）
# 将压缩后的图片放入public/images/目录
```

### 2. 启用Gzip压缩

GitHub Pages默认启用Gzip，无需额外配置。

### 3. CDN加速

考虑使用Cloudflare等CDN服务加速访问。

## 🐛 常见问题

### 1. 页面404错误

**原因：** base路径配置不正确

**解决方案：**
- 检查 `vite.config.js` 中的 `base` 配置
- 确保与仓库名称匹配
- 或使用自定义域名并设置 `base: '/'`

### 2. 样式或图片加载失败

**原因：** 资源路径不正确

**解决方案：**
- 确认所有资源都在 `public/` 目录下
- 使用相对路径：`/images/banner/banner-1.svg`
- 检查文件名大小写是否匹配

### 3. HashRouter路由问题

**原因：** GitHub Pages不支持客户端路由

**解决方案：**
- 项目已使用 `HashRouter`，无需额外配置
- 如需使用 `BrowserRouter`，需添加404.html重定向

### 4. 构建失败

**原因：** 内存不足或依赖问题

**解决方案：**
```bash
# 清除缓存
rm -rf node_modules package-lock.json
npm install

# 增加Node.js内存
NODE_OPTIONS=--max_old_space_size=4096 npm run build
```

## 📝 更新网站内容

### 1. 更新代码

```bash
# 修改代码
# ...

# 提交更改
git add .
git commit -m "Update: 描述你的更改"
git push
```

### 2. 自动部署

推送到main分支后，GitHub Actions会自动构建和部署。

### 3. 查看部署状态

在GitHub仓库页面点击 **Actions** 标签查看部署进度。

## 🎨 替换图片

### 1. 准备图片

按照 `/autocode/web/public/images/README.md` 中的规格准备图片。

### 2. 替换文件

将新图片放入对应目录，覆盖SVG占位图：

```bash
# Banner图片
public/images/banner/banner-1.jpg
public/images/banner/banner-2.jpg
public/images/banner/banner-3.jpg
public/images/banner/banner-4.jpg

# 企业风采
public/images/gallery/gallery-1.jpg ~ gallery-6.jpg

# 产品展示
public/images/products/product-1.jpg ~ product-6.jpg
```

### 3. 更新代码（如使用JPG格式）

如果使用JPG替代SVG，需要更新组件中的文件扩展名：

```javascript
// 例如：Banner组件
image: '/images/banner/banner-1.jpg'  // 改为.jpg
```

### 4. 提交并推送

```bash
git add public/images/
git commit -m "Update: 替换实际图片"
git push
```

## 📚 相关资源

- [GitHub Pages文档](https://docs.github.com/en/pages)
- [Vite部署文档](https://vitejs.dev/guide/static-deploy.html)
- [React Router文档](https://reactrouter.com/)
- [Tailwind CSS文档](https://tailwindcss.com/)

## 💡 提示

- ✅ 定期备份代码
- ✅ 使用语义化的commit消息
- ✅ 测试后再推送到生产环境
- ✅ 监控网站性能和访问统计
- ✅ 定期更新依赖包

## 🎉 完成

按照以上步骤，你的"广之优"茶几工厂网站应该已经成功部署到GitHub Pages！

访问你的网站：`https://YOUR_USERNAME.github.io/guangzhiyou-website/`

如有问题，请参考常见问题部分或查看GitHub Actions的构建日志。
