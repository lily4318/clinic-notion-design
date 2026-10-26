# Notion 深度學習｜AUTO-33｜2026-10-27（研究，無系統寫入）

- 獨立 trace：`AUTO-33-20261027-0038-RESEARCH`；工作路徑：每小時研究續作；僅限公開 UX 研究與 GitHub 記錄。
- 起始核對：main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、decision-log.md、acceptance-status.md；研究目錄 44 份文件逐檔檢查兩個新來源 slug，44/44 可讀且未發現相同 slug；sources.md 也無這兩個 slug。GitHub code search 兩個 slug 零命中僅為輔助，不當作唯一去重證據。
- 閱讀規則：每篇只有**一次**獨立 R1 主要文字與反例分析；未逐張驗證原圖、外連研究檔、互動、真人或 Notion 原生實際操作，因此不算完整深讀，不建立 R2–R10 虛構次數。
- 注意：舊來源 NN/g Progressive Disclosure（首批 evidence-register U01）與 Memory Recognition and Recall（batch-02、AUTO-22 已提及）本輪雖有閱讀，均**不算新來源**，且只登記為針對性複讀，非完整第二遍。

## AUTO33-S01｜新來源候選｜導航分類命名

- 標題：**5 Tips for Avoiding Confusing Category Names**
- 作者／來源：Hoa Loranger、Taylor Dykes；Nielsen Norman Group；發表 2013-12-15，頁面標示 2024-10-11 review。
- 原始 URL：https://www.nngroup.com/articles/category-names-suck/
- 去重 ID：`nngroup:articles/category-names-suck`（移除 query、fragment、尾斜線；同語系或鏡像不再新增篇數）。
- 取證：2026-10-27 00:38 後，直接開啟可讀文章；已讀主要正文「Users Prefer Clear Over Clever」、「Five Tips」五項與結論（頁面 web 行 40–96），並核對各例圖的**文字圖說**。層級：`R1_MAIN_TEXT_ALL_5_GUIDELINES+COUNTEREXAMPLE_1`；未逐張檢查原圖或進行 card sorting/tree testing。
- 五項論點：①名稱具體且貼近日常用語；②避免內部造詞；③分類意義不可高度重疊；④依工作者心理模型而非組織架構命名；⑤以真實使用者驗證名稱，不憑設計者直覺。
- 獨立反例／反證：若只把「政府補助」「方案用量」「本週額度」全改成看似簡短的「管理」「資料」，會讓不同角色無法預測入口內容；反之將每一項都命名為很長的正式術語也會擠占首頁。不能把 UX 文章的網購導覽範例直接推論為治療所工作者已理解哪些標籤。
- 可驗證的後續研究問題（**不是改版指令**）：以三種真實任務（查個案期別餘額、查心理師本週用量、查核方案設定）比較入口預測正確率、誤點與完成時間；無真人測試，尚無優勝命名結論。
- 限制：原始圖片未逐張驗、無原始研究樣本/量化資料、未驗證 Notion 目前 UI。**不是 FULL_DEEP_PASS**。

## AUTO33-S02｜新來源候選｜資訊分散的研究方法

- 標題：**Content Dispersion: Study Methodology**
- 作者／來源：Kim Flaherty、Tim Neusesser、Nishi Chitale；Nielsen Norman Group；2023-10-13。
- 原始 URL：https://www.nngroup.com/articles/content-dispersion-methodology/
- 去重 ID：`nngroup:articles/content-dispersion-methodology`。
- 取證：2026-10-27 直接開啟正文，讀完「Content-Dispersed Layouts」「Analysis」「The Prototypes」「Study Methodology」「Conclusion」（web 行 40–136），核對圖片圖說；層級：`R1_MAIN_TEXT_METHODS+COUNTEREXAMPLE_1`。Figma 外連原型、圖片原檔與問卷未逐項查驗。
- 方法細節：比較分散與緊湊的首頁、產品頁共四原型；分散版例子平均每視窗少於7個獨立內容元素、未用空間約30%；較緊湊例子約8–14個、空白約17%。這些是該研究的**描述性原型數據，不是通用 KPI 或 Notion 最佳欄數**。招募13人，其中5人 pilot、8人正式版本；對四原型的順序隨機化，含質性任務、問卷與訪談。
- 重要方法限制：文章承認不同品牌、不同圖像、部分文案、產品價格／規格等混淆因素難以完全排除；其網站類型與治療所行政資料庫不同，不可直接推論「資訊越密越好」。
- 獨立反例／反證：若為了消除空白而把補助資格、不同核定期別、歷史計次與每週用量壓縮成單一密集表格，雖可能減少捲動，卻會提高誤讀/誤選；若為了極簡而讓同一任務的關鍵比較值分散到數個螢幕，則增加記憶與捲動成本。必須比較**任務完整性、誤判率、操作步數與閱讀時間**，不能把 7/14 或 17%/30% 當治療所硬門檻。
- 限制：非 Notion 研究、非行政現場樣本、原型與圖像未實際操作；**不是 FULL_DEEP_PASS**。

## 既有來源針對性複讀（不新增篇數、不算完整 R2）

- `AUTO33-R01` [Progressive Disclosure](https://www.nngroup.com/articles/progressive-disclosure/)；原始清冊 U01 已登錄；本輪重讀原文 Applications vs Websites、Benefits、Usability Criteria、Staged Disclosure、Managing Complexity。**新反證**：階段式披露不同於進階資訊按需展開；需要反覆比較的「方案期別＋個案餘額＋本週額度」不可拆成連續步驟，文章的旅館房價比較案例正好支持同頁比較。狀態 `TARGETED_REVISIT_NOT_FULL_R2`。
- `AUTO33-R02` [Memory Recognition and Recall in User Interfaces](https://www.nngroup.com/articles/recognition-and-recall/)；已見 batch-02、AUTO-22 去重提醒；本輪重讀記憶提取、練習/近期/情境、選單、最近瀏覽、行動圖示。**新反證**：熟練行政人員可能靠記憶快速使用捷徑，卻不能以此要求新進工作者記住不透明的圖示或資料庫代碼；短標籤加可見選項比大量教學文案更接近識別而非回憶。狀態 `TARGETED_REVISIT_NOT_FULL_R2`。
- 同一次讀取各只計一次針對性重讀，不把不同分析角度拆成多輪。

## 本輪計數與安全

| 項目 | 本輪 | 累積嚴格達標 |
|---|---:|---:|
| 新來源候選（已查清冊去重） | 2 | 全域精確篇數待稽核 |
| 可讀主要正文 R1 | 2 | 非完整深讀 |
| 首次獨立反例分析 | 2 | 非完整深讀 |
| 舊來源針對性複讀 | 2 | 非完整 R2 |
| 每篇 10 次獨立完整深讀達標 | 0 | **0 / 10,000** |

沒有更動 Notion 正式／TEST 頁面、資料庫、Data Source、View、Formula、Relation、權限、業務列，也沒有更動 GAS、Cloud Run、Session 或部署；沒有開始重新設計。僅保存公開研究索引與進度，不存敏感資料。
