# Notion 深度學習｜AUTO-41（2026-10-27；研究紀錄，不是實作）

- 執行軌跡：`AUTO-41-20261027-0840-RESEARCH`；獨立排程研究，與手動續作共享 main，但不將同一 URL 或同次分析重算。
- 開始前重新 Fetch main：根 `README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`，並檢查研究目錄（建立前52份 Markdown）。`sources.md` 的兩個 canonical slug 均未命中；GitHub code search 對兩個 slug 均回傳零結果。**未成功完成所有52份研究檔正文逐一讀取**（批量取檔遇工具呼叫上限），因此僅列「已查索引新來源候選」，不宣稱全庫去重。
- 原文：兩篇 NN/g 的公開 HTML 在本輪實際開啟，依文章目錄逐節讀取主要正文與可見圖說。沒有逐張開啟原始圖片、實際播放影片或操作 Notion 工作區，故僅記 `R1_MAIN_TEXT+C1`，**完整深讀 0 次**。
- 身份去重：以 publisher + canonical article slug 為主鍵；移除網址追蹤參數及尾端斜線差異；不同主題或多項建議不算不同文章或多次閱讀。

## AUTO41-S01｜Mobile Tables: Comparisons and Other Data Tables

- 原文：https://www.nngroup.com/articles/mobile-tables/
- Canonical：`nngroup:articles/mobile-tables`；Amy Schade；2017-09-17。
- 閱讀紀錄：`AUTO41-S01-R1-TEXT-C1`；本輪一次獨立正文閱讀及一次獨立反例分析。
- 正文涵蓋八節：Columns Large Enough to Be Legible；Rotating the Phone Is a Last Resort；Stick Column Headers in Place；Clearly Indicate if Horizontal Scrolling Is Needed；Stick the Left Column in Place；Let Users Select the Data to View；Accordions for Groups of Data；Help Users Find What They Need。原文圖說包括運動統計欄縮寫、旋轉手機後剩餘垂直空間、表頭遺失、左右捲動線索、鎖定左欄、跨規格比較、摺疊分類；僅讀圖說，原始圖片未逐張查驗。
- 核心理解：可讀性優先於同屏欄數；強制橫向旋轉有垂直空間代價；超寬表格需保留欄名/列識別及可捲動線索；先縮小資料範圍適合查單一紀錄，卻不適合需要同時比較多筆的任務；摺疊群組可提供概覽，但需防止關鍵資料不可見。
- **C1 反例（本所情境）**：若行政人員用手機核對同一個案「本次 Session 服務日期／歷史收費期別／當期核定資格／可用額度」，把每一欄切成獨立分頁或要求先選一個資料集，會迫使人員記住上一頁數值，容易錯把現行方案金額套用歷史會談。反過來，把所有欄位在窄螢幕無限制攤開也會讓文字截斷、錯行、誤讀；應先辨認哪些欄位是**同時比較的必要集合**，哪些只是次要詳情。
- **反證與產品限制**：NN/g 例子多為一般網站與商品比較，不代表 Notion 原生資料庫可以固定首欄、固定表頭、顯示捲動箭頭或自訂 mobile layout。不能為了手機畫面而改動資料權威歸屬、實際收費或歷史紀錄；本輪沒有 Notion 手機操作實測。

## AUTO41-S02｜Leverage AI for Mock Tables and Charts When Testing Prototypes

- 原文：https://www.nngroup.com/articles/ai-data-prototype-testing/
- Canonical：`nngroup:articles/ai-data-prototype-testing`；Evan Sunwall；2024-09-06。
- 閱讀紀錄：`AUTO41-S02-R1-TEXT-C1`；本輪一次獨立正文閱讀及一次獨立反例分析。
- 正文涵蓋：Users Will Scrutinize Your Tables and Charts；Be Cautious with Your Real Data；Craft a Promptframe；7 Tactics for Generating Mock Tables with AI（情境、規模、排序、欄位約束、圖表支援資料、受試者脈絡、顯式計算與驗證）；7 Tactics for Generating Mock Charts with AI（目標、去雜訊、離群值、尺寸、SVG、人工判斷、表格轉圖）；Importing Tables into Design Tools；Differences in AI Tools；Opportunities with Synthetic Data in Regulated Industries；Conclusion/References。原文多個示例圖片有可讀圖說，原始圖檔未逐張查驗。
- 核心理解：高擬真測試資料需要事先定義分布、唯一性、格式、固定選項、極端值與跨欄數值一致性；AI 自稱核算完成不等於驗證，必須使用可重算的程式及斷言；原文 2024 年的模型/工具比較是歷史情境，不代表 2026 年仍成立。文章區分少量人工 mock data 與基於真實資料統計性質的 synthetic data；醫療等受管制領域需格外重視隱私。
- **C1 反例（本所情境）**：若用 AI 生成「看起來合理」的補助期別、Session、收款與用量測試資料，卻未約束 `Session日期→期別→金額`、`個案+期別` 唯一性、未知與確認零的不同語意，可能在 UI 測試呈現漂亮的報表，卻完全掩蓋跨期計價錯誤。即使合成資料通過公式校驗，也不能推定真實政府資格/補助額度正確。不能將實際個案/病歷/財務明細輸入未核准的外部生成服務；只能考慮完全虛構且不回寫正式環境的測試資料。
- **反證與產品限制**：文章建議的是 prototype data fidelity，不是自動核准醫療/補助資料的依據。原文展示 AI 算錯總額再修正的案例，證明僅靠文字「已驗證」不可靠。此輪未建立測試資料、未執行程式核算、未驗證 Notion Formula/Relation 或任何真實業務資料。

## 去重與進度

| 指標 | 本輪可核實 |
|---|---:|
| 起始研究目錄 Markdown 清單 | 52份（僅清單；非52份全文審閱） |
| 已查 sources.md 未登錄 canonical 新候選 | 2篇 |
| 實際取得並讀取主要正文 | 2篇各一次 |
| 首次獨立反例分析 | 2次 |
| 既有來源完整複讀 | 0 |
| 本輪完成嚴格十次完整深讀 | 0篇 |
| 累積可核實十次完整深讀 | **0/10,000篇** |

**限制**：全庫其他路徑及同文不同網址未全面去重；所有原圖、影片、互動示範、實際 Notion 手機/桌面、角色權限、效能、公式真值、政府核定資格均未測。文字 R1 不冒稱完整深讀 R1，更不冒稱 R2-R10。

## 範圍與安全

本輪只研究並記錄於 GitHub；沒有修改任何 Notion 正式/TEST 頁、資料庫、Data Source、View、Formula、Relation、權限、業務資料或正式 GAS、Cloud Run、Session、部署。研究目標未達且未獲使用者完成確認，**不進入 Notion 重新設計**。