# 治療所行政與前台系統｜高階架構

文件整理日期：2026-10-24。依使用者既有專案指示彙編，**不是本回合已重驗的 live 部署快照**。

| 層次 | 正式採用技術 | 主要責任 |
| --- | --- | --- |
| 登入／前台／BFF | Google 登入、Cloud Run、HTML／CSS／JavaScript | 身分入口、安全前台與轉接 |
| 中央 Session | Firestore | 伺服器端 Session |
| 主要業務後端 | Google Apps Script | Staff／角色／permission／資源範圍、業務處理、寫入鎖／冪等／Audit |
| 資料層 | Notion | 核心業務資料，免費版限制優先 |
| 文件與匯出 | Google Drive／Google Sheets／PDF | 文件、匯出與備份 |
| 前端元件 | SweetAlert2／Chart.js 固定版本 | 提醒與圖表，正式環境避免任意 CDN |

前端不能直接呼叫正式 GAS 或持有 Notion Token。API 僅傳必要 View Model；Notion 需批次查詢、最小欄位、避免 N+1、短 TTL 快取（L3 不共用快取）。CSS 不使用 !important，文字進 DOM 使用安全方法。

核心 Notion 類別：Staff、Intake、Cases、Care Episodes、Sessions、Matching History、Rooms、Space Bookings、Leave Requests、Meetings、Price Plans、Billing、Receipt Requests、Revenue Ledger、Groups、Group Sessions、Events、Event Registrations、Payroll Statement、Tasks、Projects、Documents、Audit Log。

**需求權威來源（以最新文件為準）**：《治療所行政前台網站需求規格書》、《治療所行政前台UX頁面清單》、《治療所前台_統一登入與系統責任分界規格》及 Stitch 前台設計素材。對話核准的新決策須同步正式設計文件。功能可參考 Ragic 醫療產品網站但不構成現有實作承諾。

本輪青壯方案工作僅 Notion；未將 GAS 或 Auth 系統變更納入。
