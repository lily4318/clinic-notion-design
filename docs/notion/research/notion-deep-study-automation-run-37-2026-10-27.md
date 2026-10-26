# Notion 深度學習｜AUTO-37（2026-10-27 04:38 Asia/Taipei）
執行軌跡：`AUTO-37-20261027-0438-RESEARCH`。**僅研究與 GitHub 證據，不授權修改 Notion 或正式系統。**

## 本輪基準與去重範圍
- 重新讀取 main：`README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`，及 `docs/notion/research/` 當期檔名清冊（48 個 Markdown 文件；最新已有 AUTO-36，未見 AUTO-37）。
- 檢查 `sources.md` 已登錄來源及 GitHub main code search 的 `ui-accelerators`、`alphabetical-sorting-must-mostly-die`、`AUTO-37`，均未命中。**全儲存庫未索引歷史文件的精確機器去重尚未完成**；本輪兩篇只能列為「已查清冊新 canonical 候選」，不是全域唯一總數的確證。
- 原文直接開啟 Nielsen Norman Group 文章正文，不將搜尋結果、作者索引或摘要計作閱讀。

## AUTO37-S01｜Accelerators Maximize Efficiency in User Interfaces
- URL：https://www.nngroup.com/articles/ui-accelerators/
- canonical identity：`nngroup:articles/ui-accelerators`；作者 Rachel Krause、Aurora Harley；2024-10-18。
- 本次閱讀證據：原文 `What Are Accelerators?`、`Examples of Accelerators`、`Discoverability of Accelerators`、`Accelerator-Design Best Practices`、`Conclusion`，逐節文字及圖說；讀取頁面約第 40–124 行。標記 `R1_MAIN_TEXT_SECTIONS+C1`；**只算一次主要正文閱讀＋一次獨立反例**。
- 原文要點：快捷方式是既有動作的替代路徑，不能成為新手完成任務的必要條件；可在一般操作後提供情境提示、在選單顯示快捷鍵、於 tooltip/hover 呈現（但觸控不可只靠 hover）、將複雜快捷入口置於多處；優先反覆高頻任務，維持跨裝置一致性，並提供操作結果回饋與錯誤復原。
- 獨立反例 C1（治療所）：如果「快速套用方案／批次確認」只是省略逐筆核定期別檢查，即使減少點擊，仍可能把歷史 Session 連到錯誤期別或改變收費。**加速器只能加速安全且已有的操作，不能跳過核對，也不能用「成功執行」代表補助資格已確認。** 應先分辨高頻低風險查閱（可能適合捷徑）與跨期批次改值（不宜直接加速）。
- 限制與反證：文章是通用 UX 原則，不能據此宣稱 Notion 支援自訂鍵盤捷徑、巨集、所有 Undo、跨平台一致行為或 hover 提示；未測 Notion 原生快捷、行動版、實際權限與使用者操作時間；文章原圖未逐張獨立檢查。

## AUTO37-S02｜Alphabetical Sorting Must (Mostly) Die
- URL：https://www.nngroup.com/articles/alphabetical-sorting-must-mostly-die/
- canonical identity：`nngroup:articles/alphabetical-sorting-must-mostly-die`；作者 Jakob Nielsen；2010-10-03。
- 本次閱讀證據：全文主要正文，包括 `People Rarely Think A–Z`、`Better Sorting than A–Z`，並讀圖說、文章提出的已知項目例外；頁面約第 40–86 行。標記 `R1_MAIN_TEXT_ALL_SECTIONS+C1`；**只算一次主要正文閱讀＋一次獨立反例**。
- 原文要點：字母排序適合已知名稱、名稱明確的選項；但有自然序位的數值、時間線、業務邏輯群組、重要性或頻率時，A–Z 可能破壞可理解順序。文中以鞋寬、鞋跟高度選項示範錯誤字母排序與合理遞增順序的差別。
- 獨立反例 C1（治療所）：政府方案期別與收費期別若按方案名稱字母／筆畫排序，容易將相同名稱的不同生效期混排；但若只顯示「最新期別優先」，回填歷史 Session 時也可能誤用現行價格。**清單的排序（閱讀便利）不等於生效期判定（業務規則）**；應以服務實際日期對應期別，必要時清楚顯示起訖日／期別識別，且不可假設清單第一筆即適用。
- 限制與反證：2010 年網站電商案例不可直接外推成 Notion 特定資料庫排序性能或台灣臨床行政驗收結果；未實測 Notion 的日期排序、篩選、權限、手機操作或任何歷史會談金額。

## 研究結論（尚非設計核准）
1. 熟練者的快捷入口應是可選的既有安全路徑，不能取代新手的完整路徑與核對。
2. 收費／補助期別清單應尊重時間與業務有效性，但「顯示排序」不可被誤用為「自動選定有效期」。
3. 以上僅作未來設計候選與風險清冊；尚未通過真實使用者、角色、Notion 原生公式、跨方案期別、效能或政府核定規則驗收。

## 嚴格進度與未完成項
- 本輪已查清冊新 canonical 候選 **2**；R1 主要正文文字閱讀 **2**；首次獨立反例 **2**；既有來源完整複讀 **0**。
- 本輪 `FULL_DEEP_PASS_10_OF_10` **0**；依已知可核實紀錄，累積仍 **0／10,000 篇**。原始圖、影音、互動與實際產品操作未完成，不冒稱任何文章已完成完整深讀 R1–R10。
- 全域去重與完整十次深讀、真人 UX、Notion 公式及權限、手機、效能、跨期實帳均 **PENDING/NOT TESTED**。
- **NO NOTION / SYSTEM WRITE**：沒有變動 Notion Page、DB、Data Source、View、Formula、Relation、權限、業務資料，亦未更動 GAS、Cloud Run、Session 或部署；沒有開始重新設計。手動與自動續作共享 main 並行，後續每次寫入仍需最新 SHA 條件與寫後驗證。
