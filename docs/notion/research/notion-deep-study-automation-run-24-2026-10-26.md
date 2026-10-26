# Notion 深度學習｜AUTO-24（2026-10-26；僅研究）
- trace: `AUTO-24-20261026-1544-RESEARCH`
- 範圍：僅公開來源閱讀、反例分析、GitHub 研究證據與進度索引；不得更動任何 Notion 正式/TEST 頁、DB、View、Formula、Relation、權限、業務資料或 GAS/Cloud Run/Session。
- 開始前已重新讀取 main 的根 README/AGENTS、docs/system/source-of-truth、docs/notion/AGENTS、sources、decision-log、acceptance-status；列出 research 目錄，查閱首批、批次02–04、十面向、MANUAL-01、AUTO-01～23 研究清冊。兩個下列 slug 在所核對清冊中未見已登錄；全域去重仍保留待稽核，不把搜尋命中當作閱讀。
- 閱讀方法：實際開啟原始官方頁，按各正文標題逐節閱讀；本輪每篇只執行一次 R1 主文字研讀與一次獨立反例分析。沒有逐圖檢查、觀看所有嵌入影片或真實帳號操作；不列為 FULL_DEEP_PASS，亦不冒稱十次閱讀。

## AUTO24-S01｜Give your to-dos a home with Task databases
- URL: https://www.notion.com/en-gb/help/guides/give-your-to-dos-a-home-with-task-databases
- canonical ID: `notion-help:guides/give-your-to-dos-a-home-with-task-databases`（語系 /en-gb 不構成另一篇）
- 作者／類別：Notion Help 官方指南；頁面標示 3 min read；實讀日期 2026-10-26；發表/修訂日期未見可核實。
- 閱讀 R1：已逐節核對 `How to set up your My Tasks page`、`Customize your My Tasks page`、`How to use My Tasks`、`Optimize your databases for My Tasks` 及其三個子節。正文約網頁行106–196（另有導航、範本/圖片，未算獨立文獻）。文字證據：Task DB 需 Status/Assignee/Due date；My Tasks 最多連接10個Task資料來源；跨庫彙整可更新任務、切換Board/Calendar、篩選排序；建議整合任務資料庫並以Relation串專案；與外部夥伴共享時官方另明示須使用 row/page-level permissions。
- 假設 H1：把所有業務紀錄統一改為Task DB、以My Tasks作唯一入口即可兼顧簡潔與可見性。
- 反例 C1：非任務的政府補助額度、個案資格、收款/核銷紀錄缺少任務語義；強制加入Assignee/Due date可能產生誤導性欄位，且My Tasks最多10來源，不能保證所有行政資料呈現。將跨個案資料放在同一共享DB，再用「篩選檢視」分給不同外部夥伴，若沒有頁面層級權限，篩選本身不能視為保密邊界。
- 修正 D1：將My Tasks視為「已授權任務」的個人彙整入口候選，不取代同頁可見的政府方案用量/服務歷程；是否轉Task DB及外部存取須另經使用者核准、實帳權限與真人UX測試。本輪僅研究不提出實作。
- 未驗：所有插圖、畫面互動、手機差異、付費/免費方案下實帳顯示、外部訪客權限、載入速度；R1僅BODY_MAIN_AND_COUNTEREXAMPLE，FULL_DEEP_PASS=NO。

## AUTO24-S02｜Enterprise Search
- URL: https://www.notion.com/en-gb/help/enterprise-search
- canonical ID: `notion-help:enterprise-search`
- 作者／類別：Notion Help 官方文件；實讀日期 2026-10-26；發表/修訂日期未見可核實。
- 閱讀 R1：已逐節核對 `Where to find Enterprise Search`、`Specify pages or people`、`Connect your third-party apps`、`Change the scope of your search`、`Switch between AI models`，及方案限制提示。正文約網頁行106–166。官方指出此功能為 Business/Enterprise 方案；可在 Notion/已連接應用/網路間切換搜尋範圍，可限定來源，搜尋回答提供來源引用；模型選擇可能影響是否實際使用工作區內容。
- 假設 H2：AI 搜尋會自動理解所有治療所資料且能直接代替日常資料表與補助核定查核。
- 反例 C2：免費/Plus 方案不具有該文件所述的 Business/Enterprise 功能保證；跨連線資料及 Web search 的預設混合來源可能令答案來自非核定依據，來源引用不等於額度計算正確、資料可被授權揭露或已同步至最新業務狀態。官方還提醒不同模型可能只看網頁內容，不能保證查到工作區資料。
- 修正 D2：Enterprise Search 只能列為需額外費用與存取權限評估的「查找輔助」候選，不能作為唯一行政入口、業務權威資料庫或自動核准補助機制；即使有引用也須回到原始業務資料/正式規則核對。本輪未啟用任何AI連線。
- 未驗：影片、所有圖片、跨連線/模型真實行為、搜尋資料範圍權限、真人帳號與方案成本；R1僅BODY_MAIN_AND_COUNTEREXAMPLE，FULL_DEEP_PASS=NO。

## 去重、計數、稽核與邊界
- 本輪兩個 canonical URL 在已取得的研究清冊及 AUTO-01～23 文件中未發現重複，暫列「新增去重來源2」，並保留全域完整機器去重未完成的限制；沒有把多個主題、圖片、範本或相同URL語系算作另一篇。
- 本輪：新URL 2；可讀主要正文 R1 2；獨立首次反例 2；舊來源針對性複讀 0；逐篇完成十次嚴格完整深讀 0。
- 累積可核實 FULL_DEEP_PASS (10/10) 仍 0/10,000。沒有十次獨立閱讀、逐圖/影片及實帳驗證，不能進入 Notion 重新設計；須待目標達成後通知使用者確認。
- 研究觀察≠本所現行Notion/公式/權限/效能驗收。未讀取或修改任何真實個案、金流、部署密鑰。
