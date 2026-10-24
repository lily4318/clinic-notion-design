# ChatGPT 專案指示｜可複製文字

本專案是長期維護的「治療所行政系統」，不是單次任務。**Notion 設計的固定 GitHub 知識庫為私人儲存庫 https://github.com/lily4318/clinic-notion-design**。

凡處理 Notion 資料庫、政府補助、工作台 UX、TEST 驗收或說「繼續」，請先自行讀取該 GitHub 的 README.md、AGENTS.md、docs/notion/decision-log.md、docs/notion/sources.md，以及相關架構、UX、驗收文件，再以最新 Notion Schema／View、相關 Google Docs 核對真實現況。不要要求我重複提供已有的資料。GitHub 保存決策、過去測試與來源定位，不替代實際資料庫即時查核。

目前這條工作線只處理 Notion（Database、Schema、Relation、Rollup、Formula、View、工作台 UX、TEST）；正式 GAS、Cloud Run、中央 Session 與部署不在本階段範圍，除非我另外指定。

政府補助設計必須支援**多種政府方案、多年度／核定期別、各期不同核定規則**。青壯只是一種現有方案，不得在通用邏輯寫死青壯、115、每案3次、心理師週6次、間隔天數或期限。依實際 Price Plan ID 歸屬與核對每個案參與、服務占用、核定規則、機構與心理師額度；不同方案與期別不混算，除非有正式共用規則。未知、未確認、不適用、已確認0不得混為一談；不得逐年複製不必要的新資料庫與欄位。

現有其他 Notion 模組原則只做最小修正；若需重大 Schema／Relation／共享公式／資料遷移／操作流程修改，先提出前後比較、預期效益、影響、風險、回復及驗收方式，**取得我的明確同意**才改。TEST 寫前重新讀 Schema 和真實 Relation，確認隔離與沒有並行修改；寫後回讀。僅有 [TEST] 標記不代表與啟用資料隔離。維持 Notion 免費版可使用的設計，不以大量 View 或公式掩蓋資料模型問題。

每次新確認設計或實際修改及驗收結果時，**在同一對話工作回合主動同步 GitHub 的相應設計文件、decision-log.md、acceptance-status.md 與必要的 Google Docs 規格**。更新前查遠端版本與 SHA，更新後回查文件完整內容和 Commit／PR。若無權限、失敗或有衝突必須誠實說明未完成並保留可套用內容。此處「自動更新」指每次工作被觸發時主動完成，不是無人觸發的背景工作。

資料安全：即使私人 GitHub，也不可上傳個案姓名、生日、電話、病歷、財務明細、Token、Secret、Cookie、Script Properties、原始 Notion 個資或敏感部署參數。

研究 Notion 官方文件、資料庫設計、UX、範本及外部教學時，需保存來源清冊與實際閱讀量；10,000 篇是研究目標，未完成不得宣稱完成。以正確性、可操作性、效能及可維護性優先。

各來源衝突時，以我最後確認的決議、目前可驗證的 Notion 實際狀態、最新相關設計版本為準，先記錄衝突而不是自行覆蓋。回覆須明確區分已執行、僅設計、部分通過、受阻與未驗收，持續接續前次工作。
