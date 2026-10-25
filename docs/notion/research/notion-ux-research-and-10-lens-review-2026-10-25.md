# 青壯額度工作台｜Notion 範本、官方技術與UX研究及十面向交叉複核（2026-10-25）

> 狀態：**研究與設計建議，不是Notion實作或真人驗收**。只處理使用者本次要求之「版面設計研究→改善建議→GitHub同步」，禁止擅改Notion任何Page、View、Schema、Formula、Relation或其他行政模組。現況以本日Notion Connector Fetch為準。

## 一、研究數量與證據級別：絕不可把索引量冒稱已閱讀

- **使用者要求**：至少10,000篇Notion設計來源、每篇深度重複學習至少10次，整理內化並提出工作台改善建議。**本次並未達成10,000篇逐篇深讀×10遍**，不宣稱達成或內化完成。
- **素材庫規模≠已讀**：2026-10-25查詢[Notion Marketplace](https://www.notion.com/templates)的搜尋介面顯示「70,000+ templates」，以及[Operations category](https://www.notion.com/templates/category/operations)列示約7,878（語系、爬取時間可能不同）。這只是平台宣稱的上架/索引量，**不等於已取得10,000個去重作品或其中任何一篇已被深讀**；同類別可能重複。
- **本回合實際證據**：對 Notion官方Help、Marketplace、Nielsen Norman Group (NN/g) 等進行分主題搜索，成功展開數十個URL中的**至少20個不同網頁**；有些是目錄頁或同主題多語系版，也有數個開啟發生403／Cache miss。只有本文「外部實際取得與檢視之代表來源」可回溯到URL及相關要點。**未逐篇下載、實際複製或測試外部付費模板，也未形成10,000筆去重證據清冊**。
- **十次深度複習狀態**：下方執行**10個不同設計面向的交叉複核**，把官方規格、模板範例與本案六個View互相對照；這不是每個來源完整重讀10遍的證據，也不把10面向等同使用者要求之「10輪逐篇深讀」。逐篇精讀10次的可核實完成篇數：**0**；完整目標狀態：**未達成**。
- **方法限制**：Notion Connector提供頁面原生文字/區塊及Saved View配置、無等價人眼登入後桌機/手機畫面截圖；下面的美感判斷屬**結構性UX假設**，非實際畫面視覺或真人操作通過。NN/g論文與模板僅提供可借鑑原則，不代表可直接移植其臨床/財務資料。

## 二、即時Notion工作台基線（匿名、無業務列）

- 現行：[政府補助｜額度與警示工作台](https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f)；**6個Linked Views**，其中5個直接展示、1個「設定收費方案（非每日額度）」收合；頁底另有「額度核對提醒」小Toggle。原始來源分別Care Episodes(4檢視)、Price Plans(1)、Staff(1)。原先許多AI技術說明及設計歷史頁已依使用者需求刪除。
- **首屏順序**：`⚠️ 青壯｜待核對資料`(4欄)→`⏳ 青壯｜最後一次已預約（待核對）`(7欄)→`🏢 治療所｜本期補助額度`(6欄)→`👨‍⚕️ 心理師｜本週額度`(5欄)→`👤 青壯｜個案使用額度`(6欄)→低頻方案設定(4欄)→文字提醒Toggle。
- **語意不一致風險（實際View設定）**：`最後一次已預約`的View `view://4038ca66-aa4d-81e3-bfbd-000cfc0ac598`條件為`💲收費方案=115青壯方案` AND `歷程狀態=進行中` AND `個案補助剩餘_自動字串=0`，**未直接設定「本歷程已預約>0」條件**。因此標題「已預約」是待核實假設；不經公式真值/實際列驗收不可保證清單每筆都已預約。僅作改善建議，**本次未修改篩選**。
- **方案期間語意**：治療所View篩`收費類型=補助 AND 服務類型=政府方案`，按方案開始日降序（可能含多方案/期別）；心理師View依原青壯專屬本週Formula；個案View硬指向115青壯Price Plan Page ID。這三種額度**不是同一個全域方案選擇器**，必須由標題/範圍標示防止誤認混算。
- **效能線索**：同頁5張同時可見的Linked Views，最後一次候選對Formula進行字串數值篩選；Notion官方指出多inline資料庫、Formula/Rollup篩選與深層參照可能拖慢，但**尚無真實毫秒測量**，不可宣稱此頁目前慢或改版必定提速。
- **歷史入口**：[補助方案管理｜TEST](https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf)另保留7個重要檢視（期別、參與歷史、週額度／回報、額度調整、Cases對照、歷程資料），不是此次要刪除或大改的頁面。

## 三、外部實際取得與檢視的代表來源及運用（非1萬篇清冊）

| ID | 檢視來源（URL） | 研究要點／可用性 |
|---|---|---|
| N01 | [Notion／Optimize database load times](https://www.notion.com/en-gb/help/optimize-database-load-times-and-performance) | 避免高流量首頁多inline DB、複雜Formula/Rollup篩選、冗餘可見欄位；一Linked DB切換多Source可能提升效能，**但不可因此犧牲使用者要求的直接看見3額度**。 |
| N02 | [Notion／Views, filters, sorts & groups](https://www.notion.com/zh-tw/help/views-filters-and-sorts) | 各Saved View個別篩選／顯示欄位；Table vs List選擇與複製同來源視圖。 |
| N03 | [Notion／Advanced filters](https://www.notion.com/help/guides/using-advanced-database-filters) | OR/AND複合過濾必須明確核實，不能用標題暗示不在篩選內的業務狀態。 |
| N04 | [Notion／Data sources & linked databases](https://www.notion.com/help/data-sources-and-linked-databases) | Linked View改外觀通常不改原View，但改property/資料列會改原來源；權限仍依來源。 |
| N05 | [Notion／Customize database layouts](https://www.notion.com/zh-tw/help/layouts) | 頁面布局全資料庫共用，**不適合為青壯專屬View隨意全域調整Cases或Care Episodes的Page Layout**。 |
| N06 | [Notion／Dashboard view](https://www.notion.com/zh-tw/help/dashboards) | Dashboard view為Business/Enterprise；本案需以免費版可用的普通頁＋Linked Views方案設計。 |
| N07 | [Notion／Chart view](https://www.notion.com/help/charts) | 免費版只能試用一張圖，且圖表不能直接改資料，不可把多圖表當成Free主要編輯介面。 |
| N08 | [Notion／Page style, callouts](https://www.notion.com/help/customize-and-style-your-content) | Callout用於必要風險而非每段裝飾；統一色彩、留白及圖示。 |
| N09 | [Notion／Columns, headings, dividers](https://www.notion.com/zh-tw/help/columns-headings-and-dividers) | 桌機可分欄，行動版不支援同等多欄畫面；不能把雙欄作唯一導覽。 |
| N10 | [Notion／List views](https://www.notion.com/help/lists) | 較少欄位的清單適合精簡，但額度比較仍需保留表格。 |
| N11 | [Notion／Table views](https://www.notion.com/help/tables) | 表格可直接比對已完成/預約/剩餘，適合額度三指標。 |
| N12 | [Notion／Database buttons](https://www.notion.com/help/database-buttons) | 基本按鈕可跨方案用，但部分動作付費且高風險操作需授權/原生動作查核；**本提案不新設按鈕**。 |
| N13 | [Notion／Using database views](https://www.notion.com/help/guides/using-database-views) | 多View呈現同一資料、各自欄位和排序；工作台並非資料庫複製。 |
| N14 | [Notion／Create a database](https://www.notion.com/help/create-a-database) | 不為視覺排版新建重複Source，沿用現有Linked Views。 |
| N15 | [Notion／Intro to databases](https://www.notion.com/help/intro-to-databases) | DB每一列是頁面，依需開啟詳細資訊；不把大段教學擠在首頁。 |
| T01 | [Notion Marketplace／Operations category](https://www.notion.com/templates/category/operations) | 大型營運模板庫索引，研究「工作情境→行動→檢視」類型；不是逐套完整試用。 |
| T02 | [Notion Marketplace／Marketplace](https://www.notion.com/templates) | 70,000+模板搜尋入口；不代表10,000篇已讀。 |
| T03 | [Medical Office Operations Dashboard](https://www.notion.com/templates/medical-office-operations-dashboard) | 描述以待辦／預約／申報異常為主的日常控制台；公開介紹不等於已下載/使用付費範本。 |
| T04 | [The Finance Dashboard](https://www.notion.com/templates/the-finance-dashboard) | 優先讓人辨識數據及期間比較；消除重複填報負擔；本案不得因此創建額外帳務欄位。 |
| T05 | [Notion Marketplace／Finance category](https://www.notion.com/templates/category/finance) | 額度使用量與剩餘量的儀表設計參照，不直接使用個人預算套版於補助業務。 |
| U01 | [NN/g／5 Principles of Visual Design](https://www.nngroup.com/articles/principles-visual-design/) | 比例、視覺層級、對比、平衡、接近性；少層級不等於每頁多色。 |
| U02 | [NN/g／Visual Hierarchy in UX](https://www.nngroup.com/articles/visual-hierarchy-ux-definition/) | 利用分組、有限色彩和對比引導掃讀。 |
| U03 | [NN/g／Progressive Disclosure](https://www.nngroup.com/articles/progressive-disclosure/) | 高頻功能直接可見、低頻功能按需展開；進入第二層須清楚標示。 |
| U04 | [NN/g／10 Usability Heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/) | 狀態可見、與實務語意一致、錯誤預防及可恢復；「待核對」與「已確認0」分清。 |
| U05 | [NN/g／UX Strategies for Complex-Application Design](https://www.nngroup.com/articles/strategies-complex-application-design/) | 醫療/財務專業軟體須研究實際行政情境、錯誤代價及多角色限制，不套大眾習慣追求造型。 |

補充：本輪亦取得官方[Notion Marketplace分類索引](https://www.notion.com/templates/category)、[Notion operations zh-TW目錄](https://www.notion.com/zh-tw/templates/category/operations)、[NN/g Visual Design topic](https://www.nngroup.com/topic/visual-design/)等導航/語系頁；另有醫療模板/小企業模板因Cache miss僅有搜尋摘要，**不得算作全文精讀**。

## 四、十個設計面向的交叉複核（不是每篇讀10遍）

| 面向 | 現況證據 | 本輪重新判斷／決議 |
|---|---|---|
| 1. 任務優先級 | 兩個待核對檢視在頁首、之後才是三額度 | 維持警示可直見（此前使用者已要求首頁直接看到），但壓縮警示欄位和標題高度，不用大量彩色區塊。 |
| 2. 資訊架構 | 目前6 View跨三來源、5張直接展開 | 不新增資料庫；主要分為「待核對→額度概況→方案設定及歷史」三個視覺區段。 |
| 3. 視覺層級 | 五個同級emoji H2 + 多個Table | 建議H1/一行範圍提示，H2三段，H3/普通字作區段內View名稱；最多兩組視覺強調。 |
| 4. 表格密度 | 六個View可見欄4／7／6／5／6／4 | 預設每張表只保留完成任務的4–6欄；特別檢查7欄警示是否縮到4–5欄而不失去核對能力。 |
| 5. 標籤與判斷一致 | 最後一次「已預約」只濾剩餘字串0，不直接濾預約數>0 | 先建議中立名稱「額度已占滿｜預約待核對」；如果業務必須精準顯示已有預約，應另案以原生條件/真值校對，不偷改Formula。 |
| 6. 資料信任與例外 | 他處使用未確認需人工核對，工作台已有簡短文字提醒 | 警示文案保留明確「未確認≠0」；不可用紅/綠裝飾代替真實資格。 |
| 7. 方案與期別語境 | Price Plans含所有補助、Staff與Episodes使用青壯115專屬 | 明確標示「治療所：全部方案」、「心理師/個案：青壯115」，不虛構一個能同步所有View的全域選擇器。 |
| 8. 效能與重用 | 同時5個inline，Formula篩選，4/6 Views來自Episodes | 首先減少可見欄與非必要計算顯示，經相同設備計時後再評估改為少數View tabs；不能以Toggle收合推論一定變快。 |
| 9. 桌機／手機適應 | 尚無截圖/真人手機測試；原頁單欄堆疊 | 優先單欄通用；若提雙欄卡片，手機須重新審核次序/溢出，不作關鍵訊息唯一呈現。 |
| 10. 安全、回復與驗收 | 多來源都是Linked View；歷史有4A使用者PASS但新設計未測 | 僅提案、須經使用者核准才改；先保存全部6 View配置，對各使用者角色測權限，真人5秒掃讀+任務測試並量載入時差。 |

## 五、改善方案：A為最小修改首選；B是需另外核准的效能探索

### A｜首屏任務分組＋欄位減量（推薦，未實作）

```text
🎫 政府補助｜額度工作台
   治療所：所有政府補助方案   ·   心理師／個案：青壯115（目前檢視範圍；不是全域篩選器）

⚠️ 需要核對                      [原本兩張待核對Linked Views，直接可見]
   待核對資料       (名稱｜開案日｜他處已確認｜額度狀態)
   額度占滿待核對   (名稱｜已完成｜已預約｜剩餘｜狀態) ← 先對照View再核可名稱

📊 額度概況                      [三張原有Linked Views，直接可見]
   治療所額度       名稱｜核定｜已完成｜已預約｜剩餘｜狀態
   心理師本週額度   名稱｜本週使用｜他處使用｜上限｜狀態
   青壯個案額度     名稱｜已完成｜已預約｜剩餘｜狀態（方案可視需要保留）

▸ 低頻操作
   設定收費方案（原6號Linked View，不刪除）
▸ 額度核對提醒：未確認不可當成0（保留）
```

- 預期效益：沒有大篇解說，清楚區分『今天要處理』和『總量是多少』，並保留已確認需要的同頁資料呈現。沿用所有6個原View／3個原Data Sources／原方案、關聯及公式，不額外增加查詢。
- 可能風險：修改標題和欄位可見性可能讓原本常用的細節不易找到；應先逐項列出原顯示屬性、新顯示屬性和每個欄位保留理由，對使用者做A/B或前後同頁對照後再改。
- 回復：針對每一個View存原本`displayProperties`、`name`及頁面原始區塊順序；只可回復相同View ID與原設計，避免整頁舊快照覆蓋並行修改。真正修改前先以最新Fetch與期別規則核對。

### B｜效能導向單Linked Database多View分頁（備案，未實作）

- Notion官方建議高流量儀表集中Linked Database，使同時只有一個檢視開啟；可能降低負荷，但使用者之前**否決從首頁跳頁才能看三種額度**，因此B不能當作單方面默認推薦或替換A。
- 須先真人比較：A是否已能迅速同頁判讀、5張inline的載入時間是否實測達到需要優化的程度。若沒有客觀效能問題，以A為先。

## 六、具體驗收與未執行範圍

- 建議在使用者核准後安排**不改真實個案紀錄**的測試：5秒觀察說出第一個需核對的項目；不點其他頁找到治療所／心理師／個案三額度；閱讀候選表能否分清「額度0但可能未預約」；手機能否直接找到相同訊息；同帳號／設備對照改前與改後載入時間。
- **無本輪Notion寫入**：沒有新增預覽頁、沒有修改任何現有View/Formula/數據、沒有建立KPI假資料、沒有調整角色權限；未量測效能、未做真人/手機操作，相關改版效果皆記為待驗證。
- 使用者若只需要研究及建議，當本文件與對應GitHub設計／決策同步後就停止；沒有明確新指令不得擅自實作Notion。

## 七、下一輪研究的可稽核要求（不建立背景工作）

若未來使用者繼續要求達到10,000篇×10，須逐URL記錄`source_id、去重URL/title、作者、來源類別、獲取日期、是否取得正文、閱讀深度/段落、應用結論、每次深度重讀的日期/比較差異/批註`；每一篇的十次深讀均需獨立可稽核記錄；在證據不足時不得填滿1萬或10次。這只是研究方法，不代表已安排背景執行或本次已完成數量。
