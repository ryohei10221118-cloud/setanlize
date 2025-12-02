# 部署指南

本項目是純靜態網站，包含多個 HTML 工具頁面，無需後端服務器。

## 📦 項目結構

```
setanlize/
├── index.html                      # 主頁（工具導航）
├── event-status-checker.html      # 賽事狀態檢查工具
├── customer-service-timer.html    # 客服計時器工具
├── README.md                       # 賽事工具說明
├── CUSTOMER_SERVICE_README.md     # 客服工具說明
├── package.json                    # 項目配置
├── vercel.json                     # Vercel/Zeabur 配置
└── .gitignore                      # Git 忽略文件
```

## 🚀 部署到 Zeabur

### 方法一：通過 Git 倉庫部署（推薦）

1. **連接 GitHub 倉庫**
   - 登入 Zeabur
   - 點擊 "Create Project"
   - 選擇 "Deploy from GitHub"
   - 選擇此倉庫

2. **配置服務**
   - Service Type: 選擇 "Static Site" 或 "Web Service"
   - Root Directory: 留空（使用根目錄）
   - Build Command: 留空
   - Install Command: 留空
   - Start Command: `npx serve -s . -p $PORT`

3. **環境變數**（可選）
   - 無需配置環境變數

4. **部署**
   - 點擊 "Deploy"
   - 等待部署完成

### 方法二：使用 Vercel（替代方案）

如果 Zeabur 有問題，可以使用 Vercel：

1. 安裝 Vercel CLI
   ```bash
   npm i -g vercel
   ```

2. 部署
   ```bash
   cd /home/user/setanlize
   vercel
   ```

3. 跟隨提示完成部署

### 方法三：使用 Netlify（替代方案）

1. 登入 Netlify
2. 拖拽整個文件夾到 Netlify Drop
3. 自動部署完成

## 🔧 Zeabur 常見問題

### 問題 1: 404 Not Found

**原因**：Zeabur 找不到入口文件

**解決方案**：
1. 確保 `index.html` 在項目根目錄
2. 在 Zeabur 設置中確認：
   - Root Directory 設為 `/` 或留空
   - 選擇 "Static Site" 類型

### 問題 2: 頁面空白

**原因**：JavaScript 沒有正確加載

**解決方案**：
1. 檢查瀏覽器控制台是否有錯誤
2. 確認所有 HTML 文件都已提交到 Git
3. 清除瀏覽器緩存後重試

### 問題 3: 無法訪問其他工具頁面

**原因**：路由配置問題

**解決方案**：
1. 確保在 Zeabur 設置中選擇 "Static Site"
2. 檢查 `vercel.json` 配置是否正確
3. 直接訪問完整 URL：
   - `https://your-domain.zeabur.app/event-status-checker.html`
   - `https://your-domain.zeabur.app/customer-service-timer.html`

### 問題 4: Start Command 錯誤

**原因**：Zeabur 需要明確的啟動命令

**解決方案**：
在 Zeabur 設置中添加 Start Command：
```bash
npx serve -s . -p $PORT
```

或者使用：
```bash
npx http-server -p $PORT
```

## 📝 建議的 Zeabur 配置

### 推薦配置 A（靜態網站）
```
Service Type: Static Site
Framework: None
Build Command: (留空)
Output Directory: .
```

### 推薦配置 B（Node.js 服務）
```
Service Type: Web Service
Environment: Node.js
Build Command: (留空)
Start Command: npx serve -s . -p $PORT
```

## 🌐 訪問工具

部署成功後，訪問：

- **主頁**: `https://your-domain.zeabur.app/`
- **賽事檢查**: `https://your-domain.zeabur.app/event-status-checker.html`
- **計時器**: `https://your-domain.zeabur.app/customer-service-timer.html`

## 💡 本地測試

在部署前可以本地測試：

### 方法 1: 使用 npx serve
```bash
cd /home/user/setanlize
npx serve .
```
然後訪問 `http://localhost:3000`

### 方法 2: 使用 Python
```bash
cd /home/user/setanlize
python -m http.server 8000
```
然後訪問 `http://localhost:8000`

### 方法 3: 直接打開文件
在瀏覽器中直接打開 `index.html` 文件

## 🔍 調試技巧

### 1. 檢查部署日誌
在 Zeabur 控制台查看部署日誌，尋找錯誤信息

### 2. 檢查文件是否存在
訪問各個 HTML 文件的直接鏈接，確認文件可訪問

### 3. 檢查瀏覽器控制台
按 F12 打開開發者工具，查看：
- Console：JavaScript 錯誤
- Network：資源加載情況

### 4. 測試跨域問題
確保所有資源都是相對路徑，沒有引用外部 CDN

## 📞 獲取幫助

如果仍然有問題，請提供：
1. Zeabur 部署日誌截圖
2. 瀏覽器控制台錯誤信息
3. 具體的錯誤描述
4. 訪問的 URL

## ✅ 部署檢查清單

- [ ] `index.html` 在根目錄
- [ ] 所有 HTML 文件已提交到 Git
- [ ] `package.json` 存在
- [ ] Zeabur 服務類型正確選擇
- [ ] Start Command 已配置
- [ ] 部署成功無錯誤
- [ ] 可以訪問主頁
- [ ] 可以訪問各工具頁面
- [ ] 工具功能正常運作

## 🎉 成功部署後

恭喜！您的客服工具集已成功部署！
- 分享鏈接給團隊成員
- 將鏈接加入書籤方便訪問
- 定期檢查功能是否正常

---

**注意**：這是純前端項目，所有數據都在瀏覽器本地處理，不會上傳到服務器。
