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
