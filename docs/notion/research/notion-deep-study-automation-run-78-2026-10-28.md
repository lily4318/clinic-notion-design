# AUTO-78｜Notion 深度學習：服務入口與交易完成頁的設計邊界（2026-10-28）
Trace: `AUTO-78-20261028-2136-RESEARCH`｜自動研究｜公開資料閱讀＋GitHub記錄｜NO NOTION/SYSTEM WRITE

## 本輪基準與去重
- 開始及寫入前重新Fetch `main`：README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、decision-log.md、acceptance-status.md、research/README.md、audit-checklist-and-research-progress.md、research-to-implementation-matrix.md。以最新Notion「同類資料同頁、開啟即見」、內部規則不放日常頁及歷史資料不可擅改為硬約束；GitHub不是Notion即時Schema。
- sources.md 全文精確URL/slug檢查及 GitHub code search `start-using-a-service`、`confirmation-pages` 均未命中；僅列 `NEW_CANDIDATE`。未完成所有歷史研究檔逐檔全文、同文異址/跨語系語義去重；不宣稱全庫唯一。
- 查核日：2026-10-28；兩頁為GOV.UK Design System team維護之公開官方指南；頁面未顯示可核實的首發/更新日期，不虛構日期。

## AUTO78-S01｜Start using a service — GOV.UK Design System
- URL：https://design-system.service.gov.uk/patterns/start-using-a-service/
- Canonical ID：`govuk-design-system:patterns/start-using-a-service`
- 獨立軌跡：`AUTO78-S01-R1-MAIN-TEXT-20261028`；本次讀取官方全文可得文字行L52–L112（含使用時機、入口內容、資格複雜性、不同入口格式及示例文字），未檢視原始截圖/外部連結及實際互動，**不是完整R1**。
- 可核原文：公眾服務入口須讓使用者理解服務用途、與動作一致的主要CTA、必要時的登入/恢復/更新、費用時間、替代管道與所需資料；複雜資格判斷不應全部擠在入口；簡單入口或多段指南取決於所需脈絡。英國政府出版流程與GDS協作規範不直接套用台灣Notion。
- 反例1（高頻工作台）：把內部Session/Billing每次作業改成「Start now→導覽→進表」，雖符合公共服務入口模式，卻增加點擊並違反使用者已驗收的同頁直接看資料。**反證**：公眾首次服務入口與既有內部高頻工作台是不同任務；不可據此增加中繼頁。
- 反例2（資格誤導）：首頁顯示「符合青壯補助」或將簡短說明當作核准，忽略方案期別、首談期限及人工資格核對。**反證**：入口可說明用途，但正式資格、期別與可用額度須另以授權流程及原始資料驗證。
- 反例3（重複建立）：讓「開始」與「繼續」共用建立新個案的動作，造成同一個案/服務歷程/收費期別重複列。**反證**：建立、恢復、更新是不同操作；需要穩定識別及防重複，不可從CTA文案推定已有技術保證。
- 本輪狀態：官方主要正文文字閱讀一次；圖片、入口示例實際操作、讀屏/手機/真人UX未驗；`FULL_R1=0`。

## AUTO78-S02｜Confirmation pages — GOV.UK Design System
- URL：https://design-system.service.gov.uk/patterns/confirmation-pages/
- Canonical ID：`govuk-design-system:patterns/confirmation-pages`
- 獨立軌跡：`AUTO78-S02-R1-MAIN-TEXT-20261028`；本次閱讀官方文字L51–L158、HTML與Nunjucks示例、必備內容、可存證、書籤返回、可及性與Known gaps；未打開互動示例、圖片/讀屏/手機，**不是完整R1**。
- 可核原文：交易完成頁應清楚顯示完成狀態、如有則顯示參考號、下一步/時程、聯絡方式、可儲存交易紀錄；書籤回訪應有合理處理；綠色確認Panel內直接放互動連結可能有對比度/焦點可及性問題；較大任務中的局部交易如何確認仍是研究缺口。
- 反例1（完成語義）：Notion頁顯示「已完成」可能僅代表表單存檔，不能直接視為政府補助資格核准、Billing已入帳或Session已完成。**反證**：完成頁必須精確對應已實際完成的業務交易及授權確認，避免將暫存與核准混用。
- 反例2（收據與隱私）：用姓名、手機或公開頁面連結當交易參考碼，可能洩漏個資；畫面可列印不等於符合正式收據、財務留存或更正規範。**反證**：最小必要識別、角色存取與可追溯的交易時點證據須獨立核實。
- 反例3（歷史與回訪）：付款後取消、退費或方案期別修訂，舊書籤的成功頁若仍顯示當時「完成」，可能誤導當前狀態；若只顯示即時關聯金額又可能改寫歷史事實。**反證**：交易當時證據、現況狀態與後續異動需區分，不能以即時頁面取代稽核軌跡。
- 本輪狀態：官方主要正文與示例程式碼文字閱讀一次；未實測HTML可及性、返回書籤、Notion原生行為；`FULL_R1=0`。

## 交叉反證、限制及嚴格計數
- 入口「開始／繼續」與交易「已完成」均是使用者理解業務狀態的**語意介面**，不構成Notion自動儲存、正式入帳、資格核准、歷史快照或角色權限的技術證明。任何轉用為治療所UX前須與既有「同類資料同頁、開啟即見」需求比較，且須經使用者核准。
- `NEW_CANDIDATE=2`；`MAIN_TEXT_READ=2`；`INDEPENDENT_COUNTEREXAMPLE_GROUPS=2`（共6情境）；`FULL_INDEPENDENT_REREAD_EXISTING=0`；`FULL_R1=0`、`FULL_R2_TO_R10=0`；`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`；累積可核實`FULL_DEEP_PASS_10_OF_10=0/10000`。
- 未完成：全部歷史來源去重、截圖與外部示例、互動、鍵盤/讀屏/手機、Notion即時Schema、Formula、角色權限、歷史Billing/Session/補助期別、真人UX與效能；不將兩篇正文閱讀冒稱完整深讀。
- **NO NOTION/SYSTEM WRITE**：僅公開文件研究及GitHub研究記錄；未修改任何正式/TEST Notion頁面、資料庫、View、Relation、Formula、權限、業務資料，也未改正式GAS/Cloud Run/Session/部署；研究門檻未達，不開始Notion重新設計；自動與手動研究可並行。
