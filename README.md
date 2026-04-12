# Jim Kuo Portfolio

郭哲瑋 Jim Kuo 的個人作品集，單頁滾動式 Landing Page。

## 開啟方式

直接用瀏覽器開啟 `index.html`（無需伺服器）。

## 匯出 PDF

使用根目錄的 Puppeteer 腳本：

```bash
# 在 resume claude/ 目錄下執行
node export-pdf.js
```

輸出位置：`portfolio/Jim_Kuo_Portfolio.pdf`

腳本會以 1440px 寬度渲染完整頁面（含導航列），並自動計算總高度輸出為單頁 PDF。

## 部署

- **GitHub**：`https://github.com/JimKuo-Lab/portfolio`
- **Cloudflare Pages**：`https://portfolio.e991009.workers.dev`（主要對外連結）
- 每次 push 到 `main` branch，Cloudflare Pages 自動重新部署

## 推送更新

```bash
cd "portfolio/"
git add index.html
git commit -m "update content"
git push
```

## 檔案結構

```
portfolio/
├── index.html              # 主要入口，所有內容與樣式內嵌
├── assets/
│   ├── images/             # 專案截圖、照片、Logo
│   └── nano banana/        # iRent 用戶旅程圖（AI 生成）
├── Jim_Kuo_Portfolio.pdf   # 匯出的 PDF 版本
├── DESIGN.md               # 設計規範
└── README.md
```

## 頁面結構

| Section | 內容 |
|---------|------|
| Hero | 姓名、職稱標籤、五張專案卡片 |
| About | 職涯時間軸、工具標籤 |
| 智慧停車解決方案 | 用戶旅程、截圖、系統模組、客製化整合 |
| 車車大檸檬 | 轉型背景、競品分析、飛輪策略、系統架構 |
| AI 與敏捷應用（`#agile`） | AI 與 Scrum 開發模式、Magic Pattern 流程 |
| iRent 共享汽車 | 違規標註三階段流程（Glassmorphism 設計） |
| Contact | 聯絡 CTA |
