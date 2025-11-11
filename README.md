# LINE 好友转址服务

这是一个简单的转址服务，用于将自定义域名重定向到 LINE 好友添加链接，并提供社交媒体分享预览功能。

## 功能特色

- ✅ 自动重定向到 LINE 好友添加链接：`https://lin.ee/r73IX45Y`
- ✅ 完整的 Open Graph 标签支持
- ✅ 社交媒体分享时显示自定义预览图和文字
- ✅ 响应式设计
- ✅ 多重备用机制确保重定向成功

## Open Graph 设置

当分享链接到 Facebook、LINE、Twitter 等社交平台时，会显示：

- **标题**：加入健瑋&俞汝LINE好友
- **描述**：婚禮邀請與婚禮訊息
- **预览图**：https://marry-form.vercel.app/images/marry_form_1_start.jpg

## 部署指南

### 方案 1：部署到 Vercel（推荐）

1. 安装 Vercel CLI：
   ```bash
   npm install -g vercel
   ```

2. 在项目目录下运行：
   ```bash
   vercel
   ```

3. 跟随提示完成部署

4. 在 Vercel 控制台设置自定义域名 `yobro.20260207-marry.me`

### 方案 2：部署到 Netlify

1. 将项目推送到 GitHub 仓库

2. 登录 [Netlify](https://netlify.com)

3. 点击 "Add new site" > "Import an existing project"

4. 选择你的 GitHub 仓库

5. 部署设置保持默认即可（无需构建命令）

6. 在 Netlify 控制台的 Domain Settings 中添加自定义域名 `yobro.20260207-marry.me`

### 方案 3：部署到 GitHub Pages

1. 将项目推送到 GitHub 仓库

2. 在仓库设置中启用 GitHub Pages，选择 main 分支作为源

3. 在 DNS 设置中配置自定义域名

4. 在仓库根目录添加 `CNAME` 文件，内容为：`yobro.20260207-marry.me`

## 域名设置

无论使用哪个部署平台，你都需要在域名提供商处添加 DNS 记录：

### 对于 Vercel：
添加 CNAME 记录：
```
yobro.20260207-marry.me → cname.vercel-dns.com
```

### 对于 Netlify：
添加 CNAME 记录：
```
yobro.20260207-marry.me → [你的netlify域名].netlify.app
```

### 对于 GitHub Pages：
添加 CNAME 记录：
```
yobro.20260207-marry.me → [你的github用户名].github.io
```

## 本地测试

由于这是纯静态 HTML 文件，你可以：

1. 直接用浏览器打开 `index.html` 文件

2. 或使用简单的 HTTP 服务器：
   ```bash
   # 使用 Python
   python -m http.server 8000

   # 或使用 Node.js
   npx serve
   ```

3. 然后在浏览器访问 `http://localhost:8000`

## 测试 Open Graph

部署后，你可以使用以下工具测试 OG 标签是否正确：

- Facebook 分享调试器：https://developers.facebook.com/tools/debug/
- Twitter Card 验证器：https://cards-dev.twitter.com/validator
- LinkedIn Post Inspector：https://www.linkedin.com/post-inspector/

## 文件结构

```
redirect-add-friend/
├── index.html          # 主页面（含 OG 标签和重定向逻辑）
└── README.md          # 项目说明文档
```

## 技术说明

- 使用 `<meta http-equiv="refresh">` 标签作为主要重定向方式
- 使用 `window.location.href` JavaScript 作为备用方式
- 提供手动链接作为最后的备用选项
- 完整的 OG 标签确保社交媒体正确抓取信息

## 注意事项

1. 确保 OG 图片链接可以公开访问
2. 图片建议尺寸：1200x630 像素
3. 部署后可能需要等待几分钟才能生效
4. 首次分享时，社交平台可能需要几分钟来抓取 OG 信息

## 授权

此项目为个人使用项目。
