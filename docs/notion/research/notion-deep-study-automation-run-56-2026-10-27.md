# AUTO-56｜2026-10-27｜多選／單選、明確的「無」與條件揭露（僅研究）
- Trace：`AUTO-56-20261027-2337-RESEARCH`；台灣時間 2026-10-27 23:37 起。研究來源：GOV.UK Design System 官方公開元件指南。
- 開始及寫入前重讀 GitHub main 的根 README、AGENTS、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、decision-log.md、acceptance-status.md 與 research README；另查 AUTO-55 研究記錄。來源索引全文及 GitHub repository code search（checkboxes/radios）未找到以下兩個 canonical URL；**沒有完成所有歷史研究文件逐檔全文及同文異址去重**，因此兩篇僅列「已查索引新候選」。
- 原始資料可讀：官方主頁及其 HTML/Nunjucks 示例、When to use/not use、選項排序、預選風險、None/unknown、條件顯示、錯誤、較小元件與 Known issues/Recent changes。沒有逐張核實圖片、真實互動、鍵盤、螢幕閱讀器及 Notion 實帳，因此兩篇僅為 **R1_MAIN_TEXT_PARTIAL**，不是完整 R1，也不是 R2–R10。

## AUTO56-S01｜Checkboxes – GOV.UK Design System
- URL：https://design-system.service.gov.uk/components/checkboxes/
- Canonical：`govuk-design-system:components/checkboxes`；標題：Checkboxes；維護者：GOV.UK Design System team；網頁首發日期未核實；本輪存取日期 2026-10-27。閱讀記號：`AUTO56-S01-R1-MAIN-TEXT-C1`。
- 已核對的文字章節：多選或單一開關可用 checkbox，但互斥單選應用 radios；不能預設勾選以免使用者漏看；用 fieldset/legend 標記群組；選項一般按字母順序或有證據的頻率排列；「沒有任何一項」為有效答案時須明確提供，並與其他選項互斥，沒有 JavaScript 時需對矛盾選擇回報錯誤；條件揭露只用於簡單的相關問題，複雜問題改分頁；較小的 checkbox 可用於高頻 caseworking 搜尋篩選。官方 Known issues 明言條件顯示的變化不一定被通知，存在 WCAG 2.2 4.1.2 問題。已閱讀頁面 HTML/Nunjucks 主示例、none 與條件揭露的片段及 Recent changes，未做真實互動驗證。
- **反例 A（空白不等於明確零）**：心理師「他處接案」與個案「他處使用」可能需要明確的「已確認沒有」；空白/未勾選不能直接推論為0。若把「沒有他處使用」與「有他處使用」當可同時勾選的多選，會產生互斥衝突。這是對既有業務規則的風險分析，**不是授權新增欄位**。
- **反例 B（單一布林無法承載多態）**：「資格已核准」的 checkbox 未勾選可能代表待審、已拒絕、未適用或未填，不宜直接映射為「不合格」。反過來把所有補助狀態做多選，也可能允許「已核准＋不合格」矛盾；須先確認狀態的互斥性與可稽核來源。
- 限制：GOV.UK 的 JS exclusive 與 aria/fieldset 不等於 Notion Checkbox 原生有同樣行為；未驗 Notion 原生 Select/Status/Formula 或任何實際資料。

## AUTO56-S02｜Radios – GOV.UK Design System
- URL：https://design-system.service.gov.uk/components/radios/
- Canonical：`govuk-design-system:components/radios`；標題：Radios；維護者：GOV.UK Design System team；網頁首發日期未核實；本輪存取日期 2026-10-27。閱讀記號：`AUTO56-S02-R1-MAIN-TEXT-C1`。
- 已核對的文字章節：互斥選一才用 radio；不預先選擇，因選定後通常無法直接回到完全未選；若業務上允許，應明列「None of the above」或「I do not know」；選項順序應謹慎避免偏差；inline 僅短且兩個選項，手機仍會垂直排列；可條件揭露一個簡單後續問題，但不應將複雜問題塞入隱藏區，也不可在 inline radio 上條件揭露。官方 Known issues 同樣記載條件揭露通知的 WCAG 2.2 4.1.2 限制；已閱讀 HTML/Nunjucks 範例、條件揭露與錯誤訊息段落、Recent changes，未進行實際鍵盤/讀屏操作。
- **反例 C（選一不代表能預設）**：Session 的「方案期別」應只有一個有效選擇，但若預選「最新期別」，補登歷史服務時可能套錯費率；單選元件只保證選項互斥，**不保證與服務日期及歷史收費相符**。
- **反例 D（未知不可偷換為否）**：補助資格若只有「符合／不符合」兩選，行政人員尚未取得外部資料時可能被迫選錯；但若在所有表單都加入未知，可能使真正必須完成的最終核准步驟被無限跳過。是否容許未知，須依資料蒐集階段與正式判定階段區分，且保留證據。
- 限制：此為一般 Web 表單設計；Notion Status/Select 的可清空、預設、角色權限及自動化行為未驗，不能當成已實作或 Notion 原生 Radio。

## 跨來源反證、計量及權限界線
- Checkbox 的核心是「多個選擇可並存」；Radio 的核心是「選項互斥」。**狀態的語義與證據，比元件外觀更重要**：未勾選≠已確認0；單選≠已按服務日期選對方案；未知≠不符合。若為了減少欄位把互斥狀態塞進多選，或為了減少點擊預選現行期別，兩者都可能損害歷史帳務正確性。
- 已查索引新候選 **2**；主要正文文字閱讀 **2**；首次獨立反例分析 **2篇（共4情境，不計4次閱讀）**；既有來源完整複讀 **0**；完整 R1 **0**；完整 R2–R10 **0**；本輪 `FULL_DEEP_PASS_10_OF_10` **0**；累積可核實 **0／10,000篇**。
- **NOT_TESTED**：圖片逐張、互動/鍵盤/讀屏/手機、全部歷史研究文件逐檔同文去重、Notion實帳、不同角色、公式、跨期金額、資格與效能。
- **NO NOTION/SYSTEM WRITE**：僅 GitHub 研究與進度記錄；不改 Notion 正式/TEST 頁、DB、View、Formula、Relation、權限、業務資料，也不改正式 GAS、Cloud Run、Session、部署。門檻未達，不進入重新設計；手動與自動研究可獨立並行。
