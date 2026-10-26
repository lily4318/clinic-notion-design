# AUTO-32｜分頁與狀態回饋：Notion 治療所行政系統研究取證
- 日期：2026-10-26（Asia/Taipei）；執行軌跡：`AUTO-32-20261026-2340-RESEARCH`
- 範圍：僅閱讀外部資料及 GitHub 研究/進度記錄。**禁止**更改 Notion 正式或 TEST Page、DB、Data Source、View、Formula、Relation、權限、業務資料，亦不修改 GAS、Cloud Run、Session 或部署；尚不開始重新設計。
- 前置：重讀 main 的 README、根 AGENTS、docs/system/source-of-truth、docs/notion/AGENTS、sources、decision-log、acceptance-status；來源索引及 GitHub repository code search 查無下列兩個 slug。此僅是**已查清冊初步去重**，不是跨所有歷史檔案的全域唯一性證明。
- 閱讀標準：兩篇均透過可讀原文頁逐節查看**主要文字、圖說、結論**並各做一次新的反例分析；未逐張開啟全部圖片、實測互動或進行十次獨立完整閱讀，故僅記 `R1_MAIN_TEXT+COUNTEREXAMPLE`，**FULL_DEEP_PASS=0**。

## AUTO32-S01｜Tabs, Used Right
- 原文：https://www.nngroup.com/articles/tabs-used-right/
- 作者：Evan Sunwall；發布 2024-08-02；最後審閱 2026-09-02；canonical `nngroup:articles/tabs-used-right`；閱讀 ID `AUTO-32-20261026-2340-RESEARCH:S01:R1`。
- 已讀正文：What Are Tabs?；When to Use Tabs；Tabs Versus Accordions；Types of Tabs（導航分頁 vs 頁內分頁）；Tab Visual Design（選取指示、未選標籤可見、與面板鄰近、單列、面板上方）；Tab Content（高頻預設、資訊分組、簡短標籤、可發現性、可及性）及結論。已讀圖說文字，但沒有逐張開啟原始示例圖。
- 原文觀察：分頁會隱藏非當前內容；若需要跨組同時比較資料，來回切換反而增加工作記憶與操作成本。導航分頁與頁內分頁不能混用行為。預設分頁有顯著注意力優勢，非預設分頁不宜藏完成任務所必需的關鍵資訊。分頁列過長、選取狀態不清、鍵盤焦點不可見，都會損害可用性。
- **獨立反例／對治療所情境的反證**：若把「心理師本週用量」與「個案補助剩餘」放在不同 tabs，櫃台在安排同一筆會談時必須反覆切換才能同時確認兩項條件，違反使用者已確認的「同頁直接看資料」。相反，將所有歷史報表也強制攤開會拖長首頁並使低頻資訊淹沒高頻工作；所以「所有內容永遠同屏」同樣不是普遍正解。分頁是否適用須依同時比對任務，而非僅看資料量。
- **未證實限制**：NN/g 一般 tabs 指南不能當作 Notion 既有 Saved View 的實際切換/權限/載入表現；也不授權重排已核准的補助頁。手機/鍵盤/真人操作未測。原文定位：When to Use Tabs、Types of Tabs、Tab Visual Design、Tab Content。

## AUTO32-S02｜Indicators, Validations, and Notifications: Pick the Correct Communication Option
- 原文：https://www.nngroup.com/articles/indicators-validations-notifications/
- 作者：Kim Flaherty；發布 2024-01-17；canonical `nngroup:articles/indicators-validations-notifications`；閱讀 ID `AUTO-32-20261026-2340-RESEARCH:S02:R1`。原文 URL 中的 `lm`/`pt` 追蹤參數已剔除，不另計文章。
- 已讀正文：Communicating System Status、Indicators、Validations、Notifications、Picking the Right Communication Option Is Important、Conclusion；並核對文內圖片說明，未逐張開原始圖。
- 原文觀察：Indicator 是與特定元素鄰近的條件性、被動提示；Validation 是針對剛輸入的錯誤、需要使用者修正；Notification 是系統事件通知，可能需要動作也可能被動。資訊類型、急迫性、是否需要動作，應決定回饋機制。短暫 toast 不適合承載需要使用者修正的關鍵錯誤；不相干的全域通知可能干擾當前任務。
- **獨立反例／對治療所情境的反證**：「資格尚未核對」是尚待人工判定的業務狀態，不能直接標成輸入錯誤 Validation；「核定期別已到期」若與當前排程直接相關，不能只在數秒後消失的 toast 中提示；「已確認為零」則不能用紅色錯誤樣式誤導為系統故障。但把每個待核對項目都做成強制彈窗，又會妨礙日常收款和排程，造成警告疲勞。需要區分狀態、真正錯誤、急迫事件三種語義。
- **未證實限制**：這是一般 UX 設計研究，不保證 Notion 原生可精確配置通知或欄位驗證，也不是授權新增警告 Callout（使用者曾否決冗長提示）。真實 Notion 通知、方案權限、跨角色/手機未測。原文定位：Indicators、Validations、Notifications、Picking the Right Communication Option。

## 本輪去重、閱讀深度與狀態
| 指標 | 本輪 | 嚴格累積 |
|---|---:|---:|
| 新 canonical 候選（已查清冊） | 2 | 全域精確唯一總數待稽核 |
| 主要正文獨立 R1 閱讀 | 2 | 不當作 FULL_DEEP |
| 首次獨立反例分析 | 2 | 不重複計次 |
| 既有來源完整 R2–R10 | 0 | — |
| FULL_DEEP_PASS_10_OF_10 | 0 | **0／10,000篇** |

- **未完成**：圖片原圖逐一檢視、影音/互動、Notion真實操作、手機/角色權限、效能、補助原生公式與核定真值、每篇十次可稽核完整深讀、全域來源去重。
- 研究假說不構成設計決議。尚未完成10,000篇各10次深讀及使用者確認，**不得進入 Notion 重新設計**。
