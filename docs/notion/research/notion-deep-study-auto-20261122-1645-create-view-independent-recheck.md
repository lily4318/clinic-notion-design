# AUTO-129｜Create a view 獨立複核｜2026-11-22 16:45 Asia/Taipei

- 執行軌跡：AUTO-129 / create-view-independent-recheck / 20261122-1645；只做研究與 GitHub 證據紀錄。
- 來源標題：Create a view — Notion Developers
- Canonical URL：https://developers.notion.com/reference/create-view
- 去重鍵：notion-developers:reference/create-view
- 前輪同來源：AUTO-128（2026-11-22 15:43）；本輪不計為新增來源，亦不把兩次部分閱讀累計成一次完整深讀。
- 取證：本輪重新取得官方搜尋索引可讀的正文（端點介紹、能力、參數、錯誤、回應節），並對照 AUTO-128。直接開啟其他 API 頁面失敗；本頁非完整逐段全文，因此 **獨立針對性部分複讀 1 次，完整深讀 0 次，新增全域唯一來源 0 篇，新增完成10/10 0 篇**。
- Repo 規範：已重新讀取 main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md、研究索引與目錄，以及 AUTO-128；不修改既有研究檔。
- 官方正文核對：POST /v1/views；database_id / view_id / create_database 三選一；data_source_id、name、type 必填；insert content + update content capabilities；filter、sorts、quick_filters、configuration 互相獨立；sorts 最多100個；position 適用資料庫分頁，placement 適用 dashboard widget；400 可由互斥欄位錯誤，404 可由無權限，429 可由限制觸發。
 
## 與前輪不同的反證／邊界假說（尚未實測）
1. 將 quick_filters 當成固定強制 filter：使用者清除快捷篩選後看到不預期的跨期紀錄；需要分別驗證兩種篩選語義。
2. 使用 filter 正確但 sorts 依不穩定欄位排序，操作人員誤以為最新服務排在最前；需要查閱排序契約與同值排序。
3. 設置 calendar 類型卻未核對日期欄位的 presentation configuration，View 建立成功但不符合日常服務日期工作流程。
4. 將 dashboard widget 的 placement 當成資料庫 tab 的 position，造成位置不符合預期；應分別驗證父物件與顯示位置。
5. 為了重現 View 直接重送 POST，未先讀取既有 View ID，可能產生重複分頁；這是操作流程假說，非官方宣稱 POST 必然非冪等。
6. 不同 Data Source 使用同名屬性，但 filter 仍沿用前一來源的屬性 ID；View 建立或呈現結果可能錯誤，需按當期 Schema 核對。
7. 建立成功回傳 View object 卻未查核實際頁面中的可見性與操作者權限；API 成功不能取代真人 UX／權限驗收。
8. 使用者以「同一方案」理解 quick filter 選項，但方案期別分屬不同 ID；篩選顯示可能讓跨期用量混淆，需與個案＋Price Plan 期別資料模型交叉驗證。

## 計量與限制
本輪是同一 canonical URL 的第二次**部分**閱讀，不是第二篇，不是完整閱讀的第2/10次。累積已核實10/10篇數沿用最近可核實基準 **0/10,000**；全歷史清冊去重未完成，不能據此聲稱已全面審計。以上反例均為研究假說，未經 Notion 實測；未修改 Notion 頁面、資料庫、View、公式、權限、GAS、Cloud Run 或 Session，未開始重新設計。
