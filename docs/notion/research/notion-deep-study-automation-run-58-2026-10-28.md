# AUTO-58｜2026-10-28｜欄位錯誤訊息與單行輸入的設計邊界（純研究）

- Trace：`AUTO-58-20261028-0141-RESEARCH`；台灣時間 2026-10-28 01:41 開始；自動續作，僅公開資料與 GitHub 研究紀錄。
- 開始前重讀 main：`README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`；另讀 `research/README.md`、audit-checklist、原16筆、batch-02/03/04、MANUAL-01、十面向研究、AUTO-57，並列出 research 目錄。當時共 69 份 Markdown（包括本批新增前）。
- 去重：`sources.md` 全文、研究基線/批次清冊、GitHub code search 及 AUTO-01～08 的逐檔檢查未找到下列兩個 canonical URL。嘗試對全部 research 目錄逐檔查重，但單次工具呼叫上限中止；**沒有完成全部歷史文件的精確去重與同文異址比對**，兩篇只算「已查索引新來源候選」，不算全庫已去重唯一篇數。
- 研究方法：實際開啟兩個 GOV.UK 官方網頁，按章節閱讀主要文字、HTML/Nunjucks 示範、錯誤狀態、使用與不使用條件、已知限制及更新紀錄。原圖、互動頁、鍵盤/讀屏、手機、Notion原生實帳均未測；故僅 `R1_MAIN_TEXT_PARTIAL`，**不是完整 R1 DEEP_PASS，亦不是 R2–R10**。

## AUTO58-S01｜Error message – GOV.UK Design System

- URL：https://design-system.service.gov.uk/components/error-message/
- canonical identity：`govuk-design-system:components/error-message`；維護者 GOV.UK Design System team；頁面首發/最後修改日未核；本次存取 2026-10-28。
- 獨立閱讀記號：`AUTO58-S01-R1-MAIN-TEXT-C1`（正文部分，非完整深讀）。
- 實際覆蓋：原文約第52–385行；何時使用/不使用、欄位旁錯誤及頁首 error summary 一致、保留使用者已輸入的內容、紅框與欄位關聯、讀屏隱藏 Error 前綴、多語系前綴、legend/label 示例、訊息應指出哪個欄位如何修正、空值/格式/長度應用不同訊息。HTML/Nunjucks 範例均有查閱，未實際執行。
- **初始假設**：所有待處理行政異常都可顯示為欄位紅色錯誤，迫使人員立即修正。
- **反例1（不能由操作者修正）**：政府資格回覆尚未取得或上游補助額度同步失敗時，這不是使用者輸入格式錯誤；若標成「資格輸入錯誤」或要求立即選擇符合/不符合，會將未知偽造成已判定。官方明確不建議把資格不符、權限不足或服務端故障當作欄位錯誤。
- **反例2（真實資料衝突）**：補登歷史 Session 時，服務日期與收費方案期別矛盾，可能是選錯關聯，也可能是舊資料或方案規則待人工查證。若一律指示「改成最新期別」，會破壞歷史計費。應先區分可由輸入者立即修正的格式/必填錯誤、業務待核狀態與系統故障；保留原輸入供追溯但不能因此忽略敏感資料顯示風險。
- **交叉反證**：AUTO-51 的 Error summary 適合彙整已確認的欄位驗證錯誤，但它不提供業務真相或核准權限；此篇是不同元件與不同 canonical URL，不能把兩篇當同一篇重讀。
- **未驗**：Notion Formula 是否能給出相同焦點、ARIA 與欄位級提示；真人對「待核對」的理解與錯誤修正率。

## AUTO58-S02｜Text input – GOV.UK Design System

- URL：https://design-system.service.gov.uk/components/text-input/
- canonical identity：`govuk-design-system:components/text-input`；維護者 GOV.UK Design System team；頁面首發日未核；2026-06 官方 Recent changes 提及 decimal inputmode 與前後綴對比度修正；本次存取 2026-10-28。
- 獨立閱讀記號：`AUTO58-S02-R1-MAIN-TEXT-C1`（正文部分，非完整深讀）。
- 實際覆蓋：原文約第52–982行；單行與多行用途、可見 label 與 placeholder 的差異、固定/流動寬度、hint 簡短、整數與小數 inputmode、`type=number` 的誤捲動風險、識別碼字距、幣別前後綴、autocomplete、複製貼上、maxlength 截斷、spellcheck、錯誤文案及更新紀錄。部分長篇 HTML/Nunjucks 只是結構性查閱，未操作實例或延伸研究影片。
- **初始假設**：對於 Session 金額、服務識別碼與方案名稱，統一使用文字輸入即可提升填寫速度。
- **反例1（文字欄不等於正確關聯）**：若允許直接鍵入方案名稱「青壯115」而不是確認對應的 Price Plan 期別 ID，名稱相似或跨年同名會令歷史 Session 錯誤歸屬。文字輸入可適合搜尋，但不等於業務唯一鍵、關聯或有效期驗證。
- **反例2（數字語義不同）**：Session 收款金額可含小數/負調整/千分位，識別碼可能有前置零；將所有欄位改為 HTML number input 或直接截斷字數，可能讓前置零消失、意外改數字、剪貼時無提示截斷。不同欄位需要分別確認格式與驗證，但 Notion 原生 Number/Title/Relation 的實際行為不能由 HTML 範例推定。
- **反例3（autocomplete 與隱私）**：官方一般建議用 autocomplete 減少重填；但在共用行政裝置或涉及個案資訊時，瀏覽器自動填寫也可能增加跨個案帶錯資料或資訊暴露的風險。是否採用須以設備、權限、敏感度與真實工作流程評估，不能直接照搬公共網站範例。
- **交叉反證**：Text input 的錯誤樣式與 S01 Error message 相互引用，但一篇是輸入控制、一篇是錯誤語義；兩篇各自只有一次主要正文閱讀，不能因交叉比較額外計一次。
- **未驗**：原圖、互動、手機鍵盤、讀屏、真實 Notion 方案選擇/金額/歷史快照、共享裝置隱私。

## 計數與硬限制

| 指標 | 本輪 |
|---|---:|
| 已查索引新來源候選 | 2 |
| 主要正文文字閱讀 | 2（各一次） |
| 首次獨立反例分析 | 2篇 |
| 既有來源完整獨立複讀 | 0 |
| 嚴格完整 DEEP_PASS | 0 |
| 本輪完成 10/10 | 0 |
| 累積可核實 FULL_DEEP_PASS_10_OF_10 | **0／10,000篇** |

所有原文閱讀與反例僅為研究證據，不構成修改 Notion 的授權，也不能推定 Notion 的欄位權限、公式真值、歷史金額、效能或實際 UI。**本輪僅 GitHub 研究寫入；Notion 頁面/資料庫/View/Formula/Relation/權限/業務列及正式 GAS/Cloud Run/Session/部署均不得更動。** 研究門檻未達，不開始重新設計。手動與自動續作仍可並行，需依最新 main SHA 進行條件更新。
