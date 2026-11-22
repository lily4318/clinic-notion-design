# AUTO-139｜Notion Formula 空值與零值的反例稽核（2026-11-23 03:43 Asia/Taipei）

- 執行軌跡：AUTO-139-20261123-0343-formula-empty-zero；範圍：純官方文件研究與GitHub紀錄；沒有操作Notion或部署。
- 官方原文：**Formula syntax & functions** https://www.notion.com/help/formula-syntax
- canonical URL：https://www.notion.com/help/formula-syntax（不帶參數）；語言：英文；來源：Notion Help；本輪直接讀取官方頁面正文（頁面包含 Properties、Built-ins、Functions 三節與函式表）。
- 去重：初始16篇證據清冊未列此精確網址；尚未對所有歷史研究檔進行完整語義去重，**不認列全域新增唯一來源**。
- 閱讀深度：獨立針對性部分閱讀（非完整深讀、非10/10之一）。核對 properties、empty、if/ifs、dateBetween、list filter/map、id、let/lets；其餘函式未逐一驗證，故不冒稱全文精讀。

## 官方可驗證要點

1. `empty(0)` 為 true，`empty("")`、`empty([])` 也為 true。這意味著把 `empty(number)` 當「沒有輸入」會混淆已確認的0與缺失。
2. Relation 在公式中是 Page list，支援 `length`、`filter`；Rollup 的公式型別依設定可為 number、date 或 list，不應假定恆為 number。
3. `ifs` 選第一個成立條件；`dateBetween` 參數方向會影響正負；`id(page)` 可取得頁面ID，但本身不構成資料庫唯一約束。
4. `filter`、`map`、`unique` 支援列表運算；不能由公式運算結果推論已阻止重複 Session 寫入。

## 獨立反例（待驗假說，非系統已發現缺陷）

- R1：心理師明確填0次他處接案，`empty(0)` 被當作未回報。
- R2：個案確認補助使用0次，系統把0與未查核合併。
- R3：Relation空清單與權限不足造成的未取得關聯，在UI都顯示0。
- R4：Rollup改為清單後，沿用數字算式導致型別錯誤。
- R5：`dateBetween(first,last,"days")` 方向寫反，期限判斷顛倒。
- R6：同案同方案期別存在兩筆用量列，公式合計仍看似合理，掩蓋重複資料。
- R7：跨方案期別 Session 關聯未先依Price Plan ID過濾，數值錯期。
- R8：取消、改期與no-show混用狀態篩選，造成有效占用計次偏差。

## 可採用的測試設計（僅研究，不實作）

建立合成測試矩陣：未知/未填、已確認0、正整數、重複關聯、跨期、取消、反向日期、rollup型別變動；核對實際 Notion 公式回傳值及真人視圖，不以離線推算當 PASS。涉及敏感資料不可複製到GitHub。

## 計量與限制

- 本輪：候選來源1、部分閱讀1、嚴格完整深讀0、已驗證10/10來源0、新增反例8。
- 全域新增唯一來源：0（尚未完成全歷史語義去重）。累積10/10沿用保守基準0/10000，不是全歷史完成稽核結論。
- 研究結論不可當作正式系統已存在缺陷；未修改 Notion Schema、View、Formula、權限、GAS、Cloud Run、Session。
