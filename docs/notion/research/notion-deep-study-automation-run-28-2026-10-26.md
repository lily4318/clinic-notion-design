# Notion 深度學習 AUTO-28｜2026-10-26（研究，不改業務系統）

- 執行標記：`AUTO-28-20261026-1943-RESEARCH`；軌道：每小時自動研究；本次獨立於聊天手動續作。
- 範圍：僅 GitHub 研究記錄；不得改 Notion 頁、資料庫、View、公式、權限或正式 GAS／Cloud Run／Session。
- 研究起始查核：重新 Fetch main README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、decision-log.md、acceptance-status.md、Git tree 與研究清冊。研究目錄共39份文件逐一以 URL slug 檢查本輪三個候選；來源索引、GitHub 搜尋亦未見相同 slug。仍不宣稱已完成所有外部或歷史來源的全域 URL 去重。
- URL 身分規則：去掉 Notion 語系前綴 /en-gb/、/fi/，使用相同 help/guides slug 作 canonical；NN/g 以 article slug 作 canonical。每篇僅一次主要文字 R1 與首次獨立反例，未將頁內不同小節重複計篇。

## AUTO28-S01｜NN/g：10 Design Guidelines for Reporting Errors in Forms

- 原文：https://www.nngroup.com/articles/errors-forms-design-guidelines/
- Canonical ID：`nngroup:articles/errors-forms-design-guidelines`
- 作者 Rachel Krause；2019-02-03 發表，2024-12-12 最近審閱；2026-10-26 取得可讀正文。
- 證據層級：`R1_MAIN_BODY_ALL_10_GUIDELINES+COUNTEREXAMPLE`；讀取原則、1–10項指引與結論；圖片僅有文字說明，未逐張檢視原圖，非完整深讀。
- 具體內容：輸入完成後就地驗證；複雜欄位適度顯示成功；錯誤貼近欄位；顏色搭配圖示而非僅靠顏色；確認對話框需節制；不要在尚未輸入完就報錯；總覽不能取代欄位旁訊息；tooltip 不適合承載關鍵錯誤；重複錯誤應改良流程。
- 先驗假設：所有待確認欄位在首頁統一顯示醒目紅／黃色警告，能確保行政人員不漏看。
- **反例1**：未填完他處回報、首次使用日期或補助資格前即顯示「錯誤」，會把正常輸入中與真正違規混為一談；應先分辨未輸入、待確認、確定錯誤。
- **反例2**：只在頁首列「3筆錯誤」或 hover 提示，不足以讓人找到是哪個個案／方案期別／欄位；但把每一欄都做成大幅警示亦違反使用者已否決的干擾設計。
- **反例3**：NN/g 談的是一般表單，不代表 Notion 原生 View 支援逐欄即時自訂錯誤樣式；需日後合法設計階段再查可行性，不得擅自建立新欄位或按鈕。

## AUTO28-S02｜Notion：Make work more efficient with database button properties

- 原文：https://www.notion.com/en-gb/help/guides/make-work-more-efficient-database-button-property
- Canonical ID：`notion-help:guides/make-work-more-efficient-database-button-property`；作者／發表日期未標明；2026-10-26 取得主要正文。
- 證據層級：`R1_MAIN_BODY+COUNTEREXAMPLE`；讀取 button property 建立、Add page、Edit pages、Show confirmation、Open page、簽核／升級／投票案例、與 Button block／DB automation 差異。部分折疊內容與示意圖未完整驗證。
- 具體內容：資料庫每列可有按鈕，連續執行建立頁面／編輯頁面屬性／開啟頁面等步驟；可加確認對話框。文章區分需要使用者點擊的按鈕與資料變動觸發的自動化。
- 先驗假設：把「確認方案資格」變成一鍵按鈕，能同時減少填寫及杜絕錯誤。
- **反例1**：按鈕的確認對話框只降低誤觸，不代表已驗證資格、核定期別、實際首次服務日或政府額度。若把待核對狀態直接改為已確認，會產生錯誤確信。
- **反例2**：按鈕可依 filter 編輯其他資料庫的多筆頁面；若篩選條件缺少期別，可能批次更改不屬於本期的紀錄。不能只憑示例宣稱有唯一性或交易式回復。
- **反例3**：每日高頻操作若處處要求二次確認，會增加點擊與認知負荷；只應在有不可逆或跨筆影響時考慮，且須實測。本文不是本所設計授權。

## AUTO28-S03｜Notion：Create streamlined project management workflows using database automations

- 原文：https://www.notion.com/en-gb/help/guides/create-streamlined-project-management-workflow-using-database-automations
- Canonical ID：`notion-help:guides/create-streamlined-project-management-workflow-using-database-automations`；作者／發表日期未標明；2026-10-26 取得主要正文。
- 證據層級：`R1_MAIN_BODY+COUNTEREXAMPLE`；讀取 trigger/action、OR 觸發、3個案例、公式變數與 Gmail 範例、方案限制說明及結尾；未展開全部互動示範／圖片，非完整深讀。
- 具體內容：新頁或欄位變更可觸發動作；多個 trigger 為 OR；可更新頁面、通知、使用公式變數。官方指南也指出自動化受方案限制，免費模板可使用不代表免費可編輯。
- 先驗假設：只要設「任一方案欄位變更」就能自動保持跨年度額度一致。
- **反例1**：OR trigger 不是「方案、期別、資格、使用日期全部通過」的 AND 條件；若任一欄位變更即更新其他頁，可能在資料未完成時覆寫正確紀錄。
- **反例2**：跨資料庫動作不代表原子交易、去重或多期隔離；重複觸發、重跑及部分失敗需要額外核對，官方文章未證明可安全承擔法定申報。
- **反例3**：文中部分操作限付費方案，未在本所帳戶實際核對，不能推定現行免費工作區能建立、編輯或可靠運行。

## 計數、反證與限制

| 指標 | 本輪可核實數 |
|---|---:|
| 初步去重的新 canonical URL | 3 |
| 取得主要正文並逐篇閱讀 | 3 |
| 首次獨立反例分析 | 3 |
| 舊來源完整重讀 | 0 |
| 本輪10次完整深讀達標 | 0 |
| 累積可稽核10/10達標 | **0／10,000篇** |

- 只讀取網站可得的文字正文、圖片說明；未逐張核對圖片、未操作互動示範／影片、未使用實際 Notion 帳戶測試、未測真人UX、手機、權限、速度或公式真值。故 `FULL_DEEP_PASS=0`。
- 三篇均為不同 canonical URL、不同文章；本輪只算 R1，不將搜尋命中、各小節或不同反例算作額外閱讀輪次。
- 設計推論僅屬研究假說，不等於 Notion 已實作／使用者核可。政府方案的未知、待核對、已確認0必須區分。
- 本輪僅允許 GitHub 記錄增量，不操作 Notion／GAS／Cloud Run／Session，也不進入重新設計。
