# 2026-10-24｜青壯115舊計算欄位永久刪除｜相依性與安全門檻

**工作線**：Notion TEST，僅核對現行Schema及Saved View，**未執行DROP或更動任何原資料**。使用者要求刪除所有與截圖三個舊Σ公式相應且真正不再需要的依賴，不能擴大誤刪仍運作的青壯方案屬性。

## 現行原生來源

- Care Episodes：`collection://6b68ca66-aa4d-8274-a691-07c605c5fb54`，50屬性，原生`<page-layout>`可讀。
- Cases：`collection://87f8ca66-aa4d-824d-8854-87355509dca8`，49屬性，原生`<page-layout>`可讀。
- Sessions：`collection://c2a8ca66-aa4d-82d2-bd6a-8772bb463796`，67屬性；其他青壯115計算仍在工作中，不得類推刪除。

## 已證明的欄位引用：三組六欄

| Care Episodes（來源Formula） | 對應 Cases Rollup（SUM） | 關聯來源 |
|---|---|---|
| `青壯115他處使用數_自動`，ID `V3dWRw` | `青壯115他處已使用_自動` | Cases `👣 關聯服務歷程` |
| `青壯115他處回報有效_自動`，ID `UGhgdQ` | `青壯115他處確認筆數_自動` | Cases `👣 關聯服務歷程` |
| `青壯115方案歷程標記_自動`，ID `Wj1cQw` | `青壯115關聯歷程數_自動` | Cases `👣 關聯服務歷程` |

以上依Cases三個Rollup的`targetPropertyUrl`和EP三個Formula的`formulaCode://` property ID一一核對。當前這是**直接證據**，不是猜想。

## 本輪新增原生 View 級證據

1. [Care Episodes原始資料庫](https://app.notion.com/p/dbc8ca66aa4d8214a7d201f5f61aa9cb)，預設`view://2d38ca66-aa4d-8371-a9f1-88a498b2641b`：**SHOW三個EP來源Formula**。
2. [Cases原始資料庫](https://app.notion.com/p/a168ca66aa4d829286ca012c54541256)，預設`view://4138ca66-aa4d-8353-96ae-8846778f41fd`：**SHOW七個帶「青壯115」字首的欄位**，其中三個是對應Rollup，另包括`青壯115他處顯示_自動`與`青壯115額度狀態_自動`。
3. Cases測試View `view://4028ca66-aa4d-8189-8a07-000cb0dac95c`，名稱`[TEST] 青壯115跨歷程占用驗證`：將`青壯115額度狀態_自動`用作**Formula Filter**，SHOW`青壯115本所占用_自動`。即使是TEST View也不保證資料隔離或無依賴，可在有可回復的完整基準後單獨決定是否撤銷。

兩份Data Source原生Page Layout都含上述舊欄位，清理不能漏掉顯示配置，也不能覆寫無關頁面版面。

## 尚未排除、因此必須停下的間接依賴

- Cases `青壯115他處顯示_自動` `formulaCode://.../UT55fA`及`青壯115額度狀態_自動` `formulaCode://.../R0d3YA`完整`formula.expression`皆未由Notion連接器取得。直接Fetch這兩個formulaCode均回`INVALID_ARGUMENT validation_error`。尚不確定是否還有其他Cases Formula／View／Button引用它們。
- Google Docs設計備份只可證歷史決策，不能等同最新完整Formula回復版本。Notion屬性DROP後按同名重建不保證保留property ID或現有關聯。
- **硬停止**：未先拿到原始Formulas、完整下游依賴閉包、Schema與Page Layout可回復基準、隔離TEST回歸證據，不執行`DROP COLUMN`，不先拆掉三個Rollup；不誤傷青壯補助額度、其他方案／期別與原UX。

## 檢查清單（尚未PASS，按序）

- [x] 核對現行兩資料源屬性個數與三組直接SUM Rollup關係。
- [x] 核對目前三個受影響原生Saved Views的SHOW／Filter。
- [x] 核對兩Data Source原生Page Layout含待清欄位。
- [ ] 取得Cases兩個下游Formula當前完整expression並追完其他間接依賴。
- [ ] 備份所有受影響來源Formula全文、頁面原生Layout、View篩選與屬性ID；確認DROP後可恢復的技術路徑。
- [ ] 在真正隔離、不指向啟用業務資料的Notion TEST演練依賴遷移及刪除。
- [ ] 檢查不同Price Plan實例、Cases／Care Episodes／Sessions及警示View結果並做人工驗收。
- [ ] 僅在所有門檻通過後，執行最小正式刪除與寫後逐項回查。

沒有變更Notion的50/49/67個原屬性、任何業務資料、View、公式、按鈕、版面、角色權限或部署。原政府補助工作台UX v4.2之4/4人工PASS保持。額外效能負載=無。此輪無Notion刪除，因此無Notion回復需求。新驗證同步Google Docs [規格第31節](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)及[修改前備份](https://docs.google.com/document/d/1EoOGkZ0WuX26u0KCKqVbqdhq-jCNrBuxD36pXs6_8M8/edit)。
