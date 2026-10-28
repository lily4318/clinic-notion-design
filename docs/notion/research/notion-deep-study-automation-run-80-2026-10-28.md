# AUTO-80｜Notion 深度學習：任務清單與資料摘要的用途邊界（2026-10-28）

Trace: `AUTO-80-20261028-2342-RESEARCH`｜自動研究｜公開文獻閱讀及GitHub進度｜NO NOTION/SYSTEM WRITE

## 基準、來源核對及限制
- 本輪開始重新讀取main的README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md，以及research/README.md、audit-checklist-and-research-progress.md、research-to-implementation-matrix.md；遵守雙軌研究與SHA競爭控制。
- sources.md全文檢查兩個精確路徑`/components/task-list/`、`/components/summary-list/`，均未命中；GitHub code search對應slug未命中，寫前檢查AUTO-80尚不存在。**未完成全部歷史AUTO檔逐篇全文及跨語系/同文異址語義去重**，僅列新來源候選，不能稱全庫唯一。
- 來源維護者：GOV.UK Design System team。實際取用日：2026-10-28。Task list頁明列元件2023-12導入、2024-08修復；Summary list頁明列2026-03對齊修復。這些是元件/指南變更記錄，**不是文章初次發表日**。
- 兩篇為英國政府服務UI指南，**不是Notion原生功能規格、臺灣醫療法規或已核准的治療所設計**。本輪核對主要說明、若干HTML/Nunjucks文字範例與已知研究限制，未完整檢視所有獨立預覽、原圖、外部歷史頁及實際操作，故不可記完整R1。

## AUTO80-S01｜Task list — GOV.UK Design System
- URL: https://design-system.service.gov.uk/components/task-list/
- Canonical ID: `govuk-design-system:components/task-list`
- Reading event: `AUTO80-S01-R1-MAIN-TEXT-PARTIAL-20261028`（本輪一次主要正文文字閱讀；非完整R1，非10次複讀）。
- 可核章節：頁面約L52–L213的元件定義/範例、L359–L414的適用/不適用、短任務名稱、提示、狀態與研究限制、L415–L420變更紀錄；核對HTML/Nunjucks示例的任務名稱、status、hint與aria-describedby。
- 來源核心：適合任務多、需分次完成、使用者可自由安排順序的長流程；應先嘗試減少步驟；**必須依固定順序**的流程不適用；任務清單不是答案摘要；狀態不是按鈕，整列連結的新版設計仍有意外點擊與對比度待測假設。
- 反例1【硬性順序誤導】：政府補助須先核對當期核定、資格/期限才可正式確認；若所有步驟都顯示可任意順序完成，會把「待核對」誤當「已可放行」。反證：自由順序只用於實際無相依的操作，必要前置條件不能由清單視覺消除。
- 反例2【清單替代原位資料】：把每日Billing、Session、個案用量改為多層「待辦→開啟→進資料庫」，違反使用者已確認的「同類資料同頁、開啟即見」。反證：任務清單只能作有證據需要的輔助導覽，不能自動取代現有直接可見的資料與操作。
- 反例3【狀態假完成】：工作者勾選「收款已完成」，不等於Billing已入帳、收據已開或跨期額度已核准。反證：任務進度/人工勾選與交易真值、資格核准分離，若將來採用須驗證狀態來源及回讀。

## AUTO80-S02｜Summary list — GOV.UK Design System
- URL: https://design-system.service.gov.uk/components/summary-list/
- Canonical ID: `govuk-design-system:components/summary-list`
- Reading event: `AUTO80-S02-R1-MAIN-TEXT-PARTIAL-20261028`（本輪一次主要正文與選定範例文字閱讀；非完整R1）。
- 可核章節：L52–L213用途與key/value對照、L308–L314行動文字與無障礙、L595–L601邊框、L688–L695缺漏資料、L803–L822多個summary cards、L1206–L1224卡片層級操作及確認、L1384–L1408研究/版本限制；部分HTML/Nunjucks示例文字已核，**全頁1435行所有重複程式碼及獨立預覽未逐一完成**。
- 來源核心：summary list適合有明確欄位標籤與值的事實摘要；不適合任務列表或大量表格資料。單列更改連結要有足夠語境供讀屏；缺漏資訊應呈現填寫入口而非假設已有值；多個相似個體可用summary cards，但只有少量資料不宜過度卡片化；不可輕易移除協助辨識的列分隔線。
- 反例1【歷史價格漂移】：在Session或Billing摘要中動態顯示「目前Price Plan金額」，可能讓歷史交易隨新期別費率調整而改變。反證：呈現層不得取代交易時點金額/有效期別的已核實來源；要區分當期價格與歷史實收。
- 反例2【缺漏與零混淆】：將未確認的補助剩餘額、未知的首次服務日期顯示為0或空白且沒有語義，可能被誤判「確定沒有額度」。反證：未知/待核對/不適用/已確認0需區分，摘要不能憑格式替資料做判定。
- 反例3【卡片跨人誤操作】：多個同名個案或相似Billing摘要卡片，若只有模糊的「修改」「核准」或在共用畫面直接展示敏感資料，可能造成誤選與越權。反證：需要最小必要且非敏感的辨識線索、清楚的操作作用域、角色權限及高風險操作確認；summary cards不是權限隔離機制。

## 交叉研究、可否移植及待驗證
- Task list是「尚須做哪些行動」，Summary list是「已知哪些事實」，**任務完成狀態≠資料摘要值≠正式交易/資格核准**；將來設計應先定義資料權威來源、期別、權限與工作者需要的直接操作，而非先套用視覺元件。
- 兩篇對「不該使用」的限制與本專案已確認同頁需求相符，但**尚未取得授權進行Notion重新設計**。不得把GOV.UK HTML元件直接視為Notion免費版可原生實現。
- 待補：全庫逐檔/語義去重、原始圖片/獨立示例與完整程式碼、鍵盤/螢幕閱讀器/手機、Notion真實介面/Schema/權限、Billing/Session/Price Plan歷史快照與原生Formula、真人UX/效能；未做即不得標PASS。

## 嚴格計量
- `NEW_CANDIDATE=2`；`MAIN_TEXT_PARTIAL_READ=2`；`INDEPENDENT_COUNTEREXAMPLE_GROUPS=2`（共6情境）；`FULL_INDEPENDENT_REREAD_EXISTING=0`。
- `FULL_R1=0`、`FULL_R2_TO_R10=0`、`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`；累積可核實`FULL_DEEP_PASS_10_OF_10=0/10000`。
- **NO NOTION/SYSTEM WRITE**：僅研究與GitHub進度；未修改Notion正式/TEST頁面、DB、View、Formula、Relation、權限或業務資料；未修改正式GAS、Cloud Run、Session或部署。未達門檻，不開始重新設計；手動/自動研究可並行。
