# Notion 深度學習｜AUTO-36｜2026-10-27（研究證據，非實作）
- 執行軌跡：`AUTO-36-20261027-0344-RESEARCH`；範圍：公開來源研究、GitHub 研究清冊；**禁止修改 Notion／GAS／Cloud Run／Session**。
- 開始前已重新讀取 main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、decision-log.md、acceptance-status.md；以 main Git tree 確認研究目錄47份 .md，逐檔查本輪候選slug。
- **去重結果**：下列 S01、S02 在當時 sources.md 與47份研究文件均無相同 canonical slug；暫列新來源候選，非全儲存庫歷史的精確唯一總數。另兩篇原本考慮作為新來源，查出已有登錄（見 R01、R02），因此不重算。
- 來源採原文正文逐節核對；網站圖片只讀到圖說，未逐張檢查原始圖片／影片、未做 Notion 實際操作。R1 僅標示 **主要文字閱讀＋首次獨立反例**，不冒稱完整深讀。

## S01｜Notion 官方：Databases reimagined— what’s changed?
- URL：https://www.notion.com/en-gb/help/guides/databases-reimagined-whats-changed
- Canonical identity：`notion:help/guides/databases-reimagined-whats-changed`；類別：Notion 官方教學；閱讀：2026-10-27，`R1_MAIN_TEXT+COUNTEREXAMPLE_01`；原文未在可讀頁面明示可核實的首次發表日期。
- 已讀段落：What's new（quick filters、data sources、View options）、Consolidate single source of truth、When to use existing data source、Views/tabs、Unified View options、Quick filters、結語。
- 原文證據：可重用同一資料來源與檢視、各 View 自訂 filter/sort/group、臨時 quick filter 可在「Save for everyone」前保持個人檢視；多來源可以用 tabs 集中。此為官方說明，不是本所實際功能測試。
- **獨立反例 C1**：官方主張用 tabs 節省版面；但治療所同時核對「個案方案餘額」與「心理師本週額度」時，若兩者被分到互斥 tab，工作人員無法同時比較，反而違反已確認的「同頁直接看見資料」；因此「集中資料來源」不等於「將所有業務資料塞進單一 tab 或單一資料庫」。
- **獨立反例 C2（同次分析，非第二次閱讀）**：個人 quick filter 未「Save for everyone」與共享 View 不同；工作者看到自己的篩選結果，不代表其他工作者看到同一範圍。若以篩選結果作補助用量核定依據，可能漏掉其他期別或未確認資料。須先界定 View 篩選的可見性與角色。
- 待核實：現行 Notion workspace 方案、原生 quick filter 行為、同步來源與多來源 tab 的實際可用性、手機呈現、資料權限、速度。無實測、無改版決議。

## S02｜NN/g：Does Your Form Really Need a Dropdown List?
- URL：https://www.nngroup.com/articles/dropdown-list/
- Canonical identity：`nngroup:articles/dropdown-list`；作者 Huei-Hsin Wang；發表 2026-07-17；類別：UX 介面選項控制；閱讀：2026-10-27，`R1_MAIN_TEXT+COUNTEREXAMPLE_01`。
- 已讀段落：Definition、Appeal、Hidden costs（discoverability / interaction cost / accessibility / illusion of clean data）、When to avoid（少量／大量選項、熟悉數值、視覺比較）、When still useful（中量選項、次要欄位、同組欄位與兩例）、Conclusion。
- 原文證據：選單隱藏選項雖省空間，會增加探索、捲動與誤選成本；大量選項可考慮可搜尋的 combobox；少量選項在能直接顯示時可比較；選單適用情況有例外，尤其密集行政介面的次要設定與成組欄位。
- **獨立反例 C1**：治療所「收費方案＋核定期別」若以兩個長選單分開選取，工作者可能在未看見完整期別有效日／金額前誤選；但若為了可見性將所有年度期別選項全攤開，當方案增多時反而擁擠。應研究可搜尋、附帶期別識別線索的選擇方式，並核對 Notion 原生 Relation/Select 能力，不得推定可客製 combobox。
- **獨立反例 C2（同次分析，非第二次閱讀）**：預設選中「本期」會讓畫面看似已有合法值，但歷史 Session 必須保留當次價格／期別，不可依目前預設自動覆蓋。**選項合法**與**業務判定正確**是兩件事。
- 待核實：原圖與行動操作、Notion 既有欄位的搜尋/標籤能力、歷史 Session 金額快照、真實使用者誤選率；文章建議的數量區間是情境參考，非 Notion 硬性規格。

## 已有來源之針對性重讀（不計新 URL、不計完整 R2）
- R01：Notion 官方 [Three key databases for teams, and how to use them](https://www.notion.com/en-gb/help/guides/three-key-databases-for-teams-and-how-to-use-them)；canonical `notion:help/guides/three-key-databases-for-teams-and-how-to-use-them`。去重：`notion-deep-study-evidence-batch-03-2026-10-25.md` 已記錄。本次重看 Meeting Notes、Docs、Tasks/Projects、relations/rollups、contextual views、linked sources 的主要文字；**新反證**：官方「三類核心資料庫」是一般團隊範例，不能取代治療所「個案×方案期別用量」等業務實體，否則會混合不同權威歸屬。計為一次針對性重讀，不算完整第二輪。
- R02：NN/g [Few Guesses, More Success: 4 Principles to Reduce Cognitive Load in Forms](https://www.nngroup.com/articles/4-principles-reduce-cognitive-load/)；canonical `nngroup:articles/4-principles-reduce-cognitive-load`。去重：`notion-deep-study-automation-run-25-2026-10-26.md` 已記錄。本次重看 Structure、Transparency、Clarity、Support 主要文字；**新反證**：文章倡議表單漸進揭露，但本所已否決把日常必要資料分頁藏起來；只可將低頻輸入欄分階段呈現，不能藏核對用量與核定狀態。計為一次針對性重讀，不算完整第二輪。

## 本輪可核實進度與限制
- 新 canonical 候選：**2**（S01、S02，依 sources.md＋研究目錄47份暫時去重）；新來源主要正文 R1：**2**；首次獨立反例：**2**（每篇至少一組；多角度不多算）；既有來源針對性重讀：**2**；新增完整 R2–R10：**0**。
- `FULL_DEEP_PASS_10_OF_10`：本輪 **0**，累積可稽核 **0／10,000篇**；全庫唯一來源總數仍需完整跨檔 canonical 去重。
- **NO NOTION/SYSTEM WRITE**：僅GitHub研究證據；不更動Notion正式/TEST頁、DB、Data Source、View、Relation、Formula、權限、業務資料、GAS、Cloud Run、Session、部署；未開始重新設計。
