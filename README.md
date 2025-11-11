# LINE 好友轉址服務

這是一個簡單的轉址服務，用於將自訂網域重新導向到 LINE 好友新增連結，並提供社交媒體分享預覽功能。

## 功能特色

- ✅ 自動重新導向到 LINE 好友新增連結：`https://lin.ee/r73IX45Y`
- ✅ 完整的 Open Graph 標籤支援
- ✅ 社交媒體分享時顯示自訂預覽圖和文字
- ✅ 響應式設計
- ✅ 多重備用機制確保重新導向成功

## Open Graph 設定

當分享連結到 Facebook、LINE、Twitter 等社交平台時，會顯示：

- **標題**：加入健瑋&俞汝LINE好友
- **描述**：婚禮邀請與婚禮訊息
- **預覽圖**：https://marry-form.vercel.app/images/marry_form_1_start.jpg

## 部署指南

### 方案 1：部署到 Vercel（推薦）

1. 安裝 Vercel CLI：
   ```bash
   npm install -g vercel
   ```

2. 在專案目錄下執行：
   ```bash
   vercel
   ```

3. 跟隨提示完成部署

4. 在 Vercel 控制台設定自訂網域 `yobro.20260207-marry.me`

### 方案 2：部署到 Netlify

1. 將專案推送到 GitHub 倉庫

2. 登入 [Netlify](https://netlify.com)

3. 點擊 "Add new site" > "Import an existing project"

4. 選擇你的 GitHub 倉庫

5. 部署設定保持預設即可（無需建置指令）

6. 在 Netlify 控制台的 Domain Settings 中新增自訂網域 `yobro.20260207-marry.me`

### 方案 3：部署到 GitHub Pages

1. 將專案推送到 GitHub 倉庫

2. 在倉庫設定中啟用 GitHub Pages，選擇 main 分支作為來源

3. 在 DNS 設定中設定自訂網域

4. 在倉庫根目錄新增 `CNAME` 檔案，內容為：`yobro.20260207-marry.me`

## 網域設定

無論使用哪個部署平台，你都需要在網域提供商處新增 DNS 記錄：

### 對於 Vercel：
新增 CNAME 記錄：
```
yobro.20260207-marry.me → cname.vercel-dns.com
```

### 對於 Netlify：
新增 CNAME 記錄：
```
yobro.20260207-marry.me → [你的netlify網域].netlify.app
```

### 對於 GitHub Pages：
新增 CNAME 記錄：
```
yobro.20260207-marry.me → [你的github使用者名稱].github.io
```

## 本機測試

由於這是純靜態 HTML 檔案，你可以：

1. 直接用瀏覽器開啟 `index.html` 檔案

2. 或使用簡單的 HTTP 伺服器：
   ```bash
   # 使用 Python
   python -m http.server 8000

   # 或使用 Node.js
   npx serve
   ```

3. 然後在瀏覽器存取 `http://localhost:8000`

## 測試 Open Graph

部署後，你可以使用以下工具測試 OG 標籤是否正確：

- Facebook 分享偵錯器：https://developers.facebook.com/tools/debug/
- Twitter Card 驗證器：https://cards-dev.twitter.com/validator
- LinkedIn Post Inspector：https://www.linkedin.com/post-inspector/

## 檔案結構

```
redirect-add-friend/
├── index.html          # 主頁面（含 OG 標籤和重新導向邏輯）
└── README.md          # 專案說明文件
```

## 技術說明

- 使用 `<meta http-equiv="refresh">` 標籤作為主要重新導向方式
- 使用 `window.location.href` JavaScript 作為備用方式
- 提供手動連結作為最後的備用選項
- 完整的 OG 標籤確保社交媒體正確抓取資訊

## 注意事項

1. 確保 OG 圖片連結可以公開存取
2. 圖片建議尺寸：1200x630 像素
3. 部署後可能需要等待幾分鐘才能生效
4. 首次分享時，社交平台可能需要幾分鐘來抓取 OG 資訊

## 授權

此專案為個人使用專案。
