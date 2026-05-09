# Vercel 部署操作手册

## 前提条件
- 代码已推送到 GitHub：https://github.com/absAline/blog
- 有 GitHub 账号

## 第一步：登录 Vercel

1. 浏览器打开 https://vercel.com
2. 点击右上角 **Sign Up**
3. 选择 **Continue with GitHub**
4. 授权 Vercel 访问你的 GitHub 账号

![Vercel登录页面]()

## 第二步：导入项目

1. 登录后进入仪表盘（Dashboard）
2. 点击 **Add New** → **Project**

![Add New Project]()

3. 在 "Import Git Repository" 列表中找到 `absAline/blog`
4. 点击 **Import**

![Import Repository]()

## 第三步：配置并部署

1. **Framework Preset**：自动检测为 `Astro`（无需修改）
2. **Root Directory**：留空（默认）
3. **Build Command**：`npm run build`（自动填充）
4. **Output Directory**：`dist`（自动填充）
5. **Environment Variables**：无需添加（本项目没有环境变量）
6. 点击 **Deploy**

![Deploy Settings]()

## 第四步：等待部署完成

- 部署约需 1-3 分钟
- 完成后会自动显示绿色 **Congratulations!** 页面
- 会分配一个域名：`https://blog-xxx.vercel.app`

![Deploy Success]()

## 第五步：配置自定义域名（可选）

1. 在项目页面点击 **Settings** → **Domains**
2. 输入你的域名，点击 **Add**
3. 按提示配置 DNS 解析

## 后续更新流程

每次在本地修改后：

```bash
git add .
git commit -m "修改说明"
git push origin main
```

Vercel 会自动检测到推送，自动重新构建和部署。

## 常见问题

| 问题 | 解决方法 |
|------|----------|
| 构建失败 | 查看 Deployments 日志，先本地跑 `npm run build` 确认无错误 |
| 文章不显示 | 确认 Markdown frontmatter 格式正确 |
| 图片 404 | 确认图片引用路径以 `/` 开头（绝对路径） |
