# VitePress 部署记录 {#vitepress-deployment-notes}

本页面记录了如何从零开始部署 VitePress 文档站点的完整过程。

## 环境准备 {#environment-setup}

1. **Node.js 环境**
   - 安装 Node.js 18 或更高版本
   - 推荐使用 nvm 管理 Node.js 版本

2. **包管理器**
   - 推荐使用 pnpm 作为包管理器
   - 安装命令：`npm install -g pnpm`

## 项目初始化 {#project-initialization}

1. **创建项目目录**
   ```bash
   mkdir my-vitepress-docs
   cd my-vitepress-docs
   ```

2. **初始化项目**
   ```bash
   pnpm init
   pnpm add -D vitepress
   ```

3. **初始化 VitePress**
   ```bash
   pnpm exec vitepress init
   ```

## 本地开发 {#local-development}

1. **启动开发服务器**
   ```bash
   pnpm docs:dev
   ```

2. **访问本地站点**
   - 默认地址：`http://localhost:5173`

## 生产部署 {#production-deployment}

1. **构建静态文件**
   ```bash
   pnpm docs:build
   ```

2. **部署平台选择**

   VitePress 支持多个部署平台：

   - **Netlify / Vercel / Cloudflare Pages**
     - 构建命令：`pnpm docs:build`
     - 输出目录：`docs/.vitepress/dist`
     - Node 版本：18 或更高

   - **GitHub Pages**
     - 使用 GitHub Actions 自动部署
     - 配置 `.github/workflows/deploy.yml`

   - **GitLab Pages**
     - 配置 `.gitlab-ci.yml`
     - 设置正确的 `base` 路径

## 注意事项 {#considerations}

1. **base 配置**
   - 如果站点不是部署在域名根路径，需要配置 `base` 选项
   - 例如：`base: '/blog/'`

2. **依赖管理**
   - 确保 `package.json` 中的依赖版本正确
   - 推荐使用 `pnpm-lock.yaml` 锁定版本

3. **性能优化**
   - 使用合适的图片格式和大小
   - 避免不必要的客户端 JavaScript

## 常见问题 {#common-issues}

1. **构建失败**
   - 检查 Node.js 版本
   - 确认依赖安装完整
   - 查看构建日志

2. **路径问题**
   - 确保 `base` 配置正确
   - 检查资源引用路径

3. **部署后 404**
   - 检查部署平台配置
   - 确认构建输出目录正确