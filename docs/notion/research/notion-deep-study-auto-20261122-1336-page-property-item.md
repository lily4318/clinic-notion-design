# AUTO-126｜2026-11-22 13:36 +08｜Retrieve a page property item

- 執行軌跡：AUTO-126-20261122T1336-GET-PROPERTY-ITEM；研究限定，沒有 Notion 寫入。
- 官方來源：https://developers.notion.com/reference/retrieve-a-page-property
- 標題：Retrieve a page property item；發行者：Notion Developers；取得日期：2026-11-22。
- 去重鍵：canonical URL `https://developers.notion.com/reference/retrieve-a-page-property`；主要來源清冊精確網址查找為 0，**未完成全歷史別名與研究檔去重，不正式認列全域新篇**。
- 閱讀證據：官方網頁取得 731 行，閱讀主要正文約 575–726 行及端點/回應示例；屬**部分針對性閱讀 1 次**，不符合完整深讀；10/10 完成數增加 0。
- 端點：GET /v1/pages/{page_id}/properties/{property_id}；property_id 可由頁面或 Data Source schema 取得，URL 編碼後使用。
- 官方區分：status/select/files/multi_select 等簡單屬性回傳單個 property_item；title/rich_text/people/relation 為可分頁清單；必須沿 next_cursor 到 has_more=false。Rollup 有計算 metadata，不能只用首頁判斷最終值。
- 權限：read content capability 不足可能 403；頁面/屬性不存在或頁面不可存取可能 404，不能直接當作已刪除。
- 研究反例（待測，不是已發生故障）：
  1. Session 與方案期別 Relation 超過首個回應頁，漏讀造成少計。
  2. 只看 Retrieve page 的縮略 Relation 而未讀 property endpoint，漏掉關聯。
  3. Rollup 在未讀完分頁前就記錄為最後統計值。
  4. 403 權限不足被誤當成無欄位。
  5. 404 被誤當作已刪除並觸發不必要的重建。
  6. URL 特殊字元的 property_id 未編碼導致查詢失敗。
  7. 將 rich_text/title 當單一 item，遺失後續片段。
  8. API 版本未固定，導致解析契約漂移。
- 對治療所的推論：未來唯讀稽核 Session、Price Plan、補助用量時，需保存分頁游標、讀取完成狀態、錯誤分類及欄位型別；本輪不做系統設計/修改。
- 計數：本輪候選 1、主要清冊精確 URL 新候選 1、全域去重確認新增 0、針對性部分閱讀 1、嚴格完整深讀 0、獨立 10/10 達標新增 0。最近可核實累積基準 0/10000，非全歷史重算。
- 未修改 Notion 頁面、資料庫、View、公式、權限、GAS、Cloud Run、Session。
