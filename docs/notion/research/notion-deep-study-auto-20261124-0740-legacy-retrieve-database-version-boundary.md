# AUTO-167｜舊版 Retrieve a database 的版本邊界（2026-11-24 07:40 Asia/Taipei）

- 執行軌跡：AUTO-167-legacy-db-0740；僅研究，未操作 Notion、GAS、Cloud Run、Session。
- 來源：Notion Developers，Retrieve a database（Databases deprecated）
- canonical URL：https://developers.notion.com/reference/retrieve-a-database
- 去重 ID：notion-dev:reference/retrieve-a-database；與新版本同名 endpoint 文件需依 URL 和版本分開辨識；全歷史正文跨檔 URL 去重未完成，**不計新增唯一來源**。
- 查閱日期：2026-11-24；官方頁面當次可讀，針對性部分閱讀 1 次，非完整深讀，非 10/10。
- GitHub 起始 main：9f28a0948df392f05d0edd484c89cee044bc2011；本輪以新獨立檔避免覆寫並行研究。

## 來源直接可核實

1. 此頁明確標示 deprecated as of 2025-09-03，描述截至 2022-06-28 的舊 API 契約；新版將 database 容器與 data source 拆開，應分別閱讀新版 Retrieve a database 和 Retrieve a data source。
2. 舊版 GET /v1/databases/{database_id} 主要取得結構與欄位，而非資料列；列資料須另查 query API。舊版文中 API 404 亦可能表示 connection 無存取權。
3. 相關資料庫未分享給 connection 時，relation-based properties 可能不在回應；linked database 不支援直接透過此端點擷取，須分享原始來源。
4. 本文件提供舊版與新版文件導航，**不能因相同 endpoint path 就假定 response schema 跨版本不變**。

## 本系統推導與反例（未實測）

- 反例 A：以舊版 properties 結構解析新版 database 回應，誤判 Price Plans 欄位消失；須依 Notion-Version 與 data source ID 查驗。
- 反例 B：只驗證 database 容器存在，就把 Sessions 資料列及 Relation 視為完整；須另查 data source schema、資料列分頁與權限。
- 反例 C：linked view 能顯示資料，但 connection 無原始來源權限，404 被誤判刪除。
- 反例 D：Relation 欄位因目標未分享而消失，誤認方案／個案關聯已被清除。
- 反例 E：舊版 SDK 範例與新版 header 混用，造成非預期資料形狀。
- 反例 F：將舊版文件標示的錯誤碼清單直接推定正式系統已測過所有失敗路徑。

## 計數及限制

- 本輪：可讀官方來源 1、針對性部分閱讀 1、反例 6、完整深讀 0、正式唯一新增 0（歷史全文去重待完成）。
- 累積可核實完成 10/10：保守 0 / 10,000；不因本輪改變。
- 未修改共享清冊；沒有進行真人 UX、Notion API、實際 Schema、權限或公式測試；研究推導不可當作驗收 PASS。
