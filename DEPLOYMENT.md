# 部署指南 - 集客消費回饋平台 App 原型

## 🚀 快速部署到 GitHub Pages

### 步驟 1：在 GitHub 建立新的 Repository

1. 前往 https://github.com/new
2. 填寫以下資訊：
   - **Repository name**: `jike-app-prototype`（或任何你喜歡的名稱）
   - **Description**: 集客消費回饋平台 - App 原型展示
   - **Visibility**: Public（公開）或 Private（私人，需付費版 GitHub Pages）
3. **不要**勾選「Add a README file」、「Add .gitignore」等選項
4. 點擊「Create repository」

### 步驟 2：推送程式碼到 GitHub

在終端機（Terminal）執行以下指令：

```bash
# 將你的 GitHub repository URL 替換到下面的指令中
# 格式：https://github.com/你的使用者名稱/jike-app-prototype.git

git remote add origin https://github.com/你的使用者名稱/jike-app-prototype.git
git branch -M main
git push -u origin main
```

### 步驟 3：啟用 GitHub Pages

1. 前往你的 Repository 頁面
2. 點擊「Settings」（設定）標籤
3. 在左側選單找到「Pages」
4. 在「Source」區域：
   - Branch: 選擇 `main`
   - Folder: 選擇 `/root`
5. 點擊「Save」

### 步驟 4：取得網址

等待約 1-2 分鐘後，GitHub Pages 會顯示你的網站網址：

```
https://你的使用者名稱.github.io/jike-app-prototype/
```

🎉 **完成！** 你可以將此網址分享給客戶。

---

## 📱 其他部署選項

### 選項 2：Netlify（推薦，更簡單）

1. 前往 https://app.netlify.com/drop
2. 將整個專案資料夾直接拖曳到網頁上
3. 立即獲得一個網址（例如：random-name-123.netlify.app）
4. 可免費自訂網域名稱

**優點**：
- 不需要 GitHub 帳號
- 拖曳即可部署
- 更新方便（再次拖曳即可）

### 選項 3：Vercel

1. 前往 https://vercel.com
2. 註冊並連結 GitHub
3. Import 你的 repository
4. 自動部署完成

**優點**：
- 每次 git push 自動部署
- 效能優秀
- 免費 SSL 憑證

---

## 🔧 更新網站內容

### 如果使用 GitHub Pages：

```bash
# 修改檔案後
git add .
git commit -m "更新內容說明"
git push

# 約 1-2 分鐘後，網站會自動更新
```

### 如果使用 Netlify Drop：

直接將更新後的資料夾再次拖曳到 Netlify Drop 即可。

---

## 💡 使用建議

### 給客戶的分享方式：

1. **簡訊/Email**：
   ```
   您好，這是「集客消費回饋平台」的互動式原型展示：
   https://your-username.github.io/jike-app-prototype/

   請使用電腦或平板瀏覽，可以點擊手機底部導航和右側控制面板來查看各功能模組。
   ```

2. **會議展示**：
   - 建議使用電腦瀏覽器全螢幕模式（F11）
   - 可以投影到大螢幕
   - 即時操作給客戶看

3. **產生 QR Code**：
   - 前往 https://www.qr-code-generator.com/
   - 輸入你的網址
   - 下載 QR Code 圖片
   - 客戶掃描即可在手機查看

---

## 📊 監控訪問數據（進階）

如果想了解客戶是否查看、停留時間等：

### 加入 Google Analytics：

1. 在 `app-prototype.html` 的 `<head>` 區段加入：

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

2. 將 `G-XXXXXXXXXX` 替換成你的 Google Analytics ID

---

## ⚠️ 注意事項

1. **圖片載入**：確保所有圖片檔案都已上傳到 repository
2. **網址分享**：給客戶前請先自己測試一次
3. **瀏覽器相容性**：建議使用 Chrome、Safari、Edge 等現代瀏覽器
4. **行動裝置**：在手機上也可以瀏覽，但建議用電腦展示效果更佳

---

## 🆘 常見問題

**Q: 網站顯示 404 Not Found？**
A: 請確認 GitHub Pages 設定正確，並等待 1-2 分鐘讓部署完成。

**Q: 圖片無法顯示？**
A: 檢查圖片檔名是否正確，以及是否已 commit 並 push 到 GitHub。

**Q: 想要自訂網域名稱？**
A: 在 GitHub Pages 設定中可以加入 Custom domain，或使用 Netlify 提供的自訂網域功能。

**Q: 如何設定密碼保護？**
A: GitHub Pages 免費版不支援密碼保護，可考慮使用 Netlify（付費功能）或 Vercel。

---

## 📞 需要協助？

如果在部署過程中遇到問題，可以：
1. 檢查 GitHub repository 的 Actions 標籤查看部署狀態
2. 確認所有檔案都已正確上傳
3. 查看瀏覽器控制台（F12）的錯誤訊息

---

**部署成功後，記得將網址儲存並分享給客戶！** 🎉
