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
