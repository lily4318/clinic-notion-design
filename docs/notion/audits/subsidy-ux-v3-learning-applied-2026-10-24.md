# 2026-10-24｜Notion 設計研究 → 實際 UX v3 原型 → 驗收證據

**狀態**：獨立 Notion TEST 預覽已建立，功能入口／資料範圍回查 PASS；**人類視覺喜好、易用性及載入速度未驗收**，未獲使用者認可前不得將原工作台直接替換或宣稱整體改版完成。青壯免週回報公式工作線維持暫停（原Formula完整原文仍不可取得）。

## 為何要改

原 [政府補助工作台](https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf) 的 Notion Fetch 具有7個 inline database區塊，18.75%寬的側邊導航與大量說明、歷史資料交錯，個案額度View落在主要兩欄結束之後。方案、個案、心理師三種額度沒有在第一視覺層級共同呈現；擴增 View 不能證明改善易用性。使用者指出現有版面難看、要求學習活用與先驗證成果。

## 本次有來源且可對照的學習（並非完成1000／10000篇）

| 來源與檢視重點 | 活用原則 | 預覽中的可核實實作 |
|---|---|---|
| [Notion 官方｜Best practices for internal communications](https://www.notion.com/help/guides/best-practices-internal-communications-on-notion) | 閱讀者優先，適度用Columns、Callouts、Toggle建立資訊層級 | 首屏3張額度導覽卡，下一層2張每日任務卡，歷史資訊1個Toggle |
| [Notion 官方｜Optimize database load times](https://www.notion.com/en-gb/help/optimize-database-load-times-and-performance) | 避免首頁同時展開過多Inline DB；縮減不必要顯示欄位 | 7個inline DB（原）→3個（獨立預覽）；11→7（機構）、5→5（心理師）、11→8（個案）欄 |
| [Notion 官方｜Views, filters and sorts](https://www.notion.com/help/views-filters-and-sorts) | 同資料源可用獨立View顯示必要欄位及不同篩選，不複製資料 | Price Plans、Staff、Care Episodes各建1個專用精簡Linked View，並讀回篩選 |
| [Notion Marketplace｜Business OS](https://www.notion.com/templates/notion-business-os)；[Company OS](https://www.notion.com/templates/company-os-business) | 從快速操作及模組導覽開始，不要求操作者先理解內部資料表結構 | 方案額度、個案額度、心理師額度三種導覽 + 個案選方案／週額度核對兩個任務入口 |
| [Notion Marketplace｜Company Operations Dashboard](https://www.notion.com/templates/company-operations-dashboard)；[Medical Office Operations Dashboard](https://www.notion.com/templates/medical-office-operations-dashboard) | 依實際營運任務分區，不複製昂貴/不必要模板或資料模型 | 保留已核可的人工資格核對→單一Care Episode選Price Plan，不引入額外資格表或付費功能 |

**研究完整性**：本輪參照以上官方指南及代表性Marketplace案例，沒有逐套下載／完整研究1000或10000篇；Marketplace模板頁面內容／展示不能冒稱每份已安裝實測。後續以真人任務結果評價研究是否有用，不以蒐集篇數代替。

## 新建內容及完整範圍

- [獨立 UX v3 預覽頁](https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f)：TEST行政管理子頁，原頁不動；3個可直接進既有Filtered Views的額度入口、2個明確操作任務入口、1個歷史Toggle、3個最小呈現的真正Linked Views。
- 治療所新 View：`view://4038ca66-aa4d-81c8-987b-000c73354bb0`，Price Plans Scope `收費類型=補助` AND `服務類型=政府方案`，SHOW 7欄。回查 **1筆**，與原政府方案使用額度View 1筆一致。
- 心理師新 View：`view://4038ca66-aa4d-81dc-b7d9-000c561447de`，Staff `在職`＋`臨床心理師`且排除歷史隔離TEST心理師，SHOW 5欄。回查 **2筆**，與原心理師週額度View 2筆一致。
- 青壯個案新 View：`view://4038ca66-aa4d-817e-8ac0-000cfb71de56`，Care Episodes Filter 到同一筆實際青壯115 Price Plan Relation，SHOW 8欄。回查 **22筆**，與原青壯個案單一歷程View 22筆一致（包含既有標記測試的重複歷程，不自行刪除）。
- 三個新 View 查詢 `has_more=false`，Fetch 逐一確認來源、篩選、欄位順序和排序。原頁仍7個既有DB區塊、各既有View及Formula不更動。
- 只使用Notion原生Columns、Callout、Toggle、Linked database view與Markdown連結，不依賴付費Dashboard或外部CDN。因共享來源，**TEST預覽並不隔離業務資料**；不能於預覽隨意修改原資料列。

## UX／效能驗收標準（尚待真人確認）

1. 三個額度入口是否能在不捲動、不讀長說明時被辨認；各1次點擊到正確View。
2. 「先核資格、再於Care Episode選方案」能否快速識別並開啟原有個案與歷程頁；不新增另一份資格表。
3. 心理師週額度與他處回報分流是否清楚，明白**免每週回報Formula目前尚未啟用**，未知他處量不等於已確認0。
4. 在真實Notion桌機／手機比較視覺層級、誤點、捲動與操作步數；記錄實際耗時及載入速度。現在只有**結構／資料範圍PASS**，**視覺、使用者操作、效能為PENDING**，不能從inline DB減少直接推導速度提升。

## 風險、保持不變、回復

原個案、會談、Price Plans、Staff、週回報、Schema、Formula、Relation、原Views、權限及正式GAS／Cloud Run／Session／部署全部未動。新建3個Linked Views顯示原資料源，可能額外載入3張表，但與原頁相比減少4張；需真人效能測試。歷史內容和已確認公式值不受改動。角色權限按使用者先前決定DEFERRED，未作角色驗收。

回復前先讀目前預覽及原TEST頁，確定無並行修改／引用；只撤銷獨立預覽頁及其3個專用Linked Views，**不得刪除 Price Plans、Staff、Care Episodes來源資料庫**。原[政府補助工作台](https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf)即為未覆寫回復參照，不須動原頁。Google Docs [青壯UX規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)已追加第二十二節，附[修改前備份](https://docs.google.com/document/d/1J3Z9zhvjtb53Ik06_JxTXobQ1s0oKsR1eyAc5WxYcpQ/edit)並讀回。

**下一步 gate**：使用者實際開新版預覽並明確確認視覺與工作流程優於原版；不通過先修預覽，不能因此跳回公式整合或把預覽強制套上原頁。

## 2026-10-24｜使用者實測UX v3：1B～5B全部FAIL；同頁直顯v4已建立（待驗收）
- **[USER CONFIRMED / UX v3 ALL FAIL]** 使用者逐題回覆 `1B 2B 3B 4B 5B`，5/5均不符合；第3題找不到先前指稱的「個案與服務歷程」操作。明確需求：**資料直接在目前頁面顯示，不要靠點擊跳別頁查看；大量說明文字應移除，一眼就能看懂**。v3原本資料範圍1／2／22的結構PASS不等於UX PASS，實際操作／視覺仍FAIL；先UX，後免週報Formula。
- **[CAUSE / MINIMAL FIX]** 原TEST v3預覽頁先顯示介紹、3張額度跳頁卡、2張任務跳頁卡及長文字，3張真正資料表卻放在最底下。已將**同一個預覽頁** https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f 更名直接顯示UX v4，完全移除頂部卡片與跳頁說明，改為四段短標題後立即放4張**inline Linked DB Views**：治療所額度、心理師週額度、青壯個案額度、進行中服務歷程之「💲收費方案」可見且可在原生View直接編輯的欄位（驗收時只看不操作業務列）。歷史／他處待確認提醒保留在唯一收合區，不新增黃色警示。
- **[SCHEMA + VIEW READBACK PASS / UX PENDING]** 維持原三資料源、三既有v3精簡View及原方案篩選；前兩張View列數1／2，第三張青壯115 Relation View 22筆，第四張新建在職? **不是Staff**，是Care Episodes既有來源篩選「狀態＝進行中」，View `view://4038ca66-aa4d-81b2-b733-000c7ed4394b`，38筆。四者has_more=false，對應欄位SHOW 6／5／6／4，第三與第四皆直接顯示「💲收費方案」。前3張數量與原一致，來源分別Price Plans／Staff／Care Episodes。Notion Fetch頁面確認四個inline資料表直接相鄰短標題且位於最上方，沒有原導覽Callout；尚無真人實際載入時間、視覺／行動裝置／可操作性PASS。
- **[BACKUP/ROLLBACK]** 已在編輯前原生Duplicate v3頁面並Fetch確認保有三張舊Linked DB與原卡片；備份 https://app.notion.com/p/4038ca66aa4d811eafe0c857a6394638 。原官方TEST工作台 https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf 未觸碰。僅v3預覽頁與其專用View顯示欄變動、新增一張同源Care Episodes Linked View；要回復先核對並行變更，以備份精準還原預覽頁與v3既有SHOW欄位，移除第四Linked View但不刪除原Care Episodes資料庫。
- **[SCOPE / PERF]** 沒有變更Price Plans、Care Episodes、Staff、Sessions、Billing、週回報等任何業務資料列、Formula、Schema、Relation、原營運Views或權限；角色權限仍DEFERRED，青壯免週回報公式仍NOT LIVE。v3只有3個inline資料庫，v4有4個，**可能增加載入量**，是否變快未知；用多一張直接可見服務歷程View換掉跳頁。
- **[MANUAL RETEST GATE]** 請真人逐題驗證：①開頁是否立即看到「治療所本期額度」表，不點跳頁；②下捲是否直接看到心理師與個案兩表；③「服務歷程」表是否直接顯示「💲收費方案」並知道可在原頁操作（**勿更動真資料**）；④整頁是否少文字、容易閱讀。各題A符合／B不符合／C未測。使用者尚未回覆，不得將v4寫作UX PASS或直接覆蓋原工作台。
- **[DOCS VERIFIED]** [現行Google Docs規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)新增第二十三節；讀回確認22/23並存，明示五題FAIL與v4。修改前原生Google Docs[備份](https://docs.google.com/document/d/1SKgodaTjbxWatRZB-nrQz0IyxptQ1Dh7__8jecQpmrU/edit)已讀回確認無第23節。
