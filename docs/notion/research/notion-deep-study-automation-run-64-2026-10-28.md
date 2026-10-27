# AUTO-64｜服務導覽與鍵盤跳至主內容：同頁可見性、無障礙及範圍界線（2026-10-28）

- 唯一執行軌跡：`AUTO-64-20261028-0735-RESEARCH`；自動研究，臺灣時間 2026-10-28 07:35 起。
- **授權範圍**：僅公開設計文件閱讀、反例分析、GitHub 研究及進度紀錄；未經10,000篇×10次嚴格深讀及使用者確認，不開始 Notion 重設。**禁止**修改 Notion 正式/TEST 頁面、Data Source、DB、View、Relation、Formula、權限、業務列、正式 GAS、Cloud Run、Session、部署。
- **開始前基準**：main README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、decision-log.md、acceptance-status.md、research/README.md、AUTO-63；另核對 research 目錄75份 Markdown 的檔名與11份非AUTO研究文件全文中是否出現本輪兩個URL。來源索引全文及GitHub程式碼搜尋（service-navigation、skip-link）均未命中兩篇完整canonical URL。**未逐一重讀全部63份AUTO研究全文、未全庫語義去重**，故僅稱「新來源候選」；不以搜尋未命中證明全庫唯一。
- **重複候選排除**：本輪先開啟 GOV.UK Summary list、Tag 官方頁，但回查 sources.md 發現已在 AUTO-50 登記。這兩篇不計新來源，也不將本輪針對性段落複查計為完整R2或新來源。
- **取證等級**：兩篇官方主要正文、HTML/Nunjucks示例及其已知限制文字已閱讀；各一次獨立的反例分析。原始圖像、真實互動、鍵盤焦點/讀屏、手機、Notion真實權限/效能均未實測；**不是完整R1，也不是R2–R10**。

## AUTO64-S01｜Service navigation — GOV.UK Design System

- 官方 URL：https://design-system.service.gov.uk/components/service-navigation/
- Canonical identity：`govuk-design-system:components/service-navigation`；GOV.UK Design System team；頁面首發日期未核。頁面明載2025-06品牌更新，不將更新日冒稱首次發表。
- 閱讀標記：`AUTO64-S01-R1-MAIN-TEXT-C1`；閱讀區段：元件定位、When to use、How it works、服務名稱與導覽連結、目前位置 active/aria-current、HTML/Nunjucks、slots與自訂JS/CSS、語言選單、aria-label準確性、Frontend升級回歸測試、研究段落。
- **官方事實**：服務導覽讓人辨識目前正在使用哪項服務，並在多區域間切換；可僅顯示服務名稱，或附導覽連結。active項目在HTML示例有`aria-current`；自訂slots的樣式與JS需自行維護，版本升級後需重新測試。導覽是否必要仍須按「Help users to navigate a service」模式判斷；**此元件不是 Notion 的原生元件規格**。
- **反例A｜導覽清楚但同頁資料被拆散**：若將治療所 Session、Billing、補助用量只放入頂端導覽入口，畫面雖較短，使用者已確認的「同類資料同頁、開啟即見」會被破壞；跨期對帳仍要反覆切換且可能忘記不同View的篩選條件。導航有助定位≠業務資料已可直接核對。
- **反例B｜active標示與角色權限混淆**：顯示某個模組為當前位置，不代表該使用者有權查看其內的個案/財務資料；若依顯示導航推定權限，可能發生越權暴露。反過來，隱藏入口也不等於資料已受權限保護。
- **可推翻條件**：對實際行政角色、不同螢幕尺寸測量模組定位時間、跨Session/Billing核對步數、登入權限與當前位置提示；若頂層導覽不降低任務時間或提高錯選率，應不採用。未獲改版授權，僅研究假說。

## AUTO64-S02｜Skip link — GOV.UK Design System

- 官方 URL：https://design-system.service.gov.uk/components/skip-link/
- Canonical identity：`govuk-design-system:components/skip-link`；GOV.UK Design System team；首次發表日未核。2026-01修正強制色彩模式下焦點樣式，不代表首發日。
- 閱讀標記：`AUTO64-S02-R1-MAIN-TEXT-C1`；閱讀區段：目的、HTML/Nunjucks、使用時機與頁面位置、鍵盤Tab啟動/視覺顯示、landmark例外、焦點與URL錨點持續的已知不確定性、2020–2026變更。
- **官方事實**：Skip link協助僅用鍵盤的人略過頂部重複導覽，跳到主要內容；在GOV.UK頁面為必要元件，通常置於body開始後（若有cookie banner則在其後）。預設隱藏直到鍵盤焦點到達；官方指出錨點可能在後續頁面造成意外跳轉，對使用者是否有益存在混合意見。**此規範只適用GOV.UK網頁，不等於可直接為Notion頁面插入HTML skip link**。
- **反例A｜同頁22個檢視不等於鍵盤可快速抵達**：治療所同頁保留資料可見性，仍可能因大量導覽與linked views導致鍵盤使用者要Tab多次才能到達常用Session區；但擅自加一個僅外觀像skip link的文字，不保證真正轉移焦點或支援讀屏。
- **反例B｜跳到主內容可能跳過必要狀態**：若把「待核對資格」「收費期別矛盾」等重要資訊放在跳過的導覽區，快捷跳轉可能使使用者漏看。另一方面，強制每次都讀完整導覽會增加重複操作；需要區分重要業務訊息與純導航元素。
- **可推翻條件**：在真正Notion/前台介面以鍵盤、讀屏、縮放及手機檢查焦點順序、跳轉後焦點位置、重要狀態可達性及返回路徑；不能由GOV.UK示例宣稱Notion可直接實作或已通過WCAG。

## 交叉反證、去重與嚴格計量

1. Service navigation回答「目前在哪個服務/模組」；Skip link回答「如何略過重複導覽到工作內容」。兩者都**不**證明資料關聯、補助核定、歷史金額或真實權限正確。
2. 可用性張力：同頁資料直接可見是使用者已核准要求；過多同頁區塊可能增加鍵盤導覽負擔。未經實測不得以單一UX原則直接取代另一需求。
3. **本輪計數**：排除已登記候選2（Summary list/Tag；不計完整複讀）；已查索引新來源候選2；主要正文文字閱讀2（各一次）；首次獨立反例2組（各2情境）；完整R1 0、R2–R10 0、`FULL_DEEP_PASS_10_OF_10`新增0；累積可核實完成仍 **0／10,000篇**。
4. **未完成**：全庫逐檔同文異址語義去重、所有原始圖片/動態示例、真人鍵盤/讀屏/手機/縮放、Notion原生實帳、角色權限、跨資料庫篩選、公式真值、效能及實際金額核對。官方GOV.UK HTML元件不是Notion能力證明。
5. **NO NOTION/SYSTEM WRITE**：本輪只記研究及GitHub進度；不修改Notion/正式系統，不開始重新設計；雙軌排程與手動續作可並行，共用文件採最新SHA條件更新。
