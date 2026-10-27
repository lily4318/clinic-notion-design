# Notion 深度學習｜AUTO-45｜2026-10-27（研究，非介面變更）

- Trace：`AUTO-45-20261027-1245-RESEARCH`；時間：2026-10-27 台灣時間。本次只讀取公開UX原文、GitHub最新規範/研究清冊，僅允許研究紀錄寫入GitHub；未對Notion或正式系統操作。
- 開始前重新 Fetch main：README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、decision-log.md、acceptance-status.md、research/README.md及batch-02；兩篇均已成功取得原文主要文字。搜尋GitHub程式碼索引與sources.md對新文章slug/標題無命中，但**未完成全儲存庫所有歷史檔及同文異址的精確去重**。
- 計數嚴格：本輪新canonical**候選1**；既有來源**針對性獨立複讀1**；本輪新反例2；新增完整DEEP_PASS_10_OF_10 **0**；累積可稽核完成10/10篇數仍**0／10,000**。不將一篇十條建議計十篇，不將正文閱讀計完整深讀。

## AUTO45-S01｜Website Forms Usability: Top 10 Recommendations（新候選；首次主要正文閱讀）

- URL：https://www.nngroup.com/articles/web-form-design/ ；canonical `nngroup:articles/web-form-design`；Kathryn Whitenton，2016-05-01；NN/g；檢閱2026-10-27。
- 閱讀軌跡 `AUTO45-S01-R1-MAIN-TEXT-C1`。實際開啟正文並逐節檢查：TSA表單的危險Clear Form示例、研究摘要、10項規則、結論與參考文獻。涵蓋縮減不必要欄位、相關欄位分組、單欄順序、欄位/選項邏輯順序、避免placeholder、輸入尺寸與型別、必要/選填辨識、格式要求預先可見、避免Reset/Clear、錯誤訊息需具體並保留已輸入資料。文章引述CHI表單研究78%與42%一次完成無錯率；這是被引研究的比較結果，**不能當作治療所Notion實測**。
- **反例C1**：行政欄位精簡若只追求「少填」而隱藏真正必要的首次補助服務日期、期別或資格核對狀態，可能造成日後錯期或錯價；但把每一個可推導的欄位都要求人工填寫，又增加互相矛盾與維護成本。對本專案應區分「可安全推導」「需留歷史快照」「待人工核對」，而不是套用一律刪欄規則。
- **反例C2**：通用表單避免Reset的建議不代表Notion已有安全Undo或確認機制；把「清空資料」或批次更新做成顯眼按鈕可能破壞歷史Session，但在特定含敏感輸入的取消情境仍須提供安全退出。未授權新增按鈕或改業務資料。
- 證據界線：正文與圖說可讀，未逐張檢查原圖、未操作TSA示例或本所Notion實帳，未追讀CHI原論文全文；級別 `MAIN_TEXT_R1`，不是完整 `DEEP_PASS_R1`。

## AUTO45-R01｜Memory Recognition and Recall in User Interfaces（既有 UX-018；獨立針對性複讀）

- URL：https://www.nngroup.com/articles/recognition-and-recall/ ；canonical `nngroup:articles/recognition-and-recall`；Raluca Budiu，2024-01-15；NN/g。原於 `notion-deep-study-evidence-batch-02-2026-10-25.md` 以UX-018 `BODY_SECTIONS` 登錄，故**新增URL 0**。
- 閱讀軌跡 `AUTO45-R01-TARGETED-REREAD-TEXT-C1`。本次重新開啟並閱讀記憶辨識/回憶定義、practice/recency/context三項活化來源、選項提示、搜尋建議、近期瀏覽歷史、可見功能/選單與情境提示、結論與文末引用；不是前輪文字的複製分析。
- **新的反例C1**：將「最近使用的收費方案／核定期別」放在最前面有助快速辨認，卻可能讓補登歷史Session的工作者過度依賴近期熟悉選項而選錯期別。辨識容易**不等於業務正確**；需由服務日、期別有效範圍及歷史價格資料獨立核對。
- **新的反例C2**：可見導覽與清楚文字標籤有助回到未完成任務，但若因此在首頁同時攤開所有稽核、內部AI規則與歷史欄位，反而擠壓使用者已確認的同頁直接看核心資料的空間。可見性應優先給工作當下必須判斷的狀態；這是待驗證假說，不是Notion重設決定。
- 證據界線：主要文字已重新開啟，原圖未逐張驗證、原始CHI引用未追讀、真人工作者任務未測；本次只計一次**針對性複讀**，不冒稱完整第二次深讀。

## 交叉分析、未驗證與停止條件

- 表單的「減少回憶需求」和「減少欄位」並非同義：必要業務狀態應可辨認，但不能以當期預設值代替歷史期別正確性。欄位少不等於資料完整；欄位多也不等於可用性高。
- 研究推論不等於Notion產品功能承諾。Notion原生欄位排序/模板、歷史金額固定機制、不同角色可見性、手機與桌面操作、載入效能、實際公式及核定金額均**NOT_TESTED**。
- 全庫去重/同文異址、原始圖、互動示例與原論文驗證仍待後續；本輪不增加任何嚴格10/10達標篇數。
- **NO NOTION/SYSTEM WRITE**：沒有修改任何Notion Page、DB、Data Source、View、Formula、Relation、權限或個案/財務資料，也沒有修改正式GAS、Cloud Run、Session或部署。未達10,000篇×10次且未經使用者確認，禁止進入Notion重新設計。
