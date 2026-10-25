# Notion 深度學習｜AUTO-12｜2026-10-26｜Export／Offline／Workspace settings

- 執行軌跡：AUTO-12-20261026-0341-Asia-Taipei；研究模式：排程獨立批次。
- 研究目的：針對治療所行政系統的備份可攜性、離線工作及工作區安全設定，建立可追溯來源與反例；不授權任何實際 Notion 改動。
- 起始核對：main 的 README、根 AGENTS、source-of-truth、Notion AGENTS、sources、decision-log、acceptance-status、研究目錄、首批與02–04批清冊、MANUAL-01、AUTO-01～11。逐URL比對後以下3篇的文章slug未在當期已知清冊中出現。語系前綴不算獨立來源。
- 取證日：2026-10-26（Asia/Taipei）；官方頁面已實際開啟，讀取主要正文、子節與 FAQ。未逐張檢查圖片、嵌入影片、外連或執行實機操作；以下全部標為 TEXT_MAIN_SECTIONS_READ + ANALYSIS_PASS_1，不列為 FULL_DEEP_PASS。

## 新來源 1｜AUTO12-S01｜Export your content
- canonical URL: https://www.notion.com/help/export-your-content
- 標題：Export your content；來源：Notion Help；去重ID：notion-help:export-your-content；首次閱讀：AUTO-12/R1，2026-10-26。
- 閱讀範圍：PDF（桌面/手機）、HTML、Markdown & CSV、列印、工作區匯出、Admin API beta、FAQs（表單視圖、所有資料庫Views、權限、Windows ZIP路徑限制）。
- 官方可查事實：Form view不能直接匯出；Markdown+CSV輸出不是完整Notion可回填的結構；資料庫只能選目前或預設View匯出，不能一次匯出所有Views；工作區匯出不含匯出者無權限頁面，無法直接完整重新匯入還原；Enterprise Admin API工作區匯出是beta且需要組織Owner與bot/token。
- 待檢驗假設：『行政工作台可匯出CSV，所以已可無損備份所有檢視、關聯、權限及歷史』。
- 反例：工作台有多個不同篩選的Linked View，僅匯出目前View可能漏掉其他列與View設定；另有他人Private頁面不在Workspace匯出中；PDF列印與CSV資料無法還原所有Relation/Formula/Share權限。
- 修正結論：未來備份驗收應分開檢查業務資料、View/Formula/Relation結構、權限與回復演練；『可匯出』≠『可還原』。本輪不進行匯出或變更。
- 不確定性：未測試任何真實治療所資料、Windows解壓縮、不同方案或API；官方介面/方案限制可能更新。

## 新來源 2｜AUTO12-S02｜Use pages offline
- canonical URL: https://www.notion.com/help/use-pages-offline （閱讀 https://www.notion.com/en-gb/help/use-pages-offline，同篇語系合併）
- 標題：Use pages offline；來源：Notion Help；去重ID：notion-help:use-pages-offline；首次閱讀：AUTO-12/R1，2026-10-26。
- 閱讀範圍：適用方案/裝置、下載頁面與資料庫、離線支援與限制、同步衝突、管理離線頁、FAQ。
- 官方可查事實：所有方案桌面/手機App可下載頁面，瀏覽器不支援；子頁不自動下載；資料庫預設只下載第一個View的前50列，其他重要列需額外下載；Forms/Buttons/Embeds/AI等進階區塊離線受限；離線不能改Share/Permissions；兩人離線修改同一Select等非文字屬性時可能只保留一方。
- 待檢驗假設：『把補助資料庫設為離線就能離線查到所有個案，並安全多人核對更新額度』。
- 反例：第51筆個案不在首View預載；手機與桌面需各自下載；兩名行政人員在無網路時改同一補助核對Status，重新連線可能只有一方值被保留。
- 修正結論：離線可讀範圍、同步衝突與權威數值確認需另設驗收，不得以離線資料庫畫面推論全體資料或最新額度；本輪不啟用離線設定。
- 不確定性：未做裝置、衝突、資料庫筆數與同步速度實測。

## 新來源 3｜AUTO12-S03｜Workspace settings
- canonical URL: https://www.notion.com/help/workspace-settings
- 標題：Workspace settings；來源：Notion Help；去重ID：notion-help:workspace-settings；首次閱讀：AUTO-12/R1，2026-10-26。
- 閱讀範圍：設定搜尋、Sidebar、名稱、Allowed email domains、Workspace/Member匯出、Analytics、Workspace刪除、Emoji、Security、Enterprise-only限制、Domain、SSO、FAQ。
- 官方可查事實：搜尋只顯示有權設定且可能未索引全部項目；Allowed email domains可能讓同網域成員加入，付費版有席次成本；Member CSV匯出限定Business/Enterprise；Disable export、禁止公開發布等屬Enterprise控制；刪除整個Workspace會讓所有成員失去內容；跨Workspace移動頂層頁會連帶子頁。
- 待檢驗假設：『工作區找不到某個安全選項就代表不需要控制，且共享Email網域只影響登入便利性』。
- 反例：免費版管理員可能看不到Enterprise-only Disable export；網域加入機制可能改變成員/擁有者角色與費用；移動父頁連帶子頁與原權限範圍，造成跨模組存取中斷。
- 修正結論：安全控制應以實際方案、角色、頁面繼承權限分層查核；設定搜尋空白不能推論功能不存在或已安全；本輪不改工作區設定。
- 不確定性：官方文內不同方案描述需要與實際帳號驗證；未實際變更成員/權限/網域。

## 去重、計量與安全
- 本批候選3篇、依canonical文章slug確認新來源3篇；各完成1次可追溯『文字主要章節閱讀＋獨立反例』，不是完整深讀，也不是10次。
- 本批嚴格FULL_DEEP_PASS=0；累積可核實每篇10次獨立完整深讀達標仍0/10,000。不得把同篇語系版本、同篇不同章節、相同分析重算新篇/新輪。
- 舊文 `back-up-your-data` 與本次 `export-your-content` 在部分匯出資訊重疊，但為兩篇不同官方文章；本輪僅將新增文章算一次。
- 未逐張檢視圖片/影片、未執行真人UX、角色權限、資料真值、效能或回復測試；任何設計提案需在10,000×10與使用者確認後另行授權。
- Notion正式與TEST Page/Database/View/Formula/Relation/Permission/資料列零修改；GAS、Cloud Run、Session與部署零修改；GitHub只存研究與進度，沒有個資或秘密。
