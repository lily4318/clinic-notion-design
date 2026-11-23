# AUTO-162｜Page property item 分頁與 Rollup 完整性（部分閱讀）
- 執行標記：AUTO-162 / 2026-11-24 02:38 Asia/Taipei / 獨立自動研究
- 讀取時 main HEAD：492c85b2c71357284e046bc283665e09fc7ed97f
- 官方標題：Retrieve a page property item
- Canonical URL：https://developers.notion.com/reference/retrieve-a-page-property
- 去重身份：notion-dev-reference-retrieve-a-page-property
- 本輪讀取：官方正文第 575–590 行及參數/回應第 603–695 行；針對性部分閱讀一次，**不是完整深讀**；嚴格完整 0/10。
- 來源去重：核對 docs/notion/sources.md、research/README.md、evidence-register、audit-checklist 與研究目錄；尚未完成全歷史逐檔 URL 掃描，故新增正式唯一來源 **0（待全域去重）**。
- 權限：純研究，不操作 Notion 內容、Schema、View、GAS 或部署。

## 已核對的 API 契約
1. GET /v1/pages/{page_id}/properties/{property_id} 依屬性類型回傳單一 property_item 或分頁清單；屬性 ID 應由 Retrieve a page / Retrieve a data source 取得，URL 編碼 ID 依原值傳送。
2. status、select、files、multi_select 等通常回傳單一項；title、rich_text、people、relation 回傳分頁清單。應逐頁依 has_more/next_cursor 讀取，不能以首批內容作完整性判斷。
3. Rollup 可能以包含計算中繼資料的清單回傳，必須讀完各頁才可使用最終計算值。
4. 需要 read content capability；403 可表示能力不足，404 可表示頁面或屬性不存在，亦可能是缺少頁面存取權。不能單憑 404 宣告資料已刪除。
5. 本輪只閱讀官方參考頁主要說明及參數，未獨立完整閱讀所連結的所有 response shape、pagination、rollup 子文件；不能將其視為同篇的十次深讀。

## 八個待驗反例（推論，非治療所已發生）
1. Session 關聯超過單頁時僅取第一頁，低估個案方案用量。
2. Relation 首頁數量小於 page_size 便推斷結束，忽略 has_more。
3. Rollup 未完成分頁即把中間計算結果當最終餘額。
4. rich_text 分頁截斷，遺漏重要行政備註後段。
5. People 屬性首批人員不完整，誤判負責心理師未指派。
6. 將 404 一律視為資料被刪除，忽略 integration 未被分享頁面的情況。
7. 以過期屬性名稱而非最新 ID 查詢，將識別問題誤當資料不存在。
8. 以 Page retrieve 回傳的部分 Relation 誤當完整，再推導跨方案計數通過。

## 對治療所的研究意義
未來只讀核對 Session / Price Plan / Care Episode / 用量時，需保留逐屬性分頁完整性、rollup 結束狀態、權限與識別碼的證據；本輪沒有實際查詢本所資料，亦不代表任何 Formula 或補助資格驗收 PASS。

## 本輪計量
- 可讀官方候選來源 1；正式新增唯一來源 0（全域去重待核）
- 針對性部分閱讀 1；嚴格完整深讀 0；新增待驗反例 8
- 累積可核實完成 10/10：保守 0 / 10,000 篇
