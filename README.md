# 广之优茶几工厂网站

> 一个现代化的金属茶几生产工厂展示网站，采用未来科技风格设计。

## 🌟 特性

- ✨ **未来科技风格** - 采用青色、蓝色、紫色的科技感配色
- 🎨 **响应式设计** - 完美适配桌面端和移动端
- ⚡ **性能优化** - 移动端深度优化，加载速度极快
- 🖼️ **本地图片** - 所有图片资源本地部署，可离线访问
- 🎯 **完整功能** - Banner、企业介绍、产品展示、生产实力、联系我们等模块

## 🛠️ 技术栈

- **框架**: React 18.2.0
- **构建工具**: Vite 4.1.1
- **语言**: TypeScript 4.8.4
- **样式**: Tailwind CSS 3.4.4
- **UI组件**: Ant Design 5.27.1
- **图标**: @iconify/react 4.1.1
- **路由**: React Router DOM 6.30.1
- **状态管理**: Valtio 1.7.0
- **动画**: Framer Motion 10.16.16

## 📦 快速开始

### 环境要求

- Node.js >= 20.19.5
- npm 或 yarn

### 安装

```bash
# 克隆项目
git clone https://github.com/YOUR_USERNAME/guangzhiyou-website.git

# 进入项目目录
cd guangzhiyou-website

# 安装依赖
npm install
```

### 开发

```bash
# 启动开发服务器
npm run dev

# 访问 http://localhost:5173
```

### 构建

```bash
# 构建生产版本
npm run build

# 预览构建结果
npm run preview
```

### 部署

```bash
# 部署到GitHub Pages
npm run deploy
```

详细部署说明请查看 [DEPLOYMENT.md](./DEPLOYMENT.md)

## 📁 项目结构

```
/autocode/web/
├── public/                 # 静态资源
│   └── images/            # 图片资源
│       ├── banner/        # Banner轮播图
│       ├── gallery/       # 企业风采图
│       ├── products/      # 产品展示图
│       └── README.md      # 图片说明文档
├── src/
│   ├── components/        # 组件目录
│   │   ├── About/        # 企业介绍
│   │   ├── Banner/       # 首页横幅
│   │   ├── Contact/      # 联系我们
│   │   ├── Footer/       # 页脚
│   │   ├── GlobalEffects/ # 全局动效
│   │   ├── Navigation/   # 导航栏
│   │   ├── Products/     # 产品展示
│   │   └── Strength/     # 生产实力
│   ├── pages/            # 页面
│   │   └── Home/         # 首页
│   ├── router/           # 路由配置
│   ├── styles/           # 样式文件
│   ├── App.tsx           # 应用入口
│   └── main.tsx          # 主文件
├── .github/
│   └── workflows/        # GitHub Actions配置
│       └── deploy.yml    # 自动部署配置
├── package.json          # 项目配置
├── vite.config.js        # Vite配置
├── tailwind.config.js    # Tailwind配置
├── tsconfig.json         # TypeScript配置
├── DEPLOYMENT.md         # 部署文档
└── README.md            # 项目说明
```

## 🎨 替换图片

请参考 `public/images/README.md` 了解如何替换占位图片为实际的企业图片。

**快速替换步骤：**

1. 准备符合规格的图片
2. 按照命名规则重命名
3. 放入对应目录覆盖SVG文件
4. 刷新浏览器查看效果

## 🚀 性能优化

### 已实现的优化

- ✅ 代码分割（React.lazy）
- ✅ 组件懒加载
- ✅ 图片懒加载（loading="lazy"）
- ✅ 移动端专项优化
- ✅ React性能优化（memo、useCallback、useMemo）
- ✅ CSS动画优化
- ✅ 分批延迟加载

### 性能指标

- 首屏加载时间: < 2秒（4G网络）
- Time to Interactive: < 3秒
- Lighthouse性能分数: > 90分
- 移动端性能分数: > 85分

## 📱 移动端优化

- 完全禁用复杂动效（粒子系统、3D效果等）
- 使用轻量级动画
- 分批延迟加载内容
- 优化图片尺寸
- 简化DOM结构

## 🌐 浏览器支持

- Chrome（最新版本）
- Firefox（最新版本）
- Safari（最新版本）
- Edge（最新版本）
- 移动端浏览器（iOS Safari, Chrome Android）

## 📄 许可证

MIT License

## 👥 关于

**广之优茶几工厂**
- 主营：金属类半成品茶几生产加工
- 地址：广东省佛山市顺德区
- 厂房面积：8600㎡
- 生产线：5条现代化生产线
- 年产能：120,000件

## 📞 联系方式

- 电话：[待补充]
- 邮箱：[待补充]
- 地址：广东省佛山市顺德区

## 🤝 贡献

欢迎提交Issue和Pull Request！

---

使用 ❤️ 构建 | Powered by React + Vite
