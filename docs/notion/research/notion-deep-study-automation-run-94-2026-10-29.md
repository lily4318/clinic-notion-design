# AUTO-94｜Notion 深度學習：WCAG 2.2 重複輸入與鍵盤焦點遮擋（2026-10-29）

- Trace：`AUTO-94-20261029-1336-WCAG-REDUNDANT-FOCUS`；本次為自動研究軌跡，與聊天手動續作獨立。
- **僅研究公開資料與 GitHub 研究紀錄**；沒有操作 Notion 正式／TEST 頁、DB、View、Formula、Relation、權限或業務資料，亦沒有修改 GAS／Cloud Run／Session／部署。
- 起始先讀 main 七份根／Notion 規範與 sources、research README、首批 evidence-register、研究進度、研究→實作矩陣及最新 AUTO-93；查 research 目錄清冊（當時105檔）。寫入前重新 Fetch sources；兩 canonical URL 在 sources 全文和 GitHub code search 均未命中。**僅新來源候選2**，全歷史逐檔與同文異址／跨語系語義去重仍待完成。
- 讀取方式：W3C 官方 Understanding 頁文字及段落，交叉查 WCAG 2.2 Recommendation 與兩篇實作技巧（G221、C43）；未逐一查證所有外鏈／原始示範、影片、實機互動、鍵盤、讀屏、行動裝置。**文字閱讀是部分取證，非嚴格完整R1**。

## S01｜SC 3.3.7 Redundant Entry（Level A）
- 標題：Understanding Success Criterion 3.3.7: Redundant Entry | WAI | W3C
- 原文：https://www.w3.org/WAI/WCAG22/Understanding/redundant-entry.html
- canonical ID：`w3c-wcag22-understanding:redundant-entry`；維護者：W3C WAI AG WG；頁面顯示更新 **2025-09-17**；本次查核 **2026-10-29**。
- 閱讀事件：`AUTO-94-20261029-1336-WCAG-REDUNDANT-FOCUS-S01-R1-HTML-EXPLANATION-EXAMPLES-TECHNIQUES-PARTIAL`。
- 取證範圍：官方頁 L21–119，逐節查看 In Brief、SC、Intent、Exceptions、Benefits、Examples、Techniques、Key Terms；另查 WCAG 2.2 規範目錄與 G221 技巧（輔助資料，不另計新來源）。
- 核心：**同一流程**已輸入的資訊再次需要輸入時，應自動帶入或提供選取；例外包括確有必要、資安需要、舊值失效。官方明言不要求跨工作階段保存；瀏覽器 autocomplete 本身不等於滿足這項準則。可供選取的資訊理想上在同頁，最好預設可見、貼近輸入欄。官方也明示不當預填可能造成個資外洩。
- 反例 A1【跨日回訪個案可自動沿用上次 Session 的收費金額／方案期別】：WCAG 限同一流程重複輸入，不要求跨次歷史自動帶入；歷史金額與核定期別須以當時有效規則判斷，不可因便利而錯套新期價格。
- 反例 A2【讓心理師在同一次工作流程重填個案、方案、日期是更安全】：不必要重複輸入增加錯誤；應優先考慮已有選取資料或同頁核對，惟涉及敏感資料時需確認權限與最小揭露。
- 反例 A3【自動填入所有欄位就是符合 WCAG 且符合個資保護】：規範有失效／資安例外；跨個案或不同登入角色自動填入可能洩漏資訊，**降低重複輸入不等於取消必要的身分與業務核對**。

## S02｜SC 2.4.11 Focus Not Obscured (Minimum)（Level AA）
- 標題：Understanding Success Criterion 2.4.11: Focus Not Obscured (Minimum) | WAI | W3C
- 原文：https://www.w3.org/WAI/WCAG22/Understanding/focus-not-obscured-minimum.html
- canonical ID：`w3c-wcag22-understanding:focus-not-obscured-minimum`；維護者：W3C WAI AG WG；頁面顯示更新 **2026-06-15**；本次查核 **2026-10-29**。
- 閱讀事件：`AUTO-94-20261029-1336-WCAG-REDUNDANT-FOCUS-S02-R1-HTML-OVERLAYS-EXAMPLES-TECHNIQUES-PARTIAL`。
- 取證範圍：官方頁 L21–145，逐節查看 SC、Intent、movable/user-opened content、sticky overlays、modal、Benefits、Examples、C43／F110；另查 WCAG 2.2 規範及 C43 技巧（輔助，不另計來源）。
- 核心：當元件取得鍵盤焦點，不應被作者產生的內容**完全遮住**。這是 AA 的最低門檻，並非「全部可見」；完全不遮擋是更高的 AAA 準則。固定表頭、底部警示、持續開啟的浮層可能遮擋；使用者主動開啟的持續浮層若可不移動焦點即揭露目標，有特定例外。合格 modal 會移轉並維持焦點；非 modal 不能逕自假定安全。
- 反例 B1【Notion 同頁直顯表格加固定工具列後，畫面看起來整齊就算可操作】：在鍵盤 Tab 移動時，焦點可能被固定列／浮層完全蓋住；要依真實視窗大小、縮放與鍵盤路徑測試。
- 反例 B2【只要焦點有一部分可見，就能宣稱使用者操作一定清楚】：AA 最低門檻容許部分遮擋，仍可能造成理解困難；應盡量完全可見，不能把規範最低值當理想UX。
- 反例 B3【把警示做成常駐浮動框就能兼顧安全提醒與資料操作】：浮層可能遮住焦點與收費欄位；對治療所高頻 Billing／Session 流程，應另驗證焦點、鍵盤復原與是否擋住必要欄位，**不授權本輪改版**。

## 交叉結論／證據分界
- WCAG 3.3.7 提醒減少**同一活動內**的重複輸入，2.4.11 提醒同頁操作時避免鍵盤焦點被遮擋；兩者皆不能推論 Notion 原生符合規範或本所工作台已通過真人操作。
- 參照的 W3C WCAG 2.2 Recommendation：https://www.w3.org/TR/WCAG22/ （頁首列2024-12-12 W3C Recommendation）；Understanding 頁屬**非規範性解說**，規範正文才是符合性依據。G221：https://www.w3.org/WAI/WCAG22/Techniques/general/G221；C43：https://www.w3.org/WAI/WCAG22/Techniques/css/C43；均為**輔助交叉核對，不另算閱讀篇數**。
- 待補：跨歷史 URL/內容語義去重、頁面所有外鏈／示範、Notion 實際多角色與歷史金額、鍵盤/螢幕閱讀器/手機、效能與可用性；未做任何正式資料測試。

## 本輪嚴格計量與停止線
`NEW_SOURCE_CANDIDATE=2`、`PARTIAL_TEXT_READ=2`、`COUNTEREXAMPLE=6`、`FULL_R1=0`、`FULL_R2_TO_R10=0`、`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`。累積可核實完成 **0/10,000篇**；不可將來源命中、兩種角度或輔助技術頁重複計數。10,000×10 未達成，**不得進入 Notion 重新設計**，與手動續作維持雙軌並行。
