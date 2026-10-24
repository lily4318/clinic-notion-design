# 治療所行政系統｜Notion 設計與驗收知識庫

> 文件基準：2026-10-24。這是已確認決策與歷史 TEST 證據的索引，不是 Notion 即時快照，也不表示未通過事項已上線。

本私人儲存庫是治療所行政系統的 Notion 設計文件、決策、研究與驗收進度的長期入口，目的為跨對話接續、不重複詢問已確認事項。**真正的資料庫現況一律重新查詢最新 Notion Schema、View、Relation 及相關 Google Docs。**

## 新工作回合必讀順序

1. [AGENTS.md](AGENTS.md)：AI 協作、核准門檻、測試與版本同步。
2. [Notion 文件入口](docs/notion/README.md)：模組索引。
3. [決策日誌](docs/notion/decision-log.md)：最新已確認決議。
4. [來源清冊](docs/notion/sources.md)：真實 Notion、Google Docs 位置。
5. [政府補助通用資料模型](docs/notion/government-subsidy-architecture.md)：多方案、多年度／期別、獨立規則。
6. [工作台與 UX](docs/notion/workbench-ux.md)：舊功能最小修改與新版構想。
7. [驗收狀態](docs/notion/acceptance-status.md)：PASS、PARTIAL、BLOCKED、PENDING 的日期與範圍。
8. [ChatGPT 專案指示可貼版本](PROJECT_INSTRUCTIONS_COPY.md)。

## 本階段邊界

**本階段只處理 Notion TEST** 的資料庫、Schema、View、Formula、Relation、Rollup、工作台 UX、資料完整性與隔離驗收。正式 GAS、Cloud Run、中央 Session、部署非此次修改範圍，除非使用者重新指定。

## 資料安全

即使本儲存庫是私人倉庫，也禁止提交姓名、電話、生日、病歷、財務明細、收據、完整原始 Notion 資料列、存取憑證、Token、Secret、Cookie、Script Properties、內部錯誤堆疊或其他敏感設定。僅存抽象設計、非識別性彙整數字與可驗證來源定位。

## 衝突與更新

使用者最後明確確認的決策優先；現有資料事實以最新實測 Schema、View 及可核實資料為準。本文舊紀錄不可自動當作現況。每次相關工作被觸發且產生新決策、修改或驗收結果，應同步對應文件、決策日誌、驗收表及必要 Google Docs；**必須讀遠端現版後最小修改、寫入後回查 Commit 與全文**。不等於可在無對話觸發時背景寫入。
