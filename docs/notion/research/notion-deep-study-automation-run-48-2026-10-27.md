# Notion 深度學習｜AUTO-48｜2026-10-27（純研究；無 Notion 寫入）

- 執行軌跡：`AUTO-48-20261027-1537-RESEARCH`；台灣時間 2026-10-27 約15:37；自動研究軌，與聊天手動續作獨立。
- 本輪開始重讀 main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、decision-log.md、acceptance-status.md，另讀 research/README.md 及 AUTO-47 研究檔；寫入前再取最新 main 規範及 blob SHA。
- 去重：兩篇 URL 的完整 canonical slug 均未見於 sources.md；GitHub repo code search 無命中。研究目錄清單59份檔案已取得，但批次逐檔 Fetch 遇工具呼叫上限，**未完成59/59逐檔全文查重**；其他路徑、別名與同文不同 URL 仍未做精確去重，因此只稱「已查索引的新來源候選」。曾考慮 `errors-forms-design-guidelines`，核對後發現已於 AUTO-28 登錄，**本輪不重複計數**。
- 計量：本輪新 canonical 候選 **2**、各一次主要正文文字閱讀 **2**、首次獨立反例分析 **2**、完整深讀 R1–R10 **0**；累積可核實 `FULL_DEEP_PASS_10_OF_10` **0／10,000篇**。正文閱讀不是完整深讀，不把多個章節或分析角度當成多次獨立閱讀。

## AUTO48-S01｜Progressive Disclosure

- 原文：https://www.nngroup.com/articles/progressive-disclosure/
- canonical：`nngroup:articles/progressive-disclosure`；Jakob Nielsen，Nielsen Norman Group，2006-12-03；本次閱讀2026-10-27。
- 獨立軌跡：`AUTO48-S01-R1-MAIN-TEXT-C1`；逐節讀取開頭定義、Applications vs. Websites、Benefits of Progressive Disclosure、Usability Criteria、Staged Disclosure: One Step at a Time（含比較表及飯店預約案例）、Managing Complexity，含文字圖說／外連標籤。
- 原文可核對的區別：**progressive disclosure** 把低頻或進階選項放在第二層，核心工作先可見；**staged disclosure** 把流程拆成必須逐步完成的線性步驟。作者提醒前者初層必須保留高頻任務、次層入口須可發現，超過兩層易迷失；後者若步驟相依、需要反覆跨步比對就可能不合適。
- **新反例 C1：** 本所先前曾實測否決「首頁只留少數表格、其餘移到另一頁」與「補助日常/設定拆頁」，確認同類資料同頁且開啟即見。若只依「漸進揭露」口號將 Session 日期、方案期別、收費金額或補助用量隱藏在二級連結，行政人員將無法在同一畫面交叉核對；但反過來把低頻技術設定和內部 AI 規則全部展開，又會遮蔽高頻資料。原則不是「越少越好」，而是依任務依賴與高頻使用決定初層內容。
- **反證條件：** 如果未來觀察證實特定維護欄位只在少數月度設定情境使用，且獨立查詢不會影響同頁核對，按需揭露可能降低首屏負擔；需要真人角色任務觀察、點擊步數、正確率、手機與桌面可視面積比較，不能從文章直接判定本所介面優劣。
- **證據限制：** 只完成可讀主要正文文字一次；未逐張開啟原圖、未讀完外連原始研究、未驗證 Notion 原生折疊／權限／資料載入，故不是完整 R1 深讀 PASS。

## AUTO48-S02｜Preventing User Errors: Avoiding Unconscious Slips

- 原文：https://www.nngroup.com/articles/slips/
- canonical：`nngroup:articles/slips`；Page Laubheimer，Nielsen Norman Group，2015-08-23；本次閱讀2026-10-27。
- 獨立軌跡：`AUTO48-S02-R1-MAIN-TEXT-C1`；逐節讀取 Two Types of User Errors、Include Helpful Constraints、Offer Suggestions、Choose Good Defaults、Use Forgiving Formatting、Summary，以及圖說與延伸資源標籤。
- 原文可核對的區別：**slip** 是意圖正確但執行時誤觸、誤輸；**mistake** 是目標或系統理解本身不正確。預防 slip 的方法包括適當限制、搜尋建議、合理預設與寬容輸入格式；原文也指出熟練使用者因自動化操作可能發生 slip。
- **新反例 C1：** 治療所行政人員補登歷史 Session，可能因熟練而快速選到「最近使用的方案」或預設當期金額。即使選單的預設值通常能降低誤輸，跨年或同年多期別時反而可能使歷史收費錯誤更隱蔽。需以服務日期對應有效方案期別並顯示異常，不能只依最近使用或資料列名稱。
- **新反例 C2：** 若硬性禁止選擇所有看似與 Care Episode 主方案不同的 Session 方案，可能阻擋合法的例外收費或歷史調整；但完全無提示又易發生 slip。故「限制輸入」與「允許有證據的例外」須依業務規則區分，未知／待人工核對不可當成已確認零或已核准。
- **反證條件：** 若真實流程證實某些欄位具有無例外的唯一規則，硬性限制可能比提醒更安全；需要獨立核定依據、例外案例、跨期樣本與角色操作測試才能選擇阻擋或警示。
- **證據限制：** 可讀主要正文文字一次，圖說已讀但原始圖片、海報 PDF、延伸書籍、真實 Notion 互動／公式／角色權限／效能均未驗證；不計完整 R1 深讀 PASS。

## 跨篇結論、未完成與安全界線

1. 「漸進揭露」應先區分**同頁交叉核對**與**低頻設定**；「合理預設」應先區分**日常新服務**與**補登歷史 Session**。兩篇原則相互制衡，不等於任何新的 Notion 版面決定。
2. 本輪**未修改**任何 Notion 正式或 TEST 頁面、Database、Data Source、View、Formula、Relation、權限或個案／收費資料；亦未修改 GAS、Cloud Run、正式 Session 或部署。GitHub 僅記錄研究及進度。
3. 僅主要正文文字與首次反例分析可稽核；所有原圖、外部延伸全文、同文異址精確去重、真人 UX、手機、權限、原生公式及效能仍 NOT_TESTED。達標 10/10 篇數新增0、累積0/10,000。**未經完成與使用者確認，不進入 Notion 重新設計。**
