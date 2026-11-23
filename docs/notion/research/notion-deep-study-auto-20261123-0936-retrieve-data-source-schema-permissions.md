# AUTO-145｜2026-11-23 09:36｜Retrieve a data source：Schema 與關聯權限研究

- 軌跡：AUTO-145-20261123-0936-retrieve-datasource；只限研究與 GitHub 紀錄。
- 標題：Retrieve a data source｜Notion Developers
- Canonical URL：https://developers.notion.com/reference/retrieve-a-data-source
- 去重身份：canonical URL；相較 AUTO-144 的 query endpoint 是不同參考頁，但全歷史去重未完成，正式新增唯一篇數暫列0。
- 來源取證：2026-11-23 官方可讀正文（頁面約663行，核心敘述約560–605行），本輪針對性部分閱讀1次；不是完整十次深讀。

## 獨立核對結果

1. GET /v1/data_sources/{data_source_id} 取得資料來源的結構與 properties，而不是資料列。資料列須另用 Query a data source。不能以 Schema 回應 properties 空值推定 Session 0筆。
2. 先從 database ID 使用 Retrieve a database 的 data_sources 清單找正確 data_source_id；新版資料庫與資料來源 ID 不可混用。
3. 回傳受到 connection capabilities、資料來源及容器 database 權限影響；404 也可能是無存取權，不能直接當成來源不存在。
4. Relation 對應的另一資料庫若未分享給 integration，relation-based properties 可能不會出現在回應；這不證明原資料庫真的沒有該欄位。
5. Linked data source 不能透過此 API 直接取回，需授權原始 source database。UI 可見的 linked view 與 API 可讀權限不可等同。
6. 官方目前顯示 Notion-Version 2026-03-11；整合程式需明確固定並測試版本，不能以舊資料庫 API 假設新 schema 結構相同。

## 待驗反例（純研究推演）

1. 補助用量 Schema 有 Relation，但目標資料庫未分享，API 回傳缺欄而誤判 Relation 被刪。
2. 用 Database ID 呼叫 Data Source endpoint，404 後錯誤重建資料庫。
3. 管理員 UI 看見 linked view，API 無法讀取原始資料來源，錯誤推論空資料。
4. 只讀取 properties 而未 query rows，誤報心理師本週用量為0。
5. 同一 database 多個 data_sources，只取第一個，漏掉其他方案期別。
6. 權限變動後原本可見 Relation 欄消失，卻被視為 Schema migration。
7. 不同 API 版本下 response 形狀改變，既有 parser 靜默漏欄。
8. 404 被歸類為資料刪除，而未先核查 integration 分享權限。

## 計量與邊界

- 本輪候選官方可讀來源1篇；針對性部分閱讀1次；反例8項；嚴格完整深讀0次。
- 全歷史語義去重未完成：全域新增唯一來源暫認列0；累積可核實完成10/10篇數仍暫採0/10,000。
- 以上未在治療所真實 Notion Schema 或權限實測，不能當成已發生缺陷或驗收 PASS。
- 不修改 Notion、View、Formula、資料列、權限、正式 GAS／Cloud Run／Session。
