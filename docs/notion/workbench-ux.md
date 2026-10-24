# Notion 工作台及 UX 漸進式改善

狀態：**研究／概念方案，未套用實際 TEST 工作台**。以 Notion 免費版確實支援的介面為前提。

## 通用政府方案工作台

依操作需求呈現「政府方案類型 → 年度／核定期別 → 治療所本期額度、心理師本週額度、個案本期次數 → 異常待核對 → 深入歷史與額度調整」。必須明確標示每個檢視所屬 Price Plan 實例，不能假設 Notion 原生有能同步所有 Linked Databases 的全域年度選擇器。

首頁只突出三類額度；提供待核對／異常入口，例如首次實際補助日未知、週回報未確認、過期已預約、會談方案與歷程方案不一致、補助逾期仍進行中的歷程；詳細會談、額度調整和他處回報收合或下鑽。逾期但歷程仍進行中者不得被 View 隱藏；同一記錄重複出現在提示與正常清單可以接受，但不得重複計次。

## 現有十個功能頁面（2026-10-24 唯讀初盤點）

- Intake 3、個案／歷程 9、會談管理 5、帳務 14、活動團體 15、人員排班 14、空間 5、行政任務 3、會議專案 3、文件 5：合計 **76 個資料庫嵌入／引用區塊**，不等於76個不同資料庫；部分頁面讀取有截斷／未知區塊。
- 帳務、活動團體、人員排班：先核對區塊用途與重複日常工作入口、條件與排序；不因區塊多就逕自刪除。
- Cases／Episodes：臨床資料模型保留，優先改善讀取與狀態呈現。
- Sessions：有34個 Formula，先分析依賴與效能，不為畫面美化直接重寫。
- Intake、空間、任務、會議、文件：只檢查欄位順序、說明、檢視命名與操作步驟，原則保留。

## 變更等級

A 不變：沒有確實問題。B 最小修正：標題、顯示欄位、分組、排序、收合、提示；需讀當前 View、備份、TEST 回查。C 重大優化：資料庫拆分、Relation / Rollup / Formula 重寫、流程重整、資料遷移等；必須先提出前後比較、效益、風險、維護成本、影響面、測試與回復方式，**獲使用者明確核准才可實施**。

## 外部研究要求

研究 Notion 官方資料庫／檢視／公式／版面／權限／效能說明、資料正規化、UX 設計、模板與網路教學；至少10,000篇為目標，必須保存每筆來源與是否實讀，不得以搜尋筆數冒充完整閱讀。僅為了參考很多範本不構成修改理由。


## 2026-10-24｜首屏提示最小修正｜目前實際狀態

**局部已實作**：TEST 青壯年度額度標題後新增一個黃底 ⚠️ 警示，明示資料未核實不能由額度數字直接核准；導向既有年度個案清單，並提醒不同政府方案／核定期別不能混算，Linked Views 仍非同步方案／期別選擇器。修正前後查詢筆數一致、原資料庫區塊與導覽保留，結構回讀 PASS。

**未完成**：整套 Notion 資料庫／UX 10,000 篇來源研究；方案／期別實際導覽、真正同步篩選、確實隔離的多政府方案 TEST、精確 Formula 值與全功能使用者操作測試。此局部修正不代表已核准整套工作台重建。

**回復**：僅移除新黃色 ⚠️ Callout；不更改其他業務資料、Schema、Relation、Formula、View。

## 2026-10-24｜依使用者要求移除黃色提醒｜最新工作台狀態

- **現在沒有黃色 Callout**。原青壯年度額度標題、治療所年度額度、心理師本週、跨年度個案清單入口、115 舊版對照與備查仍保留。
- 上一節「首屏提示最小修正」是已被使用者撤回的歷史狀態，非現行需求。未來研究行政 UX 應避免自動添加醒目黃色警示；以易讀的資訊架構與必要數據檢視為優先，重大 UX 改造仍須經使用者同意。
- 繼續優先處理多政府方案與核定期別資料模型、Notion 原生計數真值、真正隔離的 TEST 和待核對清單，但**不得**把這次撤回當成已解決資料計算缺口。

## 2026-10-24｜政府補助工作台 vNext 一次性改版｜現行介面（取代先前純概念）

TEST 主工作台已一次調整為「方案／核定期別 → 個案參與／期限 → 現有青壯115心理師週額度 → 額度調整／歷史」。Price Plans、年度參與、Staff 3張主要 linked database 展開，原週回報、額度調整、115舊版 Cases 與驗收紀錄收合；左側共用導覽保留，沒有黃色提醒。年度參與新 linked database 以既有資料源建3個檢視：「個案參與總覽｜按方案期別」「資格待核對與不符合」「會談關聯／期限資料待補」。

新年度／方案可在 Price Plans 與參與紀錄各自挑選同一方案實例，但**Notion 沒有因此實現跨資料庫全域同步切換**。Staff 上的青壯115 Formula 也尚未通用化。此為工作台已實作狀態，**不等於其他十個模組的全部 UX 重構已核准或完成**。所有 View 設定、前後比較、回復方法請參閱 workbench-vnext-2026-10-24.md。


## 2026-10-24｜研究成果完整性核對、TEST 工作台 v2 與長期目標修訂｜現行 TEST 任務導覽設計

十模組原頁不被移動或刪除；另以 [行政任務 TEST v2](https://app.notion.com/p/4038ca66aa4d814297a2dbe27e8d054d) 提供「今天先處理 → 接續個案／帳務／政府補助 → 人員與營運協作 → 測試／歷史」完整任務流程。此頁只保留原本獨立活動狀態 TEST DB 1個，不嵌入其他原十模組的高密度資料庫；主區用兩組雙欄、驗收資訊用3個toggle。歷史 B1～B3 的偵測與修正結果仍可在 GitHub 回查，並非原十頁全面重構或實際效能驗收。

未加入黃色警示；不將青壯115 Staff 公式誤稱為全部政府方案通用，Notion Free 的一般 Linked View 亦不提供真正同步全域方案切換。完整 [修改差異／備份／驗收](audits/task-workbench-ux-v2-2026-10-24.md)，研究結論採用依據見 [來源矩陣](research/research-to-implementation-matrix.md)。


## 青壯人工核對後於服務歷程選方案｜2026-10-24｜取代舊青壯資格清單入口
Notion [TEST 補助工作台](https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf)首屏現在是「人工核對資格→個案服務歷程『💲收費方案』選核定方案」。Price Plans 仍呈現政府核定方案與額度、Staff 保留現行青壯115週額度；補助參與表預設收合，僅保留歷史／跨期設計備查。原「資格待核對與不符合」View 改名為「既有資格狀態（歷史備查）」但查詢條件不變。**不得重新恢復獨立青壯資格核對清單、黃色警示或將參與紀錄當成選方案必經流程**。其他政府補助規則按實際期別處理。[改版紀錄](audits/youth-manual-eligibility-episode-plan-2026-10-24.md)。

## 2026-10-24｜依使用者要求：政府補助「使用額度」Views 已直接建置

使用者明確糾正工作重點應是「建立看使用額度的 View」，非持續追查掛號費及 Billing。因此本次只做 Notion TEST 之原生 View 與入口最小變更：

- [方案使用額度｜新 View 02](https://www.notion.so/3f68ca66aa4d8156bccfcc28f75cbb9a?v=4038ca66aa4d81278430000cd581b5e7)：保留原方案表 View 01，新增同一 linked DB 的第02頁籤；呈現方案、核定期別、核定總額、已完成、已預約、待確認、已占用、剩餘及狀態。只限政府補助分類、不寫死年份與青壯。已回查有1筆方案、末頁結束。
- [個案使用額度｜新 Care Episodes inline View](https://www.notion.so/3f68ca66aa4d81cca3b4ee43b4bd8dcf?v=4038ca66aa4d81a3ab1a000ca3244dce)：在TEST工作台頁尾新增；Quick Filter 預選當期115青壯實際 Price Plan ID，可切換其他方案；呈現**服務歷程層級**的上限、完成、預約、他處是否確認、剩餘及狀態（非已驗證每個案跨歷程總計）。回查22筆，無後頁。工作台②新增加速連結，無黃色提醒。
- [心理師青壯115週額度原 View](https://www.notion.so/c698ca66aa4d826baa8f8773b5c2cfe6?v=3f78ca66aa4d817581c9000c3420b577)：已有本週有效占用、他處顯示、上限與狀態；**保留不重建**，仍為115專用，不稱通用方案。

所有新增 View 均在現有資料庫／頁面，沒有更動資料、公式、關聯、權限或正式系統，亦不重建資格工作流。Notion 原生公式／Rollup實值、跨歷程多核定期別及真人UX／效能未驗，不能因檢視有欄位便宣稱使用額度正確。已同步既有 Google Docs 青壯 UX v3.4 第十六節並讀回。完整備份、差異、驗收和回復見[本輪專項報告](audits/subsidy-usage-views-2026-10-24.md)。

## 2026-10-24｜青壯額度 View 改為「一案一歷程」而非跨歷程加總（已在TEST修改）

依使用者明確規定：青壯於本所同個案只用**單次 Care Episode**，超過衛生局核定期限便依行政流程結案，本所不再以青壯方式為同案重新開歷程。先前「需以個案跨歷程加總青壯」的猜想**撤回，不作為正常青壯需求**；其他政府方案不受此限制。

- 在原[TEST個案額度View](https://www.notion.so/3f68ca66aa4d81cca3b4ee43b4bd8dcf?v=4038ca66aa4d81a3ab1a000ca3244dce)上**原地更名**「青壯115｜個案使用額度（單一歷程）」，將可任意改選其他政府方案的Quick Filter轉為**固定實際115青壯Price Plan Relation FILTER**，新增「開案日期、結案日期」顯示，保留上限／本歷程完成、預約／他處確認／剩餘／狀態；**不新增View、公式、Relation、資料庫**。設定回查後查詢仍22筆且僅115青壯。
- [TEST補助工作台](https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf)②的個案用量入口更名並補一段青壯單次歷程、屆期結案、原有重複資料待核對說明；方案02額度View、心理師週額度、歷史與全部原本區塊不變、沒有新增黃色提醒。
- **安全性及不確定性**：同一個案實際有2筆帶測試標記的青壯歷程仍連啟用方案；22筆歷程按個案Relation只21名，不宣稱真實個案跨歷程，也不假定[TEST]完全隔離。真人UX、缺回報顯示、原生公式數字、權限／效能仍待驗收。資料未寫入、無新權限或新計算負載，僅View與一段工作台文字；回復只還原View設定和入口文案，需保留並行更動。詳見[稽核](audits/subsidy-usage-views-2026-10-24.md)。

## 2026-10-24｜使用者要求學習成果實際活用：補助工作台UX v3獨立預覽（待真人確認）
- **[USER UX GATE]** 使用者明確反映Notion版面仍醜且難用，質疑學習成果是否真的被活用，要求先確認實際設計成果再繼續其他功能。這是修正設計優先順序的要求，**不是對UX v3最終版面的審美核准**；青壯免週報Formula工作線維持暫緩，角色權限依原決定DEFERRED。
- **[LIVE TEST PREVIEW]** 原[政府補助工作台](https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf)未覆蓋，在TEST行政管理下建立[UX v3獨立預覽](https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f)。首屏3種額度入口（治療所／個案／心理師），接著2張日常任務卡，歷史備查收合，底部3張精簡Linked Views；使用者可真實開啟並比較，不是靜態概念圖。
- **[LEARNING TRANSFER]** 對照Notion官方「閱讀者導向＋Callout／Columns／Toggle」、「減少首頁Inline DB與顯示屬性」、「各View獨立配置」及Business OS／Company OS／營運Dashboard範本之Quick Actions。實施成果：同一用途原頁7個Inline DB→預覽3個；治療所顯示欄11→7、心理師5→5、個案11→8；不新增假KPI、黃色警示或資格工作流，亦不宣稱完成過去要求1,000／10,000篇模板研究。
- **[STRUCTURE/DATA PASS]** 新三個View已Fetch核對欄位、順序、篩選、Relation目標；保存View查詢顯示治療所本期政府方案1筆、在職心理師2筆、青壯115單一歷程22筆，全部has_more=false，與舊View查詢筆數完全一致。Notion原始資料與既有Schema、Formula、Relation、原View、業務列皆未變。新TEST Linked Views共享來源，不等於業務資料隔離。
- **[HUMAN/PERFORMANCE PENDING]** 操作入口可見、配置與資料範圍PASS，**未**證明視覺舒適度、真人1-click體驗、手機排版或實際網頁載入變快。待使用者真實比較完成三任務：首屏找到三額度並點入、開始個案選方案、辨識免週回報公式仍未啟用。未獲認可不覆蓋原工作台、不續作公式。回復僅精準撤銷新預覽與其3個Linked Views，原頁已保留。
- **[EVIDENCE & DOCS]** 實際來源→設計→原生Notion實作及回查詳見[專項稽核](audits/subsidy-ux-v3-learning-applied-2026-10-24.md)；[Google Docs跨年額度UX規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)新增第二十二節並回讀，已建立[增補前備份](https://docs.google.com/document/d/1J3Z9zhvjtb53Ik06_JxTXobQ1s0oKsR1eyAc5WxYcpQ/edit)。

## 2026-10-24｜使用者實測UX v3：1B～5B全部FAIL；同頁直顯v4已建立（待驗收）
- **[USER CONFIRMED / UX v3 ALL FAIL]** 使用者逐題回覆 `1B 2B 3B 4B 5B`，5/5均不符合；第3題找不到先前指稱的「個案與服務歷程」操作。明確需求：**資料直接在目前頁面顯示，不要靠點擊跳別頁查看；大量說明文字應移除，一眼就能看懂**。v3原本資料範圍1／2／22的結構PASS不等於UX PASS，實際操作／視覺仍FAIL；先UX，後免週報Formula。
- **[CAUSE / MINIMAL FIX]** 原TEST v3預覽頁先顯示介紹、3張額度跳頁卡、2張任務跳頁卡及長文字，3張真正資料表卻放在最底下。已將**同一個預覽頁** https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f 更名直接顯示UX v4，完全移除頂部卡片與跳頁說明，改為四段短標題後立即放4張**inline Linked DB Views**：治療所額度、心理師週額度、青壯個案額度、進行中服務歷程之「💲收費方案」可見且可在原生View直接編輯的欄位（驗收時只看不操作業務列）。歷史／他處待確認提醒保留在唯一收合區，不新增黃色警示。
- **[SCHEMA + VIEW READBACK PASS / UX PENDING]** 維持原三資料源、三既有v3精簡View及原方案篩選；前兩張View列數1／2，第三張青壯115 Relation View 22筆，第四張新建在職? **不是Staff**，是Care Episodes既有來源篩選「狀態＝進行中」，View `view://4038ca66-aa4d-81b2-b733-000c7ed4394b`，38筆。四者has_more=false，對應欄位SHOW 6／5／6／4，第三與第四皆直接顯示「💲收費方案」。前3張數量與原一致，來源分別Price Plans／Staff／Care Episodes。Notion Fetch頁面確認四個inline資料表直接相鄰短標題且位於最上方，沒有原導覽Callout；尚無真人實際載入時間、視覺／行動裝置／可操作性PASS。
- **[BACKUP/ROLLBACK]** 已在編輯前原生Duplicate v3頁面並Fetch確認保有三張舊Linked DB與原卡片；備份 https://app.notion.com/p/4038ca66aa4d811eafe0c857a6394638 。原官方TEST工作台 https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf 未觸碰。僅v3預覽頁與其專用View顯示欄變動、新增一張同源Care Episodes Linked View；要回復先核對並行變更，以備份精準還原預覽頁與v3既有SHOW欄位，移除第四Linked View但不刪除原Care Episodes資料庫。
- **[SCOPE / PERF]** 沒有變更Price Plans、Care Episodes、Staff、Sessions、Billing、週回報等任何業務資料列、Formula、Schema、Relation、原營運Views或權限；角色權限仍DEFERRED，青壯免週回報公式仍NOT LIVE。v3只有3個inline資料庫，v4有4個，**可能增加載入量**，是否變快未知；用多一張直接可見服務歷程View換掉跳頁。
- **[MANUAL RETEST GATE]** 請真人逐題驗證：①開頁是否立即看到「治療所本期額度」表，不點跳頁；②下捲是否直接看到心理師與個案兩表；③「服務歷程」表是否直接顯示「💲收費方案」並知道可在原頁操作（**勿更動真資料**）；④整頁是否少文字、容易閱讀。各題A符合／B不符合／C未測。使用者尚未回覆，不得將v4寫作UX PASS或直接覆蓋原工作台。
- **[DOCS VERIFIED]** [現行Google Docs規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)新增第二十三節；讀回確認22/23並存，明示五題FAIL與v4。修改前原生Google Docs[備份](https://docs.google.com/document/d/1SKgodaTjbxWatRZB-nrQz0IyxptQ1Dh7__8jecQpmrU/edit)已讀回確認無第23節。

## 2026-10-24｜UX v4使用者4/4 PASS；新增首頁異常與最後一次候選提醒（TEST待驗）
- **[USER CONFIRMED / V4 PASS]** 使用者對既有UX v4四題回覆`1A 2A 3A 4A`（4/4真人操作PASS）；不重測或改寫為其他結果。同一回覆新增三項需求：①質疑在首頁展開38筆「服務歷程｜直接選收費方案」的必要性，②警示異常清單及下一次為最後一次提醒應在首頁直接看到，③需解釋當前資料庫設計。**這是後續新驗收項目，不得把舊4A當新增警示通過**。
- **[UX V4 REFINEMENT / ACTUAL WRITE]** 原獨立TEST預覽https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f 已以原生Notion View與內容最小修改：頁面頂部先呈現`⚠️ 青壯｜待核對資料`、`⏳ 青壯｜最後一次補助候選（剩餘1次）`兩張真正的inline Linked Views，下方保留既有三張治療所／心理師／個案額度Table，最後原38筆廣義Care Episodes「直接選收費方案」改為 `設定收費方案（非每日額度）` Toggle，不再佔首頁每日判讀；另有最末`資料來源與使用範圍`短Toggle。寫後 Fetch確認**六個**inline Linked Database blocks、正確標題順序、底部兩個Toggle，未恢復舊的黃色資格核對警示。
- **[ANOMALY VIEW / VERIFIED SCOPE]** 新建`view://4038ca66-aa4d-81b5-a7fa-000cd34b7bdb`，來源Care Episodes真實現有Data Source；Filter為當前**青壯115 Price Plan實例Relation**、進行中、（開案日期空白 **OR** 他處使用已確認未勾）。Saved View查得**2筆**，兩筆皆開案日空白，其中一筆同時他處未確認，**不是三筆**。此View僅代表列出的兩類可驗證待核對，不代表涵蓋所有數值超額、期別逾期、Sessions方案衝突等異常。
- **[FINAL-USE ALERT / CANDIDATE NOT CONFIRMED]** 新建`view://4038ca66-aa4d-81e3-bfbd-000cfc0ac598`，Care Episodes Filter為當前青壯115 Price Plan實例Relation＋進行中＋既有`個案補助剩餘_自動` Formula在Notion Saved View中精確顯示文字`1`。回查**11筆**，SHOW已完成、已預約、剩餘額度及個案狀態。這表示**剩餘1次的候選**，不能保證下個已預約療程就是補助最後一次；需驗證預約、他處已用／未知、方案特定期別及公式完整expression後才可提高精度。無自行修改公式、標記完成或結案。
- **[DATA ARCHITECTURE EXPLAINED]** Price Plans＝方案實例＋核定期別上限，連額度調整與Sessions；Care Episodes＝個案服務歷程、💲收費方案Relation和Sessions，借Rollup/Formula計已完成／已預約／剩餘及個案狀態；Sessions＝每次會談／預約與實際狀態、心理師和方案；Staff＝心理師及Sessions、補助週回報Relation，週限以當期方案規則決定；週回報＝心理師×實際Price Plan方案實例×週起始日，`未確認`與`已確認0`不混用。TEST頁只是Linked Views顯示同一份原資料，**不另建業務資料庫**或隔離寫入。
- **[BACKUP / IMPACT / ROLLBACK]** 修改前原生Duplicate v4（4張Linked Views）並Fetch核對：https://app.notion.com/p/4038ca66aa4d8159b4e5daf90a4ae662；兩個新Views加上、重排前另Duplicate 6張DB備份：https://app.notion.com/p/4038ca66aa4d819482bbd663a0e4fe4d。曾出現Notion移動Toggle位置不符合預期，已以安全次序重排及局部更新，重Fetch證明位置正確。要回復先讀當前頁與並行變更、精準保留原業務Linked DB並移除兩張新警示；原業務資料表、原營運Views、原共用Schema／Formula／Relations／會談、Price Plans、Staff、週回報列、權限、GAS／Cloud Run全不變。
- **[LIMITS / RETEST GATE]** 原4A保持通過，兩張警示的原生過濾與資料量2／11、三額度顯示結構PASS；**警示視覺／最後一次精確性／整體新UX真人尚待確認**，不得將新增內容寫PASS。v4原本展開4張表，現在展開5張（2提醒＋3額度）並有1張低頻收合，可能增加首屏負載；無真實載入時間測量。免週報原公式整合仍NOT LIVE，角色權限DEFERRED。待新增UX驗收通過，再繼續其他事項。
- **[DOCS VERIFIED]** [Google Docs青壯跨期UX規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)已新增第24節，回查第23／24節共存與4A＋新需求；[增補前備份](https://docs.google.com/document/d/1kEm7zDMddObchiJfritf9b21TaIJPDsa7i8_uEYlgf4/edit)重讀無第24節。

## 2026-10-24｜UX v4.1驗收1A／2B／3A／4A；僅修第2題至v4.2
- **[USER VERDICT]** 使用者送出UX v4.1結果`1A 2B 3A 4A`，第1異常／第3三額度／第4次要收合均PASS保持不變；第2「最後一次提醒」明確FAIL，僅單點修正第2，不重測其他3項，勿繼續青壯免週報Formula整合（仍NOT LIVE）。
- **[CAUSE CONFIRMED]** 舊第2 Alert View以`個案補助剩餘_自動`顯示文字1篩出11筆；用同一Care Episodes之`💬 關聯會談`追查Sessions狀態，8筆為已完成1＋已預約1（預約只是青壯三次中的第2次），3筆為已完成2＋未預約（最後一次待安排）。因此原來11筆不能稱「下一次已預約就是最後一次」，源頭是未區分「剩餘可用次數」及「已占用預約」；數字與匿名來源經回查，不複製個資。
- **[V4.2 LIVE TEST VIEW CHANGE PASS]** 唯一改動現有專用View `view://4038ca66-aa4d-81e3-bfbd-000cfc0ac598`：名稱改`⏳ 最後一次已預約｜額度占滿待核對`；保留同一青壯115實際Price Plan Relation＋進行中，Formula Filter由原文字`1`改為文字`0`；SHOW加入`下次會談預約_自動`、`他處使用已確認`，仍顯示已完成／已預約／剩餘／狀態。Saved View查得3筆，透過對應Sessions匿名逐筆二次核對**3/3均已完成2＋已預約1，預約日期完整、他處已確認0**。這是本日期／本方案已預約最後一次之核對候選，不能當作Notion公式完整表達式或跨期規則自動正確已驗。
- **[LIVE PAGE + PRESERVATION]** 同一TEST預覽 https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f 更名 UX v4.2；僅第2區短標題改為「⏳ 青壯｜最後一次已預約（待核對）」及收合區對應說明。Fetch確認原第1異常2筆的View與原3額度View及兩Toggle保留，頁面仍六張Linked DB且無新的展開表。Price Plans、Care Episodes、Staff、Sessions、補助週回報等原始資料列與Schema、Relation、Formula／正式營運Views、權限、GAS／Cloud Run均不變；效能未新增展示表，但真人載入未量測。
- **[BOUNDARY/OPEN ISSUE]** 3筆`已完成2＋尚未預約`目前在原「個案額度」表可見，但**未**收進「最後一次已預約」提醒；要自動細分「最後一次待安排」與「已預約最後一次」而不漏人，仍需能被Notion View正確保存的原生條件或安全新增的Formula。隔離TEST探測中對Rollup`本歷程已完成_帶入`設定FILTER時工具未保留該條件，不能將不生效之View當自動排除依據；主View現階段不宣稱跨期／跨方案全部有效。後續依使用者選項決定是否另設待安排提醒。
- **[BACKUP/ROLLBACK]** 修改前已原生Duplicate UX v4.1頁 https://app.notion.com/p/4038ca66aa4d81d89cb1e7c1a6c12273 ，Fetch證實原6張Linked Views與舊提醒標題；備份頁**後續增加一張TEST過濾探測View（共7張）**，不宜全頁盲目覆蓋。原提醒View完整舊條件（PricePlan Relation＋進行中＋剩餘文字`1`）、舊SHOW已記錄，回復需讀目前配置後只改回舊Filter及SHOW並精準恢復第2區標題；原營運頁面與原資料庫不需回復。Google Docs原生修改前備份：https://docs.google.com/document/d/1OUxhsMSIJZBOipqjwJDmOv3n_L48TGZT_oKv1K-axu8/edit 。
- **[DOCS VERIFIED/RETEST]** [Google Docs青壯方案規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)已以revision guard增補第25節，回讀原24與新25皆存在；備份第25節不存在。第2題v4.2真人驗收**PENDING**，第1／3／4保留原A結果不重測。

## 2026-10-24｜UX v4.2 介面驗收完成
使用者確認第2題A/PASS，保留第1、3、4題PASS；UX v4.2四項全通過。免週報公式未啟用，本次沒有修改Notion資料或View。

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

## 2026-10-24｜Notion TEST安全續作：清除已通過工作台的過時備份入口，滿額提醒13/13離線測試
- **[ACTUAL UX CLEANUP]** 已重新Fetch使用者UX v4.2四項已驗收PASS的[Notion TEST補助工作台](https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f)，以精確單次`update_content`**真的移除**原收合區的`[UX v4 原生備份]`舊連結；回Fetch確認連結消失，原6個Linked DB、2個Toggle、上方異常／最後一次已預約提醒與3類額度表全部保留。備份頁本體暫作回復參照，尚未刪除此備份頁；不把移除入口冒稱備份頁刪除。
- **[LIVE BASELINE / BLOCKERS]** 重新Fetch Notion原Schema：Care Episodes50、Cases49、Sessions67、Price Plans30、Staff58欄；原`未預約下次會談`Saved View仍只以狀態＋未安排判斷。三組Care Episodes青壯115原Formula→Cases SUM Rollup的舊依賴與兩段Cases下游Formula的`formulaCode://`不完整問題仍在；`青壯轉自費`只有button型別無action。依使用者核准的硬停止，不執行任何`DROP COLUMN`、不覆寫共享Formula或Button、不改原業務資料。
- **[OFF-SYSTEM REGRESSION]** 按實際Price Plan方案實例的每案上限（非寫死115／3次）擬定互斥的`轉自費或結案`、`額外預約核對`、`待確認他處`、`維持預約提醒`與`自費原流程`決策；已執行13組匿名離線JavaScript分支案例，13/13PASS，涵蓋最後一次**僅已預約未完成**不可誤當滿額、完成3有下次預約、他處已確認0與未知、跨方案上限5次等。**不是Notion原生Formula或有效能／跨期驗收**，功能仍NOT LIVE。
- **[IMPACT/ROLLBACK]** 本輪唯一Notion寫入是移除一個過時連結，無新增欄位、公式、資料庫、查詢負擔及權限影響；回復只在重讀現行頁後將舊連結`[UX v4 原生備份](https://app.notion.com/p/4038ca66aa4d8159b4e5daf90a4ae662)`精準加回，保留其他並行修改，沒有任何業務資料回復。必要公式原文／按鈕動作完整基準仍未取得，永久刪除六欄與滿額提醒上線保持BLOCKED，免週報自動邏輯亦尚未啟用。
- **[DOCS READBACK]** [Google Docs青壯方案額度與UX規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)以revision guard新增第33節，回讀原32與新33共存；[修改前原生Google Docs備份](https://docs.google.com/document/d/1aPF1fXhnuuXWXDEayUkjOuknCxElb3G-EUXau6LbHeA/edit)不含第33節。
