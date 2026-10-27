# AUTO-54｜2026-10-27｜表格比較與分頁導覽：資料可見性和跨頁一致性（僅研究）

- Trace：`AUTO-54-20261027-2141-RESEARCH`；台灣時間 2026-10-27 21:41。使用者授權僅限外部研究及 GitHub 研究紀錄，**不授權 Notion 重新設計或業務資料變更**。
- 開始前讀取 main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md、AUTO-53 研究紀錄及研究目錄清單。研究目錄查得 **65 份 Markdown**（含 README、基礎清冊及 AUTO-01～53）；另外已逐檔讀取12份非AUTO研究清冊，兩篇 canonical 未見重複；sources.md 全文與 GitHub code search 對兩篇 URL/canonical 均無命中。嘗試批次讀取所有 AUTO 歷史研究文件時遭 Code Mode 工具呼叫上限中斷，**未完成全部65份逐檔全文與同文異址精確去重**。因此兩篇只列「已查索引新來源候選」。
- 兩篇官方頁面均實際開啟並閱讀主要文字、用途、禁用情境、HTML/Nunjucks示例、可用性/無障礙注意及變更紀錄；獨立示例 URL 已開啟且可讀，但**未逐張核對所有原圖、實際互動/鍵盤/讀屏/手機測試，也未在 Notion 真實帳戶測試**。本輪每篇僅 `R1_MAIN_TEXT_PARTIAL`，不是完整第一次深讀，也沒有獨立 R2–R10。

## AUTO54-S01｜Table – GOV.UK Design System

- 原文：https://design-system.service.gov.uk/components/table/
- 獨立示例：https://design-system.service.gov.uk/components/table/default/
- 標題：Table – GOV.UK Design System；維護者 GOV.UK Design System team；首次發表日未核實；官方變更紀錄記載 2018–2024 年多項元件更新。
- Canonical：`govuk-design-system:components/table`；本輪唯一閱讀標記：`AUTO54-S01-R1-MAIN-TEXT-C1`。
- 閱讀覆蓋：表格適用於跨列、跨欄比較與掃描；不可把表格用作頁面排版；使用 caption 提供表格目的、欄列 header 的 scope 供輔助技術辨識；數字欄建議靠右；可自訂欄寬；大量資料時優先減少資訊或按任務分表/分頁，極大量表格可使用小螢幕專用字級樣式但不宜濫用；閱讀 HTML/Nunjucks 數字表、不同標題、欄寬及大表格示例。
- **反例A（只看漂亮表格）**：治療所若只保留單筆摘要卡片而移除同頁 Session 日期／方案期別／歷史金額的跨筆比較，可能增加人工比對成本；但把全部23來源庫636個欄位直接攤成超寬表格也會降低辨識與效能。應由實際「哪些欄需同時比較」決定視圖，而非表格越多越好。23來源636欄是歷史結構稽核數，非本輪即時 Schema。
- **反例B（數字呈現≠金額正確）**：數字靠右與標題清楚有助閱讀，但無法防止歷史 Session 金額因 Relation／Formula 隨期別更新而改變；表格呈現與資料保護、業務核准須分離。不能僅因表格看起來一致就標記財務驗收PASS。
- **反例C（跨裝置）**：GOV.UK 原生 CSS/HTML 的 table caption、scope、mobile class 不等於 Notion 原生 Linked View 能精確套用；不可擅自修改 Notion View 或聲稱手機/讀屏已驗證。

## AUTO54-S02｜Pagination – GOV.UK Design System

- 原文：https://design-system.service.gov.uk/components/pagination/
- 獨立示例：https://design-system.service.gov.uk/components/pagination/for-list-pages/
- 標題：Pagination – GOV.UK Design System；維護者 GOV.UK Design System team；首次發表日未核實；官方最近變更含 2026-01 空連結輸出修正（屬元件變更，非文章首發）。
- Canonical：`govuk-design-system:components/pagination`；本輪唯一閱讀標記：`AUTO54-S02-R1-MAIN-TEXT-C1`。
- 閱讀覆蓋：內容量大造成載入慢、使用者通常只需前幾頁時可分頁；只在改善效能或可用性時分頁；不建議無限捲動（鍵盤使用者問題）；表單線性旅程應使用 Continue/Back 而非資料分頁；內容頁用帶上下文的 previous/next、資料清單用頁碼；單頁不顯示分頁；頁碼及目前頁要有可理解的無障礙語意；小螢幕顯示首尾及相鄰頁；篩選/排序須套用**整個資料集合**，而非只對當頁操作，改條件後回到結果首頁。已讀 HTML/Nunjucks 及 first/last page 例子。
- **反例A（誤判資料缺漏）**：若行政人員在補助歷程的第1頁看不到較舊 Session，卻把「目前頁面沒有」誤判為「全期間沒有」，可能錯算補助占用或漏核歷史收費。分頁後應明確區分顯示筆數、篩選範圍及全量資料，但這是待驗的設計假說，不可自行改 View。
- **反例B（篩選只在當頁）**：若「本週／本期／個案」篩選只作用於已載入資料，而非整個資料集合，跨頁結果將不一致；Notion 實際 Linked View 的查詢及分頁行為需另行唯讀驗證，不能以 GOV.UK 元件說明推定。
- **反例C（效能取捨）**：使用者已明確否決把原本同頁可直接操作的資料全部換成連結入口；不能以「分頁提高效能」為由擅自把常用 Session/額度核對移出原頁。分頁應先有真人任務及載入速度證據。

## 跨來源反證、進度與邊界

- Table 強調**同一視野的可比較性**；Pagination 強調**大量內容的載入與導覽成本**。二者並非互斥，但「拆頁減少負載」可能破壞跨筆日期/期別/金額核對；「全部同頁顯示」又可能增加載入及掃描成本。要判定哪一種較好，需可重現的任務測試與實際資料量/效能證據，**本輪未進行**。
- 本輪已查索引新來源候選 **2**、主要正文文字閱讀 **2**、首次獨立反例分析 **2篇**；完整 R1 **0**、完整 R2–R10 **0**、本輪新增十次嚴格深讀達標 **0**；累積可稽核 `FULL_DEEP_PASS_10_OF_10` **0／10,000篇**。
- **NOT_TESTED**：研究目錄65/65逐檔完整去重、同文異址、原圖/影片/互動、Notion原生View/手機/讀屏/角色/效能、補助資格/歷史Session金額/公式真值。這是研究而非系統功能PASS。
- **NO NOTION/SYSTEM WRITE**：本輪僅GitHub研究與進度；不更動Notion正式/TEST頁、DB、Data Source、View、Formula、Relation、權限、個案/財務資料或正式 GAS、Cloud Run、Session、部署；未進入重新設計。雙軌研究可獨立續作，寫入以最新SHA條件避免覆寫。
