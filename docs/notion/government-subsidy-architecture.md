# 政府補助通用資料模型

## 2026-10-26｜方案參與模型與已同意清理完成

目前模型以 Price Plans 保存方案與核定期規則；「補助方案用量」按個案＋方案期別保存用量；新增的「心理師方案額度」按心理師＋方案期別保存接案確認與本週摘要，沿用既有週回報。主檔僅保留通用關聯，新增方案／年度不再增加專用輸入欄位或改年度常數。服務歷程依個案與收費方案查閱。

使用者已明確同意精確清理範圍；Staff 的「額度查閱方案、補助本週摘要_自動、免週回報方案、他處接案情形、他處接案確認日、免週回報有效至」六欄及兩補助頁的四個舊人員檢視均已實際移除並回查。各頁只保留新來源的「各方案｜本週額度」「各方案｜他處回報設定」。人員、週回報與會談來源未刪除。其他有相依的歷史青壯欄位不在此次六欄清理範圍，新方案不用它們。

原生現有資料計算已回查；9 個離線合成模型情境通過，不等於多個真實方案整合、真人 UX、角色權限或載入速度通過。詳[資料歸屬修正報告](audits/subsidy-ownership-model-2026-10-26.md)；舊階段與舊 Staff 摘要公式僅作歷史／回復依據。

## 2026-10-25 實作／2026-10-26 清除回查｜目前已套用模型
本節及[實作報告](audits/subsidy-usage-ledger-implementation-2026-10-25.md)取代下文舊階段的用量主來源／0新DB提案；下文保留作歷史依據。

- **補助方案用量**為個案用量主來源：個案ID＋Price Plan方案實例ID一筆；20筆既有非合成用量已移轉。每期各自設定上限／期間，新增期別不複製資料庫或修改年度常數。
- **Cases**增加反向用量關聯；**Care Episodes**沿用原餘額／狀態公式，以個案與自身收費方案尋找用量，缺漏或重複會警示。沒有新增各方案的用量輸入欄。原臨床歷程管理與人工選方案不變。
- 本所完成／預約由個案既有關聯會談取得，以各Session實際Price Plan ID與狀態計數；取消／改期／no-show不計入。他處只保存回報次數及確認，未知不自動零。
- 心理師週摘要取所選方案的週上限、週起算日、期間與同方案同週回報；免週回報需對應方案及完整週期涵蓋的有效確認。
- 期限未核實則提示待核對；餘額不自動批准日期／間隔／資格。13筆過去日期仍為預約的異常留待人工核實，不擅改業務狀態。
- 兩原網址同源，日常三區同頁直接顯示；低頻資料仍在同頁。舊年度欄位因歷史依賴保留並退出日常輸入。
- 14筆本次合成資料已於2026-10-26依使用者同意移到垃圾桶，回查14/14；移除測試暫時篩選後兩頁各20用量／2心理師／1啟用政府方案。真人UX、實際載入秒數及角色權限尚未取得新PASS。

狀態：**已確認原則，尚未全面 TEST 驗收**；2026-10-24。依據現行 Google Docs v3.4 的第十一節（v3.5 多方案補充）及使用者最新決策。

## 永久不變條件

1. 同時支援 **多政府方案 × 多年度／核定期別 × 當期獨立規則**。不得將青壯、115、每案3次、心理師6次、7日間隔或3個月期限寫死在共用公式／資料模型。
2. 每個核定期別／獨立額度池有一個 **Price Plans 方案實例的 Notion Page ID**。年度與計畫名稱只供標示，期別可能不等於1/1～12/31。追加減額要判斷是原額度池的調整，還是新的獨立期別。
3. 不同政府方案和不同核定期別**不得混算**，除非有主管機關可追溯的正式共用配額條件。
4. 每期規則各自核實：資格與年齡基準時點、每案／機構／心理師週額度、週起始日、有效服務狀態、第一次實際服務、總期限、會談間隔、跨機構用量、補助金額、例外及生效期間。新的期別不能自動沿用上一期。
5. 未知 ≠ 未確認 ≠ 不適用 ≠ 已確認0。無核實來源時顯示待核對；View 不是自動核准。
6. 沿用現有資料庫，只有必要且證明效益後才提出最小 Schema 變更。不預先為每年度複製 Cases 欄位或另建整套方案資料庫。

## 模型關係

- **Price Plans**：一筆獨立核定期別一個實例。現有 Schema 已包含補助方案識別（目前只有「青壯」選項）、起迄、額度控制、每案上限、心理師週上限及額度調整／Sessions 關聯。將來新增新方案時，按當期核實規則擴充必要識別或欄位，不重建資料庫。
- **補助參與紀錄｜TEST**：一筆「Cases 個案 ID × Price Plan 方案實例 ID」參與。不能只以個案＋年份唯一識別，因同年可能參加不同補助。既有欄位為資格狀態、來源原因、他處用量／確認、首次服務／期限、本方案會談及狀態；實際 Schema 2026-10-24 查得13欄。Notion 不保證跨欄唯一，須稽核重複。
- **Cases**：永久個案主檔；不再逐年擴增通用欄位。舊青壯115專用欄位先保留歷史相容。
- **Care Episodes**：管理真實歷程、開結案及原因；補助到期但歷程仍進行中不可自動結案或隱藏。
- **Sessions**：透過 Session 本身的 Price Plan ID、狀態與日期核實方案占用；與 Episode 方案不一致需待核對。取消／改期／no-show 不計一般有效占用；過期仍標已預約應列異常且未核實前不任意釋出占用。
- **Staff／心理師補助週紀錄**：心理師＋方案實例＋依當期規則認定之週期；沒有週上限的方案不可擅套青壯的6次。
- **補助額度調整**：每筆指向其核定方案實例，明確保留增減、依據與所屬期間。

## 現有核心欄位數快照（不是即時值）

2026-10-24 已 Fetch：Price Plans 30、Cases 49、Care Episodes 50、Sessions 67（其中34 Formula）、Staff 55、補助參與紀錄｜TEST 13。大量 Relation／Rollup 有依賴風險；未核實前不得大規模改動。

## 期別與同案併行驗收

須用真正隔離的 TEST 方案驗證：同一個案同年度兩個政府方案；同方案跨兩年；同年度兩期；不同資格、每案上限、心理師週起始與上限、不同期限與間隔、外部使用不適用／未知／確認0、重複參與、取消／改期／逾期未結清；核實 Session Price Plan Relation、參與表與歷程的對照，逐方案比對集合及 Notion 原生計算真值。**上述通用情境尚未全部實測，不能聲稱通過。**

## 改動門檻

非青壯舊功能以最小修正為原則；任何核心 Schema、Relation、共享 Formula、大量資料遷移或重大 UX 流程改造，須先提出變更分析與回復方式，經使用者同意。


## 2026-10-24｜政府補助 TEST 唯讀隔離與資料完整性｜隔離注意事項
歷史TEST參與列即使被View排除，仍可能連到啟用Price Plan及會談；不得將VIEW分類視為計算層隔離。必須在真正獨立的TEST來源驗證各種會談狀態、原生計次及跨期規則，才可考慮經核准修改共用Relation／Formula。[唯讀證據](audits/subsidy-readonly-integrity-2026-10-24.md)。


## 青壯人工核對後於服務歷程選方案｜2026-10-24｜資格與計數分離（最新青壯決策）
- **資格決策／前端操作**：青壯人工確認資格後，直接在 Care Episodes「💲收費方案」選該核定期 Price Plan；不另建資格核對清單、不強制每次先建立「個案×方案」參與頁才能選方案。
- **計數／追溯**：補助使用量、每案上限、心理師週額度、核定總額度仍依正確 Sessions／Price Plans 關聯及該核定期規則判斷；不以人工資格確認等同已完成額度核定。既有參與資料庫及候選複合鍵仍保留作歷史相依及其他方案設計參考，**但不可再把它說成青壯的強制資格工作流**。
- **不外推**：其他政府方案是否需要專用審核記錄，依方案／年度／期別規則決定；不在通用欄位硬編碼青壯。修改共用 Formula／Relation、批量整理歷史資料需另報前後比較與核准。
- [現行設計及已做的TEST變更](audits/youth-manual-eligibility-episode-plan-2026-10-24.md)。


## 2026-10-24｜服務歷程與會談方案對照：唯讀驗證｜主方案一致性是需核對的獨立條件
2026-10-24 的 Notion TEST 唯讀回歸：295筆會談與57筆服務歷程關聯完整，其中8筆 Session/ Episode 主方案不同；青壯兩方向各4筆。**不能因此將服務歷程的方案強制同步到每筆 Session**：可能有個別會談採不同方案之合法業務情境。必須按實際每筆 Session 的 Price Plan、狀態、方案期別與當期政府規則認列額度，並先確認使用者接受何種個別改方案操作方式。啟用青壯方案 Session集合41筆雙向一致但 Formula 未回傳原生數值；不可宣稱此方案已占用36或有可用餘額。[回歸報告](audits/episode-session-plan-consistency-2026-10-24.md)。

## 2026-10-24｜青壯／自費 8 筆方案差異之情境分類回查｜Episode 預設方案與 Session 單次方案仍需界定
現有8筆方案不一致分布於4個進行中的個別服務歷程，且只涉及青壯與自費兩種主方案，可能包含刻意的個別會談切換測試，不應強制每次 Session 方案等同 Episode 方案。**方案歸屬權威與例外邏輯尚未由使用者明確確認**；計數應待此項業務規則與 Notion 原生 Formula 真值均查核後再定稿，不把從歷程連動當作自動覆寫授權。沒有修改既有共享Schema、Formula、Relation。詳見[匿名狀態／收費分類核對](audits/episode-session-plan-consistency-2026-10-24.md)。


## 2026-10-24｜政府補助計數 Rollup 直接相依驗證｜實際 Rollup 路徑與未確定的公式權威
當次最新 Notion Schema 顯示：Price Plans 的「已完成_帶入」「已預約_帶入」「待確認_帶入」均以 `sum` 沿自身與 Sessions 的關聯加總 Sessions 三個相應計數 Formula；Care Episodes 的「本歷程已完成_帶入」「本歷程已預約_帶入」則另沿歷程↔Sessions 加總。**兩條不同彙總鏈並存**，不可將 Episode 方案選擇與 Price Plans 方案總占用視為同一個欄位。

然而上述 Sessions 計數 Formula 的程式碼與原生數值尚未可讀，不能只從 Rollup 關聯路徑確認它是否還有檢查 Episode 方案或其他條件。依使用者已確認的業務流程，先選 Care Episodes 的主收費方案，保留有必要時 Session 的個別收費方案差異；具體「個別 Session 變更方案是否計入政府額度」仍需原生值與真實規則核對，不能逕行硬編碼／批次同化。見[唯讀回查](audits/episode-session-plan-consistency-2026-10-24.md)。

## 2026-10-24｜115青壯心理師週核銷正式函：僅記錄核定期規則，不修改通用模型
- 衛福部115年3月25日函指出，**115青壯**每位醫師／心理師每週（**週日至週六**）核銷**合計六人次**，包含所有執業登記與報備支援地點；自**115/4/12**中央核銷系統實施限制。跨機構/地點是**同一位治療人員＋相同期別方案的總使用**，院內Sessions關聯完備不代表外部資料已知。
- 正式設計仍依**實際Price Plan方案實例＋適用日期及本期核定規則**配置，不能將青壯115六次上限／週起算日期寫死於其他政府方案或全年度共用Formula；如有不同年度更新須考慮版本生效日。外部未知／未回報不得視為0。
- 現有TEST週回報6/6週日起始，**本週兩筆未核實他處次數**，現有Staff原生Formula數值不可讀，故僅結構驗證PASS，**不構成計數或可用額度PASS**；無實際Data Source及通用模型修改。[當次正式依據與唯讀稽核](audits/youth-weekly-allowance-2026-10-24.md)。

## 2026-10-24｜115青壯補助請款與400元掛號費已使用獨立Price Plan及Billing
- **不是新資料模型**：現有已啟用「掛號費」Price Plan實例 `金額400／補助0／自費／收據收費項目=掛號費`；青壯115實例則 `金額1600／補助1600／補助`。Sessions以既有 `💲 收費方案`＋`💲 附加收費方案`分開關聯；Billing以`💲 收費方案`分開記載向個案400元掛號費與向衛生局1600元政府補助請款，不需要因青壯Price Plan沒有掛號費數字就新建欄位或修改政府補助額度。
- **實證／例外**：此次完整讀Sessions295、Billing203，青壯41筆中35筆附加掛號費；22筆掛號費Billing及23筆政府補助Billing共45筆的`Session↔Billing`關聯皆匹配已完成青壯Session，且掛號費Billing均是400元。已完成23筆中1筆**沒有附加掛號費或該款Bill**，意圖未知，不自動補帳。已預約13筆中12筆有附加掛號費而尚非實際收款。
- **不可過度宣稱**：此為關聯與顯式記帳欄位驗收，不是Notion Formula即時應收、政府核銷、銀行對帳、按鈕權限或真正跨年度模型完成驗收；使用者人工資格核對→Care Episodes選Price Plan的已核可流程維持不變。詳見[專項匿名稽核](audits/episode-session-plan-consistency-2026-10-24.md)。

## 2026-10-24｜青壯在汐予採一案一次服務歷程；核定期屆滿即結案（使用者已確認）

- **業務約束（只限青壯）**：同一個案於本所只有一筆青壯 Care Episode，本所不再對同個案開第二筆青壯歷程；該歷程內完成當期青壯可使用的服務。個案青壯額度直接看其單一Care Episode的本歷程已完成、已預約、個案方案上限、他處確認、個案剩餘與狀態；**不開發正常青壯跨歷程總額度計數**。
- **屆期動作**：超過衛生局核定期限後由本所依行政作業**將該青壯 Care Episode 結案**，不再承接同個案新青壯歷程。此處不等於已授權自動化無條件更改現有資料；目前沒有批次更新狀態、公式或Schema，屆期未結案者保留可見，待有權人員處理。核定期限應以當期Price Plan及其實際官方規則核實，不能用「每年12/31」當通用條件。
- **不跨其他政府方案**：其他補助可能有不同資格、期別與多次歷程規則；原多方案／期別Price Plan實例歸屬仍保留，不能因青壯單一歷程而砍通用計數架構、改共享公式或假設所有政府補助都只能有一歷程。
- **現有資料例外**：在TEST的青壯115服務歷程22筆按個案Relation去重為21名，有一個個案連兩筆歷程，**兩筆均標示測試**且連至啟用中的115 Price Plan。這是待查測試資料例外，不代表真實個案重複承接、也不因新規則自動合併、移除連結或刪除資料。
- [本輪VIEW設定、驗收、原值回復方案](audits/subsidy-usage-views-2026-10-24.md)；[Notion TEST工作台](https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf)。

## 2026-10-24｜使用者核准免週回報三欄位：Notion TEST已建立，公式整合硬停止
- **[USER APPROVAL]** 使用者回覆「同意繼續」，明確核准前一回合之三欄位方案：確實沒有在其他地點接案的心理師免每週重複確認；他處接案／可能有接案者按週回報。這是設計與最小實作核准，**不是**授權猜測現行共享公式、替現有心理師批次填零或覆蓋相關業務紀錄。
- **[NOTION STAFF SCHEMA WRITE / READBACK PASS]** 經重新 Fetch，TEST Backend 的既有 Staff Data Source 原有55個欄位、無目標3欄；以一筆明確DDL新增 `他處接案情形` Select（未確認／已確認無他處接案／有或可能有他處接案）、`他處接案確認日` Date、`免週回報有效至` Date。寫後重新 Fetch 為 **58欄**，三欄型別／選項吻合；現有在職心理師週額度 Saved View仍 **2筆、has_more=false**，新欄對該兩筆皆留空，**未設定任何人的免回報資格**。
- **[13 POLICY CASES PASS (OFF-SYSTEM ONLY)]** 已對純決策規則執行13例離線測試：有效無他處可免週報、他處已確認2／0、未知或空值、未確認、缺確認日期、有效期不到週末、週中才確認、週中接案異動、現有非零回報衝突、跨方案／期別尚未覆核、僅有未確認數字等；13/13符合預期。**這不是Notion原生公式／UI PASS**。候選公式須確保`確認日≤評估週首日`、`有效至≥評估週末`、覆蓋當期Price Plan實例且無衝突，否則fail-closed；禁止用`執業類型=本所執業`推定無他處。
- **[FORMULA HARD STOP / FEATURE NOT LIVE]** 當前Notion Fetch仍只見Formula `formulaCode://`參照，直接Fetch參照回 `validation_error`，尚無全部現行公式**完整原文**、依賴、可驗證基準與隔離TEST；按專案硬停止規則**沒有更動共享公式**。因此目前「免週回報自動判斷」**尚未實際啟用**；人員填選「已確認無他處接案」也不會自動使本週額度放行，原有缺回報待核對規則仍適用。下一步需找出目前完整公式及對應回復基準，隔離測試再做最小公式整合，不能假稱全部完成。
- **[BACKUP / ROLLBACK]** 寫入前已確認三欄皆不存在、原Staff55欄、原View五顯示欄及兩個既有Formula codeUrl。需回復時先重讀最新Schema、先確認無任何人已使用新欄和無並行修改，再僅移除這次新增的三欄（現均空白）；不得移除其他Staff欄位或覆蓋原Formula／Role／業務列。`00.config_notion`精確原件仍未定位，這次使用當次直接Fetch的實際Data Source而非GitHub舊ID。

## 2026-10-24｜UX v4使用者4/4 PASS；新增首頁異常與最後一次候選提醒（TEST待驗）
- **[USER CONFIRMED / V4 PASS]** 使用者對既有UX v4四題回覆`1A 2A 3A 4A`（4/4真人操作PASS）；不重測或改寫為其他結果。同一回覆新增三項需求：①質疑在首頁展開38筆「服務歷程｜直接選收費方案」的必要性，②警示異常清單及下一次為最後一次提醒應在首頁直接看到，③需解釋當前資料庫設計。**這是後續新驗收項目，不得把舊4A當新增警示通過**。
- **[ANOMALY VIEW / VERIFIED SCOPE]** 新建`view://4038ca66-aa4d-81b5-a7fa-000cd34b7bdb`，來源Care Episodes真實現有Data Source；Filter為當前**青壯115 Price Plan實例Relation**、進行中、（開案日期空白 **OR** 他處使用已確認未勾）。Saved View查得**2筆**，兩筆皆開案日空白，其中一筆同時他處未確認，**不是三筆**。此View僅代表列出的兩類可驗證待核對，不代表涵蓋所有數值超額、期別逾期、Sessions方案衝突等異常。
- **[FINAL-USE ALERT / CANDIDATE NOT CONFIRMED]** 新建`view://4038ca66-aa4d-81e3-bfbd-000cfc0ac598`，Care Episodes Filter為當前青壯115 Price Plan實例Relation＋進行中＋既有`個案補助剩餘_自動` Formula在Notion Saved View中精確顯示文字`1`。回查**11筆**，SHOW已完成、已預約、剩餘額度及個案狀態。這表示**剩餘1次的候選**，不能保證下個已預約療程就是補助最後一次；需驗證預約、他處已用／未知、方案特定期別及公式完整expression後才可提高精度。無自行修改公式、標記完成或結案。
- **[DATA ARCHITECTURE EXPLAINED]** Price Plans＝方案實例＋核定期別上限，連額度調整與Sessions；Care Episodes＝個案服務歷程、💲收費方案Relation和Sessions，借Rollup/Formula計已完成／已預約／剩餘及個案狀態；Sessions＝每次會談／預約與實際狀態、心理師和方案；Staff＝心理師及Sessions、補助週回報Relation，週限以當期方案規則決定；週回報＝心理師×實際Price Plan方案實例×週起始日，`未確認`與`已確認0`不混用。TEST頁只是Linked Views顯示同一份原資料，**不另建業務資料庫**或隔離寫入。
- **[LIMITS / RETEST GATE]** 原4A保持通過，兩張警示的原生過濾與資料量2／11、三額度顯示結構PASS；**警示視覺／最後一次精確性／整體新UX真人尚待確認**，不得將新增內容寫PASS。v4原本展開4張表，現在展開5張（2提醒＋3額度）並有1張低頻收合，可能增加首屏負載；無真實載入時間測量。免週報原公式整合仍NOT LIVE，角色權限DEFERRED。待新增UX驗收通過，再繼續其他事項。

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
