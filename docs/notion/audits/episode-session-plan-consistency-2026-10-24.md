# 2026-10-24｜服務歷程與會談方案對照：唯讀驗證

**工作線**：Notion TEST／唯讀資料驗證。**使用者前一回合已確認現有測試資料符合實際使用情境**；青壯資格人工確認後，直接於 Care Episodes「💲收費方案」選 Price Plan 的操作決策不變。本文件只驗證最新 Notion 結構與會談資料**關聯一致性**；不含病歷、姓名、會談頁 URL 或財務明細。

## 當次來源（2026-10-24）

- Care Episodes：`collection://6b68ca66-aa4d-8274-a691-07c605c5fb54`，原管理 ALL View `view://4bc8ca66-aa4d-82ec-894b-88a840ae6242`。
- Sessions：`collection://c2a8ca66-aa4d-82d2-bd6a-8772bb463796`，原管理 ALL View `view://1f08ca66-aa4d-83d1-a201-8864c13aa5de`。
- Price Plans：`collection://8b98ca66-aa4d-83b6-a9b0-8758b5f31f63`，政府方案工作台 View `view://3f68ca66-aa4d-81d6-a376-000ce4ea92a2`。
- 原生 [Notion TEST 設計與驗收紀錄](https://app.notion.com/p/4028ca66aa4d81298984ffd18b590a1d) 已追加本回合回歸測試結果，讀回恰一節。
- 在來源 Schema 讀回確認 Care Episodes `💲收費方案`、Sessions `💲 收費方案` → Price Plans；Sessions `👣 服務歷程` → Care Episodes，Care Episodes `💬 關聯會談` → Sessions。額度與計數皆已有 Formula／Rollup 依賴。

## View 唯讀查核與逐筆關聯彙總

用 Notion **既有** saved Views 分頁查詢：Care Episodes 57筆（1頁，has_more=false）、Sessions 295筆（3頁，最後 has_more=false）、政府啟用方案 1筆。沒有新增或修改 View，沒有依「青壯」「115」對共用業務規則硬編碼，只按當時啟用 Price Plan 實例辨識。

| 項目 | 讀回結果 | 判定 |
|---|---:|---|
| Care Episodes 有主收費方案 Relation | 57／57 | **PASS：關聯欄位存在** |
| Sessions 有服務歷程 Relation 且能對應現存 Episode | 295／295 | **PASS：關聯完整** |
| Sessions 有主收費方案 Relation | 295／295 | **PASS：非空** |
| Episodes 反向「💬 關聯會談」包含相應 Session | 295／295 | **PASS：反向關聯完整** |
| Session 主方案與所屬 Episode 主方案相同 | 287／295 | **PARTIAL：有 8 筆不同** |
| Session 與 Episode 主方案不同 | 8／295 | **待人工確認：不等於8筆錯誤** |
| 啟用青壯 Price Plan Session 反向關聯與直接選該方案 Session 集合 | 41／41完全一致 | **PASS：雙向集合一致** |

### 不一致的 8 筆，僅列匿名分類

| 類別 | 筆數 |
|---|---:|
| Session 選啟用青壯方案，Episode 選另一方案 | 4 |
| Episode 選啟用青壯方案，Session 選另一方案 | 4 |
| 其他方案彼此不一致 | 0 |
| 不一致 Session 的狀態 | 已完成4、已預約2、已改期2 |

**不可自動同步或修正這8筆**：可能是個別會談刻意採用其他收費方案，也可能是未同步的資料；需有業務語義、受控測試及使用者授權，才能判定真錯誤。不能將這些差異單憑條件刪掉，亦不影響已確認的「先在服務歷程選方案」操作原則。

### 啟用青壯方案 41 筆 Session 狀態

| 執行狀態 | Session數 |
|---|---:|
| 已完成 | 23 |
| 已預約 | 13 |
| 已取消 | 2 |
| 已改期 | 2 |
| no-show | 1 |
| **總計** | **41** |

其中37筆 Session、Episode 都選青壯，4筆為 Session 青壯／Episode 其他方案；相反方向另4筆 Episode 青壯／Session 其他方案。這是**關聯與狀態分類**，**不是政府額度最終占用數**。

## Notion 原生 Formula／Rollup 真值限制

- 啟用 Price Plan 的 `核定總額度_帶入`、`已完成_帶入`、`已預約_帶入`、`待確認_帶入` 皆返回 `rollupResult://` 指標。
- `已占用_自動`、`額度狀態_自動`、`剩餘額度_自動` 皆返回 `formulaResult://` 指標，**不是數值**。
- Sessions 的 `已完成計數_自動`、`已預約計數_自動`、`青壯115占用計數_自動`、`補助占用資格_自動` 在295筆 View 結果也只提供 `formulaResult://` 指標。
- 當次 SQL／rows 共用額度已耗盡；工具回傳說明重試會失敗。改用 View 讀取完成關聯比較，但**不能驗證每一筆原生 Formula 的數值與 Price Plan 實際餘額**。尤其不能用 23+13=36 推定現行額度占用36。
- `00.config_notion` 當次搜尋未精確定位；本回合唯讀 Schema/View 直接 Fetch 可核對，而**任何共用公式或關聯的修改**仍須先取得權威設定及先行批准。

## 影響範圍、保持不變、驗收與回復

- **本回合只有 Notion TEST 驗收歷史追加文字＋GitHub 文件更新**。沒有變更原57筆 Episodes、295筆 Sessions、Price Plans、Staff、補助參與或任何 Schema／Relation／Formula／View、權限、正式 GAS／Cloud Run／Session／部署；沒有增加青壯資格核對清單。
- **效能**：只做唯讀 View 查詢，未測量 UI 開啟時間，不聲稱效能改善；資料與權限保持不變。
- **已通過**：57／295/41 項關聯集合比較，以及所有頁面分頁完整性；匿名統計經程式雙向逐筆比對。
- **部分通過／待驗**：8筆差異的合理性、原生 Session 計數、Price Plan 已占用與剩餘額度、跨方案跨期公式、使用者角色權限及真人工作流程。
- **回復**：業務資料沒有寫入，無需資料回復。若要撤回驗收日誌或 GitHub 文件，先核對最新版本及並行修改，只撤銷當次記錄，不覆蓋其他人的進度。

## 下一個安全步驟

先對 8筆差異擬定「個別會談更換方案是否合理」的人工業務對照規則，不觸碰個資與既有資料；待原生 Formula 值可取得時，以當期已確認的實際 Price Plan ID、不同 Session 狀態及核定規則查核，必要 C級核心改動另取得核准。


## 2026-10-24｜青壯／自費 8 筆方案差異之情境分類回查（追加唯讀研究，非業務核准）

本回合重新 Fetch 即時 Care Episodes、Sessions、Price Plans Schema 和原 ALL Views，完整讀回57筆 Episodes、295筆 Sessions、當時1個啟用政府方案實例，重新做逐筆主收費方案 ID 比對。結果仍為 **287筆一致、8筆不同**；**8筆集中於4筆服務歷程，只涉及已啟用的青壯 Price Plan 與另外1個已啟用的「個別／自費」Price Plan**，並非8個彼此獨立的個案或8種不同計價方案。另個別服務類型均為「個別」，4個相關服務歷程皆標示進行中。

| 情境 | 不同主方案會談數 | 分布 |
|---|---:|---|
| Episode 青壯／Session 自費 | 4 | 1筆歷程有3筆（已預約、已完成、已改期各1），另1筆歷程有已完成1 |
| Episode 自費／Session 青壯 | 4 | 1筆歷程有3筆（已預約、已完成、已改期各1），另1筆歷程有已完成1 |

其中**1/8** Session 有附加收費方案 Relation，但其附加方案與歷程／會談的主方案差異不構成可直接判定的例外原因；在這8筆的 View 欄位中未取得備註或收據關聯可佐證每筆操作意圖。**對稱分布與使用者已確認測試情境符合使用狀況相容，但不能因此擅自確認「每筆切換都合法」**。應先明確定義：Episode「💲收費方案」是否是建立會談時的預設；何種情境可以讓 Session「💲 收費方案」與歷程不同；若允許，以何欄位及哪種可計入的執行狀態作實際補助額度歸屬。不得自動將8筆同化、刪除或斷開關聯。

**原生數值仍受限**：Price Plan 的已占用／剩餘等欄位回傳 `formulaResult://` 參照，直接以 Notion fetch 查詢該參照得到 validation error，尚未取得可以逐筆核對的原生數值，**不宣稱額度公式通過**。本回合只追加 [Notion TEST 設計與驗收歷史](https://app.notion.com/p/4028ca66aa4d81298984ffd18b590a1d) 文字並同步 GitHub，沒有寫入業務資料、Schema、Formula、Relation、View 或權限，沒有做效能量測。驗收文字若需回復，應先比對當時最新內容，只移除本次新增節，不動並行修改。


## 2026-10-24｜政府補助計數 Rollup 直接相依驗證（最新 Schema；只驗證直接依賴，未讀得公式數值）

本回合重新 Fetch 最新 Sessions／Price Plans／Care Episodes 的 Notion Data Source Schema，並用現有 Saved Views 唯讀回查目前啟用方案。與過去只比對 Session/Episode Price Plan ID 不同，本次進一步核實**實際 Rollup 來源**：

| 來源資料庫欄位 | Notion Rollup 聚合 | 關聯路徑 | 直接指向的計數欄位 | 驗證結果 |
|---|---|---|---|---|
| Price Plans「已完成_帶入」 | sum | Price Plans ↔ Sessions | Sessions「已完成計數_自動」 | Schema 結構 PASS |
| Price Plans「已預約_帶入」 | sum | Price Plans ↔ Sessions | Sessions「已預約計數_自動」 | Schema 結構 PASS |
| Price Plans「待確認_帶入」 | sum | Price Plans ↔ Sessions | Sessions「待確認計數_自動」 | Schema 結構 PASS |
| Care Episodes「本歷程已完成_帶入」 | sum | Care Episodes ↔ Sessions | Sessions「已完成計數_自動」 | Schema 結構 PASS |
| Care Episodes「本歷程已預約_帶入」 | sum | Care Episodes ↔ Sessions | Sessions「已預約計數_自動」 | Schema 結構 PASS |

這**直接證實** Price Plans 的三個 Session 計數 Rollup 不是從 Care Episodes 的「💲收費方案」欄位作直接 Rollup；但尚未得知 Sessions 的計數 Formula 是否另外檢查 Episode 收費方案，因此**不能據此推論 Session 欄位是唯一計次權威，亦不能直接按狀態自行加總**。

- **公式內容讀取失敗**：對 Sessions「已完成計數_自動」「已預約計數_自動」「補助占用資格_自動」及 Price Plans「已占用_自動」的 `formulaCode://` 參照逐一嘗試 Notion Fetch，均回傳 `INVALID_ARGUMENT validation_error`，不是有效的公式原始碼。
- **原生數值未提供**：啟用方案目前 Saved View 僅1筆；其三個 Session Rollup 為 `rollupResult://`，已占用及剩餘額度為 `formulaResult://`；會談原 View 計數亦為 `formulaResult://`，無可核對數字。無法對先前8筆青壯／自費切換情境驗證實際計次效果，也不得將歷史41筆方案會談或23完成／13預約逕行轉成額度占用。
- **保持不變**：使用者已確認測試資料符合使用情境，青壯資格人工確認後於 Care Episodes 選方案。8筆不同 Session 主方案的情境不自動同步、刪除或修復；既有 TEST 隔離關聯風險未因此消除。
- **本輪寫入**：僅在 [Notion TEST 驗收歷史](https://app.notion.com/p/4028ca66aa4d81298984ffd18b590a1d) 追加一段可回復說明並同步 GitHub。無業務資料、Schema、Formula、Relation、View、分享權限、GAS／Cloud Run／Session 改動，無可宣稱的效能變化或真人操作通過。驗收歷史若需撤回，先 Fetch 最新文字，只移除本段，保護他人並行更新。



## 2026-10-24｜原生公式數值驗收：替代唯讀入口與重試門檻

### 再讀結果（尚非數值 PASS）

- 重 Fetch 當前啟用 Price Plan 的**原生頁面**及 Data Source Schema：`已占用_自動`、`剩餘額度_自動`、`額度狀態_自動` 在原頁仍是 `formulaResult://` 參照；`已完成_帶入`、`已預約_帶入`、`核定總額度_帶入` 仍是 `rollupResult://` 參照，非可驗證的計算數字。Schema Formula 僅有 `formulaCode://` 與描述空白，沒有嵌入算式。
- 重試 Notion `query_data_sources(mode=rows)`：連接器明確回報 **SQL/rows 查詢的共享工作區配額耗盡，額度會在 60 分鐘內重置；即時重試沒有用**。這是暫時配額，而非工作區永久不支援。Saved View 唯讀模式仍可用，但其公式欄也只有結果參照。
- 查閱 [既有 Google Docs 青壯規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit) 及 2026-07-08 的歷史 `Step1_Notion_Sessions公式設定與測試_v56.md`；前者是操作與資料模型規格、後者主要為 Billing 收據及 Sessions 已開收據公式，**不能取代最新的政府補助 Session 計數算式或原生數值**。本回合未將舊公式冒充現行設定。
- `00.config_notion` 在目前 Notion 搜尋結果中仍沒有可驗證的精確入口；不能從其他含該字樣的 Google Docs 搜尋命中推定它就是權威設定。

### 下一次配額恢復後的**最小數值驗收協定**（計畫，尚未執行）

1. 重新 Fetch 已啟用方案、Care Episodes、Sessions 的當前 Schema／View 及目標頁，確認相關欄位、關聯 ID、Formula/rollup 類型及配額狀態未變。
2. 在連接器允許時，只對**必要且有既存存取權**的當期 Price Plan 頁以及現有8筆青壯↔自費差異 Sessions 嘗試唯讀 `rows`；優先核實讀回是否為**實際 number/boolean**，不是 `formulaResult://` 等不可解參照。若仍為參照，停止，改用已授權的原生 Notion UI／支持 page property item 的合法唯讀途徑；不得猜算、不得索取 Token 或繞過分享權限。
3. 需核對 Sessions 欄位：`👣 服務歷程`、`💲 收費方案`、`執行狀態`、`已完成計數_自動`、`已預約計數_自動`、`待確認計數_自動`、`補助占用資格_自動`，及只適用當期的 `青壯115占用計數_自動`。Care Episodes 的 `💲收費方案` 只用作比對；尚未核准以其值強制覆蓋單次 Session。
4. **既有案例，不新增個案或資格清單**：A（Episode 青壯／Session 青壯）、B（Episode 青壯／Session 自費；歷史4筆）、C（Episode 自費／Session 青壯；歷史4筆）、D（兩者自費）；橫跨已完成／已預約／已改期與可核實的取消、no-show 狀態。先讀原生數值與當期核定規則，再判定各案例計入哪個 Price Plan。**不預設 B/C 的有效計數結果**。
5. Price Plans 需查 `已完成_帶入`、`已預約_帶入`、`待確認_帶入`、`已占用_自動`、`剩餘額度_自動`、`核定總額度_帶入` 的原生數值，核對各期方案實例 ID、調整與排除狀態；用實際公式規則對照，**不得用 23＋13 或 41 筆直接推斷占用**。
6. 只有在 Formula 原始條件或可信原生結果可取得、案例可重現、套入結果與當期核定規則一致時，才標記 **NUMERIC PASS**。否則狀態持續 **BLOCKED／PENDING**。所有 TEST 參與與方案 Relation、業務 Session／Episode／Formula／Rollup／View 保持不變。任何 C 級變更先提出前後差異、依賴、權限及回復方案，另待使用者核可。

本回合僅有外部唯讀連接器調查及 GitHub 文件追加，**沒有任何 Notion／GAS／Google Docs 寫入**。無新增效能負荷或權限變更；若需撤回文件，須對照當前 GitHub main 和他人並行 Commit，再只還原本節。

## 2026-10-24｜再續作：295 筆會談完整 View 回歸及 41/41 雙向關聯

**工作線**：僅 Notion TEST／唯讀回歸，無臨床或財務原始列另存。

- **[LIVE SCHEMA PASS]** 重新讀取現有 Price Plans（30欄）、Sessions（67欄）、Care Episodes（50欄）Data Source 的指定 Relation／Rollup／Formula 型別；Price Plans 已完成、已預約、待確認三個 `sum` Rollup 仍直接關聯 Sessions 對應計數 Formula。公式內部條件仍無法從 `formulaCode://` 參照確知。
- **[COMPLETE VIEW PASS]** 原既有 ALL Saved Views 本輪完整查得 Care Episodes 57筆（1頁）、Sessions 295筆（3頁），政府方案 View 1筆（1頁），各最後 `has_more=false`。295/295 會談皆指向存在的歷程且反向關聯包含該會談，295/295 會談均有收費方案；287筆會談與歷程主方案一致，8筆不同，仍分布4個歷程、3/3/1/1；方向為歷程青壯／Session其他4、Session青壯／歷程其他4。這是**本輪重新完整查詢**，不是沿用舊數字。
- **[PLAN↔SESSION PASS]** 已啟用青壯 Price Plan 的「💬 關聯Sessions」有41筆，Sessions 側「💲 收費方案」實際選該方案的也有41筆；集合雙向完全相同（41/41），無遺漏或額外關聯；狀態已完成23、已預約13、已取消2、已改期2、no-show1。以上僅為**關聯與狀態分類**，不能推定實際占用次數。
- **[NUMERIC BLOCKED]** 嘗試合法的最小無篩選 `query_data_sources(mode=rows, limit=2)` 時，連接器明確回報目前工作區 SQL/rows 共用 allowance 用盡、60分鐘內重置；未取得原生 Formula 真值。帶公式精確數值篩選的候選格式在工具 schema 驗證即遭拒絕，未執行成功，不可把候選篩選視為已驗。既有 Price Plans View 的「已占用／剩餘額度」仍只有 `formulaResult://`，完成／預約 Rollup 仍只有 `rollupResult://`。原生數值、8筆差異是否占用、跨方案跨期與核定規則驗證繼續 PENDING。
- **[CONFIG / SAFETY]** Notion 名稱搜尋 `config_notion` 未精確定位 `00.config_notion`；用既有 live Schema 和 View 核對現況，並未依失效設定變更任何資料。此輪沒有改 Notion 業務列、Schema、Relation、Formula、View、角色權限、正式 GAS／Cloud Run／Session／部署；沒有 Google Docs 變更或效能實測。只有 GitHub 匿名驗收紀錄可單節撤回，撤回前應重查最新遠端版本保護並行更新。
- **[NEXT GATE]** 配額恢復後先用受支援的合法唯讀路徑取得 Sessions 原生計數真值與 Price Plan 公式／Rollup 數值；仍只返回結果指標則保持 BLOCKED，不以23＋13宣稱36；任何共享 Formula 或關聯修改另需C級設計核可。

## 2026-10-24｜再續作：SQL/rows 配額恢復，但公式值仍只能返回參照

**工作線**：Notion TEST，僅唯讀驗證既有資料；本次沒有重新執行295筆全量會談比較，該項仍引用前一節的已驗結果。

- **[QUERY QUOTA RESTORED]** 重新 Fetch 最新 Price Plans、Sessions、Care Episodes Schema 與政府方案 Saved View 後，對 Price Plans 執行最小 `query_data_sources(mode=rows, limit=1)`，已成功返回一筆，顯示先前的共享 SQL/rows 配額阻擋本次不再存在。不能再把「本次讀取失敗」歸因於配額。
- **[NATIVE METRICS BLOCKED]** 該筆 rows 的「已占用_自動」「剩餘額度_自動」仍為 `formulaResult://`，而「已完成_帶入」「已預約_帶入」「待確認_帶入」仍是 `rollupResult://`，**不是原生 number 值**；Price Plans Schema 亦將這些欄位列為 `notAvailableInQuerySql`。政府方案 View 同次重新查得1筆啟用青壯方案，`has_more=false`，仍只有公式／Rollup 參照。
- **[FILTER TOOL LIMIT CONFIRMED]** 普通 number property 的 `propertyType=number, operator=number_equals, value={type:exact,value:3}` 可通過受控 rows 唯讀查詢，checkbox filter 同樣可通過；但對「剩餘額度_自動」的多種 formula filter 候選，工具在執行前的參數 schema 檢查即拒絕，**本輪沒有成功對公式數值執行精確篩選**。先前歷史隔離方案0值篩選紀錄不等於本次成功重現，不能推斷本次啟用方案的任何精確占用／剩餘值。
- **[CONFIG / DOCUMENTS]** Notion 名稱搜尋 `config_notion` 與 Google Drive 精確檔名搜尋仍未確認 `00.config_notion` 權威設定。已唯讀讀回既有青壯 Google Docs 規格第十五節：人工核對資格後於 Care Episodes「💲收費方案」選擇 Price Plan，沒有改設計。
- **[NO WRITE / STATUS]** 沒有更動 Notion Price Plans／Sessions／Care Episodes／Staff／參與紀錄或任何 Schema、Formula、Relation、View、權限、Google Docs、正式 GAS／Cloud Run／Session／部署；沒有調整8筆方案差異，也未做真人角色、效能、跨方案核定規則驗收。**原生數值 NUMERIC BLOCKED；業務啟用驗收 PENDING**。僅追加本 GitHub 匿名紀錄，若要撤回需先確認並行 Commit，再單節還原。

## 2026-10-24｜115年啟用方案備註對照政府正式規則：四項差異

**工作線：Notion TEST／官方規則唯讀對照，未授權變更啟用方案；非公式錯誤判定。**

重新 Fetch Price Plans 最新 Schema、政府補助 Saved View（1筆已啟用、無後續頁）與該方案的**原始 Notion 頁面**，核對其「備註」欄位。該備註目前將「對象」描述為15至45歲國民、兩次間隔為 `>7天`、只寫三次總期程三個月、連續兩次無故未到描述為「將取消資格」。

與衛福部及臺北市政府衛生局的115年公開正式說明比對，發現：
1. **最短間隔邊界不一致**：官方以**不小於7天**為原則，Notion 用 `>7天`（若依一般比較語意會排除恰好7天）。需修正說明或查明是否在公式/人工流程也用錯邊界；**Formula尚未讀得，不指稱程式已錯**。
2. **最長間隔沒有寫全**：官方**兩次服務以不超過1個月為原則**，Notion備註僅列最短間隔與總期程三個月；是否有單次間隔的其他檢查尚未驗證。
3. **資格文字不完整**：衛福部115年公告包含15至45歲本國籍民眾**或持有健保卡的外籍人士**，Notion只稱國民；尚不能判斷實際治療所人工核對流程是否漏判。
4. **no-show 措辭過度確定**：官方是連續2次無故未到**機構得拒絕提供服務**，Notion描述為「將取消資格」；不得把官方的裁量語句擅自改為必然自動取消。

**正式來源**：[衛福部115年發布](https://www.mohw.gov.tw/cp-16-85046-1.html)、[臺北市政府衛生局115年公告](https://mental-health.gov.taipei/News_Content.aspx?n=FAB9374F6BCE2D48&s=1CAF0520811909A9&sms=EEA94C26A90DD864)、[我的E政府115年Q&A](https://www.gov.tw/News_Content_26_826198)。此比較只適用於**已核對的115青壯方案實例**，不能寫死於所有政府方案或期別；地方簽約附帶條件仍需以實際核定及契約為準。

**數值阻擋同時重驗**：原生 Price Plan 頁面「已占用_自動」「剩餘額度_自動」依然是 `formulaResult://`，核定總額度、完成與預約計數仍是 `rollupResult://`，無法用本次工具判定數值正確。未重新跑295會談全集；此前41/41與8筆差異保留前次回歸證據。

**處置**：列為 **RULE TEXT REVIEW REQUIRED／NUMERIC BLOCKED**。沒有擅自更動 Notion 業務記錄、備註、Formula、Relation、View、權限、Google Docs、正式GAS／Cloud Run／Session或部署；僅更新匿名 GitHub 驗收與來源。方案說明的B級小修正仍應先查核實際115核定補充，經使用者確認後再做原始頁備註最小修正，並重新讀回。任何共享 Formula 自動規則修改為C級，必須前後比對、備份及明確核准。
