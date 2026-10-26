# Notion 深度學習｜AUTO-21｜2026-10-26（研究與GitHub紀錄限定）

- 執行軌跡：`AUTO-21-20261026-1237`；來源 `AUTO21-S01`～`S03`。與手動「繼續」可並行，**不得因本次研究更動Notion**。
- 本輪先從 main 讀 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、decision-log.md、acceptance-status.md、research/README、首批與02–04研究清冊、MANUAL-01、AUTO-01～20及相關研究文檔；以 GitHub repo search 檢查下列三個文章slug均無既有登錄（搜尋索引可能有延遲，因此仍標「依當前清冊暫列唯一」）。
- 閱讀日期：2026-10-26（Asia/Taipei）。實際開啟外部文章，讀取可取得的主要正文、分節及FAQ；對官方來源不臆測發表或更新日。canonical ID 依文章原文路徑，忽略語系前綴/追蹤參數；不同URL須為不同文章，不能把同一篇的多個角度當多篇。
- **證據層級**：每篇 `R1/BODY_MAIN_AND_COUNTEREXAMPLE`；**非** `FULL_DEEP_PASS`。圖片未逐張檢視，影片未觀看，未在真人Notion工作區、手機、跨角色、API整合或正式系統實測。

## AUTO21-S01｜Workspaces on mobile
- 來源：Notion Help；標題：Workspaces on mobile；URL：<https://www.notion.com/en-gb/help/workspaces-on-mobile>；canonical：`notion-help:workspaces-on-mobile`。
- 本次實讀：導航列（Home/Search/Inbox/新頁）、Teamspaces與巢狀頁/資料庫View、Workspace切換、行動編輯工具列、•••操作、Lock page/Lock views、版本歷史與匯出、Share menu（Share to web、Everyone、群組、訪客）、手機通知與設定、Bin、FAQ。網頁正文約106–234行；其餘為導覽與頁尾。
- 原假設：桌面版精簡的首頁、資料庫入口與權限控管可無差別搬到手機；只要頁面外觀乾淨就能降低誤操作。
- **反例1（導航深度）**：手機巢狀頁和資料庫View要從Home中的Toggle展開，桌面上可一眼看到的入口未必在手機首屏；手機用`+`工具列而非桌面`/`。若把關鍵補助餘額藏在多層子頁，手機操作步數反而增加。
- **反例2（高風險操作）**：手機Share menu含`Share to web`、`Everyone`及新增訪客；可見介面不等於符合個案資料分享政策。不能假定`Lock views`會阻止所有業務資料修改，或把「手機看不到」當作權限隔離。
- 修正理解：將行動端可發現性、操作步數、誤觸分享與權限列為未來**待測假設**，不能憑桌面版截圖宣稱跨裝置驗收通過；不建議現在修改任何現有View/Share。
- 未驗：各手機尺寸、真實操作、實際Share權限、View功能差異、圖片、效能。

## AUTO21-S02｜Add & manage connections
- 來源：Notion Help；標題：Add & manage connections；URL：<https://www.notion.com/help/add-and-manage-connections-with-the-api>；canonical：`notion-help:add-and-manage-connections-with-the-api`。
- 本次實讀：Workspace安裝連線、API連線加入指定頁面、頁面斷開、Enterprise的Manage page access與連線安裝限制、workspace連線管理、OAuth授權Select pages、內部Token與第三方安裝、文件結尾；網頁正文約106–262行。
- 原假設：只要Notion頁面分享給正確的人，任何外部整合也會自動受到完全相同的存取限制；或只要安裝連線便能存取所有資料。
- **反例1（權限不同層）**：API connection須加入特定頁面才能在該頁使用；OAuth亦選擇允許的頁面；人員Share、頁面Connection與第三方授權是不同檢查層，不能將一個成功視為全部授權安全。
- **反例2（方案差異）**：Enterprise可限制誰安裝連線及誰管理連線的頁面存取；不能把這種管理能力直接假定Free工作區也有。成員可安裝連線的描述不代表已發生資料外送，需以實際權限及連線清冊核實。
- 修正理解：未來如涉及Notion與前台/GAS資料串接，必須先檢查最小頁面授權、Token管理與撤權、第三方資料處理及方案功能；**本輪沒有安裝/調整任何Connection或API Token**。
- 未驗：OAuth授權實際畫面、免費版角色差異、Token撤銷、圖片、第三方資料處理、實際API存取。

## AUTO21-S03｜Hostile Patterns in Error Messages
- 來源：Nielsen Norman Group；作者：Kate Kaplan；原文發表：2022-10-30；標題：Hostile Patterns in Error Messages；URL：<https://www.nngroup.com/articles/hostile-error-messages/>；canonical：`nngroup:articles/hostile-error-messages`。
- 本次實讀：導言與兩項原則、過早顯示欄位錯誤的多個案例、非錯誤狀態濫用紅黃警告樣式的案例、結論與四項操作準則；正文約40–118行。
- 原假設：越早、越大、越紅黃的警示越能避免行政填寫錯誤，任何「尚未確認」都該用錯誤視覺樣式強調。
- **反例1（過早判錯）**：使用者尚在輸入格式完整值時立即紅框，會把正常填寫過程當成錯誤；對政府方案期別/日期/額度欄應區分尚未輸完、已完成但格式錯誤、以及已確認業務衝突。
- **反例2（警示疲乏）**：常態資訊如「尚無附件」不應使用嚴重錯誤樣式；若把待核對/未確認0/不適用全部做成黃色警示，真正的超額或資格矛盾可能被淹沒。與使用者已明確撤回黃色Callout的決定方向一致，但**不是**要求刪除法定或真正高風險提示。
- 修正理解：先確定錯誤真值與可採取行動，再考慮提示時機/語氣/顏色；平常狀態以清楚文字為主，真正有風險才採高顯著警示。這是外部UX原則，不代表Notion原生表單可自訂即時驗證時機，也未授權改現有頁面。
- 未驗：文中每張示意圖片、可下載PDF、治療所真人表單研究、Notion表單支援度及實際錯誤率。

## 本輪交叉反證與嚴格計數
- S01的手機分享與S02的API連線，屬不同存取層：**可見、可編輯、可透過整合讀取**必須分開核實；S03則提醒不能用滿版警告掩蓋未經驗證的權限或資料真值。
- 本輪依main現有清冊及slug查核暫列新增不同文章 **3篇**；各完成可取得主要文字與首次反例分析 **3次**；針對舊文章獨立複讀 **0次**；每篇完整深讀10/10新增 **0篇**。
- 累積已能核實完成10次獨立完整深讀的文章仍 **0/10,000**；全域唯一來源精確總數未完成跨所有檔案嚴格機器去重，故不提供虛構累計。
- **研究與業務驗收分離**：圖片/影片、跨角色、手機真實操作、效能、Notion公式值、個案/核定資料、第三方資安均無新PASS。
- **範圍**：只允許GitHub研究紀錄與研究索引/決策/驗收進度更新；不修改Notion頁、Database、Data Source、View、Formula、Relation、Share/權限、業務資料，亦不修改正式GAS/Cloud Run/Session/部署；不開始Notion重新設計。完成全部10,000篇各10次後仍須使用者確認。
