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

## 2026-10-24｜Notion TEST安全續作：清除已通過工作台的過時備份入口，滿額提醒13/13離線測試
- **[ACTUAL UX CLEANUP]** 已重新Fetch使用者UX v4.2四項已驗收PASS的[Notion TEST補助工作台](https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f)，以精確單次`update_content`**真的移除**原收合區的`[UX v4 原生備份]`舊連結；回Fetch確認連結消失，原6個Linked DB、2個Toggle、上方異常／最後一次已預約提醒與3類額度表全部保留。備份頁本體暫作回復參照，尚未刪除此備份頁；不把移除入口冒稱備份頁刪除。
- **[LIVE BASELINE / BLOCKERS]** 重新Fetch Notion原Schema：Care Episodes50、Cases49、Sessions67、Price Plans30、Staff58欄；原`未預約下次會談`Saved View仍只以狀態＋未安排判斷。三組Care Episodes青壯115原Formula→Cases SUM Rollup的舊依賴與兩段Cases下游Formula的`formulaCode://`不完整問題仍在；`青壯轉自費`只有button型別無action。依使用者核准的硬停止，不執行任何`DROP COLUMN`、不覆寫共享Formula或Button、不改原業務資料。
- **[OFF-SYSTEM REGRESSION]** 按實際Price Plan方案實例的每案上限（非寫死115／3次）擬定互斥的`轉自費或結案`、`額外預約核對`、`待確認他處`、`維持預約提醒`與`自費原流程`決策；已執行13組匿名離線JavaScript分支案例，13/13PASS，涵蓋最後一次**僅已預約未完成**不可誤當滿額、完成3有下次預約、他處已確認0與未知、跨方案上限5次等。**不是Notion原生Formula或有效能／跨期驗收**，功能仍NOT LIVE。
- **[IMPACT/ROLLBACK]** 本輪唯一Notion寫入是移除一個過時連結，無新增欄位、公式、資料庫、查詢負擔及權限影響；回復只在重讀現行頁後將舊連結`[UX v4 原生備份](https://app.notion.com/p/4038ca66aa4d8159b4e5daf90a4ae662)`精準加回，保留其他並行修改，沒有任何業務資料回復。必要公式原文／按鈕動作完整基準仍未取得，永久刪除六欄與滿額提醒上線保持BLOCKED，免週報自動邏輯亦尚未啟用。
- **[DOCS READBACK]** [Google Docs青壯方案額度與UX規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)以revision guard新增第33節，回讀原32與新33共存；[修改前原生Google Docs備份](https://docs.google.com/document/d/1aPF1fXhnuuXWXDEayUkjOuknCxElb3G-EUXau6LbHeA/edit)不含第33節。
