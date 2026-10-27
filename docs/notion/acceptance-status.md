# 青壯與通用補助｜Notion TEST 驗收

## 2026-10-26｜方案參與模型與已同意清理完成

目前模型以 Price Plans 保存方案與核定期規則；「補助方案用量」按個案＋方案期別保存用量；新增的「心理師方案額度」按心理師＋方案期別保存接案確認與本週摘要，沿用既有週回報。主檔僅保留通用關聯，新增方案／年度不再增加專用輸入欄位或改年度常數。服務歷程依個案與收費方案查閱。

使用者已明確同意精確清理範圍；Staff 的「額度查閱方案、補助本週摘要_自動、免週回報方案、他處接案情形、他處接案確認日、免週回報有效至」六欄及兩補助頁的四個舊人員檢視均已實際移除並回查。各頁只保留新來源的「各方案｜本週額度」「各方案｜他處回報設定」。人員、週回報與會談來源未刪除。其他有相依的歷史青壯欄位不在此次六欄清理範圍，新方案不用它們。

原生現有資料計算已回查；9 個離線合成模型情境通過，不等於多個真實方案整合、真人 UX、角色權限或載入速度通過。詳[資料歸屬修正報告](audits/subsidy-ownership-model-2026-10-26.md)；舊階段與舊 Staff 摘要公式僅作歷史／回復依據。

## 2026-10-25 實作／2026-10-26 清除回查｜共用用量實作回查完成，真人操作待驗收
以[完整實作報告](audits/subsidy-usage-ledger-implementation-2026-10-25.md)為本輪現況；下方舊「零寫入／僅提案／0新DB」是先前階段，不代表本次結果。

- 已執行並回查：獨立用量庫、個案＋方案期別查閱、20/20原生完成／預約／餘額與移轉輸入核對；兩方案含下一期隔離、取消排除、負數超額、重複／缺用量警示；心理師不同週起算／上限、有效免報、錯期及矛盾回報測試。
- 2026-10-26經使用者明確同意，本次14筆合成測試紀錄已移到垃圾桶，逐筆確認deleted 14/14。移除測試暫時篩選後，兩原補助頁各20筆用量／2位心理師／1啟用政府方案，來源亦20筆，查詢均無下一頁。未清除其他歷史測試資料。
- 8個新通用公式不含青壯／115／116／2026／2027常數；歷程不新增專案用量輸入欄。歷史專用欄仍有相依，保留而退出日常填寫，不能宣稱全工作區公式已通用。
- 待人工：使用截止日及間隔／資格核實；13筆日期已過仍標預約的狀態；真人UX、實際載入時間、角色權限未有新PASS。
- 最少真人驗收（A符合／B不符合／C未測）：1開頁即見個案餘額與日期提示；2同頁「回報／期限核對」看得到可編輯欄；3展開服務歷程，同案同方案餘額與用量一致（不更改真實方案）；4心理師直接顯示本所／上限／回報狀態且可找到回報設定。可回「1A 2A 3A 4A」。

## 2026-10-25｜唯讀精簡審查完成：資料狀態優先於新功能
已完成[本次精簡審查](audits/subsidy-minimum-design-review-2026-10-25.md)：兩補助頁7種來源重疊、歷史檢視依賴公式狀態文字、免報提案矛盾；13筆預約日已過仍標已預約須人工核對。保留三區同頁、單一計數來源、少填寫；暫緩自動規則與額外必填。Notion零寫入，公式值與載入秒數未測，不宣稱修正PASS。GitHub曾遇409並行衝突，本次從最新SHA重新讀取並只新增本節，保留其他增量。


## 2026-10-25｜同頁方向符合期待；僅本所常見情況與複雜度審查
使用者確認目前版面方向符合期待，補充部分心理師只本所接青壯、多數個案只本所使用。已唯讀核對Staff免回報三欄、Care Episodes他處確認三欄及原週回報。設計收斂為有效確認內免零週報、個案核實0後不重複填另一套表；空白/未知不自動0，矛盾或跨期重核。第一階段0新DB、0新人工必填；候選0–2欄（可核實首次服務的截止顯示、真正跨方案的免報範圍），需先查既有能力，非決定現在新增。[更新後提案](proposals/subsidy-workflow-design-2026-10-25.md)。Notion零寫入；方向確認不等同公式/UX/效能/合規全部通過。


## 2026-10-25｜青壯額度管理周全設計：提案已完成、Notion未修改
本次使用者要求以使用場景、操作習慣與跨年方案維護重新設計。已Fetch兩補助頁與四個核心Schema，確認既有青壯人工核對後在服務歷程選方案、同頁直顯、單一歷程習慣。交付[完整設計提案](proposals/subsidy-workflow-design-2026-10-25.md)與對話內合成資料示意：院所本期、個案下一步、心理師本週三區直接顯示；低頻維護同頁相鄰。個案年度參與表不新增為必填；跨期以Price Plan實例隔離，舊115公式不得冒稱通用。明示普通Notion頁無單一年度下拉同步多表的保證；未取得完整公式原文不改共用計數。含10情境驗收、效能前後實測與回復條件。**此為設計，非已實作；本輪Notion零寫入、公式/UX/效能均無新PASS**。GitHub保留所有歷史修改記錄，前輪復原範圍另依其專項報告。


## 2026-10-25｜本輪直接授權：首頁減載與補助操作精簡已實作
使用者明確要求一次完成首頁與政府補助改版；本輪直接實作授權優先於舊研究門檻，不宣稱萬篇研究完成。首頁22→4張inline，18張原檢視移至按需查詢頁；原22個View設定22/22不變。補助日常7→3張inline，待核對/額度零/選方案整合至個案表tab；設定頁改5個fullpage入口，6個重複linked blocks已deleted且原Data Sources存活。年度參與表回歸歷史，不作青壯日常前置。修正115方案備註官方規則文字，沒有改原額度Formula/資料關聯/業務列。原生公式值、載入秒數及真人UX未驗收；Windows畫面檢查逾時。詳細實作、回復及6題驗收：[本輪報告](audits/home-subsidy-simplification-2026-10-25.md)。


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

## 2026-10-24｜舊青壯115六欄清理續查：預設View與TEST篩選仍有依賴
- **[LATEST READ-ONLY FINDINGS]** 重新Fetch現行Notion TEST，Care Episodes 50／Cases 49／Sessions 67欄未變；3個EP Formula→3個Cases SUM Rollup之property ID引用未變。新增明確的View依賴：EP原生預設View `view://2d38ca66-aa4d-8371-a9f1-88a498b2641b` 顯示三個待刪來源；Cases預設View `view://4138ca66-aa4d-8353-96ae-8846778f41fd` 顯示含三個Rollup及兩個下游公式等7個青壯115欄；Cases `[TEST] 青壯115跨歷程占用驗證` `view://4028ca66-aa4d-8189-8a07-000cb0dac95c` 以 `青壯115額度狀態_自動` 作原生Formula Filter。
- **[BLOCKED—NO DELETION]** 再次直接Fetch Cases `青壯115他處顯示_自動`與`青壯115額度狀態_自動`之formulaCode均得到 `INVALID_ARGUMENT validation_error`，下游完整expression及可回復基準仍缺。原生Care Episodes/Cases page-layout亦列出舊欄位，不能簡單`DROP COLUMN`六欄而遺留失效Formula/View配置。此輪**Notion零寫入、沒有任何DELETE或DROP**，只新增追查文件；原資料、原公式、原UX v4.2四項人工PASS、角色權限DEFERRED與正式後端皆保持不變。
- **[AUDIT AND RESUME GATE]** 新增可回讀[逐欄依賴稽核／刪除門檻](audits/youth-legacy-property-dependency-cleanup-2026-10-24.md)，含六欄SUM Rollup關係、三個View的SHOW/Filter、Page Layout與未完成檢查清單；[Google Docs設計第31節](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)寫入並回查，[前一版備份](https://docs.google.com/document/d/1EoOGkZ0WuX26u0KCKqVbqdhq-jCNrBuxD36pXs6_8M8/edit)不含第31節。若要真正永久刪除，先取得現行Cases兩個下游公式完整原文，追完可能間接依賴並通過隔離TEST與還原計畫；不把「需要使用者提供原文」視作使用者必須重述先前已給的Care Episodes預約公式。

## 2026-10-24｜使用者明確否決即移除，不累積無用實作
- **[已核准的長期原則／跨系統適用]** 使用者明確要求：「未來的實作和設計，只要我說不適合，就要直接刪掉，不要保留，否則會越來越多不必要的東西。」使用者的「不適合／不要／移除」即為對所指項目的**否決與刪除指示**；不得把已否決UI改成收合、隱藏、停用但仍堆在工作台，不得保留過時的重複TEST View、Formula、欄位、頁面、按鈕或流程當永久備案。清理範圍僅限明確遭否決的項目與已證明沒有其他用途的專屬依賴，不擴張到無關資料或並行修改。
- **[安全的實際執行]** 當回合先釐清可精確識別的目標、最新Schema／程式與下游依賴，保存**不出現在日常介面的短期回復備份**，先移除引用／安全替代，再**真正刪除**被否決的項目，寫後回查與回歸測試；完成驗收後按合理保留要求清理過時備份，不把舊版永久掛在使用頁。不能安全拆除的受引用資料、法定或審計必留紀錄、使用中其他模組及必要備份**不得強制破壞**：設為「待安全刪除／BLOCKED」，列出受阻依賴與解除方式，不冒稱已刪除，也不將單純隱藏當完成。GitHub的精簡決策／回復歷史不等於營運系統保留廢棄元件。
- **[本輪作用範圍]** 本次是管理準則確認／文件同步，不是核准不經檢查一次刪掉所有舊模組。此前青壯115三個Care Episodes Formula→Cases三個Rollup的永久刪除意向維持；Cases下游Formula expression仍不可取得，未通過安全門檻前**不執行DROP**。原Notion資料、公式、Views、歷程與UX v4.2驗收保持不變。

## 2026-10-24｜Notion TEST安全續作：清除已通過工作台的過時備份入口，滿額提醒13/13離線測試
- **[ACTUAL UX CLEANUP]** 已重新Fetch使用者UX v4.2四項已驗收PASS的[Notion TEST補助工作台](https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f)，以精確單次`update_content`**真的移除**原收合區的`[UX v4 原生備份]`舊連結；回Fetch確認連結消失，原6個Linked DB、2個Toggle、上方異常／最後一次已預約提醒與3類額度表全部保留。備份頁本體暫作回復參照，尚未刪除此備份頁；不把移除入口冒稱備份頁刪除。
- **[LIVE BASELINE / BLOCKERS]** 重新Fetch Notion原Schema：Care Episodes50、Cases49、Sessions67、Price Plans30、Staff58欄；原`未預約下次會談`Saved View仍只以狀態＋未安排判斷。三組Care Episodes青壯115原Formula→Cases SUM Rollup的舊依賴與兩段Cases下游Formula的`formulaCode://`不完整問題仍在；`青壯轉自費`只有button型別無action。依使用者核准的硬停止，不執行任何`DROP COLUMN`、不覆寫共享Formula或Button、不改原業務資料。
- **[OFF-SYSTEM REGRESSION]** 按實際Price Plan方案實例的每案上限（非寫死115／3次）擬定互斥的`轉自費或結案`、`額外預約核對`、`待確認他處`、`維持預約提醒`與`自費原流程`決策；已執行13組匿名離線JavaScript分支案例，13/13PASS，涵蓋最後一次**僅已預約未完成**不可誤當滿額、完成3有下次預約、他處已確認0與未知、跨方案上限5次等。**不是Notion原生Formula或有效能／跨期驗收**，功能仍NOT LIVE。
- **[IMPACT/ROLLBACK]** 本輪唯一Notion寫入是移除一個過時連結，無新增欄位、公式、資料庫、查詢負擔及權限影響；回復只在重讀現行頁後將舊連結`[UX v4 原生備份](https://app.notion.com/p/4038ca66aa4d8159b4e5daf90a4ae662)`精準加回，保留其他並行修改，沒有任何業務資料回復。必要公式原文／按鈕動作完整基準仍未取得，永久刪除六欄與滿額提醒上線保持BLOCKED，免週報自動邏輯亦尚未啟用。
- **[DOCS READBACK]** [Google Docs青壯方案額度與UX規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)以revision guard新增第33節，回讀原32與新33共存；[修改前原生Google Docs備份](https://docs.google.com/document/d/1aPF1fXhnuuXWXDEayUkjOuknCxElb3G-EUXau6LbHeA/edit)不含第33節。

## 2026-10-24｜使用者要求全部清除舊設計：已清兩個介面殘留，原生子頁刪除受阻
- **[USER DIRECTIVE]** 使用者明確表示「我看到還有很多舊設計被保留，請全部清除」，是對已遭否決的舊UX/備份/重複TEST元件提出真正刪除指示，不能以隱藏、改名或移動冒充清除；但不能未查相依而刪除臨床個案、Sessions、申報記錄、來源DB及其他人並行修改。
- **[LATEST TEST INVENTORY]** 重新Fetch Notion TEST行政首頁（22個Linked DB區塊、11個child page，當時含7個`[BACKUP]`子頁、UX v2、原補助舊工作台及已通過UX v4.2）、原補助頁（7個Linked DB、部分歷史/調整/回報功能）、UX v4.2已核准頁（6個Linked DB、2個Toggle）；全域搜尋至少11個以`[BACKUP]`命名的頁面。不可只靠`[TEST]`字首批量刪除真正的遷移／隔離資料列。
- **[ACTUAL NOTION WRITES + READBACK]** 已在獲使用者4/4 UX驗收的同一TEST補助頁精準刪除`[原工作台]`過時連結，並將頁面由`[TEST 預覽] 補助工作台 UX v4.2`更名為`政府補助｜額度與警示工作台`，其Parent仍是TEST行政首頁；回讀維持6個Linked DB、2個Toggle、異常／最後一次警示和三類額度。已從TEST行政首頁真正刪除冗長「本頁用途／操作順序／常見錯誤」Callout，回讀原22個Linked DB、11個child page及提醒、導航均完整，舊說明不再出現。沒有新增頁／View／Formula或多餘備份。
- **[DELETION BLOCKED HONESTLY]** 嘗試對一個只含歷史Linked Views的失敗UX v3備份child page做精準`update_content`刪除（未開啟allow_deleting_content）得到`INVALID_ARGUMENT validation_error`，並未成功；子頁仍保留。此Notion連接器沒有單獨`delete/archive page`與`delete View`動作；不可用move/hide聲稱已完成永久刪除。若啟用可刪child的高風險內容重建，依工具契約須先列明每個受影響child並經明確確認，不得一口氣刪原補助頁的業務歷史與有效計算。
- **[PENDING SCOPE / SAFETY]** 待刪的7個首頁舊備份、UX v2過時頁、原補助管理舊入口和另至少4個其他備份需先區分只含Linked Views的版面快照 vs 實際業務/歷史資料；刪除後必須驗證目標頁真的消失、啟用的Data Source及6個新工作台Views不受影響。原青壯115三個EP Formula→三個Cases Rollup仍受Cases兩段不可讀下游Formula、View/Page Layout相依阻擋；不DROP。UX v4.2四項PASS保留，權限DEFERRED，免週報與滿額轉自費尚未上線，正式GAS/Cloud Run/Session不在範圍。
- **[DOCS + ROLLBACK]** [Google Docs跨期UX規格第34節](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)已使用revision guard增補並讀回；細節含受阻的舊頁刪除。兩處小額內容移除可用Notion頁面歷史精準還原，不影響來源業務資料；本回合只清理介面字串／頁名，效能沒有新增API、公式或DB負擔。

## 2026-10-24｜舊備份子頁精查：5個純Linked View快照可作第一批刪除候選
- 逐一Fetch TEST行政首頁列出的7個舊備份子頁：以下5頁**均無子頁**、只包含指向既有Data Source的Linked Views（未擁有獨立臨床資料庫）：`4038ca66aa4d81389417ca0faadf3492`（十模組B1–B3備份，1 linked view）、`4038ca66aa4d81d89cb1e7c1a6c12273`（UX v4.1失敗版，7）、`4038ca66aa4d819482bbd663a0e4fe4d`（UX v4重排前，6）、`4038ca66aa4d8159b4e5daf90a4ae662`（UX v4修改前，4）、`4038ca66aa4d811eafe0c857a6394638`（UX v3失敗版，3）。這5份是第一批真正刪除候選，來源資料庫應保留；Notion仍未刪除它們。
- 另外2份補助舊工作台備份（`4038ca66aa4d81c3a70bd4730fdba9fe`與`4038ca66aa4d816480bad8a54db6aeab`）各含一個子頁引用，須先確定完整保留法定／驗收內容才可刪除，不能和無子頁快照同等處理。原補助管理頁另包含真實歷史、週回報與額度調整入口，不能直接刪除業務資料來源。
- 曾在未開`allow_deleting_content`下精準嘗試從父頁移除失敗版UX v3子頁標籤，回`INVALID_ARGUMENT validation_error`且目標仍可Fetch；根據Notion工具契約，對可能刪除原生child的寫入必須先展示精確目標清單並由使用者確認，不能將隱藏/移動當完成。以上待一鍵確認刪除第一批5份快照；不重問「是否不要舊設計」的既有決策。

## 2026-10-24｜使用者精準核准的5個舊設計快照：Notion deleted五頁、資料源回歸PASS
- **[USER EXACT DELETION AUTHORIZATION]** 使用者精確點名並核准移除5個歷史備份Page IDs：`4038ca66aa4d81389417ca0faadf3492`（十模組B1–B3）、`4038ca66aa4d81d89cb1e7c1a6c12273`（UX v4.1失敗版）、`4038ca66aa4d819482bbd663a0e4fe4d`（UX v4重排前）、`4038ca66aa4d8159b4e5daf90a4ae662`（UX v4修改前）、`4038ca66aa4d811eafe0c857a6394638`（UX v3失敗版）。每頁在刪除前重新Fetch：分別1／7／6／4／3個Linked Views，只引用既有Data Source、無獨立業務DB與實際子頁；五頁原parent皆TEST行政首頁。
- **[ACTUAL NOTION DELETE AND READBACK PASS]** 原`TEST 行政管理`頁刪前11 child pages及22 linked database blocks，5個精確子頁標籤各出現一次。依使用者已確認清單，`notion_update_page(update_content, five exact old_str→'', allow_deleting_content=true, allow_async=false)`執行成功；刪後首頁6 child pages、原22 linked DB、原提醒和導航、當前政府補助警示工作台入口均保持。五個原Page IDs逐一Fetch均有`<page ... deleted>`＋`<blank-page>`、0 Linked Views，而且Notion搜尋`[BACKUP]`不再回傳此5 IDs。**這是Notion可恢復的deleted狀態，不代表已從垃圾桶不可逆purge**。
- **[SOURCES/UX PRESERVED]** 刪去21個過時頁面內Linked Views（不是源資料庫）。獨立Fetch確認Care Episodes50欄、Cases49欄、Staff58欄、Price Plans30欄仍存，沒有刪源Data Source；獲使用者4/4 UX真人通過的「政府補助｜額度與警示工作台」仍6 linked DB及兩種警示，原補助管理舊工作台仍7 linked DB；個案、會談、帳務資料、Formula、Relation、View底層、GAS、Cloud Run、權限均未寫入。效能沒有實際計時，不宣稱提速。
- **[NEXT CLEANUP/SAFETY GATE]** Notion搜尋仍有7個標為`[BACKUP]`的活頁，包括兩份原補助管理備份與帳務／活動／排班／行政任務／工作文件；兩份補助備份均內含原生`<page>`的青壯驗收紀錄引用，UX v2也有11項任務路徑驗收子頁及1個TEST Linked DB，不能按標題直接刪。先核對子頁、原始資料與可用功能並依工具要求列出下一批確切受影響頁面取得核准，再移除；不將移動或隱藏當刪除。青壯115三Formula/三Rollup依賴清除和滿額後轉自費提醒，仍因Formula/按鈕原文缺漏BLOCKED。
- **[DOCS/ROLLBACK]** [Google Docs青壯跨期UX規格第35節](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)以revision guard追加，重讀第34、35節及五ID、Notion垃圾桶限制。回復如有必要僅透過Notion垃圾桶恢復指定舊快照及原parent，先確認現行並行變動，禁止用全頁快照還原6個有效子頁。

## 2026-10-24｜第一批刪除後第二批備份分類：七頁與UX v2待保護依賴
- **已刪5頁回查**：TEST首頁11→6子頁、22Linked DB不變，五個指定頁均Notion`deleted`＋`blank-page`且搜尋不再顯示。Notion官方說明刪除後預設在垃圾桶保留30天；connector沒有永久purge，**不可把移入垃圾桶當不可逆永久清除**。
- **另7份活躍`[BACKUP]`**：TEST首頁還有兩份補助舊備份（`4038ca66aa4d816480bad8a54db6aeab`、`4038ca66aa4d81c3a70bd4730fdba9fe`），分別含5與6 Linked Views、各含一個青壯設計驗收子頁引用。另5份位於Backend之下：帳務`4038ca66aa4d8145a3eec4c49740744f`（14 DB blocks）、活動`4038ca66aa4d81a890cacc9a997c6d91`（15）、排班`4038ca66aa4d81f58ffccad644e27a78`（14）、任務`4038ca66aa4d81249ff4d6b96f2ca812`（3）、文件`4038ca66aa4d81778fb9c13cc809fa85`（5）。其中多數內嵌Database blocks在Notion fetch **未標data-source-url**，未證明只是Linked View，不可直接刪以免誤傷原資料庫或模板。
- **UX v2另有子頁**：TEST行政首頁`4038ca66aa4d814297a2dbe27e8d054d`包含驗收紀錄子頁`4038ca66aa4d81a0834efc417b08fd1b`及活動獨立測試資料庫引用，必須先保護獨立驗收紀錄與資料源再移除版面。
- **下一批硬門檻**：盤清每個待刪頁及其嵌入DB所有權、子頁及實際存活業務依賴，針對精確清單由使用者確認後採Notion原生刪除、逐項查`deleted`並回驗來源；此回合只對上一批使用者具名核准5ID動手，不對此七頁或UX v2採取破壞性操作。

## 2026-10-25｜五個指定備份deleted再驗PASS；後續兩份補助備份子頁全文已被現用驗收包含
- **[BATCH 1 VERIFIED, NO DOUBLE-DELETE]** 本回合針對前輪使用者已精準核准之五PageIDs獨立重新Fetch：五頁均`<page deleted>`、`<blank-page>`、0 LinkedDB；Notion `[BACKUP]` 搜尋均不再回傳五ID，TEST行政首頁原11→6子頁、22原LinkedDB不變。現用[政府補助｜額度與警示工作台](https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f)仍6 LinkedDB及兩個警示、3類額度。這是**Notion原生刪除／移入可回復垃圾桶**，並非不可逆purge；本回合未重複刪除。
- **[NEXT BATCH DUPLICATE CONTENT PROVED]** 尚存兩個原補助備份父頁`4038ca66aa4d816480bad8a54db6aeab`(5 linked DB+子頁`7778ca66aa4d824c914b8155ecd4d25d`)及`4038ca66aa4d81c3a70bd4730fdba9fe`(6 linked DB+子頁`2fa8ca66aa4d8351959501f7c1c71095`)。兩子頁各無更深子頁/LinkedDB，曾包含歷史驗收內容。唯讀逐字比較兩舊子頁完整`<content>`分別17,462與21,918字，**完整原字串均出現在現用主驗收紀錄`4028ca66aa4d81298984ffd18b590a1d`內容49,072字中**；逐行去重後144/144、168/168筆亦全部覆蓋。不表示自動核准刪除那四個新ID；先列明父子清單取得精確批准後才能依工具契約刪除並回查。
- **[BACKUP OWNERSHIP HARD STOP]** 另五份Backend下舊帳務／活動／排班／任務／文件備份皆有多個嵌入Database；已抽查每類一個DB URL，都能獨立Fetch出`<database>`、`<data-source-state>`，因此不能僅以外層沒有data-source-url認定它們是無資料備份。須在真正刪除前確認是否只是共享既有資料源的Linked View、是否有實體子頁與有效業務依賴。UX v2仍帶驗收子頁及活動TEST來源，未納首批授權。
- **[DOCS/SCOPE]** [Google Docs青壯方案規格第36節](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)guarded update/readback PASS，記錄前五ID、下一批完整內容對照及更廣的待查；[增補前備份](https://docs.google.com/document/d/1e01gXZAakwbug2AVompDsiKDLm_R5N4lldj-lCtfSeY/edit)保留。本回合Notion僅唯讀，Care Episodes50/Cases49/Staff58/Price Plans30/Sessions67欄不變；青壯專欄永久DROP與滿額轉自費仍受原公式基準阻擋，免週報亦NOT LIVE，效能與權限未更動。

## 2026-10-25｜接續回查：五頁deleted維持，第二批四頁需精準核准
- **第一批讀回PASS／無重複刪除**：重新Fetch使用者原精確核准的五個舊快照Page ID（`4038ca66aa4d81389417ca0faadf3492`、`4038ca66aa4d81d89cb1e7c1a6c12273`、`4038ca66aa4d819482bbd663a0e4fe4d`、`4038ca66aa4d8159b4e5daf90a4ae662`、`4038ca66aa4d811eafe0c857a6394638`），每頁root `<page deleted>`且`<blank-page>`、無Linked DB；TEST行政首頁仍6個子頁與22個資料庫區塊。此狀態是可恢復垃圾桶，不是不可逆永久清除。
- **第二批安全界線**：`4038ca66aa4d816480bad8a54db6aeab`含5個指向既有Data Source的Linked Views及子頁`7778ca66aa4d824c914b8155ecd4d25d`；`4038ca66aa4d81c3a70bd4730fdba9fe`含6個及子頁`2fa8ca66aa4d8351959501f7c1c71095`。兩子頁無更深子頁／Linked DB，全文17,462／21,918字，皆逐字包含於**仍存活**的主驗收頁`4028ca66aa4d81298984ffd18b590a1d`，主驗收頁root無deleted標記；**四ID需精準列明後取得核准**，尚未執行刪除。
- **其他待查**：Backend帳務／活動／人員排班／行政任務／工作文件五個備份，分別含14／15／14／3／5資料庫區塊，抽查可連到現有共用Receipt Requests、Staff、Tasks、Documents來源；但未逐一驗證所有區塊，故維持BLOCKED、不批次刪除。UX v2另含獨立TEST活動狀態資料庫與驗收子頁，亦須保護。沒有定位到可直接確定的最新`00.config_notion`原件，仍以已重新Fetch的現況為準。
- **範圍／回歸限制**：本回合Notion僅唯讀；已確認現用政府補助工作台仍有6個Linked Views、異常與最後一次已預約提醒、3類額度、2個Toggle。未修改業務資料、Schema、Relation、Formula、View、角色權限或GAS／Cloud Run，無新增效能負擔；沒有重新測原生Formula數值、登入權限及實際載入時間。若日後清理第二批，先保留現行主驗收並回查刪除後四ID及來源Schema。

## 2026-10-25｜第二批四頁刪除PASS（使用者精確核准）
- **[USER CONFIRMED / SCOPE]** 使用者明確回覆「確認刪除第二批4頁」，精確清理範圍為兩個Notion TEST舊補助備份父頁：`4038ca66aa4d816480bad8a54db6aeab`、`4038ca66aa4d81c3a70bd4730fdba9fe`，以及各自的驗收紀錄子頁 `7778ca66aa4d824c914b8155ecd4d25d`、`2fa8ca66aa4d8351959501f7c1c71095`。此指令沒有擴及其他備份、UX v2獨立測試來源或營運資料。
- **[PRE-FLIGHT]** 重新Fetch 4頁、TEST行政首頁、現用驗收主頁及工作台；兩個父頁分別只有5／6個帶`data-source-url`之共用Linked Database、各一個驗收子頁，無自有來源Data Source。子頁全文17,462／21,918字均完整包含於現用且未刪的驗收主頁 `4028ca66aa4d81298984ffd18b590a1d`；六個涉及的Data Source全可讀，首頁兩個待刪標籤各唯一。
- **[NOTION ACTUAL WRITE AND READBACK PASS]** 使用者精確核准後，對TEST行政首頁 `de78ca66aa4d82659e7181a66fa17220` 執行原生`notion_update_page(update_content)`，只移除上述兩個父頁的完整唯一`<page>`區塊（`allow_deleting_content=true`，同步寫入），Notion回成功。寫後重新Fetch四個精確IDs的根`<page>`標記全部為 `deleted`：兩父頁成`blank-page`、無Linked DB；兩驗收子頁帶`deleted`標記且其原本文字仍在垃圾桶內；Notion工作區搜尋不再傳回這些ID。**這是可恢復的Notion垃圾桶刪除，不是永久purge**。
- **[REGRESSION PASS / LIMITS]** TEST行政首頁6→4個子頁、原22個其他資料庫區塊仍在；未刪的四個子頁是Backend、補助方案管理TEST、UX v2、現用政府補助工作台。現用政府補助工作台仍6個Linked DB（上方異常核對、最後一次已預約提醒與三類額度、設定收費方案折疊檢視），現用主驗收頁保持存活。六個涉入Data Source（Price Plans、額度調整、Staff、心理師週額度、Cases、補助參與紀錄）刪後逐一Fetch存在，並未刪除來源。沒有寫入任何Schema／Formula／Relation／View底層、營運資料、角色權限、正式GAS或Cloud Run；沒有實測負載時間、Notion公式輸出或真人互動，不宣稱性能／業務數值新PASS。
- **[ROLLBACK / NEXT GATE]** 若需撤銷，從Notion垃圾桶針對上述四ID復原，核對原始父子階層及當前首頁，採最小操作而非全頁復原；避免覆蓋別人的並行變更。其他五份Backend模組備份及UX v2含獨立測試資料來源仍待逐一依賴稽核，未獲具名授權不批量刪。青壯115專用六欄因下游Formula缺完整原文維持BLOCKED，滿額轉自費／免週報邏輯仍NOT LIVE，角色權限DEFERRED。

## 2026-10-25｜第三批五份Backend舊版備份刪除：51檢視對照及17資料源回歸PASS
- **[USER CONTINUATION / SCOPE]** 使用者承接前兩批清理後明確要求「繼續清理」，依先前「不適合／舊設計全部清除」決策，只對Backend下五個明確[BACKUP]舊版頁面刪除：帳務`4038ca66aa4d8145a3eec4c49740744f`、活動`4038ca66aa4d81a890cacc9a997c6d91`、人員排班`4038ca66aa4d81f58ffccad644e27a78`、行政任務`4038ca66aa4d81249ff4d6b96f2ca812`、工作文件`4038ca66aa4d81778fb9c13cc809fa85`；沒有擴及UX v2獨立TEST來源、正式業務頁、原始Data Source或其他任務。
- **[LIVE PRE-DELETE DEPENDENCY CHECK]** 分別重新Fetch五份備份（14／15／14／3／5=51個資料庫區塊，全部無原生子頁）以及現行同名行政模組（亦14／15／14／3／5），對每個備份Database block URL逐一Fetch，取得唯一`collection://` Data Source；相同位置的現行行政模組51個瀏覽模式也逐一Fetch比對。五組均51/51對應同一資料源ID，所有51個備份檢視已有仍存活的正式模組對應瀏覽檢視；不把資料庫區塊當獨立來源，也不誤刪原始業務資料。仍有部份備份舊畫面含不支援的按鈕區塊，但未動到現行模組中的按鈕。
- **[ACTUAL NOTION WRITE / TARGET READBACK PASS]** 使用者既有舊設計刪除指示下，重新Fetch Backend頁`f628ca66aa4d8295a5a981e21e92762f`並驗證五個目標`<page>`標籤各僅出現一次，且10個其他原始模組子頁存在，才執行單次`notion_update_page(update_content)`移除五個精確完整標籤、`allow_deleting_content=true`及同步寫入。Notion成功回傳Backend page ID。寫後重Fetch五個ID，**五個根頁全部`deleted`、`blank-page`、0 Linked Database**；Backend 15→10原生子頁、其他29個資料庫區塊不變；五個現行模組仍存活且保有14／15／14／3／5個檢視。
- **[ORIGINAL SOURCES READBACK]** 實際刪除後逐一Fetch此前51檢視指向的17種不同Data Source，全部仍有`<data-source-state>`且未標deleted，含Receipt Requests、Sessions、Event Registrations、Billing、Revenue Ledger、Price Plans、Staff、Group Meetings、Group Therapy、Events、Space Bookings、Intake、Payroll Statement、Leave Requests、Revenue Split Rules、Tasks、Documents。沒有修改任何原始資料列、Formula、Relation、Schema、Saved Views、權限、GAS或Cloud Run；無法據此宣稱公式計算值、頁面真人UX或實際載入速度PASS。可能移除51個過時檢視的入口，但沒有計時資料。
- **[ROLLBACK AND REMAINING]** 只實現Notion可恢復垃圾桶`deleted`，**不是不可逆purge**；若需回復，從Notion垃圾桶針對精確五ID單獨恢復，先確認當前Backend子頁及並行修改，不覆寫其他10個業務頁。行政首頁剩下的UX v2`4038ca66aa4d814297a2dbe27e8d054d`包含驗收子頁`4038ca66aa4d81a0834efc417b08fd1b`和獨立活動狀態TEST Data Source`collection://5864ca97-2ceb-4727-a52c-9b7cf749dcd9`，清理前須先查用途與保護。原補助管理TEST頁亦有真實功能，暫不刪；青壯舊六欄因Cases兩下游Formula原文不可讀，仍BLOCKED、不得DROP。使用者先前UX v4.2四項真人PASS維持既有紀錄，不代表本輪新驗收。

## 2026-10-25｜第四批：整體行政UX v2及獨立五筆合成TEST資料原生刪除PASS
- **[USER REQUEST / SCOPE]** 在先前已確認「不適合／過時設計需真正刪除」及前三批清理後，使用者回覆「繼續」。本次只處理首頁中無真人驗收且不再作為現用入口的「[TEST] 治療所行政任務工作台｜整體UX v2」頁`4038ca66aa4d814297a2dbe27e8d054d`、其唯一11項導覽驗收子頁`4038ca66aa4d81a0834efc417b08fd1b`、唯一獨立測試database`39f6c1322dd44106b32760a58246860e`及其五個合成活動狀態測試頁。這不是刪除原行政模組或原Events資料庫。
- **[PRE-WRITE DEPENDENCIES]** 重新Fetch TEST行政首頁（4 child pages、22 DB blocks）、舊UX v2（僅1個驗收子頁和1個獨立inline=false測試database）、驗收頁（11個導覽路徑的connector AUTO PASS、真人0/11），及獨立Data Source`collection://5864ca97-2ceb-4727-a52c-9b7cf749dcd9`。其Schema只有名稱(title)、狀態(status)、預期報名中／預期進行中兩個checkbox，**無Relation**；rows模式獨立Fetch確定恰有5個[TEST]合成狀態（籌備中、開放報名、已額滿、已取消、已結束）、無其他rows/分頁。原Events資料源`collection://2ab8ca66-aa4d-83bd-894f-87531b7fc587`不同且實存；現用活動模組`d578ca66aa4d8303bebf017bdcf7904d`之嵌入database`1278ca66aa4d833c9bd501d9606e1abf`的「可報名｜開放報名」與「進行中｜開放報名與已額滿」二個Saved Views直接引用原Events來源，非該TEST來源。核對首頁目標`<page>`標籤唯一及其他Backend、補助方案TEST、政府補助額度警示工作台存在。
- **[ACTUAL NOTION DELETE + READBACK]** 僅對行政首頁`de78ca66aa4d82659e7181a66fa17220`做`notion_update_page(update_content)`精準移除UX v2唯一`<page>`標籤，`allow_deleting_content=true, allow_async=false`，connector成功返回原頁ID。刪後行政首頁由4→3個child pages，22個原DB區塊不變。舊UX v2根標籤`deleted`、`blank-page`；其驗收子頁根標籤`deleted`（垃圾桶內仍有原本4,798字驗收文字）；獨立database根`<database ... deleted>`；五個合成TEST列頁根`<page ... deleted>`及`blank-page`。Notion搜尋結果不再列出被刪UX v2／TEST database條目。**合計本批8個Notion物件被標示deleted：2個page、1個database、5個合成資料頁；不代表不可逆purge**。已刪database的Data Source仍可用直接ID Fetch讀到Schema metadata，**不得把可讀metadata當成未刪除，也不得誤稱底層已永久抹除**。
- **[PROTECTED + NO CHANGE]** 刪後現行政府補助工作台`4038ca66aa4d814f959ceece0e8cb09f`仍6個Linked DB、原補助方案管理TEST`3f68ca66aa4d81cca3b4ee43b4bd8dcf`仍7個Linked DB及主驗收子頁`4028ca66aa4d81298984ffd18b590a1d`存在；原Events Data Source仍可讀、現有兩個活動Saved View仍保留。沒有修改任何既有業務資料列、原Events/補助Schema、Formula、Relation、Views、角色權限、GAS、Cloud Run或Session。無原生數值、跨期、真人UX或效能計時新驗收，不得標記PASS。
- **[REMAINING/ROLLBACK]** 五個合成TEST狀態的輸入規則與1／2／5筆預期結果在現存GitHub/驗收記錄可重建，但原Notion頁面、database與rows只進可恢復垃圾桶；若需回復先核對最新首頁並針對8個精確物件作Notion垃圾桶還原，不覆蓋並行變更。現用Events瀏覽模式中另有兩個「舊版｜…（停用）」Saved Views `view://3b08ca66-aa4d-8216-8abf-08275d9b29bb`、`view://9768ca66-aa4d-82d2-8284-8840f61fd407`仍待真正刪除；目前connector只提供`notion_update_view`修改View而沒有`delete_view`，不得以隱藏／重新命名假稱刪除，標記**BLOCKED**直到有官方支援的安全刪View途徑。原補助方案管理TEST含驗收及額度調整、參與歷史，未核對替代前不刪。青壯115舊Formula/Rollup受完整依賴與備份硬門檻阻擋，維持BLOCKED。

## 2026-10-25｜第五輪續作：兩個錯誤活動Saved Views只能UI原生刪除；原補助管理仍承載獨有歷史功能
- **[USER CONTINUATION / SCOPE]** 使用者「繼續」，沿用先前已核准的否決舊設計需清除原則；此輪針對現行活動模組殘留2個錯誤Saved Views與原補助方案管理TEST依賴做最新Notion唯讀稽核，沒有擴及其他欄位、業務來源或部署。
- **[NATIVE VIEW READBACK / PRECISE TARGETS]** [現行05 Events & Groups](https://app.notion.com/p/d578ca66aa4d8303bebf017bdcf7904d)的嵌入瀏覽模式Database `1278ca66aa4d833c9bd501d9606e1abf`實際含6個Saved Views、均指向現有`collection://2ab8ca66-aa4d-83bd-894f-87531b7fc587`。待真正刪除且**未執行**者：(1) `view://3b08ca66-aa4d-8216-8abf-08275d9b29bb`「舊版｜反向報名篩選（停用）」，條件`狀態 != 開放報名`、活動時間升冪、顯示＋活動報名／類型／名稱；(2) `view://9768ca66-aa4d-82d2-8284-8840f61fd407`「舊版｜過寬進行中篩選（停用）」，條件`狀態 != Complete群組`、活動時間升冪、顯示狀態／類型／名稱。替代之兩個獨立且正確Saved Views仍存在：(3) `view://4038ca66-aa4d-81fd-bb28-000c6f1f92fa`「可報名｜開放報名」（狀態=開放報名）；(4) `view://4038ca66-aa4d-819d-9082-000c961b50f5`「進行中｜開放報名與已額滿」（狀態=開放報名OR已額滿）。另外同一區塊`ALL`、`已完成活動`亦須保留。
- **[TOOL CAPABILITY HARD STOP]** 本連接器最新列出的Notion工具只有`notion_update_view`（可改名/篩選/顯示）及`notion_create_view`，**沒有真正delete_view**；無法以View Update、HIDE、改名、刪除整個linked database block或重建全部Views替代精準刪除，因會誤傷四個現存有效View IDs/設定。這兩個錯誤View因此維持**未刪／BLOCKED on connector**，不把檢視仍存在說成完成。
- **[OFFICIAL UI SAFE PATH]** Notion官方《Views, filters, sorts & groups》確認，在資料庫檢視上點選檢視名稱可進行`Delete`，每個檢視設定獨立；編輯資料庫視圖需要`Can edit`或相應更高權限，`Can edit content`無法變更view。官方文獻：https://www.notion.com/help/views-filters-and-sorts ; https://www.notion.com/help/intro-to-databases ; 預期使用者在上述現有模組的同一瀏覽模式中**只刪兩個具名舊檢視**，保留4個`ALL`、`已完成活動`、`可報名`及`進行中`。完成後必須重新Fetch瀏覽模式與四個存活View IDs、原Events Data Source、原行政頁15個DB區塊，再才可標PASS。恢復舊view若需，依此備查的條件及顯示欄位用Notion原生新增，不保證原view ID可復原。
- **[ORIGINAL SUBSIDY RETAINED / NO RESTRUCTURE]** TEST行政首頁重讀仍3個子頁、22個DB區塊。舊名[補助方案管理｜TEST](https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf)含7個使用中資料來源檢視與現行主驗收子頁`4028ca66aa4d81298984ffd18b590a1d`；其中**補助參與歷史**`collection://8546d9e1-2e10-471a-8b83-3eb235544471`、**心理師週額度與他處回報**`collection://fc0ff3b7-04c7-41ff-8efd-deac8f8202e4`、**額度調整紀錄**`collection://f1f6eabd-2f65-4d33-a230-1d1b56254c91`、**Cases歷史對照**`collection://87f8ca66-aa4d-824d-8854-87355509dca8`均未在目前6 LinkedViews的[政府補助｜額度與警示工作台](https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f)提供等價來源區塊。不能直接刪舊頁或把歷史依據搬到未經核准的新日常架構，維持保留/BLOCKED待最小移轉與驗收。
- **[NO WRITE / TEST LIMITS]** 本回合Notion只Fetch現況，沒有新增/改名/隱藏或刪除任何View、Notion page、業務data、Formula、Relation、permission；沒有測量載入速度、原生公式數值或真人操作；原115青壯舊六欄依賴DROP仍保持原硬停止。此輪僅同步GitHub工作紀錄及必要Google Docs規格。使用者下一步在Notion UI刪兩個後以Connector獨立驗收，不提前宣稱成功。

## 2026-10-25｜使用者新確認：AI設計規則不得寫進Notion日常頁面
- **[POLICY RECORD]** 使用者確定Notion日常業務頁不得混入AI設計／維護規則；示例為補助方案管理TEST的長段人工核對、收費方案操作、期別與跨方案限制說明。詳細判別界線與例外寫入`AGENTS.md`、`docs/notion/AGENTS.md`及`docs/notion/workbench-ux.md`，決策寫入`docs/notion/decision-log.md`。必要安全提示可精簡保留；禁止因此破壞業務資料或原有檢視。
- **[IMPLEMENTATION STATUS]** 本輪只修改GitHub文件並遠端回查；Notion中現有長文**沒有在本輪移除**，狀態為`PENDING_NOTION_CONTENT_CLEANUP`。若後續依已確認規則清理，先重讀頁面、核對不可失的業務操作與安全告知，精準刪文、再回讀確認首屏資訊、Views、權限及無關內容不變。沒有負載或真人UX新驗收。

## 2026-10-25｜使用者限定只清除青壯補助額度舊內容；原補助TEST過時AI長文已刪
- **已完成且寫後Fetch PASS**：Notion TEST舊補助管理頁刪除使用者明確否決的青壯額度長篇AI設計文案（545字）＋歷史資料設計理由（117字）；簡化歷史入口標籤並消除③④孤立節號；原7個Linked Views與1個主驗收子頁仍在，新工作台6個資料檢視仍在，三個原Source可Fetch。這是Notion**文字內容刪除**，不等於資料庫Rows刪除或整頁deleted。
- **保留/未動**：現行青壯Price Plan、Care Episodes、Sessions、Cases、Staff、歷史參與、週回報、額度調整、醫療／財務紀錄、Formula、Rollup、Relation、權限、正式GAS均保持不變；沒有真人UX/效能或公式真值重測。
- **BLOCKED**：青壯115專屬3 EP Formula＋3 Cases Rollup仍有下游Case公式依賴且缺原生完整expression；已標記等到可安全備份及測試才刪。原補助管理頁含仍有用歷史檢視和主驗收記錄，不可直接整頁刪除。非青壯範圍（如活動管理舊Saved Views）不在本輪處理清單。

## 2026-10-25｜使用者確認：嚴格限定當次需求、完成即停止、「繼續」不得另起任務
- **[USER MANUAL ACCEPTANCE — SPECIFIC]** 使用者回覆「檢查沒問題」：上一輪`補助方案管理｜TEST`中青壯額度舊AI設計說明及冗餘理由文字的清理，**已獲使用者確認符合要求；該次指定任務已完成並停止**。不將此結論擴張至其他補助資料、Formula、Rollup、申報數據、角色權限或新工作台UX實測。
- **[POLICY IMPLEMENTATION]** 本次新增專案執行規則：以使用者單一指令為唯一任務範圍，修復後清楚結案；附帶其他問題須先列點詢問，僅有明確授權時才能進行；「繼續」只能接續尚未完成的原任務，原任務已完成則停止。根`AGENTS.md`及`docs/notion/AGENTS.md`已有此優先條款，並修正後者既存的自動續作衝突句子。
- **[LIMITS]** 本輪僅GitHub文字決策及驗收同步、以遠端blob SHA與Commit回查，無Notion或業務寫入、無效能／權限變更。後續工作須待使用者具體提出或核准，**不自動續做待辦**。

## 2026-10-25｜青壯額度設計清理複查：歷史設計紀錄移入垃圾桶、現行工作台移除技術長文
- **[PASS: ACTUAL WRITE + FETCH]** 兩個青壯額度舊設計Notion Page物件（51,550字原驗收頁`4028ca66aa4d81298984ffd18b590a1d`及「方案設計及驗收紀錄」容器`df04a6d6725b45a4ae10a84440a16332`）均讀回`deleted`；原補助TEST管理頁的設計Toggle已實際不存在，7個資料庫檢視全數保存且child 1→0。現行政府補助額度警示頁技術長文已由精準文字替換真正移除，改保留1則必要的人工核對提醒；6 views及5個標題保留。首頁3 children／22 DB unchanged；6個相關原Source可讀。前兩次 validation_error 未造成預期變更，不以報錯寫入當PASS。
- **[LIMITS / CANNOT DELETE YET]** 因仍有真實參與歷史、核定額度、週報、調整記錄與Care Episodes→Cases的3組青壯115公式／Rollup相依且缺完整公式定義，不對資料列/Schema執行破壞性刪除；本次需求限定舊設計清除，未越權重構日常作業。當下真人UX、效能、真實額度值未實測；權限無變更。已刪頁屬可恢復垃圾桶，非永久清空。
- **[CHECK]** 現行檢查：https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f ；補助歷史入口檢查：https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf 。此輪結束後應停止，無使用者額外授權不得接續其他模組清理。

## 2026-10-25｜Notion視覺與操作版面研究：十面向交叉複核，未達萬篇×十次
- **[RESEARCH GATE, NOT COMPLETE]** 本輪已建立[研究證據及完整十面向紀錄](research/notion-ux-research-and-10-lens-review-2026-10-25.md)，內容為Notion官方／公開模板／NN/g代表來源之實際檢索證據、10個跨面向UX檢視、當前6個Linked Views層級和可驗證的版面提案。Marketplace顯示70,000+模板僅為索引；**10,000篇逐篇深讀、各10次深入重讀：未達成／不可宣稱PASS**；代表性模板沒有下載逐套測試。
- **[BASELINE STRUCTURE READ-ONLY]** 現行青壯額度/警示工作台6個Linked Views、5個直顯(4/7/6/5/6欄)+1方案設定Toggle(4欄)、1必要核對提醒；三資料源仍存在，未修改。標題「最後一次已預約」與實際僅濾剩餘0的條件不完全吻合，標記語意風險（尚未修改）。治療所視圖涵蓋政府方案、另兩視圖針對青壯115，未假稱全域同步。
- **[PROPOSED UX ONLY]** 建議「需要核對」保留兩張直接可見的警示View、接「額度概況」三張直接可見的原表、底部低頻設定，使用簡潔單欄／相同標題字級／最少必要欄位及範圍標示。若另一方案以單Linked Database多分頁求效能，須先客觀計時及使用者核准；不依賴付費Dashboard或圖表。
- **[UNCHANGED / BLOCKED VALIDATION]** 無Notion修改、無原生功能／權限／效能新測；之前UX v4.2真人4/4 PASS不自動變成新方案驗收。待使用者核准後才許可建立TEST預覽/實際改版；本次研究工作回合結束後停止。

## 2026-10-25｜續作深度學習第二批：14來源分級登錄，10,000×10未完成
- **[USER RESUME BOUNDARY]** 使用者明確指示「繼續執行」，僅指上一項尚未完成的**Notion設計材料深度學習**；使用者要求**先學習達標並確認，之後才能開始Notion設計**。本輪不新增方案、繪製預覽、修改Notion頁面或跑到其他系統。
- **[EVIDENCE PROGRESS]** 新增[2026-10-25第二批深度學習證據、閱讀深度與限制](research/notion-deep-study-evidence-batch-02-2026-10-25.md)，逐一列明14個本批去重URL：10個成功打開頁面並針對正文相關章節查閱（BODY_SECTIONS）、4個僅能從搜尋結果/公開模板摘要讀取（SUMMARY_ONLY）。其中模板未購買/未實際複製；無任何資料達嚴格的全文完整深讀10遍門檻。本批`DEEP_PASS_10_OF_10=0/10,000`，`DEEP_PASS=0/100,000`；不可將20篇以前查閱、十面向討論或Marketplace模板總數冒充讀滿。
- **[QUALITY FINDINGS NOT A REDESIGN]** Notion官方證明手機多欄塌成單欄、Page Layout會套用整個Data Source、Formula/Rollup篩選及多Inline DB可能增加負載、Data Source頁級權限功能Business/Enterprise才有。NN/g表格與漸進式揭露研究強調高頻任務、比較與操作成本的取捨。這些僅為來源證據整理和衝突假設，**尚未批准Notion重新設計**。
- **[UNCHANGED / STOP HERE]** 原青壯額度與歷史工作台、業務資料、Notion Formula/Relation/View/權限、正式GAS與Cloud Run皆無寫入，效能/真人桌機手機未測。GitHub新增來源檔與索引、驗收檔採SHA並寫後Fetch；下一次「繼續」僅可接續這個未完成的學習目標，不可在未達標時逕行版面設計。

## 2026-10-25｜Notion深度學習第三批：11新URL＋1舊文深讀，十次門檻未通過
- **[研究紀錄讀回 PASS／整體目標 FAIL]** 本次延續的是使用者已明示「先深度學習達標，再進入Notion設計」的尚未完成工作，而不是新的Notion改版授權。[第三批來源與深入評析](research/notion-deep-study-evidence-batch-03-2026-10-25.md)檢閱12個canonical URL（11個新來源＋1篇原2026-10-24 N09深入重讀）：2篇完整主要文字章節+首輪反例評析、3篇部分內文或搜尋擷取、6篇只讀商品介紹、1個模板目錄；既有Notion按鈕和NN/g表格研究URL有重查但未重複增加unique件數。
- **[重要概念驗證]** Notion Database Templates中預設Relation若誤指舊政府補助期別，套用後可能所有服務歷程連到錯的方案；Notion Synced Blocks必須核對原始區塊權限，>10份副本時原始內容刪除/Unsync all影響範圍和Undo有特別限制。兩個概念以官方全文、反例及跨來源比對記錄，沒有在真實工作區執行操作。
- **[未完成/保留]** 10,000篇×10次的逐篇深讀驗收仍`NOT_DONE`、10/10篇數`0`。本輪Notion實頁、工作台、Cases、Care Episodes、Price Plans、Views、Formula、業務紀錄、權限、GAS/Cloud Run/Session都沒有任何寫入；無真人操作、效能或權限新測。學習尚未達標，不得因此開始設計或要求使用者認可新版UX。GitHub僅研究與索引紀錄提交並回讀SHA。

## 2026-10-25｜Notion深度學習第四批：5新來源＋2舊文分析複查（未達標）
- **[PROVENANCE CHECK PASS, STUDY GOAL NOT_DONE]** 使用者「繼續」僅續作未完成之10,000篇各10次Notion深度學習；此輪新登錄5個canonical URL（4篇取得相關正文段落、1篇僅搜尋摘要），既有兩篇官方文件各有一次獨立的第二輪分析複查，及對先前Notion View規則的一次定向重查。每篇10次**嚴格全文深讀達標數仍0／10,000**。逐URL證據、閱讀級別、反例與不足在[第四批來源與第二輪分析複查](research/notion-deep-study-evidence-batch-04-2026-10-25.md)。
- **[COMPREHENSION / NONIMPLEMENTATION]** 新讀到工作區搜尋與DB內搜尋的覆蓋差異；桌機/網頁高對比模式不等同跨裝置頁面設計；任務Status類別不能擅套補助真值；資料庫模板Recurring排程不會自動核定業務期別；Synced Block原始區塊與副本有權限及跨頁刪除風險。以上仍是技術/UX閱讀判讀，不是新的Notion設計方案。
- **[SCOPE, PERFORMANCE, AUTH, TEST]** 未修改Notion現有頁面、View、Schema、Relation、Formula、角色權限、歷史資料或正式GAS/Cloud Run/Session；查閱只發生外部網頁與GitHub文件。真人/手機可讀性、業務真值、權限測試和負載量測均未實作。GitHub本批原創研究檔、來源索引與驗收/決策紀錄須用最新SHA寫入及遠端Fetch回查；**學習尚未完成，不開始Notion設計**。

## 2026-10-25｜使用者新增雙軌規則：每小時排程與手動「繼續」同步並行
- **[PASS: AUTOMATION CONFIGURATION]** 既有「Notion 深度學習續作」排程已成功更新提示並維持is_enabled=true、RRULE每小時，不新增第二份重複排程。明文確認聊天手動「繼續」直接執行未完成的深度學習、兩條流程互不等待／停用；GitHub研究來源與複讀輪次去重，寫前最新版SHA、衝突重讀合併、寫後驗證。
- **[PASS: POLICY SYNC]** 根`AGENTS.md`與`docs/notion/AGENTS.md`已新增雙軌規則，舊「完成即停止」仍適用已完成的個別任務，不阻擋仍未完成的學習研究；GitHub以最新blob SHA寫入及讀回驗證。使用者只須發送「繼續」即可啟動聊天端獨立研究，毋須關閉自動排程。
- **[LIMITS]** 此次僅確認排程及規則**設定成功**，不聲稱已實際完成下一個自動執行週期或並行競爭實測；深度學習10,000篇×10次仍未達標，不進行Notion重新設計。Notion資料/Schema/View/Formula、角色權限、正式系統及效能均未更動。

## 2026-10-25｜Notion深度學習：排程獨立批次AUTO-01（3篇官方新來源，尚未達標）
- **[EVIDENCE RECORDED; LEARNING NOT_DONE]** 本輪排程實際開啟Notion官方3篇全篇可讀文字主節並做獨立反例分析，逐節閱讀範圍及限制見[AUTO-01原始閱讀證據](research/notion-deep-study-automation-run-01-2026-10-25.md)。關鍵：Form複製他人模板可能把回答送給原作者；Board在無可用分組欄時可能建立Status、跨欄拖曳會更動資料；Page Verification不等於補助計次/權限真值驗證。三篇都**非10次嚴格完整深讀**，達標篇數仍**0/10,000**。
- **[SCOPE AND LIMITS]** 本輪僅外部文章唯讀及GitHub研究記錄；Notion業務頁/DB/View/Formula/Relation/權限、正式GAS/Cloud Run/Session皆0寫入，沒有使用者測試、真實資料核對或效能量測。手動續作與排程可同時執行，更新GitHub前以最新SHA核對並寫後讀回；不開始Notion設計。

## 2026-10-25｜手動續作MANUAL-01：3篇官方新來源（IDs／自動化／協作鎖）
- **[STUDY UNIT COMPLETED, GLOBAL GOAL NOT_DONE]** 這是使用者手動「繼續」直接執行的新研究單元，與每小時AUTO-01可並行、資料互不覆蓋。[MANUAL-01 深度學習證據與反例](research/notion-deep-study-manual-01-2026-10-25.md)新增3個逐篇已核對URL與文字主要章節首次分析：Notion唯一ID、Database Automations、Workspace Collaboration/Lock。含假設、反例、來源內部Slack/Free權益歧義與未驗證項。**10,000篇×各10次嚴格完整深讀仍0/10,000**。
- **[DATA & SAFETY]** 此次0個Notion Page／View／Data Source／Formula／Relation／權限／業務資料寫入，GAS／Cloud Run／Session皆0變更。無真人/跨裝置/免費版權限/效能實測；資料庫鎖≠資料寫入授權，Notion ID≠複合唯一業務鍵，不能根據研究假設修改補助規則。只允許GitHub research/sources/decision/acceptance最小同步、寫後重新讀取並確認SHA。

## 2026-10-25｜Notion深度學習：排程獨立批次AUTO-02（3篇官方新來源）
- **[RESEARCH INCREMENT PASS; GLOBAL GOAL NOT_DONE]** [AUTO-02閱讀證據](research/notion-deep-study-automation-run-02-2026-10-25.md)：本批3個與既有研究清冊未重複的官方URL，2篇全文可讀文字主節、一篇長文指定章節閱讀，均各做首次反例分析。主要發現：CSV匯入及Merge不更新既有列、Workspace匯出未必涵蓋所有私人頁且不可一鍵重建、公開模板複製可能出現`No access`。另對2026-08-31 Workspace PDF匯出退場資訊標時效疑點。**不能把本批算作任何篇完成10次深讀；合格0/10,000**。
- **[SCOPE]** 僅官方公開文章唯讀＋GitHub研究記錄；未對Notion TEST/正式頁、DB、Views、Formula、Relation、權限、個案/財務資料或GAS/Cloud Run/Session寫入。未進行真人、權限、資料復原或效能實測。GitHub使用最新blob SHA條件寫入，寫後核對commit與內容，保留其他並行研究增量。

## 2026-10-25｜Notion深度學習：排程獨立批次AUTO-03（權限、Sub-items、Feed，3篇官方新來源）
- **[RESEARCH EVIDENCE VERIFIED; LONG-TERM GOAL NOT_DONE]** [AUTO-03閱讀證據](research/notion-deep-study-automation-run-03-2026-10-25.md)：3個新canonical URL、3篇文字主章節閱讀、3次獨立首次反例分析；仍無10/10嚴格完整深讀合格篇數（**0/10,000**）。研究結論：`Can edit content`不防止刪業務列；自我Relation不能取代額度/期別真值；Feed不能直接取代表格比較。
- **[NO NOTION WRITE]** 本輪只改GitHub研究檔及研究索引／驗收／決策摘要，未更動Notion正式或TEST的Page、Database、View、Formula、Relation、權限或業務列；GAS/Cloud Run/Session零變更。未執行真人UX、權限、效能、手機或數值真值測試，未開始設計。GitHub各檔寫前重取main blob SHA並於寫後讀回驗證。

## 2026-10-25｜Notion深度學習：排程獨立批次AUTO-04（提醒／Inbox／通知設定）
- **[RESEARCH INCREMENT VERIFIED; GLOBAL TARGET NOT_DONE]** [AUTO-04 閱讀與反例證據](research/notion-deep-study-automation-run-04-2026-10-25.md)新增3個經已知研究清冊去重的Notion官方來源，3篇主要文字章節、各1次可稽核反例分析；未看完媒體或做實帳測試，第2–10次未執行，**10次嚴格深讀合格篇數仍0/10,000**。研究反例涵蓋提醒不等於週期工作、Inbox篩選不等於業務完成/停發、App開啟時推播可能僅Inbox徽章、Person屬性通知有角色差異。
- **[NO LIVE WRITE]** 只更新GitHub研究文件和來源/決策/驗收索引。未更動Notion TEST/正式Page、Database、Views、Formula、Relation、Permissions、個案或財務資料，未修改GAS/Cloud Run/Session。真人UX、手機、通知準時性、權限、效能及數值真值測試均未執行。每檔寫前最新SHA、寫後Fetch驗證。

## 2026-10-25｜Notion深度學習：排程獨立批次AUTO-05（Buttons／刪除復原／Enterprise留存）
- **[PASS: RESEARCH INCREMENT ONLY; GLOBAL GOAL NOT_DONE]** [AUTO-05逐篇閱讀與反例紀錄](research/notion-deep-study-automation-run-05-2026-10-25.md)：3篇新canonical URL（Buttons、Delete & restore、Custom retention），3篇主要文字章節閱讀＋3次獨立首次反例分析。未完整檢視圖片/影片、無真人/Free權益/手機/效能/資料復原實測，不列`FULL_DEEP_PASS`，**10次完整深讀合格仍0/10,000**。
- **[UNCHANGED]** 只新增GitHub研究證據與來源/決策/驗收索引。未更動Notion正式或TEST頁面、資料庫、資料列、Views、Formula、Relation、權限；未更動GAS/Cloud Run/Session。無Notion設計授權，研究未達標。並行寫入每檔使用最新SHA並回查。

## 2026-10-25｜Notion深度學習：排程獨立批次AUTO-06（Calendar／Timeline／Gallery）
- **[PASS: RESEARCH INCREMENT; NOT_DONE: GLOBAL GOAL]** [AUTO-06官方來源逐節閱讀及反例](research/notion-deep-study-automation-run-06-2026-10-25.md)：3篇新的canonical URL，3篇已讀可取得全部文字主節及FAQ，3次首次假設/反例/修正分析。未逐張檢查圖片或嵌入影片、未進行實帳/權限/行動裝置/效能/拖曳日期寫回測試；嚴格FULL_DEEP_PASS尚無新增，**完成10/10來源仍0/10,000**。
- **[NO SYSTEM CHANGE]** 只保存GitHub研究證據與來源/決策/驗收索引，未更動Notion正式/TEST任何頁面、DB、View、Formula、Relation、權限、個案或收費資料，也未更動GAS/Cloud Run/Session。與手動續作共用最新main清冊、分檔避免競爭，寫前blob SHA及寫後回讀驗證。

## 2026-10-25｜Notion深度學習：排程獨立批次AUTO-07（Simple tables／Sidebar／Wikis）
- **[PASS: RESEARCH INCREMENT; NOT_DONE: GLOBAL LEARNING]** [AUTO-07逐節閱讀與反例研究](research/notion-deep-study-automation-run-07-2026-10-25.md)：本次3個新canonical URL已讀官方可取得文字主節，分別完成一次獨立假設/反例/修正；舊N04 Data Sources與N11 Table重新研讀產生2個新分析，不新增URL或嚴格全文深讀Pass。未檢查全部圖片/影片、未實帳/角色/手機/效能測試，**嚴格10/10完成仍0／10,000**。
- **[PASS: NO SYSTEM CHANGE]** 僅GitHub研究與共用索引，Notion TEST/正式Page、Data Source、View、Formula、Relation、權限、業務資料及GAS/Cloud Run/Session均0更動。並行寫入逐檔讀取最新main blob SHA、條件寫入並回讀內容/SHA/Commit；未授權新版Notion設計。

## 2026-10-25｜Notion深度學習：排程獨立批次AUTO-08（Sidebar Presets／Sidebar自訂＋舊文複讀）
- **[EVIDENCE RECORDED; GLOBAL GOAL NOT_DONE]** [AUTO-08原始閱讀與反例研究](research/notion-deep-study-automation-run-08-2026-10-25.md)本輪新增2個未登錄官方canonical URL，分別完成可讀文字主節及第一次反例分析；另重新研讀已登錄Layouts、Dashboards各1篇，有新反例但非第2次嚴格FULL_DEEP_PASS。舊Home URL redirect到已登錄Sidebar來源，不計篇數。**10,000篇各10次完整深讀合格：0／10,000**。
- **[SAFETY / LIMITS]** 未測Notion Free實際權益、真人跨角色/行動裝置、性能、任何業務公式值；本輪Notion業務資料、頁面、資料庫、檢視、公式、關聯、角色權限、正式GAS/Cloud Run/Session**0寫入**。只同步GitHub研究與決策/來源/驗收索引，並以最新SHA條件更新、讀回核驗；未授權設計改版。

## 2026-10-26｜Notion深度學習：排程獨立批次AUTO-09（Comments／Suggested edits／Backlinks）
- **[STUDY INCREMENT VERIFIED; GLOBAL GOAL NOT_DONE]** [AUTO-09原始研究與逐篇反例](research/notion-deep-study-automation-run-09-2026-10-26.md)：3篇新增且逐清冊去重的官方文章已讀可取得文字主節，首次假設/反例/跨來源檢討各一輪。重要邊界為評論Resolved≠核定、Suggested edits≠資料庫變更審批、Backlinks=0≠無引用。未逐張驗圖/嵌入影片/實帳測試，**不計FULL_DEEP_PASS**；10/10完整深讀達標篇數仍**0/10,000**。
- **[SCOPE/PASS]** 本輪僅公開文件唯讀、GitHub研究檔與來源/決策/驗收索引最小增補；GitHub以最新blob SHA條件寫入及Fetch驗證。Notion Page、Data Source、View、Formula、Relation、權限、業務資料及正式GAS/Cloud Run/Session均0更動；真人UX、權限、效能、真值測試未做。**不啟動Notion重新設計**。

## 2026-10-26｜Notion深度學習：排程獨立批次AUTO-10（Page analytics／Roles／Guest邀請）
- **[STUDY UNIT PASS; GLOBAL GOAL NOT_DONE]** [AUTO-10原始閱讀、反例與限制](research/notion-deep-study-automation-run-10-2026-10-26.md)：本輪3篇新Notion官方來源，經清冊去重、實讀全部可取得的主要文字章節，各完成一次假設/反例/修正；來源涵蓋Page analytics、Who’s who、Manage members & guests。未逐張驗圖、嵌入影片、實帳Free/Enterprise、真人/效能/資料真值測試，**10次完整深讀合格仍0／10,000**。
- **[NO SYSTEM CHANGE]** GitHub研究/索引最小同步，寫入時使用最新blob SHA並讀回核對；Notion頁/DB/View/Formula/Relation/Share/業務資料及正式GAS/Cloud Run/Session皆未變更，未開始新版設計。

## 2026-10-26｜Notion深度學習：排程獨立批次AUTO-11（Teamspaces管理／加入／權限）
- **[PASS: RESEARCH EVIDENCE; NOT_DONE: 10,000×10]** [AUTO-11研究證據](research/notion-deep-study-automation-run-11-2026-10-26.md)新增3個已知清冊未登錄的官方唯一文章，讀取主要文字章節，各有一次假設/反例/修正；未完整檢視圖片/影片、未實帳跨角色或方案測試，不計FULL_DEEP_PASS，**累積10/10達標仍0/10,000**。
- **[SCOPE VERIFIED]** 僅GitHub研究證據與共用索引增量；Notion頁/DB/View/Formula/Relation/權限/業務資料及正式GAS/Cloud Run/Session無變更，未啟動Notion設計。Default/Closed/Private/Archive安全推論仍需實帳驗證。


## 2026-10-26｜Notion深度學習：排程獨立批次AUTO-12（Export／Offline／Workspace）
- **[PASS: RESEARCH INCREMENT ONLY]** [AUTO-12原始閱讀與反例](research/notion-deep-study-automation-run-12-2026-10-26.md)：新canonical來源3篇、主要文字與FAQ閱讀3篇、獨立首次反例分析3次。未逐張檢視圖片/影片、未測試真實匯出、離線同步、工作區權限或費用，因此**不計FULL_DEEP_PASS**；累積10次嚴格完整深讀達標**0/10,000**。
- **[UNCHANGED]** 只寫GitHub研究證據/索引/決策/驗收；Notion正式及TEST Page、DB、Views、Formula、Relation、Permissions、業務列，及GAS/Cloud Run/Session均未修改；沒有開始重新設計。雙軌去重、SHA條件更新與讀回驗證。

## 2026-10-26｜Notion深度學習：排程獨立批次AUTO-13（Formula syntax／Formula intro／Properties guide）
- **[PASS：本批研究增量；NOT_DONE：整體深讀目標]** [AUTO-13逐篇閱讀及反例](research/notion-deep-study-automation-run-13-2026-10-26.md)：本批3篇官方去重canonical來源，3篇可取得文字主節核對，各1次獨立假設/反例/修正。未逐張驗圖、外部互動模板、原生公式或真人/手機/角色/效能測試；不列FULL_DEEP_PASS。**累積10/10嚴格完整深讀達標仍0／10,000篇**。
- **[PASS：研究界線]** 僅GitHub研究/來源/決策/驗收紀錄；Notion正式/TEST Page、Database、Data Source、View、Formula、Relation、權限、業務資料及GAS/Cloud Run/Session均未修改；未開始重新設計。官方函數表`empty(0)=true`等語義為待未來驗證的設計風險，不表示現有業務公式已被實測判錯。

## 2026-10-26｜Notion深度學習：AUTO-14（Relations／Sub-items／Property Access）
- **[PASS：本批研究證據；NOT_DONE：總深讀門檻]** [AUTO-14逐篇官方原文與反例](research/notion-deep-study-automation-run-14-2026-10-26.md)新增3個canonical URL，3篇完成可取得文字主章節閱讀與各1次反例分析；未逐圖、影片、外部互動或實際帳戶/角色/公式/效能測試，FULL_DEEP_PASS=0，**累積每篇10/10完整深讀達標0/10,000**。閱讀日2026-10-26，不假定官方文件修訂日。
- **[PASS：作業界線]** 只新增GitHub研究檔及來源/決策/驗收索引，逐檔使用最新main blob SHA條件寫入、讀回驗證；Notion正式與TEST Page/DB/Data Source/View/Formula/Relation/Share/業務資料零更動；GAS/Cloud Run/Session/部署零更動；沒有開始新版設計。手動/排程仍共享去重清冊並獨立續作。

## 2026-10-26｜AUTO-15官方文件研讀與去重稽核
- **[PASS: research evidence; NOT_DONE: 10,000×10]** [AUTO-15閱讀/反例](research/notion-deep-study-automation-run-15-2026-10-26.md)（`AUTO-15-20261026-0643`）：本輪3篇新canonical官方來源，3篇可讀主要文字章節、各1次反例分析；未逐圖/嵌入影片/實帳操作，FULL_DEEP_PASS=0，累積可稽核10/10達標**0/10,000**。
- **[DEDUP CORRECTION]** AUTO-14 `relations-and-rollups`/ `database-property-access`已在首批N04/N07，AUTO-13 `formulas`已在第三批NEW05；先前「新增」描述不能直接加總成全域去重來源數。原閱讀紀錄保留、總唯一數待完整去重稽核。
- **[UNCHANGED]** 只寫GitHub研究及索引；Notion正式/TEST頁、DB、Data Source、View、Formula、Relation、Share/權限、業務資料及正式GAS/Cloud Run/Session/部署均未更動；未開始重新設計。未做真人、效能、原生公式數值或公開權限實測。

## 2026-10-26｜AUTO-16 官方 Buttons／Feed／Archive 文件研讀
- **[PASS：本輪研究證據；NOT_DONE：10,000×10]** [AUTO-16閱讀與反例](research/notion-deep-study-automation-run-16-2026-10-26.md)（trace `AUTO-16-20261026-0744`）：經既有研究清冊去重，暫列新canonical URL 3篇，完成可讀主要文字章節研讀3篇與各1次獨立反例；圖片/媒體/互動示範、真實帳戶、手機、角色/效能均未完整驗證，FULL_DEEP_PASS=0。累積可稽核每篇10/10完整深讀**0/10,000**；全域精確唯一來源數未完成核對，不虛報。
- **[PASS：只讀研究／不動正式系統]** 本輪僅新增GitHub研究檔並更新來源、決策、驗收索引；Notion正式/TEST頁面、資料庫、Data Source、View、Formula、Relation、Share/權限、業務列及GAS/Cloud Run/Session/部署均未修改；沒有開始重新設計。使用最新main blob SHA條件寫入及讀回，並行流程不得覆蓋彼此增量。

## 2026-10-26｜AUTO-17 深度學習研究增量與歷史重複計數修正（非業務驗收）
- 研究取證：[AUTO-17](research/notion-deep-study-automation-run-17-2026-10-26.md)（trace `AUTO-17-20261026-0838`）。本輪2個新的官方 canonical URL（Webhook actions、Intro to workspaces）有可讀主文字及FAQ，各1次獨立反例分析；圖片、影片、付費實帳與權限／Webhook 操作未驗，**FULL_DEEP_PASS=0**。
- 歷史計數更正：AUTO-16-S01 Buttons = AUTO-05-01；AUTO-16-S02 Feed = AUTO-03-03。AUTO-16 3筆新增宣稱應減2，暫列1個新來源；原研究不刪、不雙算。全域唯一來源累計仍需完整跨檔稽核，不冒稱已核實。
- **嚴格完成10次獨立完整深讀：累積0／10,000篇，未通過目標**。本輪僅GitHub文件研究，不是 Notion 公式、UX、權限、效能或業務驗收 PASS；沒有修改 Notion／GAS／Cloud Run／Session，未開始重新設計。

## 2026-10-26｜AUTO-18：Custom Agents/分享權限研究取證（非業務驗收）
- **[PASS: research increment only; NOT_DONE: global learning]** [AUTO-18閱讀與反例證據](research/notion-deep-study-automation-run-18-2026-10-26.md)（`AUTO-18-20261026-0938`）：新增2個目前研究清冊未登錄官方canonical來源，主要正文與FAQ閱讀2篇、獨立反例2次。未完整檢查圖片/影片、未進行Business/Enterprise付費帳戶、Guest、跨角色、資料列存取或真人操作測試，故**FULL_DEEP_PASS=0**；累積每篇10次完整深讀達標仍**0/10,000篇**。全域精確去重總數仍待跨檔核驗。
- **[UNCHANGED]** 本輪只新增GitHub研究檔與來源/決策/驗收索引；未改Notion正式/TEST頁面、資料庫、Views、Formula、Relation、Share/權限、業務資料，也未改GAS/Cloud Run/Session/部署。沒有開始重新設計；不影響手動與每小時排程雙軌續作。

## 2026-10-26｜AUTO-19 Notion 深度學習研究增量（非業務驗收）
- [研究完整紀錄](research/notion-deep-study-automation-run-19-2026-10-26.md)（`AUTO-19-20261026-1042`）：新增3個經已知研究清冊去重的Notion官方來源（Map view、Task databases & sprints、Style & customize your page），完成可讀文字主節/FAQ首次反例3次；舊Synced blocks獨立針對性R3複讀1次。初選重複來源排除，不冒稱新增；未完整驗圖/影片/實帳/手機/真人權限/效能，**FULL_DEEP_PASS=0**。
- **總目標 NOT_DONE**：累積可稽核每篇10次獨立完整深讀通過**0／10,000篇**；全域唯一URL精確總數待跨檔機器去重。此批官方文件研究不是現行系統或公式數值驗收。
- **SCOPE PASS**：僅公開資料閱讀與GitHub研究/索引/決策/驗收記錄；Notion正式及TEST Page、Database、Data Source、View、Formula、Relation、Share/權限、業務資料及GAS/Cloud Run/Session/部署均未修改；未開始重新設計。手動與排程可並行續作。


## 2026-10-26｜AUTO-20 Notion深度學習（研究取證PASS；10,000×10 NOT_DONE）
- [逐篇原始證據](research/notion-deep-study-automation-run-20-2026-10-26.md)（trace `AUTO-20-20261026-1137`）：3篇新的官方獨立指南URL（Using database templates、When to use each type of database view、Use charts to visualize data and track progress directly in Notion）各取得可讀文字主節並完成1次獨立反例；N02 Views/filters/sorts 1次新角度針對性複讀，**不計新來源或完整R2**。
- **[RESEARCH INCREMENT PASS / FULL_DEEP_PASS 0]** 未逐張檢視圖片、未看3分鐘模板影片及其他嵌入影片、未實際複製模板/拖曳View/驗證跨角色/手機/效能。故本輪嚴格10/10達標新增0，累積仍**0／10,000篇**；全域唯一URL總數尚未完成全檔機器去重，不以歷史批次宣稱加總。
- **[NO SYSTEM WRITE]** 本輪只允許且只執行GitHub研究檔與來源/決策/驗收記錄；未修改任何Notion正式/TEST Page、Database、Data Source、View、Formula、Relation、Share/權限、業務資料或正式GAS/Cloud Run/Session。真人操作、業務公式數值、角色隔離與效能沒有新增PASS。研究尚未完成，**不開始Notion重新設計**；手動與排程雙軌仍可並行。

## 2026-10-26｜AUTO-21 Notion深度學習（研究增量PASS；10,000×10 NOT_DONE）
- [本輪逐篇證據](research/notion-deep-study-automation-run-21-2026-10-26.md)（trace `AUTO-21-20261026-1237`）：新候選canonical來源3（Notion手機工作區、API連線管理、NN/g過早錯誤/警告設計），各完成可取得主要文字與獨立反例分析1次；本輪舊來源複讀0。主來源去重經main研究清冊與slug搜尋暫核，**全域精確唯一URL總數仍待完整機器去重**。
- **RESEARCH INCREMENT PASS／FULL_DEEP_PASS 0**：沒有逐圖、觀看嵌入影片、真人手機/跨角色/分享/第三方整合測試；沒有驗證Notion實際業務真值或速度。故本輪10/10嚴格達標新增0，累積可核實完成仍 **0／10,000篇**，不得將R1正文閱讀冒稱完整深讀。
- **NO SYSTEM WRITE**：只寫GitHub研究、來源索引、決策與本驗收紀錄；未修改Notion TEST/正式Page、DB、Data Source、View、Formula、Relation、權限/Share、個案或財務資料，也未修改正式GAS/Cloud Run/Session/部署；不開始Notion重新設計。手動與每小時排程可繼續並行。

## 2026-10-26｜AUTO-22 研究證據與安全界線驗收（僅GitHub文件）
- trace `AUTO-22-20261026-1335`；[本輪原始研究紀錄](research/notion-deep-study-automation-run-22-2026-10-26.md)。已在開始時重讀main權威規則與研究清冊，排除已知重複slug；本輪暫列3個新canonical官方URL（Library、People profiles、Notion Agent），3篇各一次可取得正文閱讀與新反例分析，Agent含FAQ。外部文章實際發表/更新日期不明；全域唯一總數仍待完整稽核。
- **研究R1／反例紀錄：PASS（就已取得的主要文字）**。Library隱藏≠刪除；Profile≠資料權限且mobile/guest限制；個人Agent≠共享Custom Agent；官方公式建立能力段落有 `SOURCE_INTERNAL_AMBIGUITY`。這些都不是Notion真人或跨角色業務驗收。
- **完整逐篇10次深讀：PENDING**；本輪0篇、累積可核實0/10,000。圖片、影片、實帳、真實公式/權限、手機操作、效能與真實政府方案規則：**未測**，不可標PASS。
- **範圍控制**：僅 GitHub 研究紀錄／索引／決策／驗收狀態，Notion頁面、DB、View、Formula、Relation、權限、資料及正式GAS/Cloud Run/Session均零修改；沒有進入Notion重新設計。此文件更新後須讀回SHA與Commit，不能因寫入成功回應就宣稱驗證完成。

## 2026-10-26｜AUTO-23 研究證據驗收（僅GitHub文件）
- trace `AUTO-23-20261026-1436`；[研究原始紀錄](research/notion-deep-study-automation-run-23-2026-10-26.md)。新候選去重來源2篇、可讀正文與首次反例各2次；AUTO-07既有Wiki文獻另1次針對性複讀，**不是**完整R2。新增10/10完整深讀0，累積可核實仍**0/10,000**；全域唯一來源總數未完成機器稽核。
- **研究文字證據：PASS（僅限已取得正文）**；圖片/互動折疊、實帳方案/角色/手機、權限、公式、政府規則、效能與真人操作：NOT TESTED；不將文獻結論當成Notion實作或政府核准驗收。
- **範圍**：僅更新GitHub研究/來源/決策/驗收紀錄；Notion Page、DB、Data Source、View、Formula、Relation、Share/權限、業務資料及GAS/Cloud Run/Session/部署皆未修改；沒有開始重新設計。各檔須寫後重Fetch確認SHA與內容。


## 2026-10-26｜AUTO-24 研究證據驗收（非業務系統驗收）
- trace `AUTO-24-20261026-1544-RESEARCH`；[逐篇原始研究與限制](research/notion-deep-study-automation-run-24-2026-10-26.md)。
- **RESEARCH R1 PASS / FULL_DEEP_PASS 0**：本輪兩篇官方獨立來源（Task databases/My Tasks指南、Enterprise Search）各讀取可取得主要文字及首次反例一次。暫列新增去重URL2、R1正文2、首次反例2、完整10/10達標新增0；**累積10/10達標0／10,000**。全域精確唯一來源數未完成完整跨檔稽核。
- **NOT TESTED**：頁面所有圖片、影片、實際免費/付費方案、角色/外部夥伴權限、AI連線/模型、真人手機UX、效能、政府補助業務真值、公式數值。
- **SCOPE**：僅GitHub研究與來源/決策/驗收索引；沒有修改Notion正式或TEST頁、DB、Data Source、View、Formula、Relation、Share/權限、個案或財務資料、正式GAS/Cloud Run/Session/部署；沒有開始Notion重新設計。雙軌排程與手動續作繼續獨立並行。


## 2026-10-26｜AUTO-25 研究增量（非Notion業務驗收）
- trace `AUTO-25-20261026-1736-RESEARCH`；[本輪逐篇證據](research/notion-deep-study-automation-run-25-2026-10-26.md)。已核對main規則、研究目錄36份與共用索引；兩篇NN/g不同canonical文章取得主要文字並各作首次獨立反例，暫列新增去重2篇。圖片/動畫/實帳/真人手機與權限/效能/公式均 NOT_TESTED。
- **RESEARCH R1 PASS；FULL_DEEP_PASS 0**。本輪完整10次深讀達標新增0，累積可稽核**0/10,000篇**；全域唯一來源精確總數未完成完整閱讀證據去重。
- **NO SYSTEM WRITE**：只寫GitHub研究/來源/決策/驗收；Notion正式/TEST Page、DB、Data Source、View、Formula、Relation、Share/權限、業務資料及正式GAS/Cloud Run/Session/部署均未修改。尚未開始重新設計，排程與手動續作均可獨立並行。

## 2026-10-26｜AUTO-26 Notion 深度學習研究取證（非業務驗收）
- trace `AUTO-26-20261026-1742-RESEARCH`；[逐篇閱讀、去重、反例與限制](research/notion-deep-study-automation-run-26-2026-10-26.md)。本輪已核對當期 main、sources 索引所連32份研究檔及已知十面向文件。新候選 canonical 來源2（Notion layout指南與NN/g篩選設計），主要文字R1閱讀2、首次反例2；已登錄Data Tables/Information Scent針對性重讀2，不重算新URL或完整深讀。
- **RESEARCH R1 PASS；FULL_DEEP_PASS_10_OF_10 0；累積0／10,000篇**。圖片、折疊內容、動態示範、實際Notion Layout、真人操作、手機、角色權限、載入效能、政府核定規則與公式真值均NOT_TESTED。全域唯一URL總數仍待完整去重，不能將來源數加總冒稱達標。
- **NO SYSTEM WRITE**：僅GitHub研究證據/來源/決策/驗收紀錄；Notion正式/TEST頁面、資料庫、Data Source、View、Formula、Relation、權限、業務資料與GAS/Cloud Run/Session/部署皆未修改。沒有開始Notion重新設計；手動續作與既有排程繼續獨立並行。

## 2026-10-26｜AUTO-27 Notion 深度學習研究證據（非業務系統驗收）
- trace `AUTO-27-20261026-1841-RESEARCH`；[原始研究](research/notion-deep-study-automation-run-27-2026-10-26.md)。當期 main 與已知研究清冊初步去重後，暫列新來源2篇（Notion Table view、NN/g Empty States），主要正文R1 2篇、首次反例2次、既有複讀0次；未完成全儲存庫機器去重。
- **R1_MAIN_TEXT PASS／FULL_DEEP_PASS_10_OF_10 0／累積嚴格10/10仍0／10,000篇**。圖片原圖、影片、Notion真實Table批次操作、空狀態可自訂程度、真人UX、手機、角色權限、效能、公式／政府額度真值均NOT_TESTED，不冒稱完成深讀或業務驗收。
- **NO NOTION/SYSTEM WRITE**：本輪僅GitHub研究與索引；Notion正式／TEST Page、DB、Data Source、View、Formula、Relation、Share/權限、業務資料、正式GAS/Cloud Run/Session/部署均未修改。尚未開始重新設計；雙軌研究繼續共享main並以SHA條件寫入。


## 2026-10-26｜AUTO-28 研究驗收（非業務系統驗收）
- trace `AUTO-28-20261026-1943-RESEARCH`；[原始閱讀及反例紀錄](research/notion-deep-study-automation-run-28-2026-10-26.md)。三個不同canonical URL（NN/g表單錯誤、Notion資料庫按鈕、Notion資料庫自動化）經main來源索引、研究目錄39份文件及GitHub slug搜尋初步去重；取得主要文字並逐篇一次反例分析。
- **R1_MAIN_TEXT PASS（只限已讀正文）／FULL_DEEP_PASS_10_OF_10 0／累積嚴格達標0／10,000篇**。全域精確唯一來源總數仍待跨檔稽核；不得將3篇R1視為3篇10/10深讀。
- **NOT TESTED**：原圖、影片、互動折疊、Notion真實帳戶與方案權限、按鈕批次操作、automation實際觸發、跨期資料、真人手機UX、載入速度、公式與政府補助真值。
- **NO SYSTEM WRITE**：僅GitHub研究、來源、決策、驗收紀錄；Notion正式/TEST頁、DB、Data Source、View、Formula、Relation、Share/權限、業務資料、正式GAS/Cloud Run/Session/部署均未修改。未開始重新設計；手動與每小時研究共享main並以SHA條件避免覆寫。


## 2026-10-26｜AUTO-29 研究證據驗收（非業務驗收）
- trace `AUTO-29-20261026-2044-RESEARCH`；[原始研究證據](research/notion-deep-study-automation-run-29-2026-10-26.md)。新canonical候選2（Notion Connected properties、NN/g User Mistakes），R1主要文字2篇、首次獨立反例2次；全域唯一總數待跨檔完整機器稽核。
- **R1_MAIN_TEXT PASS／FULL_DEEP_PASS_10_OF_10 0／累積嚴格10/10 0／10,000篇**。圖片、影片、實際連線授權、外部檔案權限、真實角色/手機UX、效能、跨期額度公式及操作回復均NOT_TESTED。
- **NO SYSTEM WRITE**：僅GitHub研究／來源／決策／驗收文件；Notion正式或TEST Page、DB、Data Source、View、Formula、Relation、權限、個案或財務資料，以及正式GAS／Cloud Run／Session／部署均未修改；沒有開始重新設計。雙軌研究共享main並以最新SHA避免覆寫。


## 2026-10-26｜收費期別拆分影響盤點（尚未遷移）
- 使用者已授權盤點及修改受影響屬性；本輪先完成TEST Backend 31來源／736屬性Schema盤點，非正式系統全面驗收。
- IAB確認Sessions應收金額_帶入直接依主／附加方案的補助與金額重算；最終應收金額_自動優先取手動調整再取帶入。其餘候選與直接Rollup分列[依賴報告](audits/price-plan-period-dependency-audit-2026-10-26.md)。
- 使用者指定只用內部瀏覽器，不控制其電腦；後續依此執行。IAB已可讀上述公式，不能再稱所有公式讀取皆受阻。
- 尚缺最新00.config_notion、必要公式／按鈕完整依賴、歷史映射及隔離測試。Notion零寫入，遷移BLOCKED／NOT_TESTED，不聲稱修改完成。不更動GAS、Cloud Run或Session登入系統。

## 2026-10-26｜AUTO-30 Notion 深度學習取證驗收（僅GitHub研究）
- trace `AUTO-30-20261026-2235-RESEARCH`；[逐篇研究原始紀錄](research/notion-deep-study-automation-run-30-2026-10-26.md)。已查sources.md所連36份研究文件，兩篇NN/g來源暫列新canonical URL，主要正文R1 2、首次獨立反例2；既有Notion Property access針對性複讀1，不重算新來源/完整R2。
- **PASS：本輪文字研究與GitHub記錄；FULL_DEEP_PASS_10_OF_10 = 0；累積嚴格達標仍0／10,000篇**。圖片、影片、外部示範、真實Notion權限、角色、手機、操作速度、公式與政府額度均未實測；全庫唯一URL總數未完成全面稽核。
- **SCOPE：NO NOTION/SYSTEM WRITE**。僅GitHub研究/來源/決策/驗收文檔；未修改任何Notion正式或TEST頁、DB、Data Source、View、Formula、Relation、Share/權限、業務資料，也未修改正式GAS/Cloud Run/Session/部署。尚未開始重新設計，手動與自動研究仍可獨立並行。


## 2026-10-26｜AUTO-31 研究證據驗收（非業務系統驗收）
- trace `AUTO-31-20261026-2249-RESEARCH`；[逐篇證據與限制](research/notion-deep-study-automation-run-31-2026-10-26.md)。main規範與sources所連37份研究文件已檢查；兩個NN/g slug在已查清冊未見登錄，暫列新canonical來源2、主要正文R1 2、首次獨立反例2；早期已有Charts/Forms/Dashboards/Feeds均未重算。
- **R1_MAIN_BODY PASS（文字章節）／FULL_DEEP_PASS_10_OF_10 0／累積0／10,000篇**。原圖、影片、互動、真人視覺層級/可及性、手機、角色權限、載入速度、補助公式與真實額度 NOT_TESTED；全庫未索引檔案精確去重仍未完成。
- **NO NOTION/SYSTEM WRITE**：僅GitHub研究與來源/決策/驗收記錄；未改Notion正式/TEST頁、資料庫、Data Source、View、Formula、Relation、Share/權限、業務資料，亦未改GAS/Cloud Run/Session/部署。未開始重新設計，雙軌研究仍可並行。

## 2026-10-26｜AUTO-32 Notion深度學習研究取證（非系統驗收）
- trace `AUTO-32-20261026-2340-RESEARCH`；[逐篇來源/閱讀/反例](research/notion-deep-study-automation-run-32-2026-10-26.md)。兩篇NN/g（Tabs, Used Right；Indicators, Validations, and Notifications）在已查清冊初步去重後列新canonical候選2；R1主要文字2篇、首次獨立反例2次、既有完整複讀0。
- **R1_MAIN_TEXT PASS（限可讀正文與圖說）／FULL_DEEP_PASS_10_OF_10 0／累積嚴格達標0／10,000篇**。全域精確唯一URL仍待完整稽核；原始圖片逐張、影音/互動、Notion實帳/手機/權限/效能/公式及真實補助業務未測，不能宣稱十次深讀或實作驗收。
- **NO NOTION/SYSTEM WRITE**：僅GitHub研究/來源/決策/驗收記錄，沒有修改Notion正式/TEST頁、DB、Data Source、View、Formula、Relation、Share/權限、業務資料，亦未修改正式GAS/Cloud Run/Session/部署。尚未進入重新設計，手動與排程可並行。

## 2026-10-27｜AUTO-33 研究證據驗收（非 Notion 業務驗收）
- trace `AUTO-33-20261027-0038-RESEARCH`；[逐篇證據](research/notion-deep-study-automation-run-33-2026-10-27.md)。研究目錄44份逐檔檢查兩個新slug均無既有命中；來源索引同樣未命中；本輪新canonical候選2、可讀主要文字R1 2、首次獨立反例2、舊來源針對性複讀2（不計完整R2）。
- **研究文字取證 PASS（限已讀正文）／FULL_DEEP_PASS_10_OF_10 本輪0／累積嚴格達標0/10,000**；全域唯一URL總數待完整稽核。原始圖、Figma原型、問卷、互動、Notion真人/手機/角色權限/速度/公式/補助核定數值 NOT_TESTED。
- **NO NOTION/SYSTEM WRITE**：僅GitHub研究與來源/決策/驗收紀錄；未改Notion正式或TEST頁、資料庫、Data Source、View、Formula、Relation、權限、業務資料，亦未改正式GAS、Cloud Run、Session、部署；未開始重新設計。


## 2026-10-27｜AUTO-34 研究證據驗收（非業務系統驗收）
- trace `AUTO-34-20261027-0138-RESEARCH`；[逐節閱讀、去重及反證](research/notion-deep-study-automation-run-34-2026-10-27.md)。main規範與研究目錄45份已查，兩個 NN/g URL 在已查來源清冊中未見先前登錄；新候選2、R1主要文字2、首次反例2、完整R2–R10為0。
- **研究主要正文 PASS（限已讀文字）／FULL_DEEP_PASS_10_OF_10 本輪0、累積嚴格0/10000**。原圖、影片、互動、真實 Notion 操作、手機、角色權限、載入時間、跨方案公式與核定數值 NOT_TESTED；全域唯一來源總數待完整稽核。
- **NO NOTION/SYSTEM WRITE**：本輪只在GitHub研究／來源／決策／驗收文件追加記錄；未改任何Notion正式/TEST頁、DB、Data Source、View、Formula、Relation、權限、業務資料，也未改正式GAS、Cloud Run、Session或部署；未開始重新設計。

## 2026-10-27｜AUTO-35 研究證據驗收（非Notion業務驗收）
- trace `AUTO-35-20261027-0241-RESEARCH`；[逐篇研究證據](research/notion-deep-study-automation-run-35-2026-10-27.md)。已核對main主要規範及sources.md所連40份研究清冊，暫列兩個新的canonical候選（NN/g日期輸入、前端元件指南）；R1主要正文閱讀2篇、各首次獨立反例共2次；全儲存庫未索引檔案之精確去重仍待完成。
- **RESEARCH MAIN TEXT PASS / FULL_DEEP_PASS_10_OF_10本輪0，累積嚴格達標仍0/10,000篇**。未逐張查原圖、操作互動、實際Notion日期欄/手機/角色/權限/效能、政府補助跨期規則與歷史收費公式真值；不能將研究假說冒稱系統驗收。
- **NO NOTION/SYSTEM WRITE**：僅研究與GitHub來源、決策、驗收記錄；未修改Notion正式/TEST頁面、資料庫、View、Formula、Relation、權限、業務資料，也未修改GAS、Cloud Run、Session或部署。研究目標未完成，不進入Notion重新設計；每小時研究與手動續作繼續獨立並行。


## 2026-10-27｜AUTO-36 研究證據驗收（非Notion系統驗收）
- trace `AUTO-36-20261027-0344-RESEARCH`；[研究原文取證、反例及限制](research/notion-deep-study-automation-run-36-2026-10-27.md)。main七項規範已讀，研究目錄47份 .md 已查兩個新slug；Notion Databases reimagined、NN/g Dropdown List 暫列新canonical來源2、主要正文R1 2、首次獨立反例2。Three key databases（batch03）、Few Guesses（AUTO25）均已存在，本輪針對性複讀2，未重算新URL／完整R2。
- **PASS僅限研究主要文字與GitHub證據；FULL_DEEP_PASS_10_OF_10 本輪0，累積嚴格0/10,000篇**。全儲存庫歷史唯一URL數仍待精確稽核；原始圖片、影片、互動、真人操作、Notion原生可搜尋欄位、手機、權限、速度、跨期補助公式與歷史收費真值均未測試。
- **NO NOTION/SYSTEM WRITE**：僅研究及GitHub來源／決策／驗收紀錄；未更動Notion正式或TEST頁、DB、Data Source、View、Formula、Relation、權限、業務資料，亦未更動正式GAS、Cloud Run、Session、部署。尚未開始重新設計，手動與排程研究可並行。

## 2026-10-27｜AUTO-37 深度學習研究取證（非業務驗收）
- trace `AUTO-37-20261027-0438-RESEARCH`；[原文閱讀及反例](research/notion-deep-study-automation-run-37-2026-10-27.md)。已查 main 主要規範、來源索引、研究目錄48份檔名與GitHub slug搜尋；暫列2篇新canonical候選（NN/g快捷操作、NN/g字母排序），主要正文R1 2、首次獨立反例2。全庫未索引文件仍未完成精確去重。
- **研究文字 PASS（僅已讀正文與圖說）／FULL_DEEP_PASS_10_OF_10 本輪0、累積嚴格0/10,000篇**；未完成逐張原圖、影音、互動、實際 Notion 操作、真人/手機/角色權限、載入效能、跨期金額與公式真值。兩篇均不算完整十次深讀。
- **NO NOTION / SYSTEM WRITE**：只更新 GitHub 研究、來源、決策、驗收文件；Notion正式/TEST Page、DB、Data Source、View、Formula、Relation、Share/權限、業務資料、正式 GAS/Cloud Run/Session/部署皆未修改；未開始重新設計。每小時與手動研究可並行，以最新main SHA條件避免覆寫。


## 2026-10-27｜AUTO-38 研究證據驗收（非Notion業務驗收）
- trace `AUTO-38-20261027-0543-RESEARCH`；[完整閱讀、去重、反例及限制](research/notion-deep-study-automation-run-38-2026-10-27.md)。main七項規範已查；研究目錄49份已逐檔比對候選slug與標題。新canonical候選1篇、既有DS-025/N15由SUMMARY_ONLY升級本輪主要正文1篇，首次獨立反例2；**不是兩篇新來源**。
- **PASS限原文主要文字可讀與研究記錄；FULL_DEEP_PASS_10_OF_10 本輪0，累積可核實仍0/10,000篇**。全儲存庫同文異址去重、原始圖片、影片、互動、實際Notion帳戶、手機、角色權限、效能、補助期別公式/金額均NOT_TESTED。
- **NO NOTION/SYSTEM WRITE**：僅GitHub研究檔、來源、決策、驗收；未改Notion正式/TEST Page、DB、Data Source、View、Formula、Relation、Share/權限、業務資料，亦未改正式GAS/Cloud Run/Session/部署。未開始Notion重新設計；每小時與手動研究可並行，寫入衝突以SHA安全合併。

## 2026-10-27｜AUTO-39 研究文字取證（非Notion業務驗收）
- trace `AUTO-39-20261027-0644-RESEARCH`；[兩篇來源、正文覆蓋、反例與限制](research/notion-deep-study-automation-run-39-2026-10-27.md)。已Fetch main 七項規範、sources.md引用的45份研究檔；新canonical候選2（Filters vs. Facets；Beyond the Hamburger）、主要正文獨立閱讀2、首次獨立反例2；完整R2–R10 0。
- **PASS 僅限已取得主要正文及GitHub研究紀錄；FULL_DEEP_PASS_10_OF_10 本輪0、累積可核實0/10,000篇**。全庫同文異址去重未完成；原始圖片、影音/互動、Notion實際工作區、真人/手機/角色權限、效能、跨期公式/金額均 NOT_TESTED；一般網站樣本數據不可外推為本所成效。
- **NO NOTION/SYSTEM WRITE**：本輪僅GitHub研究、來源、決策與驗收紀錄；未改Notion正式或TEST頁面、DB、Data Source、View、Formula、Relation、Share/權限或業務資料，亦未改正式GAS、Cloud Run、Session、部署；研究門檻未達，尚未開始重新設計。每小時與手動研究獨立並行，寫入前以最新blob SHA避免覆蓋。


## 2026-10-27｜AUTO-40 研究證據驗收（非Notion業務驗收）
- trace `AUTO-40-20261027-0739-RESEARCH`；[原始研究及反例](research/notion-deep-study-automation-run-40-2026-10-27.md)。重新讀 main 主要規範/索引，研究目錄51份Markdown逐檔比對兩個slug未命中；已查清冊新canonical候選2（Error-Message Guidelines；Confirmation Dialogs Can Prevent User Errors）、可讀主要正文R1 2、首次獨立反例2，**非完整深讀**。
- **PASS僅限本輪文字研究與GitHub證據記錄；FULL_DEEP_PASS_10_OF_10 本輪0、累積嚴格0/10,000篇**。全儲存庫其他路徑/同文異址去重、原始圖片、影音/互動、Notion實際帳戶/角色/手機/效能/公式、政府補助真實核定數值均NOT_TESTED。
- **NO NOTION/SYSTEM WRITE**：僅GitHub研究/來源/決策/驗收文件；未修改Notion正式或TEST Page、DB、Data Source、View、Formula、Relation、Share/權限、個案/財務資料，也未修改正式GAS/Cloud Run/Session/部署。研究門檻未達，未開始重新設計；手動與排程獨立並行。


## 2026-10-27｜AUTO-41 研究證據驗收（非Notion業務驗收）
- trace `AUTO-41-20261027-0840-RESEARCH`；[逐篇原始證據、反例及限制](research/notion-deep-study-automation-run-41-2026-10-27.md)。main主要規範/來源索引已Fetch，研究目錄清單52份；**未完成52份全文逐檔去重**，GitHub code search與sources索引對兩個slug均無命中，僅暫列新候選2。兩篇NN/g可讀主要正文各一次、首次獨立反例各一次；不算完整深讀。
- **R1_MAIN_TEXT PASS（僅文字）／FULL_DEEP_PASS_10_OF_10本輪0，累積嚴格0/10,000篇**。全庫同文異址去重、原始圖片/影音/互動、Notion真實手機/桌面/角色權限/效能/公式/政府核定真值均NOT_TESTED。
- **NO NOTION/SYSTEM WRITE**：僅GitHub研究與進度記錄；未改Notion正式或TEST Page、DB、Data Source、View、Formula、Relation、權限、業務資料，亦未修改正式GAS/Cloud Run/Session/部署；研究目標未完成，不進入重新設計。雙軌研究繼續共享main並以SHA條件寫入。
