# AUTO-50｜2026-10-27｜GOV.UK Summary list 與 Tag：研究文字取證及反例

- Trace：`AUTO-50-20261027-1738-RESEARCH`（本輪唯一標記）。
- 授權範圍：僅公開來源研究及 GitHub 進度紀錄；不修改 Notion、GAS、Cloud Run、Session 或部署。
- 啟動前讀取：main 的根 README、AGENTS、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、decision-log.md、acceptance-status.md；另查 Git tree main 的研究清冊，當時有 62 個 research Markdown 路徑。已查 sources.md 未含下述兩個完整 URL；嘗試逐檔研究全文去重時工具呼叫額度中斷，**未能證明 62/62 完整去重，也未能排除同文異址**。
- 原文可讀取日期：2026-10-27（網頁擷取顯示當日）。本輪為不同於既有 NN/g 批次的 GOV.UK 官方元件指南。
- 計量：兩篇**已查索引新候選**；各一次主要文字閱讀與首次獨立反例分析（不計完整 R1 或 R2）；10/10 完成新增 0，累積可核實 0／10,000。不可將不同段落或多種反例重複計數。

## AUTO50-S01｜Summary list
- 標題：Summary list – GOV.UK Design System
- 原始 URL：https://design-system.service.gov.uk/components/summary-list/
- Canonical identity：`govuk-design-system:components/summary-list`
- 出版／維護：GOV.UK Design System team；本輪未取得可核實的首次發表日期，**不填猜測日期**。
- 閱讀軌跡 `AUTO50-S01-R1-MAIN-TEXT-C1`：實際取得官方頁面並閱讀用途、禁用情境、key/value 結構、無 actions 變體、summary cards、卡片標題、research on this component 與下一步；HTML/Nunjucks 範例只閱讀文字與主要結構，**未逐行驗證全部程式碼，也未逐張檢查所有圖片**。
- 原文要點：summary list 是呈現一個對象的標籤—值摘要，可用於表單最後的核對；不應用來替代跨列比較的 tabular data，也不適合單純待辦清單。多個同類對象可用 summary cards，卡片標題需具識別性，資料量少時不必額外卡片化。官方承認仍需更多研究判斷何時適用。
- 治療所反例 A：若把多筆 Session 的「服務日期／方案期別／收費金額」全部拆成一張張摘要卡，可能失去跨 Session 的欄列比較能力，且在手機上需要反覆捲動；若只看單筆 Session 的重要屬性，key/value 摘要才可能有幫助。**反證了「卡片比表格更直覺」的過度推論**。
- 反例 B：若 summary card 的整體「修改」操作與逐欄「修改」操作不清楚，使用者可能以為只更動一個欄位，卻更動整個補助參與記錄。若只呈現「可用餘額」而未顯示核定期別及人工資格狀態，摘要會產生假安全感。
- 推論與界線：僅提出資訊呈現與權限可見性的研究假說；不代表 Notion 原生支援 GOV.UK summary-list 元件，也沒有授權建立新 View 或修改既有資料庫。
- 待補：所有原始示例逐張檢視、輔助技術可及性、Notion 原生可行性、真實行政人員跨期核對測試。

## AUTO50-S02｜Tag
- 標題：Tag – GOV.UK Design System
- 原始 URL：https://design-system.service.gov.uk/components/tag/
- Canonical identity：`govuk-design-system:components/tag`
- 出版／維護：GOV.UK Design System team；原始發表日期未核實。頁面「Recent changes」明載 2026-02 品牌色更新，不能把更新日期當首次發表日期。
- 閱讀軌跡 `AUTO50-S02-R1-MAIN-TEXT-C1`：取得官方頁面並閱讀用途、何時用、狀態數量、tag 不可作連結/按鈕、形容詞命名、顏色與 WCAG 2.2 1.4.1、研究與更新紀錄。HTML/Nunjucks 表格程式碼未逐行核驗，原圖未全部獨立驗證。
- 原文要點：Tag 用來表達狀態，不應假裝可點擊操作；狀態種類先從最少的可用集合開始；顏色不能作唯一資訊通道，同一狀態跨頁顏色應一致。官方記載過去深色標籤被誤認為按鈕，2026-02 又更新對比與樣式。
- 治療所反例 A：把「待人工核對」「核定資格不符」「尚未收款」「資料同步待驗證」統一用一個黃色 Tag，雖減少狀態種類，卻把不同責任與後續處置混成一種狀態；反之將每個技術細節都變成狀態又會造成辨識負擔。
- 反例 B：將「資格待核對」標籤做成點擊即可核准的操作，可能使人誤以為只是查看狀態，實際卻觸發不可回復的資料變更；**狀態呈現與高風險操作應區分**。但僅改顏色/文字不會修復資料庫中的錯誤資格判定。
- 反例 C：如果只靠紅黃綠色表示「已核准／待核／不適用」，色覺差異或跨 View 色彩設定可能造成錯讀；需可見文字語意，且 Notion 實際可用控制與權限另行驗證。
- 推論與界線：這是 GOV.UK Web UI 指引，不是 Notion 原生 Tag/Status 的功能保證，不可直接據此改 Notion。
- 待補：原圖、可及性與鍵盤/螢幕閱讀器驗證、真實 Notion Status/Select/Formula 顯示限制、不同角色實測。

## 去重／品質／進度
- 來源 URL 正規化：移除追蹤參數、保留上述官方 canonical 路徑；不同標題或分析面向不增加來源數。當前 sources.md 全文未見上述完整 URL；研究目錄逐檔掃描曾嘗試但工具呼叫上限中斷，**僅列候選，不宣稱全儲存庫去重 PASS**。
- 主要文字閱讀每篇 1 次，獨立反例各 1 組；這是 `R1_MAIN_TEXT_PARTIAL`，**非完整深讀**，不計 10 次中的任何完整輪次。
- `FULL_DEEP_PASS_10_OF_10`：本輪新增 **0**，累積可核實 **0／10,000**；全庫唯一來源總數仍待稽核。
- 未驗收：Notion 真實工作區、手機、角色權限、View/Formula/Relation、補助核定與歷史收費真值、效能、所有圖片/影片/互動；研究結論不等於業務系統驗收。
- NO NOTION/SYSTEM WRITE：只在 GitHub 建立/更新研究與進度記錄；未開始 Notion 重新設計。雙軌續作仍可並行，任何後續 GitHub 共同檔案更新都必須重讀最新 SHA 條件寫入。
