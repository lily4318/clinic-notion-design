# AUTO-102｜2026-11-21｜Database Views 共用資料與篩選誤讀（僅研究）

Trace: AUTO-102-20261121-0941-USING-DATABASE-VIEWS-PARTIAL

## 原始來源與讀取證據
- 官方來源：[Using database views | Notion](https://www.notion.com/help/guides/using-database-views)
- canonical URL: https://www.notion.com/help/guides/using-database-views；identity: notion-help-guide:using-database-views；發布者 Notion Labs；原始發表日期未核實；擷取日 2026-11-21。
- 取得 HTML 227 行，正文 L107–140（文字主文）已逐行核讀；L114–120 的六分鐘影片無法播放，圖片、影片、外部連結未逐項檢視。只記 PARTIAL_MAIN_TEXT_READ=1；**不計 FULL_R1 或任何10/10**。
- main 研究資料夾讀取時114個頂層項目；已讀最新核心七份及 docs/notion/research/README.md、AUTO-101；尚未逐檔完成所有歷史紀錄全文/跨語系語義去重。故本網址只算候選來源，不宣稱唯一新篇。
- 獨立事件：AUTO102-S01-20261121-0941-HTML-L107-140-PARTIAL。與 AUTO-101 database templates 不同 URL。

## 原文支持的規則與待驗反例
1. L126–129：同一資料庫可有多個不同呈現方式的 Views，資料仍為同一批。CE1：把同一 Session 放入不同收費／本週／個案檢視，不代表多筆不同 Session；跨 View 加總可能重複計數。
2. L131–135：View 可以依屬性分組、篩選、排序。CE2：某 View 顯示零筆可能只是篩選排除，不代表來源不存在或已刪除；需核對底層資料來源及篩選。
3. L133–135：卡片可顯示選定屬性。CE3：卡片沒有呈現方案期別，不等於該欄位為空或無法追溯；須分辨隱藏顯示與真實缺值。
4. L127–129：表格、清單、看板、圖庫、日曆、時間軸皆可顯示資料。CE4：改變 View 型式不能證明資料歸屬、權限、有效會談占用邏輯正確。
5. L135：篩選與排序為顯示行為。CE5：在「已預約」View 看不到過期但狀態未更新的 Session，不能推定這些資料已被正確處理；仍需跨狀態稽核。
6. L136：每筆卡片自身也是頁面。CE6：把同一資料庫放進多個工作台入口，不能視為隔離複本；原頁面修改的影響需另核實。

以上均為官方文字延伸的**待測假說**，不是已在治療所實機驗證的缺陷。此簡介型指南文字短且主要影片未讀，不得冒充完整深度閱讀。

## 計量與限制
- NEW_SOURCE_CANDIDATE=1（未全歷史去重）；PARTIAL_MAIN_TEXT_READ=1；COUNTEREXAMPLE=6；FULL_R1=0；FULL_R2_TO_R10=0；NEW_10_OF_10=0。
- 最近已驗證的完整10/10基準：0/10,000；本次未重新全量核定。
- 僅 GitHub 研究紀錄；未更動 Notion 頁面、資料庫、View、Formula、Relation、權限、正式 GAS、Cloud Run 或 Session；未進入重新設計。雙軌研究持續。
