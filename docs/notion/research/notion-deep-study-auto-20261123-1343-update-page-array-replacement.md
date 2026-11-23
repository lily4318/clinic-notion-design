# AUTO-149｜Update page 陣列覆寫與局部更新安全研究

- 日期：2026-11-23 13:43 Asia/Taipei
- 執行標記：AUTO-149 / update-page-array-replacement / independent-partial-01
- 來源：Notion Developers — Update page
- canonical URL：https://developers.notion.com/reference/patch-page
- 來源身分：官方 API reference；全歷史唯一來源尚未完整去重，暫不認列新增唯一篇數
- 閱讀證據：本輪取得官方網頁正文約1121行，重點檢視 API 用途、PATCH 範例、狀態碼、Use cases 與 Updating properties 段落；屬一次獨立針對性**部分閱讀**，不是完整深讀10次之一。

## 可核對的來源事實

1. PATCH /v1/pages/{page_id} 可更新頁面屬性、icon、cover 等；不是新增 Session 的 API。
2. 更新 data source 子頁的 properties 時，欄位名稱或 ID 必須符合父 data source schema；非 data source 頁面一般只允許更新 title。
3. 未列在 PATCH 的屬性會維持原值，但**陣列型屬性以提交的整個陣列取代原陣列**，不是自動合併。
4. 文件列有 409 conflict、429 rate_limited、503 service_unavailable、504 gateway_timeout 等狀態；成功回應不等於相關統計與下游業務核對已完成。

## 治療所情境反例（待驗，非實際缺陷）

1. 管理者同時在 Relation 加入新 Session，另一流程依舊快照 PATCH 關聯陣列，將新 Session 關聯抹除。
2. 方案期別關聯原含兩項，PATCH 只提交一項，誤以為是追加而實際覆寫。
3. 以欄位顯示名稱更新，但 schema 已改名，失敗後將錯誤誤判為無資料。
4. 多選欄位僅送新選項，覆蓋原有標記，造成資格狀態誤判。
5. PATCH 成功但 Rollup/Formula 尚未重新核實，就將補助額度標為通過。
6. 503/504 後不先讀回遠端狀態就再次 PATCH，造成覆蓋其他人較新修改。
7. 將未列欄位維持不變錯誤推廣到「列出部分 Relation 成員也不會刪舊成員」。
8. 以非 data source 一般頁面當成資料列寫入完整 properties，忽略父層限制。

## 研究結論與界線

後續設計若涉及關聯陣列更新，必須先取得最新完整值、確認期別與權限、比對並行修改並在寫後讀回；不能以 PATCH 作為自動追加關聯的保證。本輪未連接或修改任何 Notion 資料。

## 嚴格計數

- 本輪可讀官方來源：1篇；部分針對性閱讀：1次；新增反例：8項。
- 本輪完整深讀：0次；新增經全歷史驗證唯一來源：0篇；完成10/10：0篇。
- 累積10/10暫採保守0/10,000，須全歷史清冊逐篇稽核後方能更新。
- 與前輪 AUTO-148 大型查詢上限為不同 canonical URL 和不同研究主題；不得將同次閱讀拆算多次。

## 安全

僅研究紀錄，不更動 Notion Schema、頁面、View、公式、權限、GAS、Cloud Run 或 Session；不包含真實個案資料。
