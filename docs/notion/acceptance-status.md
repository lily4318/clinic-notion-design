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

## 2026-10-24｜青壯啟用TEST：角色權限本階段暫緩、其餘驗收續作
- **[USER DECISION / DEFERRED]** 使用者明確表示「角色權限目前無法設定，不需要處理，其他部分繼續完成」：本階段 Notion TEST 的角色權限設定與真人分角色驗收不再列為阻擋條件，狀態改 **DEFERRED（暫緩／不適用本階段）**，絕不標記 PASS，亦不更動任何分享設定。正式系統後端權限／fail-closed要求不因這項暫緩而解除。
- **[LIVE SCHEMA + VIEW PASS]** 重新 Fetch Price Plans／Care Episodes／Sessions／Staff／心理師補助週額度 Schema 與政府補助工作台；政府總額、青壯單一歷程及心理師週額度 Views仍存在，工作台既有入口與無黃色提示維持。Price Plans非刪除來源完整取回7筆，只有1筆政府方案（青壯115）；因此「多政府方案同時使用、同方案不同年／核定期」**尚無獨立測試案例**，不得冒稱通用公式跨方案驗收 PASS。
- **[WEEKLY KEYS / SCOPE PASS]** 心理師補助週額度原始 Saved View共6筆（無下一頁），以心理師 Relation＋Price Plan Relation＋週起始日匿名核查：6個不同鍵、重複0。4筆屬已啟用115青壯（10/11週2、10/18週2），另2筆連到一筆**目前 Notion Fetch 明示 deleted 的歷史隔離TEST方案**（10/18週1、10/25週1），不屬當前7筆可見Price Plans，不可當成新政府方案的有效跨期計算案例或現有心理師回報。
- **[UNKNOWN VS ZERO PASS / TIME GATE]** 2026-10-18～24週的啟用方案×兩位在職臨床心理師各1筆回報均為他處未確認、數字空白（UNKNOWN）；2026-10-11～17週兩筆已確認0屬**上週**，不得帶入本週；2026-10-25～31新週目前2位心理師×啟用青壯115方案**0筆回報**，且歷史隔離TEST 10/25筆不符合此作用域。這是截至10/24的唯讀來源／Relation驗收，並非10/25當天Notion原生週額度狀態驗收。無回報不能視為0／可安排；10/25週日換週的UI行為需屆時驗證。
- **[UX LINK STRUCTURE PASS / PERFORMANCE PENDING]** 原工作台及個案與歷程入口可Fetch；青壯人工資格核對→Care Episodes選Price Plan→方案、個案、心理師額度Views的連結存在，沒有回復已撤回黃色警示。此為路徑結構驗證，不是使用者實際點擊、任務時間、操作步數或Notion網頁載入速度測量；連接器往返時間不等於前端效能。人工畫面額度數值的 USER CONFIRMED PASS 保留。
- **[SAFE STOP / SCOPE]** 不建立第二個政府補助／年度方案、不改已啟用青壯Price Plan、Sessions、Episodes、Staff、週回報及其 Schema／Formula／Relation／View／權限；不改正式GAS／Cloud Run／Session。精確`00.config_notion`仍未定位，TEST字首不保證與啟用資料隔離；新增核心結構與真正隔離多方案端到端驗收須先提供前後比較並取得明確核可。此回合僅更新版本化驗收／規格，保留可回復性。
- **[GOOGLE DOCS VERIFIED]** [跨年度額度模型與UX規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit) 已用 revision guard 追加第十九節，修改後原第十八節與第十九節均回讀存在；[修改前備份](https://docs.google.com/document/d/1X0X71wtOR0Nw3RD-DdrGvVOxR9BfbhjiB4W0m1BTiew/edit) 回查未含第十九節。可保留並行修改後精準撤銷新增段落；本輪無Notion業務資料需回復。

## 2026-10-24｜他處無接案心理師免每週回報：已確認需求與待核可設計
- **[USER-APPROVED OPERATIONAL REQUIREMENT]** 使用者明確要求：**確定沒有在其他地方接案的心理師，不需每週確認他處使用次數**。這取代「所有在職心理師無當週回報一律待回報」的過度一體化操作要求；不意味未確認者皆可視為0，亦未核可現在直接重寫公式或批量套用現有員工。
- **[LIVE SCHEMA READ / CAUSE]** 重新讀Staff 55欄、心理師補助週額度19欄、Price Plans 30欄及在職心理師週額度View；Staff現有「執業類型」Select只有「本所執業／支援報備／不適用」，不能推導出該心理師是否在本所以外接案、是否在他處參與青壯。Staff既有`青壯本週他處顯示_自動`及`青壯本週額度狀態_v2_自動`是共享Formula，原碼僅`formulaCode://`參照未可驗證；現有週回報的`他處回報已確認`＋`他處已占用`仍是每週資料來源。
- **[PROPOSED MINIMAL DESIGN / NOT YET APPROVED]** 初期以Staff增加3個小欄位為候選：「他處接案情形」Select＝未確認／已確認無他處接案／有或可能有他處接案；「確認日期」Date；「免週回報有效至」Date（經確認且不可自動跨核定期別承接）。絕不直接借用`執業類型=本所執業`作免週報。已有外部接案者維持原週回報；確認全無外部接案者在聲明有效期間不須新建每週0次資料，使用本所Sessions計數並由週額度公式將「本所外」視為已確認0；其他未知、逾期、相矛盾、有外部案件而未回報時fail-closed。
- **[CONTROL / ACCEPTANCE GATE]** 需有申報及管理員確認日期、有效截止與生效區間；開始他處接案前更新狀態，若在週中變動則當週改採完整他處用量核對；若歷史週回報已有非0或衝突資料，禁止用長期免回報覆蓋。須隔離TEST驗證：新週免回報0、正常他處回報、未知、過期、週中變動、衝突及週日切週、不同期別不沿用；真人驗收與角色權限仍按先前分級，權限本階段DEFERRED。
- **[COMPARISON / ROLLBACK / SCOPE]** 現況每週所有人員皆可能被當成缺他處回報；建議改成僅已核實無外部接案者免週報，減少重複記錄與人工確認。風險是人員變更未申報或聲明逾期、原Formula依賴不明；須先備份Staff Schema及涉及的Formula/View／原值、驗證再最小修改，失敗時精準恢復3欄所涉設定／公式舊版本，保留並行改動及業務列。此輪**純設計＋唯讀核對，未寫Notion或Google Docs、未改正式系統**；因涉及新增Staff欄位及共用Formula，分級C，**尚待使用者對候選實作明確核准**。

## 2026-10-24｜使用者核准免週回報三欄位：Notion TEST已建立，公式整合硬停止
- **[USER APPROVAL]** 使用者回覆「同意繼續」，明確核准前一回合之三欄位方案：確實沒有在其他地點接案的心理師免每週重複確認；他處接案／可能有接案者按週回報。這是設計與最小實作核准，**不是**授權猜測現行共享公式、替現有心理師批次填零或覆蓋相關業務紀錄。
- **[NOTION STAFF SCHEMA WRITE / READBACK PASS]** 經重新 Fetch，TEST Backend 的既有 Staff Data Source 原有55個欄位、無目標3欄；以一筆明確DDL新增 `他處接案情形` Select（未確認／已確認無他處接案／有或可能有他處接案）、`他處接案確認日` Date、`免週回報有效至` Date。寫後重新 Fetch 為 **58欄**，三欄型別／選項吻合；現有在職心理師週額度 Saved View仍 **2筆、has_more=false**，新欄對該兩筆皆留空，**未設定任何人的免回報資格**。
- **[OLD VIEW/FORMULAS UNCHANGED]** 既有 Staff `青壯本週他處顯示_自動`、`青壯本週額度狀態_v2_自動`之Formula codeUrl與寫前相同，原心理師週額度View名稱、五個顯示欄完全一致。未修改Staff現存任何人員資料、週回報、Price Plans、Care Episodes、Sessions、Billing、其他Data Source Schema、Relation、Role、GAS或部署；暫無新增重算公式的運算負荷。
- **[13 POLICY CASES PASS (OFF-SYSTEM ONLY)]** 已對純決策規則執行13例離線測試：有效無他處可免週報、他處已確認2／0、未知或空值、未確認、缺確認日期、有效期不到週末、週中才確認、週中接案異動、現有非零回報衝突、跨方案／期別尚未覆核、僅有未確認數字等；13/13符合預期。**這不是Notion原生公式／UI PASS**。候選公式須確保`確認日≤評估週首日`、`有效至≥評估週末`、覆蓋當期Price Plan實例且無衝突，否則fail-closed；禁止用`執業類型=本所執業`推定無他處。
- **[FORMULA HARD STOP / FEATURE NOT LIVE]** 當前Notion Fetch仍只見Formula `formulaCode://`參照，直接Fetch參照回 `validation_error`，尚無全部現行公式**完整原文**、依賴、可驗證基準與隔離TEST；按專案硬停止規則**沒有更動共享公式**。因此目前「免週回報自動判斷」**尚未實際啟用**；人員填選「已確認無他處接案」也不會自動使本週額度放行，原有缺回報待核對規則仍適用。下一步需找出目前完整公式及對應回復基準，隔離測試再做最小公式整合，不能假稱全部完成。
- **[BACKUP / ROLLBACK]** 寫入前已確認三欄皆不存在、原Staff55欄、原View五顯示欄及兩個既有Formula codeUrl。需回復時先重讀最新Schema、先確認無任何人已使用新欄和無並行修改，再僅移除這次新增的三欄（現均空白）；不得移除其他Staff欄位或覆蓋原Formula／Role／業務列。`00.config_notion`精確原件仍未定位，這次使用當次直接Fetch的實際Data Source而非GitHub舊ID。
- **[GOOGLE DOCS VERIFIED]** [現用跨年額度UX規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit) 以revision guard追加第二十節，已重新讀回，第十九及二十節均存在，明確保留公式未啟用狀態；[修改前備份](https://docs.google.com/document/d/1XlRg7xVs1dV8Apey5V0EJLhHv2w-ikPP-c-bEZnETek/edit)重讀無第二十節。撤回時精準移除新增節，保留其他並行修改。
- **[FINAL NONDESTRUCTIVE ROW READBACK]** 最終另外回查原 Staff 主資料庫 Default Saved View 全部4筆（has_more=false）：4筆新增三欄均保持空白，無代填任何免週回報聲明。原心理師週額度 View仍是2筆，原週回報 Saved View仍有6筆（均has_more=false）。此為新增Schema後的資料留存檢查，不代表免回報公式已啟用或真正資料庫完整備份。

## 2026-10-24｜免週回報：公式原文安全追查與依賴定位（唯讀，尚未啟用）
- **[LIVE DEPENDENCIES VERIFIED]** 重新Fetch現行Staff58欄、心理師補助週額度19欄、Sessions67欄、Price Plans30欄及心理師額度View。Staff `青壯本週他處占用_自動`和`青壯本週他處已回報_自動`均從`🎫 補助週額度紀錄`關聯，對週回報Formula做SUM Rollup；Staff `青壯本週有效占用_v2_自動`從`關聯Sessions`的會談計數Formula SUM Rollup；週回報`心理師週上限_帶入`則Rollup Price Plans週上限。最終顯示／狀態為Staff `青壯本週他處顯示_自動`及`青壯本週額度狀態_v2_自動` Formula。上述只為可驗證Schema鏈，**Formula內部完整依賴仍未取得**，不能把空SUM當「已確認0」。
- **[SOURCE SEARCH / HARD STOP]** 已讀main最新基準、過去23章完整設計備份、7個既有青壯v3.x規格／備份、另外4份原Schema／View備份、三份Notion TEST設計與驗收紀錄；僅有舊案例數值/行為PASS、Formula名稱或`formulaCode://`參照，**未見與現在相同的完整原文**。Notion `fetch(formulaCode://...)` 仍不支援（validation_error）；故不重寫共享Formula、不建立新Relation／欄位或業務測試列，也不調整既有2名心理師。
- **[OFFICIAL API vs CONNECTOR]** 由[Notion官方資料來源API](https://developers.notion.com/reference/retrieve-a-data-source)及[Property object說明](https://developers.notion.com/reference/property-object)確認官方認證後的 Data Source Property含`formula.expression`；現有Notion connector的`fetch`卻只顯示`codeUrl`指標，未提供直接請求原始API的已授權動作。不能傳Token到對話、GitHub或Web，也不能以歷史備份／自編公式覆蓋當前業務邏輯。
- **[INTEGRATION GATE]** 必須先取得當前Staff `青壯本週他處顯示_自動`、`青壯本週額度狀態_v2_自動`兩份Formula完整原文（在Notion屬性→編輯公式複製），再核對依賴的週回報公式完整原文、製作**可回復的原始表達式備份**及最小差異，才能在確實隔離的TEST驗證免回報、已確認0、未知、期滿、週中異動、衝突、週日換週、跨方案期別，切勿把本輪視為功能已啟用。
- **[UNCHANGED/TEST]** 本輪Notion全部零寫入，Staff新增3欄保持先前已完成狀態、原共享Formula／View／Relations/Rows及本期Price Plan不變；未啟用自動免週回報，角色權限DEFERRED，未進行真人效能測試。回復僅涉及本回合文件增補；本輪不需Notion資料回復。
- **[DOCS VERIFIED]** [Google Docs現行青壯額度UX規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit) 已以revision guard追加第二十一節，寫後回讀確認第二十、二十一節存在；[修改前備份](https://docs.google.com/document/d/16pDQkusnEuRsqLMct8-R1eU4HnzRsv0ni5uSm2sr-dQ/edit) 回讀無第二十一節。精準回復僅撤銷新增文字，保留其他編輯。

## 2026-10-24｜使用者要求學習成果實際活用：補助工作台UX v3獨立預覽（待真人確認）
- **[USER UX GATE]** 使用者明確反映Notion版面仍醜且難用，質疑學習成果是否真的被活用，要求先確認實際設計成果再繼續其他功能。這是修正設計優先順序的要求，**不是對UX v3最終版面的審美核准**；青壯免週報Formula工作線維持暫緩，角色權限依原決定DEFERRED。
- **[LIVE TEST PREVIEW]** 原[政府補助工作台](https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf)未覆蓋，在TEST行政管理下建立[UX v3獨立預覽](https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f)。首屏3種額度入口（治療所／個案／心理師），接著2張日常任務卡，歷史備查收合，底部3張精簡Linked Views；使用者可真實開啟並比較，不是靜態概念圖。
- **[LEARNING TRANSFER]** 對照Notion官方「閱讀者導向＋Callout／Columns／Toggle」、「減少首頁Inline DB與顯示屬性」、「各View獨立配置」及Business OS／Company OS／營運Dashboard範本之Quick Actions。實施成果：同一用途原頁7個Inline DB→預覽3個；治療所顯示欄11→7、心理師5→5、個案11→8；不新增假KPI、黃色警示或資格工作流，亦不宣稱完成過去要求1,000／10,000篇模板研究。
- **[STRUCTURE/DATA PASS]** 新三個View已Fetch核對欄位、順序、篩選、Relation目標；保存View查詢顯示治療所本期政府方案1筆、在職心理師2筆、青壯115單一歷程22筆，全部has_more=false，與舊View查詢筆數完全一致。Notion原始資料與既有Schema、Formula、Relation、原View、業務列皆未變。新TEST Linked Views共享來源，不等於業務資料隔離。
- **[HUMAN/PERFORMANCE PENDING]** 操作入口可見、配置與資料範圍PASS，**未**證明視覺舒適度、真人1-click體驗、手機排版或實際網頁載入變快。待使用者真實比較完成三任務：首屏找到三額度並點入、開始個案選方案、辨識免週回報公式仍未啟用。未獲認可不覆蓋原工作台、不續作公式。回復僅精準撤銷新預覽與其3個Linked Views，原頁已保留。
- **[EVIDENCE & DOCS]** 實際來源→設計→原生Notion實作及回查詳見[專項稽核](audits/subsidy-ux-v3-learning-applied-2026-10-24.md)；[Google Docs跨年額度UX規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)新增第二十二節並回讀，已建立[增補前備份](https://docs.google.com/document/d/1J3Z9zhvjtb53Ik06_JxTXobQ1s0oKsR1eyAc5WxYcpQ/edit)。

## 2026-10-24｜使用者驗收採逐題、具體操作、簡碼回覆（已確認）
- **[USER CONFIRMED]** 使用者指出「請評估美觀、直覺、好不好用」太籠統，要求每次請使用者驗證時：**逐題明確列出要點什麼／看什麼／通過條件**，提供容易回覆的固定選項（A=符合、B=不符合、C=未測試），可只回「1A 2B 3C」等簡碼，遇B才選擇補一句原因；**不應要求自由敘述整體感想**。
- **[TEST UX V3 CHECKLIST]** 本輪新預覽 https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f 。本次人工驗證四題：(1)開頁第一眼能否看到並區分「治療所／個案／心理師」三額度入口；(2)點「查看治療所本期額度」，能否看到正確的本期補助額度表；(3)回預覽點「開啟個案與服務歷程」，能否找到既有歷程／收費方案入口（只看不更動）；(4)點「查看心理師週額度」，能否看懂本週用量及狀態；(5)整頁字距／卡片／表格是否容易閱讀、視覺舒適。每題可選A/B/C，最後可選擇補充不順手部位。
- **[ACCEPTANCE LEVEL]** 之前數值與Linked View範圍的結構PASS維持；上列5題尚待使用者真人作答，不能填PASS或猜測。只需在現有Notion UI導覽、不建立或修改實際個案／Staff／會談列；新TEST預覽與舊頁都連接原資料庫，標記TEST不構成隔離。原GAS、Cloud Run、Session、共享Formula、Role全部保持不變。
- **[GENERAL RULE]** 以後所有需使用者驗證的 Notion／專案功能，每題給明確入口／操作／預期結果／選項，將「不用測」、「無法測」、「失敗」分開；只問此輪所需的最少題數，能用連接器自動驗證的不要轉嫁使用者。使用者提供簡碼後逐題記錄成功／不成功／未測，失敗先針對該題最小修改，沒有完成的驗證不假稱通過。

## 2026-10-24｜使用者實測UX v3：1B～5B全部FAIL；同頁直顯v4已建立（待驗收）
- **[USER CONFIRMED / UX v3 ALL FAIL]** 使用者逐題回覆 `1B 2B 3B 4B 5B`，5/5均不符合；第3題找不到先前指稱的「個案與服務歷程」操作。明確需求：**資料直接在目前頁面顯示，不要靠點擊跳別頁查看；大量說明文字應移除，一眼就能看懂**。v3原本資料範圍1／2／22的結構PASS不等於UX PASS，實際操作／視覺仍FAIL；先UX，後免週報Formula。
- **[CAUSE / MINIMAL FIX]** 原TEST v3預覽頁先顯示介紹、3張額度跳頁卡、2張任務跳頁卡及長文字，3張真正資料表卻放在最底下。已將**同一個預覽頁** https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f 更名直接顯示UX v4，完全移除頂部卡片與跳頁說明，改為四段短標題後立即放4張**inline Linked DB Views**：治療所額度、心理師週額度、青壯個案額度、進行中服務歷程之「💲收費方案」可見且可在原生View直接編輯的欄位（驗收時只看不操作業務列）。歷史／他處待確認提醒保留在唯一收合區，不新增黃色警示。
- **[SCHEMA + VIEW READBACK PASS / UX PENDING]** 維持原三資料源、三既有v3精簡View及原方案篩選；前兩張View列數1／2，第三張青壯115 Relation View 22筆，第四張新建在職? **不是Staff**，是Care Episodes既有來源篩選「狀態＝進行中」，View `view://4038ca66-aa4d-81b2-b733-000c7ed4394b`，38筆。四者has_more=false，對應欄位SHOW 6／5／6／4，第三與第四皆直接顯示「💲收費方案」。前3張數量與原一致，來源分別Price Plans／Staff／Care Episodes。Notion Fetch頁面確認四個inline資料表直接相鄰短標題且位於最上方，沒有原導覽Callout；尚無真人實際載入時間、視覺／行動裝置／可操作性PASS。
- **[BACKUP/ROLLBACK]** 已在編輯前原生Duplicate v3頁面並Fetch確認保有三張舊Linked DB與原卡片；備份 https://app.notion.com/p/4038ca66aa4d811eafe0c857a6394638 。原官方TEST工作台 https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf 未觸碰。僅v3預覽頁與其專用View顯示欄變動、新增一張同源Care Episodes Linked View；要回復先核對並行變更，以備份精準還原預覽頁與v3既有SHOW欄位，移除第四Linked View但不刪除原Care Episodes資料庫。
- **[SCOPE / PERF]** 沒有變更Price Plans、Care Episodes、Staff、Sessions、Billing、週回報等任何業務資料列、Formula、Schema、Relation、原營運Views或權限；角色權限仍DEFERRED，青壯免週回報公式仍NOT LIVE。v3只有3個inline資料庫，v4有4個，**可能增加載入量**，是否變快未知；用多一張直接可見服務歷程View換掉跳頁。
- **[MANUAL RETEST GATE]** 請真人逐題驗證：①開頁是否立即看到「治療所本期額度」表，不點跳頁；②下捲是否直接看到心理師與個案兩表；③「服務歷程」表是否直接顯示「💲收費方案」並知道可在原頁操作（**勿更動真資料**）；④整頁是否少文字、容易閱讀。各題A符合／B不符合／C未測。使用者尚未回覆，不得將v4寫作UX PASS或直接覆蓋原工作台。
- **[DOCS VERIFIED]** [現行Google Docs規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)新增第二十三節；讀回確認22/23並存，明示五題FAIL與v4。修改前原生Google Docs[備份](https://docs.google.com/document/d/1SKgodaTjbxWatRZB-nrQz0IyxptQ1Dh7__8jecQpmrU/edit)已讀回確認無第23節。

## 2026-10-24｜UX v4使用者4/4 PASS；新增首頁異常與最後一次候選提醒（TEST待驗）
- **使用者真人驗收**：UX v4 `1A 2A 3A 4A`，原四題4/4 PASS；補充提出異常提醒、最後一次候選提醒與資料庫解說，**新需求尚待真人驗收**。
- **TEST 實作回查**：預覽頁頂端加入青壯待核對 View（開案日期缺漏或他處未確認）2筆、補助剩餘1次候選 View 11筆；保留原3額度View，38筆廣義歷程管理View移入底部Toggle；Notion Fetch確認6 linked views及排列。只是原有資料來源的Linked Views，未改Schema、Formula、資料列、原營運View或正式部署。剩餘1次不等於下一個已預約就是最後一次。
- **回復**：Notion原生備份 https://app.notion.com/p/4038ca66aa4d8159b4e5daf90a4ae662 ；Google Docs第24節備份 https://docs.google.com/document/d/1kEm7zDMddObchiJfritf9b21TaIJPDsa7i8_uEYlgf4/edit 。免週報自動Formula仍未啟用，角色權限本階段DEFERRED；UX新警示需使用者另測。

## 2026-10-24｜UX v4.1驗收1A／2B／3A／4A；僅修第2題至v4.2
- **[USER VERDICT]** 使用者送出UX v4.1結果`1A 2B 3A 4A`，第1異常／第3三額度／第4次要收合均PASS保持不變；第2「最後一次提醒」明確FAIL，僅單點修正第2，不重測其他3項，勿繼續青壯免週報Formula整合（仍NOT LIVE）。
- **[CAUSE CONFIRMED]** 舊第2 Alert View以`個案補助剩餘_自動`顯示文字1篩出11筆；用同一Care Episodes之`💬 關聯會談`追查Sessions狀態，8筆為已完成1＋已預約1（預約只是青壯三次中的第2次），3筆為已完成2＋未預約（最後一次待安排）。因此原來11筆不能稱「下一次已預約就是最後一次」，源頭是未區分「剩餘可用次數」及「已占用預約」；數字與匿名來源經回查，不複製個資。
- **[V4.2 LIVE TEST VIEW CHANGE PASS]** 唯一改動現有專用View `view://4038ca66-aa4d-81e3-bfbd-000cfc0ac598`：名稱改`⏳ 最後一次已預約｜額度占滿待核對`；保留同一青壯115實際Price Plan Relation＋進行中，Formula Filter由原文字`1`改為文字`0`；SHOW加入`下次會談預約_自動`、`他處使用已確認`，仍顯示已完成／已預約／剩餘／狀態。Saved View查得3筆，透過對應Sessions匿名逐筆二次核對**3/3均已完成2＋已預約1，預約日期完整、他處已確認0**。這是本日期／本方案已預約最後一次之核對候選，不能當作Notion公式完整表達式或跨期規則自動正確已驗。
- **[LIVE PAGE + PRESERVATION]** 同一TEST預覽 https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f 更名 UX v4.2；僅第2區短標題改為「⏳ 青壯｜最後一次已預約（待核對）」及收合區對應說明。Fetch確認原第1異常2筆的View與原3額度View及兩Toggle保留，頁面仍六張Linked DB且無新的展開表。Price Plans、Care Episodes、Staff、Sessions、補助週回報等原始資料列與Schema、Relation、Formula／正式營運Views、權限、GAS／Cloud Run均不變；效能未新增展示表，但真人載入未量測。
- **[BOUNDARY/OPEN ISSUE]** 3筆`已完成2＋尚未預約`目前在原「個案額度」表可見，但**未**收進「最後一次已預約」提醒；要自動細分「最後一次待安排」與「已預約最後一次」而不漏人，仍需能被Notion View正確保存的原生條件或安全新增的Formula。隔離TEST探測中對Rollup`本歷程已完成_帶入`設定FILTER時工具未保留該條件，不能將不生效之View當自動排除依據；主View現階段不宣稱跨期／跨方案全部有效。後續依使用者選項決定是否另設待安排提醒。
- **[BACKUP/ROLLBACK]** 修改前已原生Duplicate UX v4.1頁 https://app.notion.com/p/4038ca66aa4d81d89cb1e7c1a6c12273 ，Fetch證實原6張Linked Views與舊提醒標題；備份頁**後續增加一張TEST過濾探測View（共7張）**，不宜全頁盲目覆蓋。原提醒View完整舊條件（PricePlan Relation＋進行中＋剩餘文字`1`）、舊SHOW已記錄，回復需讀目前配置後只改回舊Filter及SHOW並精準恢復第2區標題；原營運頁面與原資料庫不需回復。Google Docs原生修改前備份：https://docs.google.com/document/d/1OUxhsMSIJZBOipqjwJDmOv3n_L48TGZT_oKv1K-axu8/edit 。
- **[DOCS VERIFIED/RETEST]** [Google Docs青壯方案規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)已以revision guard增補第25節，回讀原24與新25皆存在；備份第25節不存在。第2題v4.2真人驗收**PENDING**，第1／3／4保留原A結果不重測。

## 2026-10-24｜UX v4.2 最後一次補助提醒：使用者人工驗收PASS（4/4完成）
- **[USER CONFIRMED / UX PASS]** 使用者明確點選「UX v4.2 第2題：A，現在符合需求。請記錄PASS，保留其他已通過項目。」記錄第2題「最後一次已預約提醒」**使用者人工UX PASS**，原第1異常、第3三額度直顯、第4次要收合均保留既有PASS。四項UX驗收完整為1A、2A(v4.2)、3A、4A；舊v4.1第2題B仍是歷史失敗紀錄，勿改寫過去。
- **[CURRENT TEST CONFIRMED / NO NOTION WRITE]** 唯讀Fetch確認現行[TEST UX v4.2](https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f)仍有第2「最後一次已預約（待核對）」區、異常警示、三種額度資料表、六個原Linked DB與兩個Toggle；第2專用View `view://4038ca66-aa4d-81e3-bfbd-000cfc0ac598`仍以當期Price Plan、進行中、剩餘0篩選，未改業務資料或計算。
- **[ACCEPTANCE LIMITS / FUTURE WORK]** 這是使用者對**版面及提醒呈現**的驗收，不代表Formula原文已取得、跨方案／核定期別通用公式、效能或權限PASS。3筆尚未預約但剩餘最後1次的歷程未在「已預約」提醒中，不另新增待安排警示（使用者此次確認A並未要求擴充）；角色權限DEFERRED。Staff免每週他處0回報的Schema三欄仍存在，但共享公式整合仍NOT LIVE，**本輪不續作**。
- **[DOCS/ROLLBACK]** [Google Docs青壯UX規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)以revision guard新增第26節並回讀確認原25與新26共存；[增補前原生備份](https://docs.google.com/document/d/1t-HtAnmQjc9LSwXh02vrnwsdgfrF5wVHKoXxrcYHV_k/edit)已讀回第26節不存在。本輪Notion沒有寫入、沒有新效能或權限影響，無Notion回復作業；需撤銷文件時只移除本節，保留並行修改。

## 2026-10-24｜青壯完成核定次數但未結案：預約提醒應改為轉自費或結案
- **[USER CONFIRMED REQUIREMENT]** 使用者要求青壯方案完成3次但Care Episode仍在進行中時，個案與服務歷程管理頁不得繼續顯示一般「預約下次」，而應提醒「轉自費或結案」。僅是對提醒流程的明確需求；不得擅自結案、改會談收費方案或直接按未核實的「青壯轉自費」資料庫按鈕。既有UX v4.2四項人工PASS保留。
- **[LIVE CAUSE]** 重新Fetch實際TEST `02_Cases and Care Episodes` https://app.notion.com/p/a188ca66aa4d82c69764810ab99f8663 及其linked DB `https://app.notion.com/p/68f8ca66aa4d83deb2060154fbc3a052`：原 `view://0128ca66-aa4d-83a6-8711-08f23fa15fce`「未預約下次會談」以Episode狀態進行／待辦群組AND`下次會談預約_自動`=`未安排`判斷，完全**沒有補助已完成達上限排除條件**（當次Saved View 32筆）。Cases還有`下次會談預約_自動(顯示)`、Episodes有`歷程摘要_自動(顯示)`共享公式；需同時核對文字呈現，不可只改View但保留其他地方的錯誤提醒。
- **[ACTUAL TEST COHORT]** 現行115青壯Price Plan的每案上限=3，當期22筆青壯Care Episodes匿名連結41筆Sessions；`有效已完成≥3且仍進行中`為**0筆**，已完成2＋已預約1有3筆。因此找出結構風險不代表「完成3的提醒」已具Notion原生PASS；不得改真實會談狀態做測試。
- **[PROPOSED SCOPE AND PRIORITY]** 最小實作預計僅在Care Episodes按**實際Price Plan實例**取該期每案上限並計對應`已完成`的Sessions（取消、改期、no-show、一般自費與僅預約不計），若Episode未結案且已完成≥核定上限，優先提示`補助次數已完成｜轉自費或結案`，從普通`未預約下次`排除；同時若已預約下次則加獨立超額預約核對提示。不滿額者仍走原流程，已轉自費者依自費規則，已結案者不提示。外部未知不得被當0，但已在本所確認完成滿額時應顯示處置提醒，外部待核對可另列；跨方案／期別各自算。
- **[HARD STOP AND TEST]** Episode與Cases原Formula `formulaCode://`皆無完整原文、`青壯轉自費` Button現有Action也不可從連接器驗證；不能猜測覆蓋共享Formula，更不能改`💲收費方案`關聯導致已完成歷史補助紀錄統計消失。實作前先取得可回復的原Formula／按鈕配置與完整依賴、核對設計前後及獨立TEST隔離，重要結構/公式修改另須精確核准。本輪僅唯讀＋離線**11/11決策案例PASS**，不是Notion本機Formula、UI或週限驗收；無Notion資料、Schema、View、Formula、角色權限、正式GAS改動。
- **[SPEC & BACKUP]** [跨期方案UX規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)已以revision guard追加第27節，回讀第26/27節；[新增前備份](https://docs.google.com/document/d/1lT4mzcL4lVhvIBIePxdiFNCRUcXCIypSzwTFY6wVw3o/edit)回讀沒有第27節。本輪沒有Notion變更需回復；要撤銷本輪文件變更精確撤去第27節／GitHub本段並保留其他同步修改。角色權限維持DEFERRED，免週回報Formula仍NOT LIVE。

## 2026-10-24｜滿額後轉自費或結案：使用者已核准，但公式與按鈕無法回查而硬停止
- **[APPROVAL]** 使用者同意在 Notion TEST 為補助額度完成且未結案的 Care Episode 顯示「轉自費或結案」，取代普通未預約提醒；並明確要求先取得原共享公式及 `青壯轉自費` 按鈕的安全基準，未取得時停止覆寫。
- **[LIVE SOURCE / BLOCKER]** 重新Fetch實際「個案與服務歷程管理」及原「未預約下次會談」View，原條件僅 `狀態=進行中／待辦` 且 `下次會談預約_自動=未安排`，沒有補助滿額排除。Care Episodes原`下次會談預約_自動`、`歷程摘要_自動(顯示)`、`個案補助剩餘_自動`、`個案補助狀態_自動`、Cases `下次會談預約_自動(顯示)`等公式在Notion connector只提供codeUrl，Fetch `formulaCode://`與`collectionProperty://`均validation_error；按鈕`青壯轉自費`只呈現type=button、無action。Google Docs舊規格與備份亦無可證明為現況的完整原文；`00.config_notion`未找到精確原件。
- **[HARD STOP]** 依使用者明示的停止條件，**本輪對Notion全部唯讀，不改任何Formula、Button、View、Schema、Relation、Episodes或Sessions資料列**，不以Formula「剩餘0」取代真實已完成達上限（已預約最後一次但未完成亦可能剩餘0），不觸碰原先UX v4.2四項使用者已通過的介面。
- **[ACCEPTANCE]** 按當次真實方案資料，青壯115每案上限3，22筆青壯Care Episodes關聯41筆Sessions；目前已完成3且尚未結案的案例為0，不能宣稱新增滿額分支已通過原生Notion回歸。前輪離線決策規則11/11為設計測試，**不是新功能實測**。此項標記`APPROVED / BLOCKED BY MISSING EXACT FORMULA & BUTTON ACTION / NOT IMPLEMENTED`，角色權限DEFERRED，免每週回報的Formula也仍NOT LIVE。
- **[RESUME & ROLLBACK]** 可安全繼續前必須讀取**現行**Care Episodes的`下次會談預約_自動`、`歷程摘要_自動(顯示)`、Cases的`下次會談預約_自動(顯示)`完整公式，以及`青壯轉自費` Button動作，再比對已完成Session與Price Plan上限／原方案Relation、備份原始定義、隔離TEST。不可用歷史猜測或要求Token；本輪無Notion寫入、無Notion回復作業，文件更新可精準撤回，不覆蓋並行修改。
- **[DOCS]** Google Docs[青壯方案額度UX規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)已追加第28節並實際讀回確認27／28共存；[本節前原生備份](https://docs.google.com/document/d/1ZgskUXhRdIGGjSV315csgl762xoMxyCQo1DC6f1gQ90/edit)已讀回不含28節。

## 2026-10-24｜滿額轉自費／結案提醒續查：原文仍不可讀、直查額度暫時耗盡
- **本輪僅查證，Notion零寫入。** 已重新Fetch TEST Care Episodes Data Source 50欄、Cases 49欄、Sessions 67欄、Price Plans 30欄，以及原`未預約下次會談` Saved View及UX v4.2。Care Episodes `下次會談預約_自動`、`歷程摘要_自動(顯示)`及Cases `下次會談預約_自動(顯示)`依舊只提供`formulaCode://`、沒有expression；`青壯轉自費`只返回button類型，沒有action。無可驗證原始設定及回復基準，**按已核准硬停止，未修改Formula／Button／原View／資料。**
- **新的唯讀觀察：** 使用`mode=view`重新查Saved View，青壯115服務歷程現有22筆、全為進行中；原「未預約下次會談」現為33筆（前輪32筆），當期方案額度View為1筆。這只代表本次View現況，不推定特定個案或已完成3次狀態變更；公式回傳`formulaResult://`參照，不能冒稱原生數值已直接取回。原UX v4.2六個Linked DB及最後一次提醒仍在，先前四題真人PASS保留。
- **查詢阻擋：** Notion connector回應此工作區`query_data_sources`的`rows/sql`額度已用盡、約一小時內重置，要求不要立刻重試；此次rows查詢未執行，無副作用。`mode=view`仍可使用；工具的套餐選項不是更換方案或必須付費才能讀Formula完整expression的證據。已停止嘗試直接查詢，未驗證新的Sessions逐筆狀態。
- **後續必要條件：** 從Notion現行公式編輯器或可授權且直接返回`formula.expression`／Button action的正式能力，取得完整原文與設定並建立可回復基準；沒有這些不能對共享Reminder作推定式修改。此輪沒有Notion schema/業務資料/權限/效能影響，免週報公式亦仍未啟用。

## 2026-10-24｜已取得使用者提供的預約公式；截圖3個疑似舊Formula不可直接刪除（有Cases依賴）
- **[NEW USER SOURCE]** 使用者貼出Care Episodes `下次會談預約_自動`完整Notion公式；精確原文已存入[Google Docs跨期UX規格第29節](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)，並以revision guard寫入、讀回，附[新增前備份](https://docs.google.com/document/d/1QRBOf06I9tbzf3lN5UdaDJyt05u1CC35Si9QZFs56JA/edit)。**這是使用者提供的現行公式原文、未由connector獨立取回expression**；寫回前仍需比對當下編輯器。
- **[ROOT CAUSE]** 原公式只找`💬 關聯會談`中`預約時間>=now()`且不是`已改期/已取消`的下一筆預約，否則`style("未安排","red")`；並無政府Price Plan、每案完成次數、是否結案的先行分支，因此原`未預約下次會談`View會把已完成補助上限但未結案者錯誤列入。不可把`個案補助剩餘=0`直接等同已完成上限，因最後一次已預約也可能令剩餘0。
- **[USER DELETE REQUEST / HARD STOP]** 使用者另要求刪除截圖中的3個Σ青壯115欄位。Fetch現行Care Episodes(50欄)與Cases(49欄)確認三個**仍被跨資料庫Rollup直接引用**：Care Episodes `青壯115他處使用數_自動`(V3dWRw)→Cases `青壯115他處已使用_自動`；`青壯115他處回報有效_自動`(UGhgdQ)→Cases `青壯115他處確認筆數_自動`；`青壯115方案歷程標記_自動`(Wj1cQw)→Cases `青壯115關聯歷程數_自動`。空白或0不表示無依賴；**沒有DROP**，先提出安全隱藏或完整汰換後移除的路徑。
- **[SCOPE / BASELINE]** 目前已取得一段完整Formula作為候選修改基準，但Cases `下次會談預約_自動(顯示)`及Care Episodes `歷程摘要_自動(顯示)`仍僅formulaCode參照，`青壯轉自費` Button設定僅type=button、無動作詳情。依使用者「不知原文即停止覆寫」的核准條件，本回合不改任何Notion Schema、頁面排版、View、Formula、Button、業務資料；不自動結案、不覆寫既有補助Session歸屬。原UX v4.2 4/4 PASS保留，角色權限DEFERRED，免週報Formula未啟用。
- **[VISIBILITY RISKS]** Notion Data Source目前Fetch未暴露custom page-layout；使用page_layout隱藏三個欄位會影響整個Care Episodes來源的所有紀錄頁，不能未經確認用全新layout覆蓋預設版面。單純從個別View HIDE也不保證頁面屬性區不出現。此輪沒有Notion寫入及新增效能負擔，也沒有Notion rollback必要；Google Docs修改可只撤回第29節並保留並行編輯。

## 2026-10-24｜使用者要求永久刪除三組舊青壯115欄位與全部對應依賴（待安全清理）
- **[USER DECISION]** 使用者在確認截圖三個Care Episodes舊Σ欄位有Cases Rollup依賴後，明確要求「刪除所有對應的屬性」。解讀為**永久汰除三組來源與其真正無用的下游**，不是隱藏；不擴大為無差別刪除所有`青壯115`前綴的當期業務功能。此要求已有刪除意向，但尚未通過可靠恢復與無關公式依賴測試。
- **[LIVE DEPENDENCY MAP]** 本回合重新Fetch Notion TEST Care Episodes 50欄、Cases 49欄：Care Episodes `青壯115他處使用數_自動`(V3dWRw)→Cases `青壯115他處已使用_自動`Rollup；`青壯115他處回報有效_自動`(UGhgdQ)→Cases `青壯115他處確認筆數_自動`Rollup；`青壯115方案歷程標記_自動`(Wj1cQw)→Cases `青壯115關聯歷程數_自動`Rollup。均是真實Rollup targetPropertyUrl直接證據，至少六欄。
- **[UNCERTAIN INDIRECT DEPENDENCIES]** Cases現存`青壯115他處顯示_自動`(Formula UT55fA)、`青壯115額度狀態_自動`(Formula R0d3YA)及其他可能引用上述Rollup的公式/Views；Notion連接器僅有formulaCode參照、**無formula.expression**，不能證明刪除後公式完整。EP/Cases皆有原生`<page-layout>`設定含六欄或其顯示位置。此輪未取得完整可回復來源Formula與依賴閉包，故**硬停止，不執行DROP COLUMN**；不能先刪三個Cases Rollup後放任啟用公式錯誤。
- **[STATUS/SCOPE]** 0筆Notion寫入、原50/49 Schema、所有原業務資料／Views／Rollup／Formula／Button／Page Layout與原UX v4.2 4/4使用者PASS保持不變；政府補助滿額轉自費或結案提醒和免每週回報整合仍未啟用，角色權限DEFERRED，正式GAS/Cloud Run/Session不在範圍。本輪沒有執行Native Notion刪除、效能或還原驗收，不得標示清除完成。
- **[NEXT SAFE GATE]** 需從目前Notion取得被刪來源與受影響的全部公式完整expression、檢查其他Formula/View/Button依賴、保存每個Data Source的Schema/Page Layout及可重建之運算邏輯，先在真隔離TEST做依賴遷移與刪除順序演練，再確認跨期補助額度、Cases、Sessions與原有UI不受破壞。Notion屬性刪除再新增可能生成新property ID，**不能保證原生回復**，不得只用名稱與schema類型當安全備份。
- **[DOCS/BACKUP]** [青壯跨期UX規格第30節](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)已記錄原生字段級依賴與硬停止，guarded write/readback PASS；[修改前Google Docs備份](https://docs.google.com/document/d/1rmVZTz0J4e-7odp_Miff_W8pgNLd7-1F7hkpyfxnWro/edit)回讀沒有第30節。此次沒有Notion資料更動、無Notion回復。
