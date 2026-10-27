# AUTO-52｜2026-10-27｜GOV.UK Details 與 Warning text：公開原文閱讀與反例（僅研究）

- Trace：`AUTO-52-20261027-1937-RESEARCH`；本次僅公開研究及 GitHub 進度記錄；**未授權 Notion 重新設計或任何正式系統寫入**。
- 先讀 main：根 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、sources.md、decision-log.md、acceptance-status.md、research/README.md、前輪 AUTO-51；另核對 evidence-register、batch-02/03/04、manual-01、10-lens 與研究進度清冊。
- 研究目錄 git tree 在本輪開始列出 **63 份 Markdown**；本輪未逐檔讀取全部63份，**不能聲稱63/63全文去重**。sources.md全文、上述早期清冊及 repo code search 對兩個 canonical slug 均未命中；同文不同URL、未索引路徑仍未完成全庫精確去重，故兩篇暫列「已查索引新候選」。
- 兩篇各一次主要正文、HTML/Nunjucks範例與官方變更紀錄閱讀，外加一次獨立反例分析；**不是完整 R1 深讀**，沒有獨立 R2–R10；不將不同分析角度或兩次抓取同頁當成多次閱讀。

## AUTO52-S01｜Details – GOV.UK Design System
- 原文 URL：https://design-system.service.gov.uk/components/details/
- 例子 URL：https://design-system.service.gov.uk/components/details/default/
- 標題：Details – GOV.UK Design System；維護者 GOV.UK Design System team；首次發表日未核實。頁面變更紀錄載有 2024-10 修正 iOS 展開狀態宣告及邊距，**此為修改日期而非首發日**。
- Canonical：`govuk-design-system:components/details`；閱讀證據：`AUTO52-S01-R1-MAIN-TEXT-C1`。
- 本輪實際閱讀：頁面目的；何時使用／不使用；Details、Accordion、Tabs 之間的選擇；單段內容的適用性；短且描述性的展開標籤；HTML `details/summary` 與 Nunjucks 範例的可見文字與語意；官方提及部分使用者以為展開連結會離開頁面，以及語音輔助操作可能遇到名稱／角色辨識問題；近期變更表。已打開官方獨立例子，確認其文字內容；**未用實際瀏覽器點擊、鍵盤／讀屏測試或逐項核對所有歷史修訂**。
- 官方原則：只把「部分使用者才需要」的輔助內容放入 Details；大多數使用者都需要的內容不應藏起。只有一段次要內容時比 Tabs/Accordion 更合適；展開標籤應清楚說明內容。
- 反例 A：如果把「歷史 Session 收費金額與期別不一致」或「補助資格待人工確認」放入預設收合的說明，工作者可能看不到關鍵異常；收合能減少首屏字數，但不等於提升業務正確性。
- 反例 B：如果把每個補助方案的低頻填寫指引全部展開，可能讓同頁必看的服務日期、歷史金額、額度表更難同時掃描。應依**當下任務是否必需**而非字數長短決定是否收合。
- 反例 C：Notion 原生 Toggle 或頁面區塊不能假設等同 GOV.UK `details` 的鍵盤、ARIA、語音與展開宣告；需要後續真實產品和不同使用者驗證。以上僅設計推論，不是已核准方案。

## AUTO52-S02｜Warning text – GOV.UK Design System
- 原文 URL：https://design-system.service.gov.uk/components/warning-text/
- 例子 URL：https://design-system.service.gov.uk/components/warning-text/default/
- 標題：Warning text – GOV.UK Design System；維護者 GOV.UK Design System team；首次發表日未核實。頁面列出 2024-10、2024-04、2023-12 等元件修訂，不能視為首次發表日期。
- Canonical：`govuk-design-system:components/warning-text`；閱讀證據：`AUTO52-S02-R1-MAIN-TEXT-C1`。
- 本輪實際閱讀：警示的用途（重要後果，如未行動的法律風險）；HTML 及 Nunjucks 範例；`!` 圖示配合 `aria-hidden`，另外以 visually-hidden 的「Warning」作為非視覺文字；隱藏文字可因情境調整；2023–2024 對隱藏文字、強制配色及字重的修改。已打開官方獨立例子，核對可見警告文字；**未實際用讀屏／高對比模式／Notion 測試**。
- 官方原則：重要行動或不行動後果值得顯著警示；圖示本身不是可供所有人理解的唯一訊息，需可辨識的文字。
- 反例 A：治療所若以驚嘆號警告「補助資格已失效」，但只是「尚待人工確認」，會把未知誤呈為已判定；對歷史 Session 的真實收費或資格造成誤導。**狀態證據不足時不能用確定語氣警告**。
- 反例 B：若每一個日常欄位都套用強烈警告，真正的日期／期別不符、可能超額或法律告知會淹沒在警示疲勞中。應區分待核、一般提醒、可驗證的高後果警示；但這些分類目前只是研究推論，未取得本所業務核可。
- 反例 C：GOV.UK 的 CSS/ARIA/隱藏文字方案不代表 Notion 可原樣實現；不能宣稱 Notion 具有等效的無障礙語意或自動驗證能力。

## 交叉反證與嚴格進度
- Details 適合非必要的輔助解釋；Warning text 用於確有重要後果的訊息。兩者與 AUTO-51 的 Notification banner、Error summary 是**不同目的**：當前任務的核心待核狀態不宜藏在 Details，也不能用「系統成功」或紅色警示替代業務證據。
- 研究推論不得直接轉成 Notion 新欄位、公式、View 或頁面改版；本輪沒有進行任何產品測試、資料模型修改或正式核定。
- **本輪計數**：已查索引新 canonical 候選2；可讀主要正文文字2；首次獨立反例2；完整 R1=0、完整 R2–R10=0、完成10/10=0；累積可核實 `FULL_DEEP_PASS_10_OF_10` **0/10,000篇**。
- 未驗：全庫同文異址去重、所有原始圖像、動態互動、外連討論全文（GitHub 討論連結讀取逾時）、真實 Notion 原生元件、手機、鍵盤／讀屏、角色權限、載入效能、歷史 Session 金額與補助資格真值。
- **NO NOTION / SYSTEM WRITE**：只在 GitHub 記錄研究，不修改任何 Notion Page、Database、Data Source、View、Formula、Relation、權限、個案／財務資料，也不修改 GAS、Cloud Run、Session、部署。研究未達標，未開始重新設計。
