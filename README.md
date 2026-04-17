# 行事曆事件產生器

一個純前端的 `.ics` 行事曆檔案產生器，無需後端伺服器，單一 HTML 檔案即可使用。

![screenshot](https://img.shields.io/badge/platform-Web-green) ![license](https://img.shields.io/badge/license-MIT-blue)

---

## 功能特色

- **多事件支援**：可新增任意數量的事件，一次匯出為單一 `.ics` 檔案
- **完整事件設定**：
  - 事項標題、地點、描述備註
  - 開始 / 結束日期時間
  - 全天事件切換（符合 RFC 5545 全天格式）
  - 多筆提醒通知（可設定分鐘 / 小時 / 天 / 週前提醒）
  - 重複規則（每天 / 每週 / 每月 / 每年，每週可選指定星期幾，並可設定結束日期）
- **即時預覽表格**：填寫過程中自動顯示所有事件摘要，確認後再下載
- **三種輸出方式**（單一事件時）：
  - 下載 `.ics` 檔案（適用 Apple 日曆、Outlook、各行事曆 App 匯入）
  - 直接開啟 Google 日曆新增頁面
  - 複製 Google 日曆短網址（透過 TinyURL 縮短），可貼到 LINE 群組分享
- **多事件時**：僅提供下載 `.ics`
- **表單驗證**：即時檢查結束時間不得早於開始時間（全天事件亦同），必填欄位紅色提示並自動展開錯誤事件卡片

---

## 使用方式

### 直接開啟

下載 `calendar-generator.html`，用瀏覽器直接開啟即可，**不需要任何安裝或伺服器**。

### 部署至 GitHub Pages

1. Fork 或 clone 此 repo
2. 至 GitHub repo 設定 → Pages → Source 選擇 `main` branch
3. 透過 `https://<username>.github.io/<repo>/calendar-generator.html` 存取

---

## ICS 格式規範

本工具產生的 `.ics` 檔案符合 [RFC 5545](https://datatracker.ietf.org/doc/html/rfc5545) 標準：

| 規範 | 實作方式 |
|------|---------|
| 行長折行 | 使用 UTF-8 byte 計算，超過 75 octets 自動折行 |
| 全天事件 DTEND | exclusive end（結束日期 +1 天） |
| 文字跳脫 | `;` `,` `\n` `\\` 正確跳脫 |
| UID 唯一性 | 隨機亂數 + 時間戳 + 計數器 |
| 行尾 | CRLF (`\r\n`) |

---

## 相容性

| 平台 | `.ics` 匯入 | Google 日曆連結 |
|------|------------|----------------|
| Google 日曆（Web） | ✅ | ✅ |
| Google 日曆（Android） | ✅ | ✅ |
| Apple 日曆（iOS / macOS） | ✅ | — |
| Outlook | ✅ | — |
| LINE 分享連結 | — | ✅（TinyURL 短網址） |

> iOS 需在行事曆 App 選擇「匯入」，無法直接點擊 `.ics` 自動加入。建議 iOS 用戶使用 Google 日曆連結或複製分享連結。

---

## 技術細節

- **純前端**：單一 HTML 檔案，無任何外部依賴（字型除外）
- **字型**：[Noto Sans TC](https://fonts.google.com/noto/specimen/Noto+Sans+TC)、[DM Mono](https://fonts.google.com/specimen/DM+Mono)（Google Fonts CDN）
- **短網址 API**：[TinyURL](https://tinyurl.com/api-create.php)（免費、無需 API Key，失敗時自動 fallback 為原始長網址）
- **無 Cookie、無追蹤、無伺服器**：所有資料僅在瀏覽器本地處理

---

## 檔案結構

```
.
└── calendar-generator.html   # 主程式（單一檔案）
└── README.md
```

---

## License

MIT
