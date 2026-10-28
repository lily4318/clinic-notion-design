# AUTO-77｜Notion 深度學習：Chart View 與 Workspace Search（2026-10-28）
Trace: `AUTO-77-20261028-2038-RESEARCH`｜自動研究｜只讀公開文件與 GitHub 研究紀錄｜NO NOTION WRITE

## 先行基準與去重
- 開始前 Fetch main：README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md、research/README.md、audit-checklist-and-research-progress.md、research-to-implementation-matrix.md 與 AUTO-76 研究紀錄；這些是決策與研究索引，不是即時 Notion Schema。
- 檢查 sources.md 全文：`notion-help:charts`、`notion-help:search`、`/help/charts`、`/help/search`均未命中；GitHub code search 這四個查詢也都沒有回傳匹配。未完成所有歷史研究檔逐檔全文與同文不同網址語義去重，因此只標 `NEW_CANDIDATE`，不能視為已核實全庫唯一。
- 2026-10-28 公開官方頁面正文可讀；兩篇均不計模板、搜尋命中、頁內相關文章為獨立篇數。作者/維護者：Notion Help Center；原始發布或更新日期頁面未標明，僅記錄本次查核日。

## AUTO77-S01｜Chart view — Notion Help
- URL：https://www.notion.com/help/charts
- canonical ID：`notion-help:charts`；本次閱讀軌跡 `AUTO77-S01-R1-MAIN-TEXT-20261028`。
- **閱讀範圍**：官方可讀正文 L107–L325：建立圖表、類型、X/Y軸、Donut、樣式、圖表操作、Drilldown、匯出、Dashboard 與免費方案限制。一次文字主要正文閱讀，未逐張檢查圖片與影片，非完整深讀 R1。
- **原文可核事實**：圖表最多200個groups/50個subgroups；Free僅一張圖表；Chart View 不直接編輯資料列，Drilldown為Table，不能直接批次操作/新增/計算；複雜Relation/Rollup公式可能拖慢載入，部分型別不支援座標軸；隱藏群組、子項目Flattened list與累計模式會影響解讀。
- **文本自相矛盾待驗**：同一頁的 `Omit zero values` 說明先稱開啟會排除零值，接著卻稱開啟會顯示包含零筆的所有Status選項（約L185–L186，Y軸同樣重述）。不能依此文字直接認定開關語義；尚未做UI實測。
- **反例A（財務）**：以圖表 `Count` / `Sum` 直接當作已入帳Billing或核定補助額度，可能把取消/預約/未確認狀態混入；**反證**：Chart為視覺摘要，不是交易快照、正式對帳或核准證據，母體與排除條件需另外核對。
- **反例B（跨期）**：用當期Price Plan關聯衍生的Formula畫跨期趨勢，可能將歷史Session套入現行費率，或因不支援軸型別而缺資料；**反證**：先證實期別與交易時點固定、型別可用、零值及缺漏語義，再討論視覺化。
- **反例C（UX與權限）**：圖表一眼可見不等於同頁可直接修改個案/會談，且點入drilldown不等於取得超出原資料來源的授權；**反證**：既有「同類資料同頁、開啟即見」不應被圖表跳頁取代，權限與資料正確性另驗。
- **未驗證**：圖片/影片/圖表互動、Android匯出、真實Free方案額度、中文顯示、鍵盤/讀屏、Notion角色/載入/Formula；`FULL_R1=0`。

## AUTO77-S02｜Search in your workspace — Notion Help
- URL：https://www.notion.com/help/search
- canonical ID：`notion-help:search`；本次閱讀軌跡 `AUTO77-S02-R1-MAIN-TEXT-20261028`。
- **閱讀範圍**：官方可讀正文 L107–L226：Workspace Search、Command Search、AI Search、結果排序/篩選、Database Search、Page Search、FAQ與CJK支援。一次文字主要正文閱讀，未逐張檢查圖片/實際操作，非完整深讀 R1。
- **原文可核事實**：Database Search 搜尋資料庫頁標題與Property values，不搜頁面內文；Workspace Search 搜頁面內文，但其FAQ稱評論/討論及Select/Multi-select Property values不包含在工作區搜尋結果；資料庫搜尋可查這些Property值。Workspace結果偏重標題/最近修改；可依Title only、Created by、Teamspace、In、Date等條件過濾；支援CJK查詢，但官方仍表示持續改善。
- **反例A（尋找個案）**：行政人員在Workspace Search找不到標籤或Status，就以為個案/收款不存在而新增重複資料；**反證**：搜尋索引範圍與存在性不同，應分清DB Search與Workspace Search、穩定識別與既有Relation。
- **反例B（歷史稽核）**：只用最近修改優先的搜尋結果核對歷史方案/付款，可能把較新的編輯當作有效期別或正式入帳；**反證**：搜尋排序不是業務效期與交易憑證，需用原始時間/狀態核對。
- **反例C（敏感資料）**：為了容易搜尋，把病歷、個案聯絡與收款資訊複製到一般知識頁或AI搜尋範圍；**反證**：可搜尋性不構成資料共享授權，臨床/財務資料應依角色與最小必要原則維持既有界線。
- **未驗證**：中文/同音/全半形實測、搜尋延遲、實際workspace權限、AI Search結果/訂閱、圖片與真人操作；`FULL_R1=0`。

## 本輪研究判斷與進度
- 新來源候選2篇，官方可讀正文文字各讀1次，共2次；首次獨立反例2組6情境；既有來源完整複讀0；全篇含原圖影音/互動的嚴格R1=0，R2–R10=0；`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`。
- 依本次讀回最新GitHub進度，**累積可核實10/10完整深讀0／10,000篇**；不能把2次正文閱讀或6個分析角度冒充10次深讀。
- 只產生研究推論，不核准任何Chart/Search新設計；未修改Notion正式/TEST、資料庫、View、Relation、Formula、權限、業務資料、正式GAS/Cloud Run/Session或部署。使用者明確確認完成10,000篇各10次前不進入Notion重新設計；自動/手動兩路獨立並行。
