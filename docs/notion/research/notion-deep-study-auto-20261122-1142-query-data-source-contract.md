# AUTO-124｜2026-11-22 11:42｜Query a data source 契約針對性閱讀

- 來源標題：Query a data source｜Notion Docs
- Canonical URL：https://developers.notion.com/reference/query-a-data-source
- 去重身份：notion-developers:reference/query-a-data-source；主要 sources.md 精確URL檢查未命中；全歷史語義去重未完成，僅列候選，不正式認列新篇。
- 讀取：2026-11-22 本輪取得可讀官方正文（網頁約1322行），核讀 API 端點、request/response、overview 及錯誤範例；**部分針對性閱讀1次，非完整深讀，非10次之一**。
- 證據：官方頁面第 445–468 行端點 POST /v1/data_sources/{data_source_id}/query；第 806–810 行 Overview 指明可能少於 page_size、游標須依 pagination 處理，wiki 回傳資料來源型態；第 310–356 行範例含 has_more、next_cursor、request_status；第 359–444 行列錯誤碼。

## 反例與反證假說（非已驗證治療所缺陷）

1. 以回傳筆數少於 page_size 判定查詢完成，漏掉下一頁；需以游標判定。
2. 將 Database ID 誤傳為 Data Source ID，造成查詢失敗或錯誤來源；先查實際 schema/ID。
3. 將 wiki 查詢回傳的 data_source 當成一般 page，造成資料遺漏；需辨識 object type。
4. 只檢查 has_more 而忽略 request_status 的 incomplete 訊號，誤認完整備份；須交叉核對大型資料查詢指南。
5. 只依第一頁統計方案用量，導致補助剩餘額失真；需遍歷並依 page ID 去重。
6. 404 直接當成已刪除，未核對連線權限與 data source 身份；需另查授權。
7. 429/503 後無節制重試造成共享額度壓力；應採錯誤類型處理。
8. 將 API 範例中 is_archived:true 當成所有正式查詢的預設條件；需明確定義查詢範圍。

## 計數與界線

本輪：候選來源1、完整深讀0、獨立部分閱讀1、反例8、10/10達標新增0。累積可核實10/10維持最近基準0/10000（全歷史稽核未完成）。此記錄僅供研究，不授權 Notion 或 GAS/Cloud Run/Session 寫入。

研究軌跡：AUTO-124-20261122-1142-query-data-source-contract。避免與 AUTO-123 大型查詢指南重複計算，兩者 canonical URL 不同但研究主題相關。
