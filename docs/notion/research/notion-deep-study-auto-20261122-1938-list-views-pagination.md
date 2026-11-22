# AUTO-132｜List views API：跨工作台 View 清冊與分頁完整性（部分閱讀）

- 執行軌跡：AUTO-132-20261122-1938-LIST-VIEWS-READ-PARTIAL
- 來源：[List views | Notion Developers](https://developers.notion.com/reference/list-views)
- Canonical URL：https://developers.notion.com/reference/list-views
- 去重身份：notion-developers:reference:list-views；寫前 sources.md 精確 URL 未命中、research 目錄無同主題檔名；**跨全歷史語義去重未完成，僅候選，不正式認列新篇**。
- 閱讀事件：AUTO132-S01-R1-20261122-1938-HTML-API-REFERENCE-PARTIAL；讀取官方 HTML 端點正文、參數、回應、權限及錯誤節（約頁面 L334–695）；未讀所有外鏈、SDK版本歷史、實際 API 結果，**非完整深讀**。
- API：GET /v1/views；至少提供 database_id 或 data_source_id；後者涵蓋工作區中連結至同一 data source 的 views。支援 start_cursor/page_size（上限100），回應含 results/has_more/next_cursor/request_status；需 read content capability；404 亦可能是無權存取。文件當時顯示版本 2026-03-11。

## 待驗反例／反證（非本所已發生問題）
1. 只以 database_id 查原始資料庫，漏掉其他行政頁的 linked views，錯判所有 Session 檢視均已盤點。
2. 第一頁剛好100筆便停止，未跟進 next_cursor，誤報 View 完整清冊。
3. has_more=true 但 next_cursor 缺失或循環，程式仍宣稱完整，而非標記不確定性。
4. 只按 View 名稱去重，把不同頁的同名「全部」View 合併，遺失篩選差異。
5. 將 404 當作 View 已刪除，忽略整合權限不足，導致重建重複 View 的錯誤建議。
6. 只拿到 view reference ID 就推定 filter/sort、權限及實際資料列均正確；應再查 View metadata/查詢結果，仍不能替代真人驗收。
7. 忽略 request_status 的異常或不完整標記，只用 HTTP 200 判定稽核成功。
8. 以 API 盤點清冊代替現場工作者的頁面可見性、操作便利性及資料存取權限測試。

## 計量與邊界
- 新來源候選：1；正式全域唯一來源：0（尚未完成語義去重）；本輪獨立針對性部分閱讀：1；完整 R1：0；R2–R10：0；新增反例：8；本輪完整10/10：0。
- 累積可核實10/10：沿用最近已稽核基準 **0／10,000**，未做全歷史重新計數。
- 本輪僅研究和 GitHub 新研究檔案，不改 Notion、資料庫、View、Formula、權限、GAS、Cloud Run、Session 或正式部署；不進入重新設計。
