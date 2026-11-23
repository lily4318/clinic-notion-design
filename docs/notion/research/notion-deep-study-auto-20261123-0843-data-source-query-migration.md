# AUTO-144｜2026-11-23 08:43｜Notion Data Source 查詢 API 版本遷移研究

- 執行軌跡：AUTO-144-20261123-0843-datasource-query；僅研究，禁止任何 Notion 或正式系統寫入。
- 官方來源 A：Query a data source｜https://developers.notion.com/reference/query-a-data-source
- 官方來源 B（版本對照）：Post database query（deprecated）｜https://developers.notion.com/reference/post-database-query
- 去重鍵：canonical URL；A/B 各為獨立 API 參考頁，但尚未完成全歷史語義去重，正式新增唯一篇數暫計 0。
- 閱讀層級：A 針對 endpoint、請求、response、error schema 的獨立部分閱讀 1 次；B 針對 deprecation、分頁、Relation/Formula 限制部分閱讀 1 次；兩者均非逐篇全文完整深讀，10/10 計數不增加。

## 來源核對

1. 舊版 POST /v1/databases/{database_id}/query 官方標記於 Notion-Version 2025-09-03 起 deprecated；新版改為 POST /v1/data_sources/{data_source_id}/query。不可將 database_id 當成 data_source_id 直接代入。新版 SDK 使用 notion.dataSources.query。
2. 新版請求可提供 filter、sorts、start_cursor、page_size、is_archived；回應具有 results、next_cursor、has_more，以及 request_status 等狀態。不能以第一頁數量或單次 HTTP 200 推定查詢全集已完整。
3. 新版文件列出 406 row_limit_exceeded、409 conflict_error、429 rate_limited、503 service_unavailable 等錯誤範例；不能一律視為空資料或業務0次。
4. 舊版明確警告 Relation 超過25筆可能使依賴它的 Formula 評估不完整，多層 Relation/Rollup 亦可能不準確。此為舊版頁面所述限制；新版是否仍完全相同須另行查核，不擅自外推。

## 反例假說（非實測）

1. GAS/匯出程式升版後仍使用舊 database query 路徑，產生 404 或非預期錯誤。
2. 將 database_id 誤作 data_source_id，導致漏查方案用量。
3. 單次查詢成功但 has_more=true，後續頁面未取回，導致少計 Session。
4. request_status 表示結果受限時，仍把 results 當完整全集。
5. 406 row_limit_exceeded 被當成「無方案用量」。
6. 429 或 503 後未記錄查詢不完整，卻將缺失當成0。
7. 多層 Relation/Rollup 計算與直接逐筆查詢不一致，沒有差異警示。
8. 升版後只驗證舊資料庫查詢，未驗證多 Data Source、不同方案期別的隔離。

## 計量與邊界

- 本輪可讀官方頁 2、針對性部分閱讀 2、待驗反例 8；完整深讀 0、全域唯一新增 0（待全歷史去重）。
- 累積可核實達成 10/10 篇數仍暫採 0/10,000；未完成全歷史清冊稽核。
- 不修改 Notion、資料庫、View、Formula、權限、GAS、Cloud Run、Session；無任何業務驗收 PASS。
