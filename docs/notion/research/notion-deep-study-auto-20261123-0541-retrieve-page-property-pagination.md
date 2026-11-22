# AUTO-141｜Retrieve a page property item：分頁與權限反例研究

- 執行軌跡：AUTO-141 / 2026-11-23 05:41 Asia/Taipei / 唯讀研究
- 來源標題：Retrieve a page property item — Notion Docs
- Canonical URL：https://developers.notion.com/reference/retrieve-a-page-property
- 去重身份：notion-developers:reference/retrieve-a-page-property（與 property-item-object 不同端點說明，但內容相關；全歷史語義去重未完成）
- 取證：2026-11-23 直接讀取官方網頁正文（本次取得 731 行頁面，其中大量為範例及介面重複；重點正文在 575–590 行）。
- 閱讀等級：獨立針對性**部分閱讀** 1 次；不認列完整深度閱讀、不認列 10/10。

## 官方正文可核對的行為

1. GET /v1/pages/{page_id}/properties/{property_id} 依欄位類型回傳單一 property_item 或分頁 list；property_id 可取自 Retrieve a page 或 Retrieve a data source，URL 編碼 ID 應照 API 回傳處理。
2. status/select/files/multi_select 等一般為單一 item；title、rich_text、people、relation 可能是分頁清單，應循 next_cursor 直到 has_more=false。
3. Rollup 回傳含 property_item.rollup 的計算 metadata；計算結果不可在未讀完分頁時視為完成。
4. 讀取內容能力不足可回 403；404 同時可能是頁面／欄位不存在或無頁面存取權，不能單憑 404 判定資料已刪。
5. API 文件列有 429、409、500、503 等失敗回應；本輪未對治療所真實 API 發送任何請求。

## 對治療所模型的反例假說（未實測）

- R1：Session Relation 超過單頁時，只取第一頁使有效會談低估。
- R2：Care Episode 的 rich_text／people 被截斷後，人工核對者資訊不全。
- R3：Rollup 未完成分頁就將中間數字寫入方案餘額摘要。
- R4：API 404 被誤當用量紀錄已刪，實際可能是分享／權限缺失。
- R5：403 被誤當無資料，進而錯誤地將未知轉為 0。
- R6：欄位改名後以名稱定位失敗，誤將舊欄位當不存在；應核對穩定 property ID。
- R7：同一 Session 關聯在多頁分頁回應被錯誤合併或重複計數；應依關聯 page ID 去重並核對原始筆數。
- R8：讀取遇 429／503 時僅保留部分結果，仍被標為完整盤點。

## 計量與界線

本次：來源候選 1、針對性部分閱讀 1、反例假說 8、嚴格完整深讀 0。全歷史去重未核完，正式新增唯一來源認列 0。全庫 10/10 完成篇數仍採先前保守可核實基準 0／10,000，非重新全庫盤點。這些反例不是實際缺陷或已通過驗收；只記錄研究，不修改 Notion／GAS／Cloud Run／Session。
