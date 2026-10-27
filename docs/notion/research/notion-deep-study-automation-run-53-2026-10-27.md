# AUTO-53｜2026-10-27｜Check answers 與 Task list：提交前核對和跨階段工作狀態（純研究）

- Trace：`AUTO-53-20261027-2041-RESEARCH`；台灣時間 2026-10-27 20:41 起始。本輪授權**只限外部公開研究與 GitHub 進度記錄**，未授權 Notion 重新設計或正式系統操作。
- 先重新讀 main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md；讀 research/README.md、原始證據登錄表、batch-02/03/04、MANUAL-01、十面向研究、前輪 AUTO-52；另查研究目錄路徑清單。
- 研究目錄起始列出 **64 份 Markdown 文件**（包含研究 README 與既有 AUTO-01～52）。已檢索 sources.md 全文、七份早期清冊與 GitHub code search，兩個新候選的完整 URL／canonical slug 未命中；嘗試逐檔抓取全研究目錄時遭工具呼叫上限中斷，**不可宣稱64/64全文去重**；同文異址、其他未索引路徑仍未完成全儲存庫精確去重。兩篇僅列「已查索引新來源候選」，不視為已全域去重。
- 閱讀層級：兩篇各一次公開主要正文文字、範例 HTML/Nunjucks 與適用限制閱讀；官方獨立示例頁已開啟並確認可讀。**未實際用瀏覽器點擊互動、鍵盤／讀屏測試、逐張核對原圖、讀完所有外部研究連結，也未在真實 Notion 測試**。故標為 `R1_MAIN_TEXT_PARTIAL`，不是完整 `DEEP_PASS`；未執行獨立 R2～R10。

## AUTO53-S01｜Check answers – GOV.UK Design System

- 原文：https://design-system.service.gov.uk/patterns/check-answers/
- 示例：https://design-system.service.gov.uk/patterns/check-answers/default/
- 標題：Check answers – GOV.UK Design System；維護者：GOV.UK Design System team；首次發表日期未核實。
- Canonical：`govuk-design-system:patterns/check-answers`；本輪唯一閱讀標記：`AUTO53-S01-R1-MAIN-TEXT-C1`。
- 實際閱讀範圍：頁面用途、完整 HTML 與 Nunjucks 摘要清單／變更連結／送出按鈕範例；何時適合（小至中型交易的送出前單一核對頁，超大型可分段）；版寬、欄位分組、只顯示相關區塊；明確區分「資料已填」與「交易已送出」；修改欄位後回到核對頁、保留先前填寫、非必填項以 Not provided 表示；官方指向 Carer's Allowance 使用者研究但該外部全文未納入本次深讀。
- 可支持的設計原則：送出前給第二次發現錯誤的機會；修改動作應能返回原核對上下文；送出按鈕名稱應對應真正動作；頁面不應宣稱交易已完成。
- **反例 A（Notion 自動儲存）**：若治療所行政人員修改 Session 的服務日期、收費方案或期別時，Notion 欄位已即時保存，事後再顯示「提交前檢查」不能被當成資料庫尚未寫入的原子交易；核對頁可能只是事後檢查，無法保證撤銷。不能照搬 GOV.UK 交易流程而假設 Notion 原生有提交／回滾。
- **反例 B（歷史資料與計算變動）**：核對頁即使顯示當下金額，也不保證 Relation／Rollup／公式稍後不變。歷史 Session 應有獨立的業務金額證據與日期/期別核對，但此為研究風險推論，尚未取得產品能力與業務核可，**不得據此擅自新增快照欄位**。
- **反例 C（高頻負擔）**：若每次日常 Session 建立都被迫穿過完整審核頁，可能降低效率並增加忽略確認的習慣；是否需要核對頁應以交易不可逆性、風險與真人操作測試決定，而非一律套用。

## AUTO53-S02｜Task list – GOV.UK Design System

- 原文：https://design-system.service.gov.uk/components/task-list/
- 示例：https://design-system.service.gov.uk/components/task-list/default/
- 標題：Task list – GOV.UK Design System；維護者：GOV.UK Design System team；官方變更表記載元件於 **2023-12** 引入、2024-08 修正空內容列（不是本文首發日）。
- Canonical：`govuk-design-system:components/task-list`；本輪唯一閱讀標記：`AUTO53-S02-R1-MAIN-TEXT-C1`。
- 實際閱讀範圍：HTML/Nunjucks 任務清單範例、使用/不使用條件、可自行決定順序的長流程、短標籤與單句提示、整列可點擊與狀態呈現、分組、官方使用者研究、Known issues/gaps 與近期變更。
- 官方限定：只有使用者確實無法一次完成、且需自由決定工作順序時才優先考慮；若流程必須按固定順序或可先簡化，不應機械套用。狀態標籤不應誤當按鈕；官方也承認整列可點擊與誤觸的取捨尚待更多測試。
- **反例 A（行政流程誤套）**：治療所「新方案／新核定期別的跨人員資料蒐集」可能需要跨日、可跳步工作清單；但每次高頻 Session 收款或排班若都被拆成多個任務，可能徒增跳轉與重複操作。
- **反例 B（完成≠核准）**：資料已上傳、人工已檢查、補助資格已核准、款項已收妥屬不同證據層級。若任務狀態 Completed 被解讀為政府資格核准，可能產生錯誤請款；不能用前端標籤取代實際核定證據。
- **反例 C（整列可點擊與Notion原生限制）**：官方任務列連結、焦點與狀態語意並不代表 Notion Linked View 或資料庫頁可原樣實現；整列導覽可能讓需要同頁核對多筆歷史資料的人員被迫跳頁，且需測試誤觸風險。

## 交叉反證、驗收邊界及計數

- Check answers 是**送出前資料核對**，Task list 是**跨步驟任務完成狀態**。兩者不能相互替代：完成所有資料蒐集任務不代表歷史收費金額正確，更不等於已提交或已取得補助核准；送出前核對也不能替代多日協作進度追蹤。
- 本輪成果：已查索引新來源候選 **2**、主要正文文字閱讀 **2**、首次獨立反例分析 **2**、既有來源完整複讀 **0**、本輪完整 R1 **0**、完整 R2–R10 **0**、新增完成十次嚴格深讀 **0**；累積可稽核 `FULL_DEEP_PASS_10_OF_10` **0／10,000篇**。
- **NOT_TESTED**：全儲存庫同文異址去重、原始圖像逐張、真實互動／讀屏／手機、Notion 原生核對或任務列能力、不同角色權限、載入速度、補助資格/收費公式/歷史 Session 真值；研究推論不是已實作功能或業務 PASS。
- **NO NOTION/SYSTEM WRITE**：本輪只允許 GitHub 研究紀錄及來源／決策／驗收進度。Notion 正式與 TEST Page、DB、Data Source、View、Formula、Relation、權限、個案/財務資料，正式 GAS、Cloud Run、Session、部署均不修改；研究門檻未達，不進入 Notion 重新設計。
