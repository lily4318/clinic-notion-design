# 青壯與通用補助｜Notion TEST 驗收

歷史快照截至 2026-10-24（台灣時間），不是即時統計。這些結論源自既有 Notion 驗收紀錄與 Google Docs，**不代表本次 GitHub 建檔時重新執行了全部業務測試**。

| 項目 | 歷史驗收結果與限制 |
|---|---|
| 年度參與清單 | 115遷移22筆＋1筆獨立隔離TEST。遷移22筆中21待核對、1不符合；03／05檢視曾涵蓋22筆。清單完整性唯讀通過，不等於資格通過。 |
| 115年度會談基準 | 關聯 Sessions 41筆：已完成23、已預約13、已取消2、已改期2、no-show1；一般有效占用候選36筆。必須按實際日期與收費來源重新核對。 |
| 逾期已預約 | 查核時13筆已預約中12筆的預約日期已過；須待行政核對，不擅改完成或取消。 |
| 參與記錄對 Sessions | 22筆遷移參與的「本方案會談」Relation 當時全部空白；不能直接用既有總數當成新年度表 Formula 真值。 |
| 首談與期限 | 遷移22筆的使用期限屆滿日當時全部空白；不可用開案日替代真實第一次補助服務日。 |
| Session / Care Episode 收費方案 | 41筆中發現4筆關聯不一致；其中3筆狀態可能影響有效占用。涉及真實收費／申報須人工核實，不改原資料。 |
| 週回報 | 兩位非隔離心理師10/18～10/24週報均未確認；次週10/25～10/31均無有效本週回報；缺漏辨識通過，不代表 UI 明確警告及拒絕行為驗收完成。 |
| v2 週末分界 | 隔離週六／週日計數及部分重複週報案例曾通過，尚不可推廣所有方案與年度。 |
| 機構正餘額 +1 | Notion 原生剩餘額 Formula 真值與文案仍未驗收。先前只確認隔離調整的原始算術結果；已恢復試驗值與 View。 |
| 通用跨方案／跨年度 | 同年兩方案、同年兩期、跨年新規則隔離等還沒有完整隔離實測。 |
| UX 與資料庫研究 | 10,000篇實讀研究尚未完成；不能用範本庫總量代替閱讀量。 |

## 高優先安全注意事項

- 曾有三筆標示 [TEST] 的跨歷程 Sessions 仍連到啟用中的115 Price Plan，雖狀態不占用，**不可直接將它們改成已預約／已完成來測試額度**。
- 有一筆已由管理者確認首次使用年齡不符合115條件的歷史個案，原 Care Episode 關聯仍待按收費／申報影響核對；GitHub 不存個案真實身分。
- 新版01／02分類部分依賴管理分類及不完整條件；零筆且不錯誤放行的顯示不代表自動分類計算已經準確。
- 連接器無法取得 Notion 原生 Formula 真值時，不以原始欄位算術或被忽略的公式 View 篩選推定 PASS。

## 建議接續順序（Notion only）

1. 先重讀最新實際 Schema／View／驗收日誌，核對所有歷史問題是否仍存在，保持既有業務資料不變。
2. 唯讀交叉核對當期 Price Plan、Sessions、參與 Relation、過期已預約及歷程不一致，先訂出需人工釐清清單；不得批量自動修正臨床資料。
3. 建立真正不連到任何啟用方案的可回復 TEST 情境，驗證多方案、多期別、未知／不適用與週限額。
4. 只有取得 Notion 公式真實值、有效且完整的關聯與當期官方規則，才標記相應狀態 PASS。
5. 同步更新本文件的測試日期、輸入、預期／實際、保留／回復證據與 GitHub 決策日誌。


## 2026-10-24｜首屏提示最小修正｜實作與回讀 PASS（Notion TEST）

- **問題與目標**：青壯 TEST 工作台原無醒目的「待核對／不可憑本頁核准補助」提示，容易誤解額度數字。採用局部 B 級最小修正，不做整體 UX 重設。
- **實際修改**：僅在「補助方案管理｜TEST」頁面青壯年度額度標題下新增一個黃色 ⚠️ Callout，要求先核對方案實例／年度期別、個案待核對清單、心理師當週回報、首談與期限，並明說 Linked View **沒有全域同步方案／期別切換**。
- **讀回通過**：Callout 只出現 1 次；原 5 個嵌入資料庫區塊、左側共用導覽、三個主區塊、115 舊版對照、備查均保留。修改前／後 view query：03 待核對 22 筆（21 待核對、1 不符合）、04 全部相關 22 筆、01 續用待核 0 筆，無下一頁。
- **保持不變**：沒有動 Price Plans／Sessions／Staff／Cases／Care Episodes 的任何業務列、Schema、Relation、Formula、View 或權限，也沒改正式 GAS／Cloud Run／中央 Session／部署。
- **限制與回復**：只驗證頁面結構和查詢筆數，尚未人工檢查實際螢幕可視效果、公式值、跨期計算和可核准業務規則。回復時僅移除該 ⚠️ Callout，保留原標題及其後的「🏢 ① 治療所年度用量」標題，不動其他內容。
- **證據**：Notion TEST 工作台與驗收日誌（見 sources.md）；Google Docs 既有 UX 規格第十二節已追加並備份。10,000 篇研究尚未完成，不因此進行全面重設。

## 2026-10-24｜依使用者要求移除黃色提醒｜TEST 回復驗收 PASS

- **範圍**：僅撤回前一回合自行新增的 TEST 頁面黃色 ⚠️ Callout。未更改 Price Plans、Staff、Sessions、Cases、Care Episodes、年度參與紀錄、Schema、View、Relation、Formula 或正式程式。
- **Notion 直接讀回 PASS**：「TEST｜補助資格及額度尚待核對」文字及該黃底警示不再存在；頁面只剩原「青壯方案｜年度額度管理」標題直接銜接「🏢 ① 治療所年度用量」。原 5 個資料庫嵌入、左側共用導覽、心理師區、個案年度參與入口、115 舊版對照、備查皆仍存在。
- **文件**：Notion TEST 驗收紀錄追加撤回理由；Google Docs 現行 UX 規格第十三節確立撤回，舊第十二節保留為歷史。更新前 Google Docs 已備份且回讀 106 段，更新後 110 段、舊段落保持一致，撤回節只出現一次。
- **非本輪驗收**：未重新執行任何計數、公式實值、跨年／跨方案測試或人工作業驗收；原有未完成項目保持未完成。
- **後續約束**：不能將歷史「首屏提醒已實作 PASS」錯認為現況；黃色提醒為使用者明確撤回，不得自動恢復。

## 2026-10-24｜政府補助工作台 vNext 一次性改版｜TEST 工作台與 View 驗收

**[PASS：Notion 結構／清單]** 原主頁 ID 未變、無黃色警示、原5個 linked database 保留並新增年度參與1個（共6）、左側同步導覽保留、驗收子頁保留；原生[備份頁](https://app.notion.com/p/4038ca66aa4d816480bad8a54db6aeab)已讀回原5個 linked database。六個 View 即時查詢無分頁：政府方案1、年度參與22（資格待核21、不符合1）、資格待核22、會談關聯或期限待補22、在職臨床心理師2、115舊個案22。

**[改進]** 僅 TEST 主頁 Price Plans linked View 由「只看青壯」改為「收費類型=補助 且 服務類型=政府方案」，可自行按方案／啟用快篩；Staff linked View 由「曾有週回報 Relation 才顯示」改為「在職臨床心理師、排除隔離人員」，避免新心理師因沒有歷史週回報而漏列。未新增任何業務資料或更改 Schema、Relation、Formula。

**[未驗收]** 心理師週 Formula 仍青壯115專用；Notion 原生 Formula 精確值、跨方案年度規則、當期核定官方規範、真正零週回報人員案例、真人 UI／效能驗收、22筆會談／期限資料完整性、10,000篇研究尚未完成；不能視為正式自動核准。其他既有10個行政模組未修改。詳細回復見 workbench-vnext-2026-10-24.md。



## 2026-10-24｜GitHub 研究知識庫建立（僅文件驗證）

- **本輪範圍**：新增 docs/notion/research 六份文件，包含資料庫建模、工作台 UX、效能／免費版權限、完整稽核清單與16筆來源證據清冊。此次未更新 Notion TEST 頁面、View、Schema、公式、真實業務資料或正式系統。
- **研究取證進度**：16筆唯一 URL；14筆正文可取得並核對相關段落、2筆只有搜尋摘要；符合逐篇完整精讀標準：**0篇**；外部模板逐套比較：**0份**。使用者要求10,000篇目標**未達成**，不能冒充已研究完成。
- **文件類 PASS 不等於業務 PASS**：GitHub blob SHA、Commit、遠端內容回讀通過後方標示文件同步完成；先前 Notion vNext 結構已驗收之結果不變，通用公式／跨政府方案計次／權限及真實 UX 測試仍未完成。
- **後續研究／TEST**：參照 research/audit-checklist-and-research-progress.md，對舊十模組以現況 Schema／View 做唯讀完整盤點，再提出經使用者同意的改版比較。


## 2026-10-24｜十個既有行政模組完整唯讀稽核｜唯讀取證 PASS；優化實作 PENDING

- **[已完成／唯讀]** Notion 10個原管理頁、76個 unique database block IDs、177個 View 配置、23個不同 Data Source Schema；共636欄：152 Formula、147 Relation、48 Rollup。這些是配置盤點不是目前真人效能測試。
- **[高優先發現，非實作]** Events「報名中」View 實際使用 `狀態 status_is_not 開放報名`；「進行中活動」只排除 Complete 群組；Projects頁「本週會議」區塊內有全部 Projects 檢視；多個名為「ALL」的 View 具有固定篩選。改法已列入整批 B 級改善提案，待 TEST、備份及核准；當前未修復。
- **[尚未驗收]** 00.config_notion 的全域設定頁搜尋未精確取得；公式原生求值、前後載入時間、同意書 checkbox NULL 語義、活動狀態 TEST、各角色隔離和現場操作尚未驗收。無修改 Notion、資料、Schema、View、角色或權限；青壯既有歷史 TEST 驗收狀態不變。
- 完整證據與各模組建議：[audits/ten-module-structure-ux-audit-2026-10-24.md](audits/ten-module-structure-ux-audit-2026-10-24.md)。


## 2026-10-24｜B1～B3 獨立 TEST 預覽與狀態驗證｜NOTION TEST／PARTIAL

- **[PASS]** 已建立 Notion [整批操作預覽頁](https://app.notion.com/p/4038ca66aa4d814297a2dbe27e8d054d) 及一張4欄、**無 Relation** 的獨立 TEST 活動狀態 Data Source `collection://5864ca97-2ceb-4727-a52c-9b7cf749dcd9`，僅5筆完全合成資料；三個實際 View 回傳「可報名」1、「進行中」2、「全部」5，與預期完全相符且無查詢分頁。
- **[原頁未變]** 兩個原 Events View 仍是反向／過寬狀態篩選；原 Events 頁15個 linked blocks 保留。原十個業務行政頁、原資料來源／公式／關聯／權限皆未修改。
- **[PARTIAL]** B2／B3 的十模組任務導航已集中在 TEST 預覽，但未改原頁、尚無真人 UI／操作時間／效能／角色權限實測。B1 只在完全獨立 TEST Data Source 中驗證，不表示原業務 View 已修復。
- **[待確認]** 原業務 View 的狀態語義、所有原頁 B 級修正套用、00.config_notion 全域映射、10,000篇學習目標。回復僅涉及新增 TEST 頁與獨立 DB，須經使用者同意後封存，不得觸動原資料。
- 設計、所有 TEST View IDs、回復與對照見 [獨立 TEST 詳報](audits/b1-b3-test-preview-2026-10-24.md)。


## 2026-10-24｜B1–B3 行政頁整批 B 級修正與回查｜PARTIAL PASS／原頁有限 B 級修正

- **PASS**：5個 Notion 原生 BACKUP 頁已確認與改前 block 數一致（Billing14、Events15、Staff14、Tasks3、Documents5）。原 Billing/Events/Staff 頁新增4/4/3個 H4 工作階段標籤，原 linked DB 數字不變；原共用導覽仍在。
- **B1 特殊限制**：`update_view` 的 `CLEAR FILTER` 未能去掉既有 `simpleFilters`，故新增2個無舊 simpleFilters 的正確新 View，原2個舊 View 標停用且原篩選保留，未刪任何頁籤。新 View 即時查詢皆0筆且 has_more=false，**不能宣稱真實活動案例驗收通過**；隔離 TEST 1/2/5 的既有驗收保持有效。
- **B3 PASS**：Tasks 的 ALL →「全部未完成｜依任務類型」，原 Done=false、分組保留，查詢3筆；Documents ALL →「待更新＋草稿｜總覽」，原僅待更新／草稿的選項集合保留，查詢4筆。
- **修正稽核誤判**：Projects/Meetings 實際已分 h3「本週會議」與 h2「專案」兩個區域，沒有改該頁，原報告 F-03 不應再當作待修 BUG。
- **未改動**：個案、會談、收費、收據、薪資或 Events 真實資料列；任何 Schema／Relation／Formula／權限／正式 GAS。未做真人操作、效能／角色驗證、完整十模組批次改造。
- **驗收／回復證據**：[詳細 B 級修改紀錄](audits/b1-b3-legacy-batch-2026-10-24.md)。

## 2026-10-24｜研究成果完整性核對、TEST 工作台 v2 與長期目標修訂｜研究知識庫完整性 PASS（就已記錄部分）／Notion 結構 PASS／實際業務 PENDING

- **研究盤點已核**：GitHub既有 research/ 六文件、16筆唯一來源、14筆歷史正文查核／2筆只有摘要、深度逐篇實讀可驗證0、模板逐套評比0。保存了資料庫模型、UX、Free／效能／權限、10模組23來源636欄稽核、政府補助跨期設計及B1～B3修改；**缺漏**是逐篇深讀、外部模板實測、研究到實作的直接關聯矩陣（本輪新建）。不能聲稱「所有學習」已完整精讀。
- **Notion TEST v2 結構 PASS**：原任務預覽頁已改名「[TEST] 治療所行政任務工作台｜整體 UX v2」，重排四個主題區、4個欄區／2組雙欄、3個 Notion toggle、1個原獨立 TEST活動資料庫；十模組與補助原頁入口保留，無黃色警示；原頁完整 Fetch 回查。原生備份：https://app.notion.com/p/4038ca66aa4d81389417ca0faadf3492 。原 TEST活 動資料庫ID保持不變，備份複製出不同子資料庫，回復不得混用。
- **保持原狀**：十個業務行政頁、核心 Schema、Relation、Formula、業務資料列及 Notion 分享權限沒有被此輪更動；正式 GAS／Cloud Run／Session／部署不在範圍。
- **未驗收**：真實角色的導覽／操作步數、載入效能、活動業務 View 真正可報名紀錄、政府補助跨方案週／次數 Formula、真實權限隔離與 1,000／10,000篇研究歷史需求。
- **長期目標新依據**：[long-term-goals.md](long-term-goals.md) 與 [研究→實作對照](research/research-to-implementation-matrix.md)；下次先測完整任務集，不以不斷增加零碎區塊當進度。


## 2026-10-24｜行政任務工作台 11 情境路徑驗收｜AUTO PASS／MANUAL PENDING
- **AUTO 11/11 PASS**：TEST工作台11個入口與11個目標頁Fetch成功；部分關鍵Views已核對。舊頁有未知／截斷區塊，不能擴張成完整功能驗收。
- **TEST寫後回查 PASS**：新[11項驗收子頁](https://app.notion.com/p/4038ca66aa4d81a0834efc417b08fd1b)有11個情境、11個未勾選人工測試方框；父頁原活動TEST DB存在且無黃色提示。
- **真人0/11／速度／權限 PENDING**：不接觸業務資料、不改Schema、View、Relation、Formula或GAS，保留原權限。
- 回復先檢查子頁有無後續人工測試紀錄及並行修改，不自動刪除。詳見 [本輪驗收](audits/administrative-task-path-acceptance-2026-10-24.md)。


## 2026-10-24｜政府補助 TEST 唯讀隔離與資料完整性｜唯讀查核完成，計算及隔離未通過
- 來源23筆／工作台總覽22筆；另1筆隔離分類仍與啟用方案和3筆會談有共同關聯。
- 一般22筆中21待核對、1不符合；會談Relation／期限／他處次數皆未填，確認checkbox未勾，不等於確認0。
- 11項真人UX測試目前0完成；原生Formula額度影響、跨期規則、角色權限及效能均未驗證。
- 本輪Notion唯讀、未變動Schema／Relation／View／Formula及原始資料。00.config_notion尚未定位。[報告](audits/subsidy-readonly-integrity-2026-10-24.md)。


## 青壯人工核對後於服務歷程選方案｜2026-10-24｜青壯 TEST UI PASS，計數仍 PENDING
- **[PASS]** Care Episodes 現有「💲收費方案」是 Price Plans Relation，可按使用者確認直接選方案，未建新欄位。Notion TEST 工作台已改「人工確認→服務歷程選方案」，舊參與表改在歷史收合區；原6個 linked DB、同步側欄保留且無黃色提醒。
- **[PASS]** 原資格 View 只改名稱為「既有資格狀態（歷史備查）」，讀回篩選／排序／欄位完全未變；Notion 工作台已保留改版前備份與追加歷史紀錄。Google Docs 規格第十五節追加成功，修改前117段讀回完整一致。
- **[PENDING]** 真實人員完成核對與選方案後，Sessions Price Plan 的實際歸屬、額度占用、跨方案與期別 Formula 及權限均未實測。原23筆參與／TEST 資料、相依的啟用方案關聯不能直接清除。效能未量測。
- [完整差異、備份與回復](audits/youth-manual-eligibility-episode-plan-2026-10-24.md)。


## 2026-10-24｜使用者確認青壯測試資料符合實際使用情境｜情境適切性 USER CONFIRMED，系統驗收仍 PENDING

- **[USER CONFIRMED]** 使用者認為目前青壯 TEST 資料符合實際使用情境；無須再為此重建額外青壯資格核對清單。此確認屬測試資料／工作情境適切性，不是原生計數或完整操作通過。
- **[KEEP]** 青壯資格人工核對、服務歷程「💲收費方案」選方案流程維持已確認設計；既有測試及參與資料、方案／會談關聯不更動。
- **[PENDING]** 實際在服務歷程選方案後的 Sessions Price Plan 歸屬、原生 Formula/Rollup、補助餘額、跨方案／核定期別、各角色權限與使用效能尚未驗收；11項行政任務的既有真人操作0/11亦不因此視為完成。
- **[NO WRITE]** 本次只有 GitHub 驗收文件更新，沒有 Notion 或正式程式部署修改；不涉及效能與資料回復。


## 2026-10-24｜服務歷程與會談方案對照：唯讀驗證｜關聯完整性 PASS、方案一致性 PARTIAL、原生額度 PENDING
- 既有 Saved Views 完整讀回 Care Episodes 57筆、Sessions 295筆（3頁）、政府啟用方案1筆；57歷程均有主收費方案，295/295 Sessions 均連到歷程且其反向 Relation 無缺漏。
- 287/295 Session 與 Episode 主收費方案一致；**8筆不同**，其中 Session 青壯／Episode其他4筆、反向4筆。**不得自動更改**，需依真實收費情境確認是否刻意差異。
- 啟用青壯方案 Session雙向關聯 **41/41集合一致**：已完成23、已預約13、已取消2、已改期2、no-show1。僅為關聯與狀態驗證，**不是計數/剩餘額度 PASS**。
- Notion Formula／Rollup 目前返回結果參照，SQL／rows 查詢額度已用完，無法讀出原生占用與剩餘數值。原業務資料、Schema、Formula、Relation、View、權限、GAS皆未改；僅追加Notion TEST驗收文字及本 GitHub 紀錄。完整[技術證據](audits/episode-session-plan-consistency-2026-10-24.md)。

## 2026-10-24｜青壯／自費 8 筆方案差異之情境分類回查｜情境分類 PASS、意圖／公式 PENDING
- **[AUTO PASS／唯讀]** Care Episodes 57、Sessions 295及Price Plans原View重新查詢，287會談與歷程主方案一致，8筆不同僅分布4個進行中個別服務歷程、且只涉及**青壯與同一個自費個別方案**；兩個方向各4筆，均有3筆的已預約／完成／改期配對及另外1筆已完成。與歷史資料缺關聯不同，這是**主方案選擇差異**。
- **[PENDING／業務]** 對稱組合有刻意測試的可能，但沒有逐筆佐證，不得將8筆全列缺陷、亦不得以「測試資料符合使用」推論每筆已核准。Episode方案預設與Session個別改方案的權威關係需後續確認；不自動修復／同化。
- **[PENDING／原生數值]** `formulaResult://`參照不支援直接Fetch（validation error），不能驗證政府額度占用或剩餘額度。沒有真實操作、權限或效能驗收。
- **[NO DATA WRITE]** 本輪只在Notion TEST驗收歷史追加文字及GitHub紀錄；原 Sessions／Episodes／Price Plans資料列、Schema、Relation、Formula、View、GAS保持不變。證據見[原完整關聯報告及本輪追加](audits/episode-session-plan-consistency-2026-10-24.md)。


## 2026-10-24｜政府補助計數 Rollup 直接相依驗證｜Rollup 來源 PASS；Session 計數公式與額度 PENDING
- **[SCHEMA PASS]** Price Plans「已完成_帶入」「已預約_帶入」「待確認_帶入」的 `sum` Rollup 透過該方案與 Sessions 的直接關聯，指向 Sessions 各自的已完成／已預約／待確認計數 Formula。Care Episodes 有自己的 `sum` Rollup（服務歷程↔Sessions），不得將兩種彙總混同。
- **[FORMULA BLOCKED]** `formulaCode://` 參照無法以 Notion Fetch 讀取（validation error）；`formulaResult://` 和 `rollupResult://` 在 View 只作引用，無原生數值。Session 計數 Formula 是否額外引用 Episode 方案、Price Plans「已占用」內部算式與剩餘數字，**都未通過驗收**。
- **[NO DATA CHANGE]** 原8筆青壯／自費切換與目前已啟用方案資料均不修改。TEST 驗收歷史追加文字已回查；其他既有業務資料、欄位、View、權限、GAS／部署及效能保持不變。下一步需經可信原生公式數值來源再核對，不得自行以狀態加總計次。詳見[完整相依性報告](audits/episode-session-plan-consistency-2026-10-24.md)。



## 2026-10-24｜原生公式數值驗收：替代唯讀入口與重試門檻｜原生數值依然 BLOCKED（可恢復的 SQL/rows 配額）
- **[VERIFIED]** 啟用 Price Plan 的原頁與 Saved View 都只露出 `formulaResult://`／`rollupResult://` 結果參照，Schema 只有 `formulaCode://` 參照及空白描述，非算式或數值。
- **[TEMPORARILY BLOCKED]** 本輪嘗試 `rows`，連接器回報 SQL／rows 工作區共享配額已用完，60 分鐘內重置；View 可讀但無法直接取原生數值。勿在同一個配額視窗重複嘗試並聲稱通過。
- **[NOT AUTHORITATIVE]** 歷史青壯 Google Docs 與 2026-07 的 Sessions 收據公式文件不是目前補助占用公式版本；`00.config_notion` 仍未精確定位。
- **[NEXT GATE]** 既有8筆青壯／自費切換只做受控唯讀數值驗證，需原生 Sessions Formula 結果及 Price Plan 額度後才核實計次歸屬；不改資料、不增加資格清單。操作、效能、跨期與權限仍待驗。詳見 [驗收協定](audits/episode-session-plan-consistency-2026-10-24.md)。


## 2026-10-24｜青壯方案啟用測試續作：現況唯讀前置核對
- **[SCHEMA READBACK PASS]** 重新 Fetch 現行 Price Plans（30欄）、Sessions（67欄）、Care Episodes（50欄）Data Source：Price Plans「已完成_帶入」「已預約_帶入」「待確認_帶入」仍分別以 `sum` 沿方案↔Sessions Relation 加總 Sessions 同名計數 Formula；Care Episodes「💲收費方案」與 Sessions「💲 收費方案」均仍為 Relation。此結果只證實**直接 Rollup 相依結構**，不證實 Formula 內部條件或數值。
- **[VIEW READBACK PASS]** Notion「補助方案管理｜TEST」有6個 linked database，沒有被使用者撤回的黃色提醒；原政府方案 View 本次回傳1筆已啟用、收費類型「補助」、服務類型「政府方案」的青壯方案，`has_more=false`。本輪沒有重新逐筆讀完295筆 Sessions，歷史8筆差異分類仍以先前已驗結果為準，不稱本輪已重驗。
- **[NUMERIC BLOCKED]** 同一筆方案的「已完成_帶入」「已預約_帶入」仍僅有 `rollupResult://` 參照，「已占用_自動」「剩餘額度_自動」仍僅有 `formulaResult://` 參照；最新 Schema 將這些欄位列為 `notAvailableInQuerySql`。沒有取得原生數值、Formula 原始碼，也沒有重新嘗試尚在前次共享配額限制視窗內的 SQL/rows 查詢。不能把23完成＋13已預約推定為已占用36。
- **[SCOPE/SAFETY]** 只做 Notion 原頁、Schema、View 與 GitHub 文件唯讀核對。Notion 搜尋尚未定位名稱精確吻合的 `00.config_notion`。不修改 Price Plans／Sessions／Care Episodes／Staff／參與紀錄、Formula、Relation、View、共享權限、Google Docs 或正式 GAS／Cloud Run／Session／部署；未做效能和角色操作實測。此記錄更新只影響 GitHub 文件，可在確認後續並行更新後單獨撤回。
- **[NEXT GATE]** 待連接器共享配額恢復後，依既定受控協定僅用唯讀 formula 精確篩選／可信 Notion 原生值對照8筆青壯↔自費 Session，以及相同 Price Plan 的已占用、剩餘及核定額度；若只能返回參照，仍維持 BLOCKED，不寫入任何業務列。

## 2026-10-24｜青壯續作：全量關聯回歸 PASS、數值 BLOCKED
- **[本輪 LIVE 回歸 PASS]** Notion 既有 Saved Views 重新完整取得 Care Episodes 57筆、Sessions 295筆（3頁）、政府方案1筆；295/295有現存服務歷程及反向會談關聯，295/295收費方案非空，287/295與歷程主方案一致；8筆差異仍分布4個歷程（3/3/1/1）、兩方向各4筆，不擅自同化。
- **[雙向關聯 PASS]** 啟用青壯 Price Plan「💬 關聯Sessions」與 Sessions「💲 收費方案」各41筆、兩方向完全同集合；其中已完成23、已預約13、已取消2、已改期2、no-show1。
- **[原生公式數值 BLOCKED]** Price Plans 原 View 仍只有 `formulaResult://`／`rollupResult://`，而最小 `rows` 查詢被 Notion 連接器以工作區共享 SQL/rows 配額用盡拒絕；精確公式篩選候選格式尚未通過工具 schema 驗證。故額度已占用、剩餘、個別 Session 公式值、8筆收費切換計次與跨方案／期別**均未通過**，不推算或核准。
- **[未改動]** Notion Price Plans、Sessions、Care Episodes、Staff／年度參與資料列、Schema、Relation、Formula、View、權限；Google Docs、正式 GAS／Cloud Run／Session／部署也未動；未實測效能／真人權限。找不到精確 `00.config_notion`，不得進行核心結構變更。詳細證據與回復界線見 [同日關聯稽核](audits/episode-session-plan-consistency-2026-10-24.md)。

## 2026-10-24｜青壯續作：SQL/rows 恢復後原生數值仍 BLOCKED
- **[PASS：工具可用性]** 本輪 Notion Price Plans 的最小 `rows` 唯讀查詢成功（上一輪「配額耗盡」已不再阻擋）；普通 Number／Checkbox 原生篩選亦成功。原 Price Plans／Sessions／Care Episodes Schema 和政府方案 Saved View 重新 Fetch，View 仍只有1筆已啟用的政府方案，無分頁。
- **[BLOCKED：公式結果值]** `rows` 與 Saved View 仍僅回傳額度的 `formulaResult://`、計數的 `rollupResult://`，不是原生數字。針對 Formula number 的自訂 rows 篩選候選均遭連接器參數 schema 拒絕，未實際完成原生公式精確值比對；Formula 算式亦未取得。不得以41筆關聯、23完成＋13預約推定政府額度占用／剩餘或核准啟用。
- **[KEEP]** 先前57筆歷程、295筆會談、41/41與8筆方案差異的完整回歸維持前一輪已驗紀錄；本輪沒有重新逐筆執行，不自動修復差異。青壯資格人工核對後直接在 Care Episodes 選 Price Plan 的已確認流程不變。
- **[NO NOTION WRITE]** 無業務資料、Schema、Formula、Relation、View、權限、Google Docs、GAS／Cloud Run／Session 或部署更動；沒有真人操作、效能與角色權限測試。詳細失敗邊界、回復與下次合法數值入口見 [當次完整稽核](audits/episode-session-plan-consistency-2026-10-24.md)。

## 2026-10-24｜115青壯官方規則 vs 啟用方案備註：四項差異待確認
- **[READBACK PASS]** 本輪重新 Fetch Notion「青壯世代心理健康支持方案｜115」原始頁、Price Plans Schema、政府方案 Saved View，確認方案啟用且 View 僅1筆；原始頁六個額度／計數相關 Formula、Rollup 均返回參照而非數字，**NUMERIC BLOCKED**。本輪沒有重做295筆會談全量回歸。
- **[RULE TEXT REVIEW REQUIRED]** 現行 Price Plan「備註」有四項與115年政府公開規則不符或不完整：`>7天` vs 最短**不小於7天**；未寫原則上**不超過1個月**；「國民」少列**持健保卡之外籍人士**；連續2次無故未到「將取消資格」vs **機構得拒絕提供服務**。這只是原頁備註文字的驗證，不證明 Formula 或人工資格核對已錯。來源及限制見 [比對報告](audits/episode-session-plan-consistency-2026-10-24.md)／[來源索引](sources.md)。
- **[SAFE HOLD]** 不自動修正啟用方案、所有8筆Session異方案、公式、跨期規則或資格核對流程；方案備註最小修正待確認本期地方執行細則，使用者確認後再寫回查；共享Formula需另申請C級核可。沒有本回合的Notion資料、View、Schema、分享權限、Google Docs或正式服務寫入，無真人操作、效能、角色權限實測。

## 2026-10-24｜汐予115青壯：桃園合作機構來源已核對、地方契約仍待查
- [SOURCE PASS] 汐予位於桃園市八德區，桃園市官方115年青壯合作機構公開檢索結果可找到汐予；不能直接以臺北公告替代桃園契約。
- [CENTRAL PASS / LOCAL CONTRACT PENDING] 衛福部115年公開公告明示15–45歲本國籍或持健保卡外籍人士；桃園115年公告明示當期期間與三次個別心理諮商。桃園當年計畫書PDF附件仍無法完整檢閱、已連接Drive未找到已簽汐予115年契約全文；因此最短7天、最長1個月、連續2次無故缺席的具體桃園合約處置，仍待核對後才可把前輪文字差異改成正式修正。
- [LIVE NOTION READBACK / NUMERIC BLOCKED] Price Plans、Sessions、Care Episodes Schema、當期啟用方案原頁及政府方案View重讀；1個政府方案啟用，公式／Rollup仍只返回參照非原生數值。未重新逐筆檢查全部295筆Sessions，保留先前41/41及8筆差異歷史驗收。
- [NO BUSINESS WRITE] 僅GitHub匿名來源／驗收紀錄更新；Notion備註、方案、Session、Relation、Formula、View、權限、Google Docs及正式程式均不動。後續最小備註修正候選與回復程序見當日完整稽核。

## 2026-10-24｜中央115青壯連續缺席裁量條文已核對：備註仍未修、額度仍受阻
- **[CENTRAL RULE TEXT PASS]** 桃園公部門託管衛福部115年計畫書的可搜尋條文片段＋我的E政府115年FAQ相互印證，連續兩次無故未到的中央措辭是「合作機構得拒絕提供服務」，不是現行Notion備註的「將取消資格」；至少7天、至多1個月與總3個月之原則亦有中央115年FAQ依據；衛福部115年公告已包含持健保卡外籍人士。這是**中央層級規則文字確認**，非合約附款全文驗收。
- **[LOCAL CONTRACT PENDING / PDF LIMIT]** 桃園115年官方公告版計畫書與另一桃園公部門託管中央計畫PDF可定位，但Web閱讀工具下載cache miss，未完成附件全文逐頁閱讀；未核實汐予115年實際簽署契約的補充條文。部分其他縣市可能另有暫停規定，不假定桃園也有或必然沒有。
- **[LIVE NOTION READBACK]** 啟用115年Price Plan原始備註仍寫「>7天」「連續兩次未到將取消資格」，官方文字差異確認；政府View仍1筆且無後頁；已占用、剩餘及核定額度仍為不可直接驗收的Formula/Rollup參照，NUMERIC BLOCKED。
- **[NO NOTION WRITE]** 本輪沒有變更現行Price Plan備註、Sessions、Episodes、Staff、Formula/Relation/View、角色權限、Google Docs或正式系統；僅GitHub匿名驗收及來源記錄。8筆既有不同收費方案會談仍保留，前輪關聯回歸不冒稱本輪重跑。詳見[相依稽核](audits/episode-session-plan-consistency-2026-10-24.md)。

## 2026-10-24｜115青壯服務方式與政府同意書驗收入口已核對
- **[OFFICIAL DIRECTORY READ PASS]** 桃園市衛生局115年可搜尋合作機構網頁列有汐予，當期遠距/通訊心理諮商核准欄顯示「否」，另載明需自付掛號費。此為公開清單當次狀態，不等於個別契約或永久權限；不得誤將青壯補助做成自動允許遠距。
- **[CONSENT SOURCE PASS; WORKFLOW NOT TESTED]** 桃園市政府託管中央115年計畫同意書搜尋片段與中央FAQ相互印證，跨機構同方案累計最多3次、須據實告知已使用次數，及連續2次無故未到時機構「得拒絕服務」。官方同意程序不能與Notion新增額外資格清單混為一談；實際機構的同意簽署/收據/政府平台查詢**尚未真人實測**。
- **[NOTION READBACK; NUMERIC BLOCKED]** 本輪重新Fetch啟用青壯原頁與三張來源Schema、政府補助View仍1筆。方案備註舊文字尚未修正；公式值依然只有不可直接驗收的參照。先前41/41關聯及8筆跨方案Session分類仍為歷史驗收，本輪不冒稱重新執行。
- **[NO WRITE]** 無Notion活躍業務記錄、Schema/Formula/Relation/View、權限、Google Docs或正式服務改動；本輪新來源／驗收記載僅寫入GitHub。詳見[唯讀稽核](audits/episode-session-plan-consistency-2026-10-24.md)。

## 2026-10-24｜115青壯週額度：中央4月12日硬上限與本週未確認
- **[OFFICIAL RULE VERIFIED]** 衛福部115年3月25日函明確：每週日～週六、每位醫師／心理師跨執業登記處所及報備支援處所青壯服務**合計六人次**；自115/4/12開始中央系統限制每週維護及核銷六筆。不能把院內個別上限當成跨地總額，不能寫死成其他補助方案規則。
- **[SOURCE / RELATION TEST PASS]** Notion週額度來源完整6筆TEST記錄，6/6週起始日都是星期日；其中4筆同時連啟用115青壯方案及Staff工作台2筆在職心理師，4/4反向關聯一致，故TEST名稱不等於真正隔離。
- **[CURRENT WEEK FAIL-CLOSED]** 2026/10/18～10/24兩筆本週回報**均未確認他處使用，且次數為未知空白**；前週10/11～10/17兩筆均已確認他處使用0。未知不等於已確認0，不能自動宣稱本週有可用6次。
- **[NATIVE NUMERIC STILL BLOCKED]** Staff週額度的Formula/Rollup及Sessions相關週次計數僅有參照，不能從「週起始日」欄位或關聯PASS推定真正演算法PASS；Price Plans占用及剩餘亦未驗收。沒有重新執行全部295筆Session回歸或真人跨地核銷測試。
- **[NO DATA WRITE]** 本回合沒有修改Notion Staff、週紀錄、啟用方案、Sessions/Episodes、Schema/Formula/Relation/View、權限、Google Docs、GAS/Cloud Run/Session/部署，只新增GitHub匿名稽核與索引。[詳細檢查](audits/youth-weekly-allowance-2026-10-24.md)。

## 2026-10-24｜青壯115本週跨機構額度：完整295筆Session再驗與6／4預約風險
- **[FULL SESSIONS VIEW PASS]** 本輪真正完整分頁重新查詢Notion ALL Sessions共**295筆**，用啟用115青壯Price Plan實際關聯找出**41筆**，其中已完成23、已預約13、已取消2、已改期2、no-show1。**38筆實體、3筆形式未知、0筆線上**；缺心理師的3筆與形式未知3筆相同，均標記TEST且狀態各為已取消1、已改期1、no-show1，有服務歷程／日期；**不對其自動修復**。
- **[THIS WEEK CONDITIONAL RISK]** 2026/10/18～10/24本所青壯已預約Session：在職2名心理師分別為**6筆與4筆**；這是排程數，不是完成／核銷數。對應兩人本週週回報**都未確認他處使用，次數未知**，故不能以本所預約不超六筆宣稱當週可再預約、亦不能推論政府最終核銷。
- **[NO LOCAL >6 CANDIDATE FOUND]** 以單次Session日期（手動執行調整日期優先）及單一心理師Relation、週日到週六分組，對已完成／已預約／待確認之本所41筆青壯方案會談未見院內同人同週候選超過六筆；仍不代表官方跨處總額未超。
- **[NATIVE FORMULA ACCESS BLOCKED]** 嘗試透過Notion.fetch對Staff及週回報Formula Code指標作唯讀存取，回傳INVALID_ARGUMENT；Staff/Price Plans原生Formula、Rollup仍僅結果指標，沒有真值／原始碼，**原生計數仍BLOCKED**，不能判定Staff v2公式是否fail-closed。
- **[NO WRITE / TEST LIMIT]** 無Notion業務資料、Schema／Formula／Relation／View／權限及Google Docs／GAS／Cloud Run變更；未做真人權限、政府系統跨地核銷、效能實測。只在GitHub追加匿名驗收紀錄；下一步先在原有人工流程核實本週外部使用與官方額度，再取得真正的Notion原生顯示值交叉驗收。[專項稽核](audits/youth-weekly-allowance-2026-10-24.md)。

## 2026-10-24｜週回報原始與工作台View 6／6一致；原生狀態仍待驗
- **[VIEW CONSISTENCY PASS]** 找到「補助週額度紀錄」原始Saved View及TEST補助工作台嵌入View；View模式直接取得雙方**各6筆且集合6/6相等**，無分頁遺漏。6筆「心理師Relation＋Price Plan Relation＋週起始日」複合鍵**0筆重複**。
- **[TEST SCOPE VERIFIED]** 6筆TEST週回報中4筆連現有啟用115青壯方案與工作台顯示2位在職心理師，其他2筆連不同Price Plan／未顯示之TEST人員。因此就這6筆特定關聯而言可分辨作用域，但TEST標籤仍不能當作完整資料隔離。
- **[CURRENT WEEK HOLD EXPECTED; NOT NATIVE PASS]** 10/18～10/24的兩位心理師他處回報都未確認、次數未知；與前輪本所已預約6及4筆搭配，**應維持待核對，不應自行核准有剩餘額度**。目前只能驗證資料源，無法讀原生週額度Formula值，不能宣稱其已實作fail-closed。
- **[CONNECTOR LIMIT]** 普通Staff Select rows篩選可用，Formula文字篩選遭schema拒絕，另有validation_error；隨後Query Data Source的SQL／rows模式**配額用盡且該次查詢未執行**，但Saved View查詢仍可用。採View完成上述核對，未寫入任何Notion資料。原生Formula結果、政府跨地人次、真人權限及效能仍**BLOCKED/NOT TESTED**。
- **[NO BUSINESS WRITE]** 本回合只將新集合與配額邊界匿名同步GitHub；沒有修改Staff、週回報、Sessions、Price Plans、Schema／Formula／Relation／View、權限或Google Docs／正式服務。詳見[專項稽核](audits/youth-weekly-allowance-2026-10-24.md)。

## 2026-10-24｜補齊歷史v2週額度隔離PASS及當前Staff顯示覆蓋2／2
- **[HISTORICAL ISOLATION PASS / NOT RERUN]** 新回查[2026-10-23精簡前23章設計備份](https://docs.google.com/document/d/1gqI_lPdW9z1-mLIOUQFu5c0thjMXZUe07-DUd6bzyfY/edit)第八節：既有Sessions跨週六／週日、Staff v2週占用及狀態，曾在隔離TEST人員測出「超額」「已滿」「重複／取消確認轉待核對」「已確認5＋本所0剩餘」並記PASS。**應保留已發生的歷史隔離通過記錄，不可再說v2公式完全從未測過**，也不能冒稱本輪重新實測。
- **[CURRENT VIEW FILTER / FULL STAFF COVERAGE PASS]** 該備份第九節所述舊版「要求週回報Relation非空才能顯示」門檻，**現行**青壯週額度View已不再使用；本輪從TEST Backend Staff原始資料庫Default View完整讀4筆，其中在職臨床心理師2筆，週額度View也正確列這2筆，**0人被漏列、0人多列**。此為目前View/人員集合PASS，非未來沒有週回報的真人情境驗收。
- **[CURRENT LIVE FORMULA STILL BLOCKED]** 現行2名心理師本週10/18～10/24他處占用仍未核實，前輪6／4筆本所已預約不是政府已核銷；連接器的原生Formula值／原始碼仍無法讀，本週「青壯本週額度狀態_v2_自動」是否呈待核對尚不能標記PASS。不得由歷史v2隔離通過直接宣稱真實跨機構核銷及正式授權已驗。
- **[NO BUSINESS WRITES]** 本回合僅GitHub來源／專項稽核／驗收及決策修訂，Notion Schema/View/Formula/關聯/業務列及Google Docs/正式GAS、Cloud Run、Session、部署不動；未做真人操作、權限和效能實測。[詳情](audits/youth-weekly-allowance-2026-10-24.md)。

## 2026-10-24｜隔日10/25新週缺回報：原始關聯／Sessions跨週回查PASS，Formula待驗
- **[DATE / RELATION PASS]** 2026-10-24星期六重新回查週回報原始Saved View完整6筆；現有2名在職臨床心理師×啟用115 Price Plan的當週10/18～10/24回報**2筆均未確認他處使用**，前週10/11～10/17為**2筆已確認0**，**新週10/25～10/31不存在任何符合此兩人＋Price Plan的回報**。10/25的一筆另外方案／隔離TEST人員回報不可混用。
- **[SESSION COMPLETE READ PASS]** 重新分頁取得Notion Sessions ALL **295/295筆**，用Price Plan實際Relation找出青壯**41筆**；2026/10/25～10/31關聯該方案會談**0筆**（其中已預約0筆）；10/18～10/24共11筆，10筆是已預約有效候選，本所兩人各6／4；此為當前日期快照，不代表核銷。
- **[SUNDAY RESET FORMULA STILL NOT LIVE VERIFIED]** 10/25進入週日至週六的新週時，無當週有效外部回報應繼續顯示**待回報／待核對**，不能繼承前週或認定外部0而自動顯示可安排。該日尚未到來，連接器目前只能回傳原生公式結果參照，故**這項換週顯示並未測試通過**；過去2026/10/23的v2隔離PASS仍保留，不可冒稱是10/25實測。
- **[NO WRITES]** 無Notion業務資料、Staff／Sessions／Price Plans／週回報、Schema／Formula／View／權限、Google Docs、GAS及部署異動；本回合只把新的無敏感資料時間邊界驗收事實寫入GitHub，權限與效能未真人實測。[詳見專項稽核](audits/youth-weekly-allowance-2026-10-24.md)。

## 2026-10-24｜115方案備註B級最小修正已完成差異設計，未執行寫入
- **[LIVE PAGE READBACK PASS]** 本輪重新Fetch啟用115青壯Price Plan「備註」原文；對照衛福部115公告及政府FAQ確認4項文字修正需求：國籍／健保外籍、至少7日（非>7）、原則最多1個月、連續2次無故缺席僅為合作機構「得拒絕」，非自動取消資格。
- **[CONTRACT SOURCE BLOCKED]** 已在連結的3個Google Drive帳號依名稱與內容找汐予青壯簽約資料，未見可核對的115桃園個別合作契約；另找到名稱似官方青壯方案PDF，實為當前Notion方案資料匯出且含同樣舊錯句，不能視為獨立政府依據。Gmail兩帳號相關搜尋未找到簽約函，另一帳號搜尋失敗；**僅稱目前未取得，不能聲稱不存在**。
- **[B CHANGE NOT APPROVED / NO NOTION WRITE]** 已在[原有方案一致性稽核](audits/episode-session-plan-consistency-2026-10-24.md)列出單一「備註」欄位四處替換、保持不變、回查／單欄回復。契約及使用者核准前**不修改啟用Price Plan**，不更動Staff、Sessions、Care Episodes、公式／關聯／View、權限、Google Docs及正式系統。原生公式數值與2026/10/25實際換週結果亦維持未驗收。

## 2026-10-24｜青壯115備註全文候選無損差異測試PASS；寫入仍BLOCKED
- **[READ ONLY NOTE ROUNDTRIP PASS]** 重新Fetch啟用115青壯Price Plan原生「備註」text完整欄位，產生可閱讀的**全文候選**；以**3處恰好一次的字串替換**解決**4項既有官方規則差異**（適用外籍、7日含第7天、1個月原則上限、無故缺席不自動取消資格），再反向替換與原值**完全相等**。期程、3次／1600元、行政費與3個月總期限均保持不變；原HTML文字排版需未來寫入時完整保留。[全文及回復檢查](audits/episode-session-plan-consistency-2026-10-24.md)。
- **[NOTION WRITE NOT APPROVED]** 汐予115年個別合作契約／附款及此啟用Price Plan備註修正的使用者核准**尚未取得**；沒有修改Notion欄位、沒有真人UI寫後回查，不能標記正式文字修正PASS。已驗證的是候選文本差異及其可逆性。正式GAS／Cloud Run／權限與效能不在本輪工作界線。

## 2026-10-24｜新增115-05-13中央FAQ與外縣市契約差異：備註修訂繼續暫緩
- **[SOURCE PASS]** 已開啟並以PDF截圖核對衛福部心理健康司**115年5月13日更新版完整FAQ**，Q8/Q9/Q14確證間隔、無故缺席「合作機構得拒絕」及外籍有健保資格；機構篇確認不得額外收諮商差額、新立非原訂行政費及同次服務不得中央／地方雙請。
- **[REGULATORY CONFLICT / UNRESOLVED]** 新北市政府公開的115年合作機構**合約PDF搜尋索引**出現「兩次無故缺席後暫停90日」的不同文字，但其PDF直接開啟失敗，未做逐頁檢查；**新北契約不是汐予適用的桃園契約**。桃園公告之中央計畫PDF索引含「地方不得訂更嚴格限制」，其全文亦未能以網頁PDF工具讀到。必須以本機構適用契約／主管機關釐清，**不得逕行判斷新北條文有效性或套用於桃園**。
- **[NOTE DRAFT SUSPENDED]** 過去完整備註候選的三處可逆替換仍是文字測試PASS，但不是核准版；因地方缺席規範差異及現行「掛號／場地等行政費用」的事前告知與既有規費要件尚未核實，啟用Price Plan「備註」修改仍**BLOCKED、完全未寫**。詳見[稽核](audits/episode-session-plan-consistency-2026-10-24.md)。
- **[GOV PLATFORM PATH EVIDENCED, NOT PERSONALLY TESTED]** 同份FAQ系統篇Q13已截圖確證：服務日第0日、三日內暫存，**暫存可供其他機構查詢個案已使用次數**。這是現有人工核對流程依據，沒有在Notion建立青壯額外參與DB／清單。未操作正式政府平台、不得以未查得當作確定0；該個案維度不代替心理師週6次查核。[週額度稽核](audits/youth-weekly-allowance-2026-10-24.md)。
- **[NO WRITES]** Notion啟用Price Plan／Sessions／Staff／週回報／Schema／Formula／Relation／View／權限、Google Docs及正式GAS／Cloud Run皆未改動；無新效能開銷／分享範圍變動。僅GitHub匿名證據修訂，沒有真人UI或角色權限／效能驗收。

## 2026-10-24｜桃園115官方名冊費用對照：400元掛號費有獨立來源，應付公式未驗
- **[OFFICIAL LIST INDEX EVIDENCE]** 2026-10-24網路搜尋索引的[桃園市115青壯合作機構名冊](https://mental.tycg.gov.tw/cp.aspx?n=19932)列汐予心理治療所及「掛號費400元」、通訊核准「否」；**直接開啟的同網址卻為較舊快照且未列汐予**，故僅證明公開官方索引有這項具體費用記載，不假稱已對當下資格進行無歧義即時核驗。
- **[NOTION FEE DISPLAY UNVERIFIED]** 重讀啟用115 Price Plan「備註」仍只泛稱「掛號費、場地費等」，沒有具體400元；Page/Schema中沒有「掛號費」單獨欄位，而`應付_自動`僅回Formula參照，**不可聲稱Notion應付=400已通過，亦不可認定公式有錯**。官方FAQ限制其他收費須為既有規費及事前告知。[詳細稽核](audits/episode-session-plan-consistency-2026-10-24.md)。
- **[NO NOTION WRITE]** 無使用者啟用方案備註改動核准、無汐予簽署契約；未改任何Notion資料、Schema、Formula、Relation、View／權限或Google Docs、正式系統。只新增GitHub匿名來源比對；角色、效能、收費原生數值未實測。

## 2026-10-24｜青壯115既有400元掛號費分帳路徑交叉驗證PASS（公式／款項仍未驗）
- **[NEW DATA MODEL FACT / READ PASS]** 找到**原有**啟用的[「掛號費」Price Plan](https://app.notion.com/p/3d88ca66aa4d83b88e9b0197e9f794a0)，收費400、補助0、收據項目「掛號費」，不同於115青壯本體1600／補助1600。Sessions 已有 `💲 附加收費方案` Relation；Billing已有 `💲 收費方案`、`💬 Session`、`請/收款對象`、`實收金額` 和「＋掛號費營收」按鈕。**不得再以青壯方案沒有掛號費單獨欄位推斷系統無法收掛號費**。
- **[ALL ROWS RELATION PASS]** 完整 Saved Views：Sessions295/295、Billing203/203（`has_more=false`）；青壯方案41筆Sessions，35筆已加附加「掛號費」（完成22／預約12／取消1）；Billing掛號費22筆均向個案、狀態已收款、實收400；政府補助Billing23筆均向衛生局、待請款9／請款中14。**共45/45筆**Billing均連到存在且已完成的青壯Session、其反向Relation一致；掛號費Billing **22/22**對應Session附加掛號費、政府補助Billing **23/23**涵蓋全部已完成青壯Sessions。[詳細稽核](audits/episode-session-plan-consistency-2026-10-24.md)。
- **[EXCEPTION / NO MUTATION]** 23筆已完成中1筆**未附加掛號費且無掛號費Billing**，已預約另有1筆未附加，原因未確認；不得假設都應收400，更不得批次自動開帳。其餘取消／改期／no-show不附費不構成此驗收的失敗。
- **[FORMULA/REVENUE/AUTH UNVERIFIED]** `應付_自動`、`最終應收金額_自動`、`應收金額_自動`公式原生結果仍不可讀；「已收款」並非對帳證據，「請款中」不是政府撥款通過。沒有驗證Billing按鈕、收據、真人權限或效能。**不更改任何現有Price Plans、Billing、Sessions、Schema、Formula、View、權限、Google Docs及正式系統**，只有此GitHub匿名驗收證據更新。

## 2026-10-24｜使用額度 View 功能實際建立（方案1筆／歷程22筆；數字真值待驗）
- **[VIEW CREATE / READBACK PASS]** 已在 TEST 工作台原 Price Plans linked database **新增**[第02頁籤「政府補助使用額度」](https://www.notion.so/3f68ca66aa4d8156bccfcc28f75cbb9a?v=4038ca66aa4d81278430000cd581b5e7)，完整顯示原有核定總額／已完成／已預約／待確認／已占用／剩餘／額度狀態；依補助＋政府方案分類，沒有寫死115。重新 Fetch 原 linked DB 可見新舊2頁籤，新 View Query 1筆且 has_more=false；原 View 01 不改。
- **[EPISODE VIEW CREATE / READBACK PASS]** 同頁新增[Care Episodes 個案使用額度 inline View](https://www.notion.so/3f68ca66aa4d81cca3b4ee43b4bd8dcf?v=4038ca66aa4d81a3ab1a000ca3244dce)，原「💲收費方案」關聯 Quick Filter 預選青壯115方案，View有上限／已完成／已預約／他處確認／剩餘／額度狀態；查詢22筆、has_more=false。新 inline DB 實際追加於工作台**頁尾、原雙欄外**；在主頁②新增1行快速入口，讀回確認有連結且保留原3主要展示區、黃色提醒不存在。**這是服務歷程的額度檢視，不代表個案跨歷程真實額度計數通過**。
- **[STAFF VIEW REUSED]** 原有青壯115心理師週額度 View 已含有效占用／他處使用／上限／狀態，無須再建同樣資料；仍是特定115期別，原View及篩選不動。
- **[NUMERIC / AUTH / UX STILL UNVERIFIED]** 連接器只能取Formula/Rollup結果引用，不能核定任何已用、預約、剩餘的原生數字、跨方案／期別及缺回報判斷；真人操作流程、載入耗時及權限測試未做。**僅額度顯示欄位與來源查詢PASS**。未變更 Notion 業務列、Schema／Formula／Relation、分享權限、Billing 或 GAS。Google Docs UX v3.4 已追加第十六節並回讀通過。[完整報告](audits/subsidy-usage-views-2026-10-24.md)。

## 2026-10-24｜青壯「一案一歷程、屆期行政結案」規則確認；TEST View已對齊

- **[USER-APPROVED BUSINESS RULE]** 使用者明確確認汐予青壯服務在**同一個案、單一Care Episode**完成；逾衛生局核定期限就結案，本所不再另接同個案青壯服務。正常青壯額度不需設計跨歷程加總；僅限青壯，不改其他政府方案的跨期／個案計次規則。**行政結案規則不是未經確認的自動化批次寫入指令**，歷程應在核對期限後依實際權限結案，未完成不能自動隱藏。
- **[VIEW UPDATE + READBACK PASS]** 直接修改既有[Care Episodes個案額度View](https://www.notion.so/3f68ca66aa4d81cca3b4ee43b4bd8dcf?v=4038ca66aa4d81a3ab1a000ca3244dce)，原地更名「青壯115｜個案使用額度（單一歷程）」、清除舊跨方案Quick Filter、固定以啟用115青壯Price Plan Relation過濾；顯示「開案日期」「結案日期」並保留原額度各欄。Fetch View確證新設定，Query **22筆**、無下一頁、**22/22皆匹配當期青壯**。
- **[WORKBENCH TEXT READBACK PASS]** 原[TEST補助工作台](https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf)②將個案View入口改為青壯單一歷程並加入屆期結案條件、既存重複測試資料不自動處理之說明；Fetch確認原Price Plans、心理師週額度、後方新Care Episodes linked database仍在、沒有新增黃色警示。
- **[TEST DATA EXCEPTION]** 22筆TEST青壯115歷程只對應21個不同個案Relation，1個個案有2筆青壯歷程（2筆**均帶測試標記**、都仍關聯啟用115方案）；全22筆目前狀態均「進行中」、未填結案日；當期Price Plan官方期程欄位為2026-01-01～2026-12-31，2026-10-24尚未到期，不能用新增決策冒充已實際結案。**不刪資料、不改其業務關聯或狀態**。
- **[FORMULA / REAL UX NOT PASSED]** 未取得Notion原生Formula/Rollup額度數值；未核實個別政府核定期限、真人權限、UI載入速度或用戶實際操作。只更新原View設定與工作台文字；Notion原業務列、Schema、Formula、Relation、其他View與權限、Billing/GAS均未修改。既有跨多政府方案設計保留。[詳細稽核](audits/subsidy-usage-views-2026-10-24.md)。

## 2026-10-24｜青壯額度 Views 續作唯讀回歸（15時）
- **[LIVE VIEW / SOURCE PASS]** 重新 Fetch「補助方案管理｜TEST」頁、Price Plans / Care Episodes / Sessions Data Source Schema（30／50／67欄），及治療所、青壯單歷程、心理師週額度3個原生 View。首頁仍保留「人工核對→Care Episodes 選方案」、單一歷程／期滿行政結案說明、原資料庫入口及無黃色提示。治療所 View 專用「補助＋政府方案」、青壯 View 固定115方案實例 Relation、心理師 View 在職臨床心理師篩選均未變。
- **[VIEW ROWS PASS]** 當次原生 Saved View 查詢：政府方案1筆、青壯115 Care Episodes 22筆、心理師週額度2筆，三者均 has_more=false；22筆皆「進行中」，依個案Relation去重21位，其中1位重複兩個青壯歷程，保留待人工核對；22筆結案日皆空白。當前Price Plan表列開始2026-01-01、結束2026-12-31，不代表每位個案首次服務三個月截止已驗。
- **[OPEN DATE CONSISTENCY PASS]** Saved View 的22筆 Care Episodes 中，20筆 `開案日期` 非空、2筆空白；比對 `😶 個案` Relation 確認兩筆空白者正是同一個案的兩筆標記 [TEST] 重複歷程，與前次稽核「該兩筆開案日期皆空」一致，**不存在先前誤記的『全部22筆開案日空白』衝突**。22筆結案日仍全空白，未改任何歷程狀態、日期或關聯。
- **[NUMERIC BLOCKED]** 同一 Price Plan 的核定總額、已完成、已預約為 `rollupResult://` 參照，已占用／剩餘為 `formulaResult://` 參照；Care Episodes 的完成／預約／剩餘與 Staff 本週有效占用／他處／狀態亦僅返回 Rollup / Formula 結果參照。另用 Price Plans 最小 `rows` 查詢回傳相同參照。無原生可核算數值、公式原碼，不能以22筆歷程或歷史Sessions狀態推定實際額度通過。
- **[SCOPE/NO NOTION WRITE]** 本次僅唯讀驗證，Notion原業務列／Schema／Formula／Relation／View／分享權限、Google Docs、Billing、GAS、Cloud Run／Session／部署完全未改；新增GitHub匿名驗收紀錄。`00.config_notion` 以名稱搜尋仍未精確定位；真人UX、載入效能、角色權限、計數與本地契約逐人截止日尚未實測。GitHub追加文字可由版本紀錄精準撤回，任何 Notion 資料無須回復。

## 2026-10-24｜青壯115使用額度畫面數值：使用者人工驗收 PASS
- **[USER CONFIRMED / VISUAL NUMERIC PASS]** 使用者檢視本輪呈現的三個 Notion TEST 額度 View 後，明確回覆「數值正確」。本所青壯115治療所政府補助使用額度、單一 Care Episode 個案使用額度、心理師本週使用額度的**目前畫面顯示數值**，列為使用者人工確認 PASS；「請使用者查看畫面數字」這一步完成，不因無法透過連接器直接取得原生數值而重做 View／公式。
- **[TECHNICAL LIMIT STILL OPEN]** 使用者的畫面人工確認**不是**本助手獨立取得 Notion Formula／Rollup 原生數字、逐筆公式驗算、不同核定期別／方案回歸、政府核銷、角色權限或效能 PASS。先前連接器僅回傳 formulaResult://／rollupResult:// 參照的客觀限制仍適用；留存既有技術 PENDING，而不是覆蓋成全部通過。
- **[SCOPE / NO NOTION DATA EDIT]** 本回合不修改 Notion Price Plans、Care Episodes、Sessions、Staff 任何資料列／Schema／Formula／Relation／View、權限，也未修改 Billing、正式 GAS／Cloud Run／Session／部署；原 TEST 重複歷程、屆期結案及其他政府方案的未驗項仍保留。
- **[GOOGLE DOCS READBACK]** 已在既有 [青壯跨年額度模型與 UX 規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit) 以 revision guard 追加第十八節使用者人工驗收，寫後回讀第十六、十七節與新第十八節均存在；[追加前原生備份](https://docs.google.com/document/d/1JTAtf8jUvvaE8rrvevDdhokkvAM9a3owdmXUhMS-Olw/edit) 亦已驗證無第十八節。回復只應精準撤銷該次新增段落，並保留並行修改；GitHub 亦可沿 commit 歷史還原新增節。
