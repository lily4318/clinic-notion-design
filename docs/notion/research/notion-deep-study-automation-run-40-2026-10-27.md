# Notion 深度學習｜AUTO-40（2026-10-27；僅研究，不是實作）

- 執行軌跡：`AUTO-40-20261027-0739-RESEARCH`；渠道：每小時獨立研究。與手動續作並行，不停用或延後另一渠道。
- 起始基準：重新讀取 main 的根 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md；並逐檔檢索 docs/notion/research 當期 **51/51 個 Markdown**（含 AUTO-01～39、batch02～04、MANUAL-01、十面向及其他研究清冊）。兩個候選 slug 在這些文件與來源索引未見命中；GitHub code search 零結果僅為輔助，不代表全儲存庫歷史檔案已全域精確去重。
- 本輪原文：NN/g 兩篇均實際開啟可讀 HTML，逐節研讀主要文字、原文圖說及結論。未逐張開啟圖片原檔、未播放影片、未操作示範或 Notion 真實帳戶；**R1_MAIN_TEXT+C1** 不等於一次「完整深讀」，更不等於 10 次獨立完整深讀。
- 來源計量：以 publisher + article slug 為 canonical 身份；每篇只登錄一次來源，分別一個文字研讀回合與一個首次反例，不把同篇多段/八條原則拆成多次閱讀。

## AUTO40-S01｜Error-Message Guidelines
- 原文：https://www.nngroup.com/articles/error-message-guidelines/
- Canonical：`nngroup:articles/error-message-guidelines`；標題：*Error-Message Guidelines*；作者：Tim Neusesser、Evan Sunwall；日期：2023-05-14。
- 閱讀紀錄：`AUTO40-S01-R1-TEXT-C1`，主要正文一次，涵蓋 Visibility Guidelines（位置、可及性、風險層級、觸發時機）、Communication Guidelines（自然語言、具體說明、補救指引、非責備語氣）、Efficiency Guidelines（保留輸入、減少更正成本、避免連鎖錯誤）、Mitigate Failure 與 Conclusion；頁面圖說可讀，圖片原檔未逐張檢查。
- 主要理解：錯誤訊息須靠近來源、文字與視覺冗餘而非僅顏色、分辨提示與嚴重阻擋、避免在使用者尚未完成輸入時提前判錯；說明如何補救且盡量保留使用者已輸入的工作。
- **首次獨立反例 C1（治療所行政）**：「待人工核對資格」是業務不確定狀態，並非系統輸入錯誤；若一律顯示紅色『錯誤』與強制警示，可能導致行政人員誤認已不符合補助，或在正常流程產生警告疲勞。反之，若核定期別與 Session 服務日期明確衝突，僅用不顯眼提示又可能讓跨期錯帳持續。訊息必須區分『未知／待核對／已確認0／不適用／實際輸入錯誤』，但這是**研究假說**，未核准新增欄位、驗證規則或 UI。
- **反證與界線**：原文舉一般網站/電商例子，不能證明 Notion 原生可客製所有驗證訊息、toast 或自動復原。不能把『錯誤訊息精準』等同於政府核定正確；顯示詳情時也須避免未授權人員看到個案敏感資料。與先前 AUTO-32 狀態回饋、AUTO-28 表單錯誤屬相關但**不同 canonical 文章**，不可把重疊主題誤當相同閱讀。

## AUTO40-S02｜Confirmation Dialogs Can Prevent User Errors — If Not Overused
- 原文：https://www.nngroup.com/articles/confirmation-dialog/
- Canonical：`nngroup:articles/confirmation-dialog`；標題：*Confirmation Dialogs Can Prevent User Errors — If Not Overused*；作者：Jakob Nielsen；日期：2018-02-18，頁面標示 2026-08-07 reviewed。
- 閱讀紀錄：`AUTO40-S02-R1-TEXT-C1`，主要正文一次，涵蓋確認對話框的目的、單筆/多筆刪除的具體性差異、警告疲勞、8項指引（高風險才確認、避免例行確認、具體後果、動詞式選項、分層說明、無預設同意、極高風險非慣常確認、例行確認可避免）與最後復原建議；圖說可讀，原圖未逐張查。
- 主要理解：單純『確定嗎？』不能提供有效的二次檢查。應在高風險操作明示受影響對象與後果；反覆例行確認可能使人自動點同意。Undo/回復能力可補充但不取代風險辨識。
- **首次獨立反例 C1（治療所行政）**：跨核定期別批次更動歷史 Session 的收費方案，若只有泛用『確定更新』，操作者無法核對受影響的服務日期與期別；但每次普通檢視切換或新增草稿都跳出確認，會使真正危險的提醒被忽略。相反地，若確認框列出全部個案姓名、收費明細給權限不足者，也會帶來個資暴露。具體性應限於當前角色有權查閱的必要資訊，且**不能假設 Notion 有原生自訂 modal、完整 Undo 或交易回滾**。
- **反證與界線**：原文是通用應用設計原則，不等於 Notion 已提供對應客製功能；需要核對真實 Schema、權限、可回復性、操作頻率與真人情境後才能決定是否適用。本輪**未**進行這些實測，也**未**修改任何確認流程。

## 去重、閱讀次數與完成門檻
| 指標 | 本輪可驗證 |
|---|---:|
| 已查研究目錄 Markdown | 51/51 |
| 已查清冊新 canonical 候選 | 2 |
| 可讀主要正文 R1 | 2 |
| 首次獨立反例 C1 | 2 |
| 既有來源完整複讀 | 0 |
| 本輪達成 10/10 完整深讀 | 0 |
| 累積可核實 10/10 完整深讀 | **0／10,000篇** |

未完成全儲存庫未索引路徑、不同URL相同文章的精確機器去重，因此新來源只稱「已查清冊新候選」。即使某篇正文 R1 充分，原始圖片/影片/互動等仍未完整核對，不冒稱 FULL_DEEP_PASS_1/10。不同角度反例不算獨立完整閱讀。未驗證 Notion 真實頁面、資料庫、View、Formula、Relation、權限、手機、效能、政府資格、歷史收費公式與真人 UX。

## 範圍與安全
僅研究及 GitHub 研究證據/來源/決策/驗收進度紀錄；**Notion正式與TEST頁面、資料庫、Data Source、View、Formula、Relation、權限、個案及財務資料零寫入；正式GAS、Cloud Run、Session、部署零寫入**。本輪不執行 Notion 重新設計。未達10,000篇各10次完整且可稽核深讀，亦未獲使用者對完成的確認；保持雙軌並行。
