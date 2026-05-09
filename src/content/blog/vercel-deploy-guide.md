---
title: 'Vercel 部署全记录：从本地到线上'
description: '手把手教你将 Astro 博客部署到 Vercel，包含常见问题排查。'
pubDate: 'May 09 2026'
---

## 准备工作

在开始部署之前，确保你已经有：
1. 一个 GitHub 账户
2. 本地 Astro 项目已提交到 GitHub 仓库
3. 一杯咖啡（部署只需要 3 分钟）

## 部署步骤

### 1. 推送代码到 GitHub

```bash
git add .
git commit -m "初始化博客"
git push origin main
```

### 2. 注册 Vercel

访问 [vercel.com](https://vercel.com)，点击 "Sign Up" → "Continue with GitHub"，授权后自动导入仓库。

### 3. 导入项目

1. 在 Vercel 仪表盘点击 "Add New" → "Project"
2. 选择你的博客仓库
3. 框架预设会自动识别为 Astro
4. 直接点击 "Deploy"

### 4. 等待部署完成

约 1-2 分钟后，你会看到一个 `your-project.vercel.app` 的域名。点击即可访问。

## 常见问题

### 部署失败：Build Error

去 Vercel 项目页面看 "Deployments" 里的构建日志。90% 的原因是：

```bash
# 本地忘记安装依赖
npm install

# 有 TypeScript 错误
npm run build  # 先在本地跑一遍
```

### 页面 404

检查 `astro.config.mjs` 中的 `site` 和 `base` 配置：

```javascript
export default defineConfig({
  site: 'https://你的项目名.vercel.app',
  // 如果是根目录部署，不需要 base
  // base: '/my-blog', // 只有在子路径部署时才需要
})
```

### 图片不显示

用绝对路径引用 public 目录下的文件：

```markdown
<!-- 正确 -->
![图片](/images/cover.jpg)

<!-- 错误 -->
![图片](public/images/cover.jpg)
```

## 配置自定义域名（可选）

在 Vercel 项目设置 → Domains 中添加你的域名，按提示配置 DNS 即可。

域名推荐：
- 国际：Cloudflare（成本价，无 markup）
- 国内：阿里云（方便备案）

## 部署后检查清单

- [ ] 首页正常加载
- [ ] 文章列表显示正确
- [ ] 文章内图片正常
- [ ] 移动端显示正常
- [ ] RSS 订阅可用
- [ ] Sitemap 可访问

## 小结

Vercel + Astro 是 2026 年个人博客的最佳部署组合。全程免费，一键部署，自动 HTTPS，支持自定义域名。

如果部署遇到问题，检查构建日志比百度搜索更有效。
