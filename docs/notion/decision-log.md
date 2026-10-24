# 設計決策與變更日誌

本檔區分「已由使用者明確確認」與「設計草案／尚未核准」。新紀錄應附日期、影響範圍、來源及實際回查證據；勿默默覆寫既有決策。

## 2026-10-24｜多政府方案 × 年度／核定期別（已確認）

- 目前僅青壯，但需容納多種政府補助及每期不同規則；通用模型、公式、View、統計不可寫死青壯或115等具體年度、次數、期限。
- 各獨立核定期別用 Price Plans Page ID 辨識；同案可在同年度參加多種方案。參與紀錄候選鍵「個案ID＋方案實例ID」；不同方案與期別不混算，除非有明確共用規則。
- 現有青壯跨年度 Google Docs v3.4 後追加第十一節 v3.5 設計補充，有修改前備份和讀回確認。沒有同步修改 Notion Schema。

## 2026-10-24｜只針對 Notion 的階段界線（已確認）

- 青壯啟用 TEST 與全面 UX／資料庫研究：僅 Notion。正式 GAS、Cloud Run、中央 Session、部署非此次修改範圍。
- 原有非青壯功能優先最小修正；較大結構／公式／操作變更先提出比較和回復方案，取得使用者同意後才動。

## 2026-10-24｜資料庫、工作台和 UX 共同研究（已確認研究方向）

- 研究至少10,000篇 Notion 官方文件、模板、網路教學、資料庫架構與 UX 文獻；實讀數尚未達標，須做可追溯研究清冊。原有十個功能頁也列入盤點。
- 初查10頁有76個資料庫區塊（非76個唯一資料庫），五個核心資料庫共有251欄、70 Formula、53 Relation、38 Rollup（2026-10-24當次Schema快照）。未證明需要大幅重構，僅為稽核起點。

## 先前仍適用的已確認決策

- 首頁主要顯示治療所本期額度、心理師本週額度、個案當期額度，深入歷史與調整收合。
- 補助到期但 Care Episode 尚進行中仍顯示異常提醒，不能自動結案或隱藏。
- Cases 不應不斷新增專年通用欄位；Sessions 依實際 Price Plan Relation 判定候選占用，收費方案矛盾先待人工核對。
- TEST 字首不構成隔離性保證；未確認他處回報與日期不得視為0或合格。

## 尚未核准

舊模組大規模重構、增加大量 Schema、全面替換原工作台、批量關聯既有真實會談、未經核實的跨方案共用配額實作，皆非已獲批准事項。

## 後續追加模板

日期｜狀態（決策／唯讀／TEST PASS／PARTIAL／BLOCKED／修改）｜模組｜原因｜已核可範圍｜影響項目｜驗收／回復證據｜GitHub commit／PR｜Google Docs 同步狀態。


## 2026-10-24｜設計知識庫跨系統擴充（保留 Notion-only 執行範圍）

為符合專案指示 8,000 字限制，沿用私人 GitHub 本儲存庫，新增 docs/system 與 docs/gas；舊 Notion 專屬 AGENTS 全文保留在 docs/notion/AGENTS.md，根 AGENTS 只做跨系統分流。此次僅整理文件，**沒有改 Notion 資料／Schema／View 或正式 GAS**。青壯方案啟用 TEST 仍嚴格 Notion-only。


## 2026-10-24｜首屏提示最小修正（已實作，非重大 UX 重構）

為降低現有 TEST 首頁將未核實補助額度視為已核准的風險，僅在青壯年度額度標題下新增一個黃色 ⚠️「TEST／尚待核對」提示與既有年度參與表連結；同時說明目前各 Linked View **沒有同步的政府方案／年度／期別選擇器**，不同 Price Plan 實例不可混算。這符合既有「未知視為待核對」「異常優先」設計決策，沒有引入新資料庫、公式或關聯，也沒有改動非青壯舊模組。

已從 Notion 原頁回讀確認新增提醒恰有一個、五個嵌入資料庫及共用導覽均保留。既有 03 待核對22、04全部22、01續用0的查詢結果在修改前後一致。TEST UI 警示**不是核准權限保證**；全面 UX／資料模型改版仍須完成研究及使用者核可。

恢復方法：只刪除新增的黃色 Callout；原來的年度額度標題與其後的治療所用量小標保留。詳細驗收見 acceptance-status.md。

## 2026-10-24｜依使用者要求移除黃色提醒（最新 UI 決策）

- 使用者明確表示「不需要黃色提醒的部分，請移除」，因此先前 2026-10-24 的黃色 ⚠️ TEST Callout 屬**已撤回的歷史實作**，不可當成最新需求。禁止未經使用者同意再次加回該提醒。
- Notion TEST「補助方案管理」已僅移除年度額度標題下的黃色 Callout；重新 Fetch 已確認其文字與黃底區塊不存在，主標題直接接「🏢 ① 治療所年度用量」。側欄共用導覽、5 個嵌入資料庫區塊、三個主要區域、年度個案入口、115 舊版額度對照和備查均保留。
- 現有補助規則、待核對資料及未驗收的公式／關聯仍依原規則保留，這次只是介面取捨，不表示已核准補助使用，也不應以另一種同樣醒目的黃色警示替代。
- Notion TEST 驗收日誌已新增「撤回 TEST 主頁黃色提醒（依使用者最新決定）」；Google Docs 青壯 UX 規格已追加第十三節覆蓋第十二節的現行 UI 決定，並有修改前備份；其他資料庫、Schema、Formula、Relation、View、權限及正式系統未修改。

## 2026-10-24｜政府補助工作台 vNext 一次性改版（已實作，Notion TEST）

依使用者要求，不再小幅加警示，而是一次重整原「補助方案管理｜TEST」主頁：①政府方案與核定期別（通用補助方案篩選）；②個案參與與期限（新增1個 linked database、3個 View）；③心理師週額度（現有青壯115專用並修正缺週回報 Relation 漏列條件）；④額度調整與歷史（原週回報／額度調整／115專用 Cases 與驗收紀錄收合）。保留側欄、原5個資料庫區塊與既有業務資料，不新增黃色提醒。新主頁6個 linked database。

已使用 Notion 原生複製備份舊主頁（https://app.notion.com/p/4038ca66aa4d816480bad8a54db6aeab），讀回新頁及View：方案1、參與22、資格待核22、關聯／期限待補22、在職心理師2、115舊個案22，各無下一頁。Google Docs UX 規格第十四節已追加並另建備份。這是 UI／View 修改，不是通用年度公式、跨方案額度或10,000篇研究已驗收。受影響 View 和回復見 workbench-vnext-2026-10-24.md。



## 2026-10-24｜Notion／資料庫／UX 研究結果系統化保存（文件同步；無新重大設計核准）

依使用者「繼續」要求，把前次未完整保存的設計研究轉成 GitHub [docs/notion/research](research/README.md) 知識庫。首批登錄16個去重 URL，14個取得正文並查核相關段落，2個僅搜到摘要；深度精讀0篇、10,000篇目標未達。綜合 Notion 官方效能／View／Relation／Formula／Free權限、NN/g UX、Microsoft／IBM 正規化文件形成設計研究摘要。

本回合只新增／更新 GitHub 研究及索引文件，**沒有修改 Notion TEST 工作台、Schema、Relation、Formula、View 或正式程式**。研究原則僅提供日後比較與驗收參考；青壯115不可通用硬編碼、其他既有模組只做最小修正、重大重構需使用者批准、不要黃色警示等既有決策維持不變。


## 2026-10-24｜十個既有行政模組完整唯讀稽核（稽核結果，**不是新的重大修改授權**）

依上一輪 GitHub 研究的接續計畫，已完成原十個行政模組的頁面、Linked Database View 與直接資料來源 Schema **唯讀**稽核。合計76個嵌入區塊、177個 View 定義、23個不同資料來源，636欄，其中152 Formula、147 Relation、48 Rollup。發現活動「報名中」篩選反向、進行中活動排除群組過廣、專案／會議區域標籤含未設本週篩選、表格 ALL 命名不精確等問題／風險，分類為 B 類整批改善候選。**沒有修改 Notion 頁面、檢視、業務資料或公式**。後續重大資料庫／權限／UX 改造仍須使用者同意，不恢復黃色警示。

完整頁面盤點、反例、差異、影響與回復方案：[2026-10-24 十模組稽核報告](audits/ten-module-structure-ux-audit-2026-10-24.md)。


## 2026-10-24｜B1～B3 獨立 TEST 預覽與狀態驗證（TEST 預覽／B1 已驗證，尚非正式管理 View 修改）

接續十模組唯讀稽核，新增位於 TEST 行政管理下的「十模組 B1～B3 整批優化預覽」，以任務流程整合所有十模組的導覽提案，並保留所有原始行政頁。另建立四欄、零 Relation、五筆完全合成狀態的獨立 Notion TEST 資料庫：開放報名篩選1筆、進行中開放報名＋已額滿2筆、所有狀態5筆，與預期完全一致。此為**獨立 TEST 邏輯通過**；原 Events「報名中」仍是反向 filter、進行中仍排除 Complete 群組，均未改。B2、B3 僅預覽尚未在原頁落實，正式業務列、Schema、Formula、Relation、權限、GAS 與其他模組均未變更。不恢復黃色提醒。詳見 [TEST 報告](audits/b1-b3-test-preview-2026-10-24.md)。


## 2026-10-24｜B1–B3 行政頁整批 B 級修正與回查｜最新執行決策

接續前次 B1 獨立 TEST 1／2／5 筆 PASS，在 TEST 行政管理的原工作頁一次做有證據的 B 級批次改善：Billing／Events／Staff 以小標區分相近資料庫工作階段；Tasks、Documents 把誤導的 `ALL` 改成精確名稱；Events 因 `CLEAR FILTER` 不會刪除現有 `simpleFilters`，未強行覆寫，而是在原 Linked DB 新增精確活動篩選的2個 View（原簡易篩選0、正確 advancedFilter），原2個錯誤 View 標「停用」保留供回復。五個原頁複本備份完成，原 DB block 數、同步選單、業務資料及權限不變。真實 Events 新 View 查到0筆，尚無業務案例驗收。**更正先前 F-03：會議與專案本來已有獨立 h3/h2 分區，無須修改 Projects 頁。** 具體差異／回復見 [本輪報告](audits/b1-b3-legacy-batch-2026-10-24.md)。

## 2026-10-24｜研究成果完整性核對、TEST 工作台 v2 與長期目標修訂

使用者要求再次確認先前的 Notion／資料庫／UX 學習都有存 GitHub，缺少的補入，並依研究設計實作 Notion 及**修正長期目標**。已重新核對全部六份既有研究文件、16筆去重來源清冊、政府補助多方案架構、10模組稽核、B1～B3驗收與備份記錄；其中確有文件，但缺乏「來源→決策→Notion實作／未驗收」的逐項追溯，故新增 research-to-implementation-matrix.md。歷史「至少1000份模板」與 GitHub 續寫「10,000篇跨範疇研究」互有範圍／數字差異，保留原需求未完成之事實，不冒稱已讀，也不自行把兩者等同。

Notion 中已將「十模組 B1～B3 TEST 預覽」改版為 [TEST 行政任務工作台 v2](https://app.notion.com/p/4038ca66aa4d814297a2dbe27e8d054d)：工作先後、個案會談／帳務／補助、人員營運、驗收歷史四區，兩組左右欄及三個收合區；原獨立活動測試 DB 保留；原十行政頁及其業務資料、Schema／View／Formula／Relation／權限無改動。已建立原生頁備份並 Fetch 驗證。正式使用者工作步數、效能與角色隔離尚未測。長期目標改以**操作效率、正確性、安全、效能、可回復／可追溯**驗收，不以無證據篇數當作上線門檻；詳見 [long-term-goals.md](long-term-goals.md)。


## 2026-10-24｜行政任務工作台 11 情境路徑驗收（非真人驗收核准）
依長期目標 G1 新建 TEST v2 [11項任務驗收子頁](https://app.notion.com/p/4038ca66aa4d81a0834efc417b08fd1b)。工作台11個目標入口與目的頁均可 Fetch；部分關鍵 View 實際篩選已回查（活動進行中 OR、未完成 Done=false、文件待更新＋草稿、收據待審核／處理失敗）。真人0/11，角色、時間及真實業務流程未測；既有行政頁、Schema、Formula、Relation、財務病歷、正式GAS均不改。完整 [路徑稽核](audits/administrative-task-path-acceptance-2026-10-24.md)。


## 2026-10-24｜政府補助 TEST 唯讀隔離與資料完整性
最新唯讀來源顯示：TEST管理分類只在View隱藏一筆紀錄，該列仍連到啟用補助方案及3筆Sessions。一般22筆缺參與會談Relation、期限及他處使用次數；尚不能自動核准或把空白當0。Formula真值未取回、未改原資料。下次須先取得00.config_notion及真正隔離的測試環境，再依核准方案驗收。[詳報](audits/subsidy-readonly-integrity-2026-10-24.md)。


## 青壯人工核對後於服務歷程選方案｜2026-10-24｜使用者已確認並實作 TEST UX
使用者明確決定：青壯資格不複雜，人工核對後在 Care Episodes「💲收費方案」直接選適用 Price Plan，**不另建立資格核對清單、不把補助參與紀錄設為使用前置**。此決策覆蓋歷史「以青壯資格待核對 View 作日常操作入口」的設計，不覆蓋其他政府方案及額度計算規則。已查核既有 Care Episodes→Price Plans Relation；TEST 補助首頁新增服務歷程入口，原參與表收合成歷史備查、資格 View 更名但所有篩選保持原樣。修改前 Notion 已備份，Google Docs 第十五節及 Notion 驗收歷史已同步。**未修改任何原始資料、Schema、Relation、Formula、角色權限、GAS**。詳見 [本輪驗收](audits/youth-manual-eligibility-episode-plan-2026-10-24.md)。


## 2026-10-24｜使用者確認青壯測試資料符合實際使用情境

使用者明確表示「測試資料符合使用狀況」。此為使用者對**現有青壯 TEST 情境與實際工作需要相符**的確認，沿用既定「人工確認資格 → Care Episodes『💲收費方案』選擇對應 Price Plan」操作設計；**不要求重建測試資料或另外建立青壯資格核對清單**。此回覆不等於已由真人完成每個 UI 操作、驗證 Sessions 方案歸屬、Notion 原生 Formula／Rollup 占用、跨政府方案／核定期別及角色權限。沒有 Notion 頁面、Schema、Relation、Formula、真實資料或 GAS 寫入。詳見 [原 TEST 變更及本次確認](audits/youth-manual-eligibility-episode-plan-2026-10-24.md)。


## 2026-10-24｜服務歷程與會談方案對照：唯讀驗證｜僅實證紀錄，無核心模型變更授權
承接使用者確認青壯 TEST 資料符合實際使用及「人工確認→服務歷程💲收費方案」流程，進行唯讀關聯回歸測試。Care Episodes 57筆、Sessions 295筆皆有歷程關聯且雙向完整；287筆主方案與歷程相同，另8筆不同（雙方向各4），不能不經確認直接改掉。啟用青壯方案所連41筆 Sessions 與 Sessions 直接 Price Plan Relation 完全一致，狀態23完成、13預約、2取消、2改期、1 no-show。這些事實證明當次**關聯結構**，但實際 Formula/rollup 返回指標而非數值，原生計次/剩餘額度未驗收。無Notion業務列或Schema變更，保留未來需核准的C級改動界線。[唯讀報告](audits/episode-session-plan-consistency-2026-10-24.md)。

## 2026-10-24｜青壯／自費 8 筆方案差異之情境分類回查｜保留個別會談方案差異，不擅自認定錯誤
在使用者先前確認「測試資料符合使用狀況」前提下，進一步做即時Notion唯讀分類：8筆不同主方案的Sessions實際集中4筆服務歷程，且只有青壯政府方案與另一個已啟用的自費個別方案互換；方向各4筆，各有一組已預約／完成／改期3筆及另1筆已完成。這可能是在驗收個別會談採不同收費方案的場景，但意圖尚未有逐筆業務證據。**決議仍為不修改任何Session或Episode主方案，也不建立新審核清單**；僅整理待核對的Episode預設方案與Session單次方案有效性規則，避免把已有測試組合當成錯誤批次修正。原生Formula/rollup值尚未可讀，無額度驗收宣稱。Notion驗收歷史已追加並回查；詳見[驗證報告](audits/episode-session-plan-consistency-2026-10-24.md)。


## 2026-10-24｜政府補助計數 Rollup 直接相依驗證｜數值未取得，維持原業務決策
已唯讀核實 Price Plans 三個計數 Rollup 使用 Price Plans ↔ Sessions Relation，直接加總 Sessions 已完成、已預約、待確認計數 Formula；Care Episodes 本歷程計數另外沿 Episode ↔ Sessions Relation 加總相同來源 Formula。因計數 Formula 定義與原生值無法從目前 Notion 連接器取回，**此依賴證據不是「以單次 Session Price Plan 為唯一計次權威」的核准，也不是政府額度已正確的驗收**。保留使用者的青壯人工確認→服務歷程選方案、符合使用情境的TEST資料，以及先前8筆青壯／自費切換差異；任何自動同步與共用 Formula 修改仍不授權。本輪只追加 Notion TEST 驗收文字及 GitHub 文件；詳見[結構與限制](audits/episode-session-plan-consistency-2026-10-24.md)。



## 2026-10-24｜原生公式數值驗收：替代唯讀入口與重試門檻｜取得原生數值前停止推論與寫入
這一回合額外核實已啟用方案的原生 Notion 頁和 Saved View 仍只回傳 Formula/Rollup 結果參照；`rows/SQL` 暫時配額耗盡但可在一段時間後重置，不是永久不支援。Google Drive 中的歷史 Sessions 收據公式文件不可冒充當前補助計數公式。決策不變：青壯人工核對後於 Care Episodes 選主方案，現有8筆青壯／自費切換不自動同化；沒有可信原生數值前，不判定 Session 計數或 Price Plan 餘額正確，不操作既有業務資料或共享公式。已為配額恢復後整理 [最小數值驗收協定](audits/episode-session-plan-consistency-2026-10-24.md)，待實際讀值才能進行下一步。此次僅 GitHub 記錄，無 Notion 寫入。


## 2026-10-24｜青壯額度原生數值續作前置核對（唯讀／非新決策）
- 本輪依上次驗收停點只重驗 Price Plans／Sessions／Care Episodes Schema、Notion TEST 工作台與政府方案 View；三個 Price Plans 計數 Rollup 來源保持不變、工作台6個 linked database 與撤回黃色提醒的決策保持不變，現有啟用政府方案 View 僅1筆。
- Price Plans「已占用_自動」「剩餘額度_自動」仍沒有原生數值，而是不可直接驗證的 `formulaResult://` 指標；計數 Rollup 也是指標。原生計數、8筆青壯／自費方案差異的計數影響、跨期／跨方案、真人權限及效能仍**未通過**。本輪沒有重新跑完整295筆會談對照，也沒有用狀態筆數冒充公式驗收。
- **未形成新業務決策**，既有青壯人工核對→Care Episodes 先選方案與不得自動同化8筆差異的原則不變。沒有改 Notion Schema／資料／View、Google Docs 或正式服務；僅將這次前置回查記入 GitHub，詳見 [驗收紀錄](acceptance-status.md)。

## 2026-10-24｜青壯方案測試續作：完整會談回歸（未新增業務決策）
- 本輪再次完整核實現行57筆 Care Episodes、295筆 Sessions、啟用政府方案1筆之既存 View，與原生 Price Plans↔Sessions 41/41 完整雙向關聯；287筆主方案一致、8筆差異仍待業務確認，分布4個歷程。只更新匿名測試證據，未新增「一律以歷程／單次會談計次」決策。
- Notion SQL/rows 共用配額仍用盡，Formula／Rollup 值只有參照，原生額度與跨期仍 BLOCKED；不可將狀態筆數當成扣額結果。保留原人工核對→Care Episodes選方案流程與禁止自行同化8筆差異。
- 所有 Notion 資料、Schema、View、角色權限、Google Docs、正式 GAS／Cloud Run／Session／部署保持不變；本回合只同步 GitHub 驗收與稽核文件。詳見 [驗收狀態](acceptance-status.md) 與 [技術稽核](audits/episode-session-plan-consistency-2026-10-24.md)。

## 2026-10-24｜配額恢復後額度數值讀取仍受阻（唯讀驗收，非新業務核准）
- Notion `query_data_sources(mode=rows)` 已恢復可讀，證實前輪 SQL/rows 配額阻擋非永久；惟原生 Price Plans 已占用與剩餘欄位依然僅返回 `formulaResult://`、計數 Rollup 為 `rollupResult://`，本輪 Formula 精確數值篩選尚無符合連接器參數 schema 的有效呼叫。現有政府方案 Saved View 回傳1筆已啟用政府方案，並非公式驗收。
- 這是**讀取能力與驗收阻礙更新**，未形成新的方案計次／資格業務決策。既有人工確認→Care Episodes 選 Price Plan、8筆主方案差異保留、禁止錯誤宣稱額度已驗收，均不變。未修改 Notion／Google Docs／正式程式；詳見 [當次稽核](audits/episode-session-plan-consistency-2026-10-24.md) 和 [狀態](acceptance-status.md)。

## 2026-10-24｜115青壯官方規則文字差異：記錄待修，尚非方案或公式修改決策
- 本輪官方來源與原始 Notion Price Plan 備註唯讀比對，核實四項需澄清的文字差異：最短間隔 `>7天` vs 官方不小於7天；官方原則上最長1個月未註明；外籍持健保卡資格未列；連續2次無故未到「必然取消」與官方「機構得拒絕服務」不同。來源與影響詳見[匿名比對稽核](audits/episode-session-plan-consistency-2026-10-24.md)。
- **此為驗收風險登錄，不是新業務核可或確認程式錯誤。** 115年當期規則不可外推跨期；先確認地方契約與原生Formula，再提出最小文字修正及驗收，不能擅改啟用方案或既有8筆異方案Session。原青壯人工確認資格→Care Episodes選Price Plan、不新增資格清單的使用者決策持續有效。數值驗收仍BLOCKED；本輪無Notion/Google Docs/正式服務寫入。

## 2026-10-24｜青壯115地方適用範圍核對（非新業務變更授權）
- 本輪確認汐予心理治療所屬桃園八德且列桃園市115年青壯官方合作機構公開清單。後續本115期別應按衛福部＋桃園衛生局＋本機構適用合作契約；先前臺北衛生局公告是參考對照，尤其兩次無故未到的具體處置，不得未查桃園契約就視為最終規則。
- 已核實中央公告的外籍持健保卡適用資格，桃園115年計畫書附件可定位但未能完整檢閱，已連接Drive亦無可核實的汐予115年已簽契約。7天／1個月及no-show差異記為待查候選；未核准啟用方案備註或共用Formula修改。
- 原使用者決策「青壯人工確認→Care Episodes選Price Plan」、保留8筆差異、各年度方案實例分期隔離、不得將歷史會談筆數當額度值均保持不變。Notion公式數值仍BLOCKED；本輪只增補GitHub文件，詳見[稽核](audits/episode-session-plan-consistency-2026-10-24.md)。

## 2026-10-24｜確認中央115連續缺席規範為得拒絕：地方契約及最小修正仍待核
- 新搜尋取得桃園公部門刊載衛福部115年中央計畫條文片段，連續2次無故未到時**合作機構得拒絕提供服務**，並有中央115 FAQ交叉印證，不再僅依據臺北市公告推論；同時FAQ可核最短7天、最長1個月的原則。
- 這是**官方來源驗證結果，不是新增啟用業務或修改規則的核可**。汐予實際適用的115年合作契約未能回查全文，Notion啟用中的 Price Plan「備註」仍是舊文字；先維持唯讀、等待完整地方補充再做單欄位備註最小修正。共用Formula、Relation、方案計數和8筆既有差異仍不自動變更。原生占用／剩餘額度繼續BLOCKED，詳見[完整稽核](audits/episode-session-plan-consistency-2026-10-24.md)與[驗收](acceptance-status.md)。

## 2026-10-24｜青壯115通訊方式與同意流程：核實風險但不新增Notion前置欄位
- 桃園市衛生局當次可搜尋的115合作機構名冊列有汐予，且「通訊心理諮商核准」欄為否；另有民眾自付掛號費的公告資訊。此為官方清單唯讀證據，不能當成永久/跨計畫的授權狀態，亦未因此修改系統可用服務方式。
- 桃園政府託管中央115方案同意書的可搜尋片段和中央官方FAQ，已能核對跨機構累計3次及無故缺席時「合作機構得拒絕」文字。**不新增另一本青壯資格核對清單或參與記錄**；使用者已確認的「人工確認後於Care Episodes選方案」仍有效。政府要求的同意與查核程序為既有營運義務，不意味其已在系統中完成驗收。
- 沒有本輪新業務變更授權；115方案備註B級最小修正仍待當期汐予適用契約核對及使用者同意，共用Formula/Relation或權限改動均未授權；額度原生值NUMERIC BLOCKED。詳見[新增驗收證據](audits/episode-session-plan-consistency-2026-10-24.md)。

## 2026-10-24｜中央115年每週六次跨地核銷上限：唯讀規則核實，未核准改公式
- 依衛福部115年3月25日函（1151760792號），青壯115週次為週日至週六，心理師跨執業登記／報備支援地點合計每週6人次，中央平台自2026/04/12以每週6筆限制核銷。此是**新取得的當期官方依據，而非使用者核准的系統設計變更**，不得套到其他政府方案／年度。
- 實際Notion TEST週回報6/6週日起始；其中連啟用115 Price Plan及2名在職心理師的4筆雙向關聯完整，**本週2筆他處使用都未知且尚未確認**，只能保持待核對。Staff公式與真正跨地服務數值仍無法讀取；**不能聲稱週額度已正確或可用**。
- 使用者已核准的人工資格確認→Care Episodes選方案流程，以及8筆不同收費方案會談都不改；沒有新增資格清單、沒有資料／Formula／Relation寫入。完整來源、風險、驗收和回復見[專項稽核](audits/youth-weekly-allowance-2026-10-24.md)。

## 2026-10-24｜青壯本週已預約6／4與他處未知：驗收事實非自動修正授權
- 本輪重新分頁核實Notion Sessions295筆、啟用青壯方案Relation41筆；在115/10/18～10/24在職兩位心理師本所**已預約**各6及4筆；對應週回報他處使用仍未確認／數字未知。中央115年限制是跨地服務每週合計6人次，因此**院內已預約6不等於已核銷6，但絕不能拿本所未超六筆推論可增加安排或核銷資格已確認**。
- 青壯41筆中的3筆缺心理師／形式同時是已取消、已改期、no-show的TEST紀錄，不屬本週已預約候選，且有服務歷程及日期；暫無證據需批次補值或刪除。Staff/週回報Formula Code入口不支援讀取，原生計算與fail-closed仍待驗收。
- 此為**唯讀測試結果及風險登錄，不是更改業務規則的使用者核准**；不操作既有TEST與啟用Price Plan、Formula、Relation、Session、Staff或補助週回報，不新增強制青壯資格清單、不改既有8筆不同方案會談。下一個實證關卡為真人確認本週他處已使用及政府核銷，再與Notion原生顯示值比對。[週額度匿名稽核](audits/youth-weekly-allowance-2026-10-24.md)。

## 2026-10-24｜週回報View一致與未確認須待核：僅驗收證據，非新公式核准
- 已用Notion既有Saved View核實補助週回報的原始資料庫與TEST工作台內嵌檢視各6筆、紀錄集合完全一致；「心理師＋方案實例＋週起始日」無重複。已啟用青壯方案及2位在職心理師所屬4筆關聯，與另2筆不同方案／TEST人員可區分，但**TEST名稱不是資料隔離**。
- 本週10/18～10/24兩位他處使用均未知，應保持**待核對／不可直接宣稱可用**。公式計數本身未驗收：普通Notion rows篩選成功、Formula篩選不支援所試語法，工作區SQL/rows配額亦暫時用盡；以View可回查資料，但不能讀Formula數值。此為資料與工具狀態的驗收紀錄，不是使用者對共享公式修改的許可。
- 沒有更動Notion任何資料、Formula、Relation、View、權限、Google Docs或正式系統；保留青壯人工資格核對→Care Episodes選方案與既有8筆不同方案會談。完整證據見[週額度稽核](audits/youth-weekly-allowance-2026-10-24.md)。

## 2026-10-24｜恢復2026-10-23 v2隔離PASS、釐清現行View已無舊週回報門檻
- Google Drive原始23章設計備份第八節已記載**2026/10/23隔離測試中Staff v2公式的超額、已滿、缺失／重複回報待核及週日切週曾PASS**；這是補回遺漏的既有驗收歷史，**非新業務決策、非本輪重新執行、非本週實際人員原生數值驗收**。
- 該備份第九節記載的舊版主視圖「無週回報Relation的合格人員可能被隱藏」門檻，在本輪重新Fetch最新Staff週額度View後已不存在；目前View按在職與臨床心理師篩選（排除指定TEST），而且與Staff主表4筆唯讀交叉比對，2名在職臨床心理師2／2均列、無多列。未來新增心理師及未建立週回報時的公式輸出仍待TEST。
- 不更動已確認人工資格核對→Care Episodes選方案、保留8筆不同方案Session，不修改共享Formula/Relation、Staff、週回報、Notion View、Google Docs或正式程式；原生即時結果及跨機構政府核銷**仍未驗收**。[證據與限制](audits/youth-weekly-allowance-2026-10-24.md)。

## 2026-10-24｜115青壯週日換週缺回報：以未知處理，不預填0
- 這是**依既有規則產生的新時間邊界驗收紀錄，非新增設計或寫入授權**：新週2026/10/25～10/31（週日至週六）在2026/10/24唯讀時，啟用115青壯方案及當前兩位在職臨床心理師**0筆對應週回報**、全部295筆Sessions中的當週青壯會談**0筆**。其他方案TEST的10/25回報不屬兩位工作心理師。
- 新週無確認外部使用紀錄**不等於已確認他處0**，也不得帶入10/11／10/18的歷史回報。預期Staff v2欄位應呈「待回報／待核對」，但目前連接器只能見Formula參照，**未完成10/25原生UI驗收**。不為測試新增本所預約、週回報或黃色警示，不擅改公式。詳情：[週額度唯讀專項稽核](audits/youth-weekly-allowance-2026-10-24.md)。

## 2026-10-24｜115青壯備註文字：官方來源與匯出PDF釐清，未核准變更
- 複核[衛福部115年公告](https://www.mohw.gov.tw/cp-16-85046-1.html)與[政府115方案FAQ](https://www.gov.tw/News_Content_26_826198)，活躍青壯115 Price Plan「備註」現有四處差異：僅列國民、以「>7天」取代至少7天、未提間隔原則上最多1個月、連續2次無故未到誤稱自動取消資格。
- 同名Google Drive PDF經讀取確認是**Notion既有Price Plan匯出**，不能證明備註正確；跨三個連結Drive與Notion、可用郵件搜尋均未取得汐予115年個別合作契約及附款。應以中央官方規則及機構實際適用條款分層驗證，不以其他縣市契約替代。
- **沒有新增使用者核准決策**。本輪只完成單欄「備註」的前後差異與回復方案，維持既有人工核對後於Care Episodes選方案，不增加資格清單、黃色提醒或修改公式、Relation和正式服務。待契約及同意後才准寫入；見[方案稽核](audits/episode-session-plan-consistency-2026-10-24.md)。

## 2026-10-24｜青壯115備註修正候選全文已備妥，非使用者核准
- 本輪僅從最新Notion活躍Price Plan備註全文產生3處最小替換候選（涵蓋四項中央規則差異），並完成反向還原原文的無損測試。全文、官方來源與單欄回復方式收錄於[方案稽核](audits/episode-session-plan-consistency-2026-10-24.md)。
- **未有修改啟用Notion方案的使用者核准**，汐予115年個別合作契約仍未取得。故未更動Notion資料、Schema、Formula、Relation、View與權限，也未建立新的青壯額外審批／參與流程。當次只同步設計候選及驗收分類，不代表新業務規則已實施。

## 2026-10-24｜中央新版FAQ與地方契約No-show差異：暫緩青壯備註定稿
- **非新核可決策，為新增正式證據與未解衝突**：已回查[衛福部115-05-13完整版FAQ](https://www.mohw.gov.tw/dl-100808-d77b3248-bcdb-4d2a-bc81-40b589438ca7.html)，中央No-show Q9為「連續2次無故未到，合作機構得拒絕服務」；[新北市115青壯合約官方公告](https://www.health.ntpc.gov.tw/article/%E3%80%8C15%EF%BC%8D45%E6%AD%B2%E9%9D%92%E5%A3%AF%E4%B8%96%E4%BB%A3%E5%BF%83%E7%90%86%E5%81%A5%E5%BA%B7%E6%94%AF%E6%8C%81%E6%96%B9%E6%A1%88%E3%80%8D%E7%9B%B8%E9%97%9C%E8%B3%87%E8%A8%8A2026032416)之合約PDF公開索引另載90日暫停補助。後者未完成PDF逐頁閱讀，**不適用以其取代桃園／汐予契約**。桃園中央計畫索引載地方不得訂較嚴格限制，尚須法定主管機關或適用文件確認如何協調。不能以先前3處無損替換的測試成功，當成啟用方案已核准可改。
- 衛福部新版FAQ並規範**既有行政規費及提前告知、不可補收諮商費差額、同次服務不可重複中央地方核銷**。汐予實際行政規費種類／事前告知尚未查核，因此不擅改「掛號費、場地費」也不宣稱原收費合規或違規。
- 同份FAQ系統篇Q13說明政府平台的**服務紀錄暫存可供其他機構計算個案使用次數**；這支持現有人工核對→Care Episodes選方案（仍禁止另設青壯資格清單），但資料未上傳／未確認不等於0，且個案跨機構3次不取代心理師跨地本週6次。
- 本回合Notion全資料／Formula／Relation／View／分享權限、Google Docs、正式GAS／Cloud Run／Session／部署皆不變；只在GitHub記錄證據分級與暫緩狀態。[備註稽核](audits/episode-session-plan-consistency-2026-10-24.md)、[週額度稽核](audits/youth-weekly-allowance-2026-10-24.md)。

## 2026-10-24｜官方汐予青壯費用項目比對：備註修正候選更精確、未實施
- 桃園115青壯合作機構[官方名冊的當日搜尋索引](https://mental.tycg.gov.tw/cp.aspx?n=19932)顯示汐予「掛號費400元」、通訊核准否；同URL較舊直接開啟快照未列汐予，**來源時間差需保留為待即時確認**，不可直接聲稱機構即時簽約資格驗證通過。
- 對照現行已啟用Price Plan，其備註泛稱「掛號費、場地費等行政費用」，未寫明官方可見的400元掛號費；Page/Schema無「掛號費」獨立欄位、`應付_自動`原生值不可讀。**不由資料屬性不在等同於公式錯誤**，也不將官網公開價當作Notion真正應付公式驗收。中央FAQ要求原有合法規費及事前告知，不能自動另加場地費。
- 這是**新驗證依據／備註候選收斂**，**不是使用者新核准**。汐予個別合作契約及缺席處置仍需確認；未修改啟用Price Plan備註、Fee Formula、Staff、Sessions、Care Episodes、其他Notion資料／Schema／View／分享權限或正式服務。[稽核與回復](audits/episode-session-plan-consistency-2026-10-24.md)。

## 2026-10-24｜重新找到原有掛號費Price Plan與補助分帳紀錄：避免誤設計新增費用欄
- **新發現是現況，不是新核准需求**：原Price Plans中已存在並啟用**400元「掛號費」自費方案實例**；Sessions的`💲 附加收費方案`可加掛，Billing已分別記載向個案的掛號費（22筆，各400並標已收款）及向衛生局的本期青壯請款（23筆，待請款9／請款中14）。完整Sessions295/Billing203關聯驗證，所有45筆本類Billing都回指相應已完成青壯Session，22筆掛號費又符合Session附加方案。不得因青壯主方案本身沒有掛號費欄位就新增欄位或逕加400到1600補助額。
- **一筆已完成青壯Session沒有附加掛號費／對應掛號費Billing**，另一筆已預約亦無附加，尚無合理減免或漏收證據；**不自行開收據或補帳**。Price Plans、Sessions與Billing的Formula原生數值、按鈕、政府撥款及真人權限未實測，維持BLOCKED。[詳細讀回及恢復界線](audits/episode-session-plan-consistency-2026-10-24.md)。
- 原使用者核可青壯人工確認後於Care Episodes選方案、原8筆跨方案不同會談保留；本回合只在GitHub修正現況記錄，不改Notion Price Plans的備註草案或當前值，不改任何Finance/Schema/Formula/Relation/View或正式系統。

## 2026-10-24｜使用者重申優先任務「建立額度 View」，已在 Notion TEST 執行
- 使用者指出原本要求是建立**補助使用額度 View**，先前多回合追查收款屬於偏離主要任務。本回合依其既有要求直接作B級 View 最小建置，不再進行無關 Billing 分析，亦不需要等待掛號費契約問題才建立只讀檢視。
- [補助方案使用額度 View 02](https://www.notion.so/3f68ca66aa4d8156bccfcc28f75cbb9a?v=4038ca66aa4d81278430000cd581b5e7)顯示原Price Plans的核定、已完成、已預約、待確認、已占用、剩餘、狀態，不覆蓋舊View01；[個案使用額度 View](https://www.notion.so/3f68ca66aa4d81cca3b4ee43b4bd8dcf?v=4038ca66aa4d81a3ab1a000ca3244dce)在本TEST工作台頁尾，現預選青壯115方案，以 Care Episodes單段歷程為資料列；心理師週額度沿用原115專用View。兩個新View查詢分別1／22筆且無後頁，新增1行主區快速入口。原核心資料、公式、關聯、View01、Staff／權限不動。
- 這是**已發生的TEST最小UI/View修改**而非使用者核准「重構共享公式或所有舊模組」。原生額度數值、個案跨歷程累計、跨政府方案期別、權限／效能和真人UX仍未通過，未知不得當作0或可安排。同步原[Google Docs跨年 UX 規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)第十六節及[可回復的實施報告](audits/subsidy-usage-views-2026-10-24.md)。

## 2026-10-24｜使用者確認青壯單一Care Episode與逾核定期結案，覆蓋先前跨歷程設計假設

**[使用者明確核准的青壯業務規則]** 本所同一個案的青壯服務全部在**一次服務歷程 Care Episode**完成；超過衛生局核定時間便依行政程序**結案**，治療所**不會再接同一個案的另一筆青壯服務歷程**。因此取消正常青壯須跨Care Episodes彙總使用次數的設計需求；以單一歷程呈現已完成、預約、剩餘等額度即可。**只適用青壯**，其他政府方案及年度/核定期別仍按自身規則，不硬改共用資料模型。

**[與前一決策差異]** 舊「補助到期但歷程進行中保留顯示且不可自動結案」作為**未經確認不得自動改資料或藏資料**的安全原則仍適用；此次更明確的是青壯**行政上應結案且不再開第二筆青壯歷程**，而不是授權AI或公式自動批次改成結案。逾期未結的紀錄仍要可見供行政處理。後續如需自動化關案，須獨立規格、測試、授權及回復方案，不從本句推導。

**[Notion TEST實際修改]** 原[個案額度View](https://www.notion.so/3f68ca66aa4d81cca3b4ee43b4bd8dcf?v=4038ca66aa4d81a3ab1a000ca3244dce)已更名青壯115單一歷程額度、把可切換其他方案的Quick Filter改為固定青壯115 Price Plan Relation FILTER、新顯示開案與結案日期；查詢22筆且全部屬115期。TEST工作台②相應更新入口及一段青壯結案說明。22筆中1個個案關聯2筆青壯歷程，兩筆都帶**測試標記**；僅為已有資料例外待核，未擅自修復。其餘來源、Formula、Relation、業務列與正式系統未更動。Google Docs跨年UX規格追加第十七節，本回合後讀回確認。[詳細驗收](audits/subsidy-usage-views-2026-10-24.md)。

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
- **[UX LINK STRUCTURE PASS / PERFORMANCE PENDING]** 原工作台及個案與歷程入口可Fetch；青壯人工資格核對→Care Episodes選Price Plan→方案、個案、心理師額度Views的連結存在，沒有回復已撤回黃色警示。此為路徑結構驗證，不是使用者實際點擊、任務時間、操作步數或Notion網頁載入速度測量；連接器往返時間不等於前端效能。人工畫面額度數值的 USER CONFIRMED PASS 保留。
- **[SAFE STOP / SCOPE]** 不建立第二個政府補助／年度方案、不改已啟用青壯Price Plan、Sessions、Episodes、Staff、週回報及其 Schema／Formula／Relation／View／權限；不改正式GAS／Cloud Run／Session。精確`00.config_notion`仍未定位，TEST字首不保證與啟用資料隔離；新增核心結構與真正隔離多方案端到端驗收須先提供前後比較並取得明確核可。此回合僅更新版本化驗收／規格，保留可回復性。
- **[GOOGLE DOCS VERIFIED]** [跨年度額度模型與UX規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit) 已用 revision guard 追加第十九節，修改後原第十八節與第十九節均回讀存在；[修改前備份](https://docs.google.com/document/d/1X0X71wtOR0Nw3RD-DdrGvVOxR9BfbhjiB4W0m1BTiew/edit) 回查未含第十九節。可保留並行修改後精準撤銷新增段落；本輪無Notion業務資料需回復。

## 2026-10-24｜他處無接案心理師免每週回報：已確認需求與待核可設計
- **[USER-APPROVED OPERATIONAL REQUIREMENT]** 使用者明確要求：**確定沒有在其他地方接案的心理師，不需每週確認他處使用次數**。這取代「所有在職心理師無當週回報一律待回報」的過度一體化操作要求；不意味未確認者皆可視為0，亦未核可現在直接重寫公式或批量套用現有員工。
- **[LIVE SCHEMA READ / CAUSE]** 重新讀Staff 55欄、心理師補助週額度19欄、Price Plans 30欄及在職心理師週額度View；Staff現有「執業類型」Select只有「本所執業／支援報備／不適用」，不能推導出該心理師是否在本所以外接案、是否在他處參與青壯。Staff既有`青壯本週他處顯示_自動`及`青壯本週額度狀態_v2_自動`是共享Formula，原碼僅`formulaCode://`參照未可驗證；現有週回報的`他處回報已確認`＋`他處已占用`仍是每週資料來源。
- **[PROPOSED MINIMAL DESIGN / NOT YET APPROVED]** 初期以Staff增加3個小欄位為候選：「他處接案情形」Select＝未確認／已確認無他處接案／有或可能有他處接案；「確認日期」Date；「免週回報有效至」Date（經確認且不可自動跨核定期別承接）。絕不直接借用`執業類型=本所執業`作免週報。已有外部接案者維持原週回報；確認全無外部接案者在聲明有效期間不須新建每週0次資料，使用本所Sessions計數並由週額度公式將「本所外」視為已確認0；其他未知、逾期、相矛盾、有外部案件而未回報時fail-closed。
- **[SCHEME SAFETY]** Staff「在其他地方完全沒有接案」是跨方案皆成立的更嚴格事實聲明，不把特定青壯115數值、週6次或自然年底寫死到共用欄位。若將來要讓「其他場所有自費案件、但本期不提供指定政府方案」的人也免週回報，須另以Staff＋Price Plan實例ID管理本期聲明，不能僅憑Staff單一全域旗標替不同方案推定0；本次不新增資料庫或專年旗標。
- **[COMPARISON / ROLLBACK / SCOPE]** 現況每週所有人員皆可能被當成缺他處回報；建議改成僅已核實無外部接案者免週報，減少重複記錄與人工確認。風險是人員變更未申報或聲明逾期、原Formula依賴不明；須先備份Staff Schema及涉及的Formula/View／原值、驗證再最小修改，失敗時精準恢復3欄所涉設定／公式舊版本，保留並行改動及業務列。此輪**純設計＋唯讀核對，未寫Notion或Google Docs、未改正式系統**；因涉及新增Staff欄位及共用Formula，分級C，**尚待使用者對候選實作明確核准**。

## 2026-10-24｜使用者核准免週回報三欄位：Notion TEST已建立，公式整合硬停止
- **[USER APPROVAL]** 使用者回覆「同意繼續」，明確核准前一回合之三欄位方案：確實沒有在其他地點接案的心理師免每週重複確認；他處接案／可能有接案者按週回報。這是設計與最小實作核准，**不是**授權猜測現行共享公式、替現有心理師批次填零或覆蓋相關業務紀錄。
- **[NOTION STAFF SCHEMA WRITE / READBACK PASS]** 經重新 Fetch，TEST Backend 的既有 Staff Data Source 原有55個欄位、無目標3欄；以一筆明確DDL新增 `他處接案情形` Select（未確認／已確認無他處接案／有或可能有他處接案）、`他處接案確認日` Date、`免週回報有效至` Date。寫後重新 Fetch 為 **58欄**，三欄型別／選項吻合；現有在職心理師週額度 Saved View仍 **2筆、has_more=false**，新欄對該兩筆皆留空，**未設定任何人的免回報資格**。
- **[OLD VIEW/FORMULAS UNCHANGED]** 既有 Staff `青壯本週他處顯示_自動`、`青壯本週額度狀態_v2_自動`之Formula codeUrl與寫前相同，原心理師週額度View名稱、五個顯示欄完全一致。未修改Staff現存任何人員資料、週回報、Price Plans、Care Episodes、Sessions、Billing、其他Data Source Schema、Relation、Role、GAS或部署；暫無新增重算公式的運算負荷。
- **[FORMULA HARD STOP / FEATURE NOT LIVE]** 當前Notion Fetch仍只見Formula `formulaCode://`參照，直接Fetch參照回 `validation_error`，尚無全部現行公式**完整原文**、依賴、可驗證基準與隔離TEST；按專案硬停止規則**沒有更動共享公式**。因此目前「免週回報自動判斷」**尚未實際啟用**；人員填選「已確認無他處接案」也不會自動使本週額度放行，原有缺回報待核對規則仍適用。下一步需找出目前完整公式及對應回復基準，隔離測試再做最小公式整合，不能假稱全部完成。
- **[BACKUP / ROLLBACK]** 寫入前已確認三欄皆不存在、原Staff55欄、原View五顯示欄及兩個既有Formula codeUrl。需回復時先重讀最新Schema、先確認無任何人已使用新欄和無並行修改，再僅移除這次新增的三欄（現均空白）；不得移除其他Staff欄位或覆蓋原Formula／Role／業務列。`00.config_notion`精確原件仍未定位，這次使用當次直接Fetch的實際Data Source而非GitHub舊ID。
- **[GOOGLE DOCS VERIFIED]** [現用跨年額度UX規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit) 以revision guard追加第二十節，已重新讀回，第十九及二十節均存在，明確保留公式未啟用狀態；[修改前備份](https://docs.google.com/document/d/1XlRg7xVs1dV8Apey5V0EJLhHv2w-ikPP-c-bEZnETek/edit)重讀無第二十節。撤回時精準移除新增節，保留其他並行修改。

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
- **[BACKUP/ROLLBACK]** 已在編輯前原生Duplicate v3頁面並Fetch確認保有三張舊Linked DB與原卡片；備份 https://app.notion.com/p/4038ca66aa4d811eafe0c857a6394638 。原官方TEST工作台 https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf 未觸碰。僅v3預覽頁與其專用View顯示欄變動、新增一張同源Care Episodes Linked View；要回復先核對並行變更，以備份精準還原預覽頁與v3既有SHOW欄位，移除第四Linked View但不刪除原Care Episodes資料庫。
- **[MANUAL RETEST GATE]** 請真人逐題驗證：①開頁是否立即看到「治療所本期額度」表，不點跳頁；②下捲是否直接看到心理師與個案兩表；③「服務歷程」表是否直接顯示「💲收費方案」並知道可在原頁操作（**勿更動真資料**）；④整頁是否少文字、容易閱讀。各題A符合／B不符合／C未測。使用者尚未回覆，不得將v4寫作UX PASS或直接覆蓋原工作台。
- **[DOCS VERIFIED]** [現行Google Docs規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)新增第二十三節；讀回確認22/23並存，明示五題FAIL與v4。修改前原生Google Docs[備份](https://docs.google.com/document/d/1SKgodaTjbxWatRZB-nrQz0IyxptQ1Dh7__8jecQpmrU/edit)已讀回確認無第23節。

## 2026-10-24｜UX v4使用者4/4 PASS；新增首頁異常與最後一次候選提醒（TEST待驗）
- **[USER CONFIRMED / V4 PASS]** 使用者對既有UX v4四題回覆`1A 2A 3A 4A`（4/4真人操作PASS）；不重測或改寫為其他結果。同一回覆新增三項需求：①質疑在首頁展開38筆「服務歷程｜直接選收費方案」的必要性，②警示異常清單及下一次為最後一次提醒應在首頁直接看到，③需解釋當前資料庫設計。**這是後續新驗收項目，不得把舊4A當新增警示通過**。
- **[UX V4 REFINEMENT / ACTUAL WRITE]** 原獨立TEST預覽https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f 已以原生Notion View與內容最小修改：頁面頂部先呈現`⚠️ 青壯｜待核對資料`、`⏳ 青壯｜最後一次補助候選（剩餘1次）`兩張真正的inline Linked Views，下方保留既有三張治療所／心理師／個案額度Table，最後原38筆廣義Care Episodes「直接選收費方案」改為 `設定收費方案（非每日額度）` Toggle，不再佔首頁每日判讀；另有最末`資料來源與使用範圍`短Toggle。寫後 Fetch確認**六個**inline Linked Database blocks、正確標題順序、底部兩個Toggle，未恢復舊的黃色資格核對警示。
- **[ANOMALY VIEW / VERIFIED SCOPE]** 新建`view://4038ca66-aa4d-81b5-a7fa-000cd34b7bdb`，來源Care Episodes真實現有Data Source；Filter為當前**青壯115 Price Plan實例Relation**、進行中、（開案日期空白 **OR** 他處使用已確認未勾）。Saved View查得**2筆**，兩筆皆開案日空白，其中一筆同時他處未確認，**不是三筆**。此View僅代表列出的兩類可驗證待核對，不代表涵蓋所有數值超額、期別逾期、Sessions方案衝突等異常。
- **[FINAL-USE ALERT / CANDIDATE NOT CONFIRMED]** 新建`view://4038ca66-aa4d-81e3-bfbd-000cfc0ac598`，Care Episodes Filter為當前青壯115 Price Plan實例Relation＋進行中＋既有`個案補助剩餘_自動` Formula在Notion Saved View中精確顯示文字`1`。回查**11筆**，SHOW已完成、已預約、剩餘額度及個案狀態。這表示**剩餘1次的候選**，不能保證下個已預約療程就是補助最後一次；需驗證預約、他處已用／未知、方案特定期別及公式完整expression後才可提高精度。無自行修改公式、標記完成或結案。
- **[BACKUP / IMPACT / ROLLBACK]** 修改前原生Duplicate v4（4張Linked Views）並Fetch核對：https://app.notion.com/p/4038ca66aa4d8159b4e5daf90a4ae662；兩個新Views加上、重排前另Duplicate 6張DB備份：https://app.notion.com/p/4038ca66aa4d819482bbd663a0e4fe4d。曾出現Notion移動Toggle位置不符合預期，已以安全次序重排及局部更新，重Fetch證明位置正確。要回復先讀當前頁與並行變更、精準保留原業務Linked DB並移除兩張新警示；原業務資料表、原營運Views、原共用Schema／Formula／Relations／會談、Price Plans、Staff、週回報列、權限、GAS／Cloud Run全不變。
- **[DOCS VERIFIED]** [Google Docs青壯跨期UX規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)已新增第24節，回查第23／24節共存與4A＋新需求；[增補前備份](https://docs.google.com/document/d/1kEm7zDMddObchiJfritf9b21TaIJPDsa7i8_uEYlgf4/edit)重讀無第24節。

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
