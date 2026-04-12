# 設計指南 — Portfolio Design System

> Jim Kuo Portfolio 的全域視覺設計規範。
> 單頁滾動式 Landing Page，暖色調商務風格。

---

## 1. 風格基調

- **暖棕米色調**：米白底色搭配深棕 `#7B4A32` 作為主強調色
- **精緻商務**：資訊密度適中，留白有節奏感
- **數據優先**：KPI 數字、成果指標視覺上最突出
- 無斜體、無鮮豔漸層、無裝飾性插圖
- iRent section 採用 Glassmorphism 進階視覺

---

## 2. 色彩系統

```
主強調色     #7B4A32   深棕，project-header、邊框、KPI 數字
次要棕       #3D2010   深色 project-header 變體
金色強調     #C4824A   arrow、sub-title bar、hover
琥珀背景     #FEF6E9   amber-bg，卡片底色
琥珀邊框     #F5D8A8   amber-pale，分隔線

最深文字     #0f172a   標題、主要文字（text-dark）
中灰文字     #475569   正文（text-body）
說明文字     #64748b   輔助說明（text-muted）
輔助色       #94a3b8   次要標籤（text-sub）
線條         #cbd5e1   分隔線（line）
分隔線       #e2e8f0   淺分隔（line-light）

頁面底色     #f8fafc   bg-pale sections
接觸區底色   #0f172a   Contact section 黑底
```

### iRent 專屬色（Glassmorphism）
```
膠囊漸層     #8B5A3A → #B07850   Phase pill background
KPI 卡漸層   #5C3318 → #7B4A32   ir-kpi-card
金色文字     #F5C98A              KPI 數字色
標籤金框     rgba(196,130,74,0.3) ir-tag border
```

---

## 3. 字體規範

| 層級 | 字體 | 大小 | 用途 |
|------|------|------|------|
| 主標題（名字） | `Playfair Display` 700 | 52px | `.hero-name` |
| 英文副標 | `Playfair Display` 400 | 22px | `.hero-name-en` |
| Section 標題 | `Noto Serif TC` 700 | 30px | `.section-title` |
| Project 標題 | `Noto Serif TC` 700 | 22px | `.project-header-title` |
| 卡片標題 | `Noto Serif TC` 700 | 15–18px | `.card-title` |
| 內文 | `Noto Sans TC` | 13–15px | 說明文字 |
| Section label | `Noto Sans TC` 600 | 11px | `.section-label`，uppercase |
| KPI 數字（全域） | `serif` 900 | 36px | `.kpi-num` |
| KPI 數字（iRent） | `sans-serif` 900 | 36px | `.ir-kpi-num` |
| Nav 名稱 | `Noto Sans TC` 700 | 14px | `.nav-logo` |
| Nav 認證小字 | `Noto Sans TC` 400 | 10px | `.nav-logo span:last-child`，letter-spacing 0.05em |
| Nav 連結 | `Noto Sans TC` 500 | 13px | `.nav-links a` |

**語言原則**：100% 中文，專有名詞例外（API、SOP、B2B2C、Scrum、GCP、Line Login 等）

---

## 4. 頁面結構

```
<nav>                    ← 固定頂部，高度 56px，backdrop-filter: blur
                           左上角：郭哲瑋 Jim Kuo + IPAS 認證 AI 應用規劃師（小字）
                           右側：關於我 / 智慧停車 / 車車大檸檬 / AI 與敏捷應用 / IRENT / 聯絡
<section#about>          ← 照片（左）+ 核心實戰卡片 + 職涯時間軸（右），雙欄
<section#smart-parking>  ← 智慧停車，bg-pale
<section#lemon>          ← 車車大檸檬，bg-white
  └── #agile             ← AI 與敏捷開發模式子區塊（錨點）
<section#irent>          ← iRent，bg-pale，Glassmorphism 內容
<section#contact>        ← 黑底聯絡區
```

---

## 5. 容器規範

```css
.container {
  max-width: 1100px;
  margin: 0 auto;
  padding: 0 40px;
}
section { padding: 80px 0; }
```

---

## 6. 常用元件

### 6-1. Project Header（深棕頂欄）
```html
<div class="project-header">   /* background: #7B4A32 */
  <div class="project-header-label">Project 0X · 名稱</div>
  <div class="project-header-title">標題</div>
</div>
<div class="project-body">  /* border: 1.5px solid #7B4A32; border-top: none */
  <!-- 內容 -->
</div>
```

### 6-2. KPI Strip
```html
<div class="kpi-strip">
  <div class="kpi-item">
    <div class="kpi-num">1,000+</div>
    <div class="kpi-right">
      <div class="kpi-label">主要說明</div>
      <div class="kpi-sub">次要說明</div>
    </div>
  </div>
</div>
```

### 6-3. Cards（棕框重點 / 灰框次要）
```html
<div class="card blue">
  <div class="card-title blue">標題</div>
  <div class="card-body">內容</div>
</div>
```

### 6-4. Section Label
```html
<div class="section-label">LABEL TEXT</div>
```

### 6-5. Tags
```html
<span class="tag-primary">主標籤</span>   <!-- 深棕底白字 -->
<span class="tag-outline">副標籤</span>   <!-- 棕線框 -->
<span class="tag">一般標籤</span>         <!-- 灰線框圓角 -->
```

### 6-6. Flow 垂直流程
```html
<div class="flow-v-step">
  <div class="flow-v-step-label">步驟名稱</div>
  <div class="flow-v-step-content">說明</div>
</div>
<div class="flow-v-arrow">↓</div>
```

---

## 7. iRent Glassmorphism 元件（`#irent` 專屬）

所有 class 前綴為 `.ir-`，僅在 `#irent` section 內生效。

| Class | 用途 |
|-------|------|
| `.ir-body` | 主容器，backdrop-filter: blur(14px)，半透明磨砂 |
| `.ir-phase-pill` | Phase 膠囊標籤，深棕漸層 + 金色圓點 |
| `.ir-phase-title` | 膠囊右側標題文字 |
| `.ir-flow-arrow` | 漸層色數據流線箭頭 |
| `.ir-block` | 內容區塊，白色半透明 + 細陰影 |
| `.ir-block-label` | 區塊標籤，uppercase 小字 |
| `.ir-block-content` | 區塊內文 |
| `.ir-tag` | 標籤雲圓角 pill（資料來源用） |
| `.ir-tag-muted` | 灰色版標籤（法規參考資料用） |
| `.ir-sub-card` | 三欄分析子卡片 |
| `.ir-sub-title` | 子卡片標題，左側金色 bar |
| `.ir-bullet-list` | `›` 符號列點清單 |
| `.ir-kpi-card` | 深棕漸層 KPI 卡，flex 垂直置中 |
| `.ir-kpi-num` | 36px 金色大數字，入場動畫 |
| `.ir-kpi-label` | KPI 說明小字 |
| `.ir-kpi-divider` | KPI 卡內分隔線 |
| `.ir-benefit-row` | 效益列，圓形圖示 + 雙層文字 |
| `.ir-benefit-icon` | 圓形漸層圖示容器 |
| `.ir-benefit-label` | 效益類型標籤 |
| `.ir-benefit-desc` | 效益說明文字 |

---

## 8. 格線系統

| 用途 | Class |
|------|-------|
| 雙欄等寬 | `.grid-2` |
| 三欄等寬 | `.grid-3` |
| 策略三欄 + 箭頭 | `.strategy-grid` (1fr 32px 1fr 32px 1fr) |

---

## 9. 對齊原則

- 嚴格**置左對齊**（`text-align: left`）
- 禁止文字區塊置中（KPI 數字、closing CTA 例外）
- 圖片需有 `border-radius: 3–4px` + 細邊框，不得裸貼

---

## 10. 禁止事項

- 禁止斜體
- 禁止鮮豔漸層（iRent 的深棕漸層除外）
- 禁止使用 Reveal.js / 簡報框架
- 禁止使用純黑 `#000`（改用 `#0f172a` 或 `#111`）
- 禁止 emoji 作為圖示（iRent 效益列 emoji 為設計決策例外）

---

## 11. 響應式斷點

| 斷點 | 行為 |
|------|------|
| `> 768px` | 全版雙欄、三欄排列 |
| `≤ 768px` | 全部折為單欄，nav links 隱藏 |

---

## 12. 各 Section 狀態

| Section | 內容 | 狀態 |
|---------|------|------|
| Hero | 姓名、標籤、五張專案卡片 | ✅ |
| About | 職涯時間軸雙欄 | ✅ |
| 智慧停車解決方案 | 用戶旅程、截圖、系統模組、客製化整合 | ✅ |
| 車車大檸檬 | 轉型背景、競品、飛輪策略、問題與解法配適 | ✅ |
| AI 與敏捷應用（`#agile`） | AI 與 Scrum 開發模式、Magic Pattern 流程 | ✅ |
| iRent 共享汽車 | 違規標註三階段（Glassmorphism） | ✅ |
| Contact | 聯絡 CTA | ✅ |
