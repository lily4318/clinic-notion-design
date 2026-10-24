# Notion 設計研究知識庫｜長期可追溯入口

**此目錄保存「已查到的正式規範／已審閱段落／本專案推導／尚未實測」的明確分界。** GitHub 是研究與決策索引，不是 Notion 即時 Schema、正式會談或核定規則來源。

## 研究文件

1. [證據登錄表](evidence-register-2026-10-24.md)：首批 16 個去重網址，14 個取得正文並審閱相關段落、2 個僅有摘要；**深入逐篇完整研究為 0**。
2. [資料庫設計原則](database-design-principles.md)：辨識資料實體、關聯、複合唯一鍵候選與跨期隔離。
3. [工作台／UX 設計原則](workbench-ux-principles.md)：工作導向、三層呈現、資訊氣味與復原。
4. [效能、權限與免費版限制](performance-permissions-free-plan.md)：低成本讀取、公式深度、保密及圖表額度。
5. [實施前驗證清單與研究進度](audit-checklist-and-research-progress.md)：舊10模組盤點、驗收標準、尚未研究的 10,000 篇目標。

## 各文件的證據狀態

- **官方產品事實**：附 Notion URL；與時效相關的方案限制需在實作前重查。
- **一般資料庫設計原則**：附 Microsoft、IBM；Notion Relation 並不完全等同 SQL 外鍵或唯一限制，應轉成 CHECK／查核情境而不是假定 DB 約束。
- **UX 启發規則**：附 NN/g；屬研究原則，不代表真實治療所人員已完成可用性測試。
- **本系統已確認決策**：GitHub `docs/notion/government-subsidy-architecture.md`、`workbench-vnext-2026-10-24.md` 與 `decision-log.md`；每次操作仍需最新 Notion Schema／View／Relation。
- **未批准設計**：不可憑研究報告直接拆資料庫、改共享 Formula／Relation 或批量修改啟用資料。

## 本批範圍

在前述整體工作台改版後，這一輪**只新增 GitHub 研究文件，不操作 Notion 頁面、資料列、Schema、View 或部署**。將「大量公式與 Relation 依賴可能影響效能」「免費版沒有頁面與欄位細粒度權限」「不能以 115 專年欄位當通用模型」納入未來審查規範。

## 後續標準流程

來源發現 → 以 URL 去重 → 取證層級標記 → 摘要／限制與反例 → 對應治療所模組 → 變更前後比較 → TEST 隔離及回復 → 使用者明確核准（重大改動）→ 修改／回查 → GitHub 決策與驗收同步。
