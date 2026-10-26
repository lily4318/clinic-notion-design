# AUTO-38｜2026-10-27 05:43 Asia/Taipei｜Notion 資料庫範本與權限語意研究

Trace: `AUTO-38-20261027-0543-RESEARCH`；範圍：公開原文閱讀、反例研究、GitHub 證據記錄；**Notion 與正式系統零寫入**。

## 本輪基準與去重

開始與寫入前已 Fetch `main`：`README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`；研究目錄列出49份 Markdown（含README/原理/各輪/清冊）。逐檔讀取49/49並比對本輪候選的 URL slug/標題：`using-database-templates-for-teams` 未見登錄；`intro-to-databases` 在 batch-02 及十面向研究已登錄，不重計新來源。索引中 `database-templates` 其他連結不等於本篇獨立教學。只稱已檢查當期研究清冊；全儲存庫其他路徑及同文不同 URL 的全域去重仍未完成。

## AUTO38-S01｜新來源候選：Using database templates to help cement your team's process

- URL（canonical）: https://www.notion.com/help/guides/using-database-templates-for-teams
- 去重ID：`notion:help/guides/using-database-templates-for-teams`
- 來源／作者：Notion 官方；網頁未確認具體作者或發布日；檢索與閱讀：2026-10-27 05:43–本輪；類別：Notion 官方指南、資料庫範本與標準化流程。
- 本次獨立閱讀識別：`AUTO38-S01-R1-TEXT`，僅一次。可讀正文覆蓋「What are database templates?」「How to make database templates」「How to customize your database templates」「Where to use database templates」及各例子；來源頁面可見約6分鐘閱讀標記，非實測耗時。原始圖片、可展開的 template buttons、外部模板實體、影片及帳戶操作**未完整查核**；狀態 `R1_MAIN_TEXT_ALL_FOUR_SECTIONS+C1`，**不等於完整深讀1/10**。
- 原文可核實機制：資料庫範本是**特定資料庫內**可重用的頁面格式，與 Marketplace 模板不同；可從 New 選單建立；可預設屬性值、標題、填寫提示、linked database；可修改範本以影響後續建立頁面的格式。文章列會議、任務、文件三類重複性工作。原文沒有證明範本會自動保證業務規則正確。
- 首次獨立反例 `C1`：若為「收費方案期別」建立含「目前金額」「當期期別」預設值的範本，工作人員新增歷史 Session 時可能保留不適用的預設值；**格式標準化不能替代按服務日期核定有效期、歷史金額快照與人工核對**。反方向反例：若為所有會談強制增加大量欄位和說明，雖然統一格式，卻可能違反使用者要求的少填寫與同頁直顯。兩者均屬對本所的研究假說，**不是實際系統已出錯的證據**。
- 設計研究判斷（未核可／未實作）：範本只適合重複性工作之最少必要提示與不具風險的預設；不能以預設金額、預設資格、預設已確認狀態代替跨期邏輯。任何提案仍須先讀現況 Schema／依賴與業務規則。
- 來源核對：網頁正文 https://www.notion.com/help/guides/using-database-templates-for-teams；正文段落與例子均可取得。未複製原文大量文字。

## AUTO38-R01｜已登錄來源：Intro to databases（由 SUMMARY_ONLY 升級為主要正文研讀）

- URL（canonical）: https://www.notion.com/help/intro-to-databases
- 去重ID：`notion:help/intro-to-databases`；既有登錄：`notion-deep-study-evidence-batch-02-2026-10-25.md` 中 `DS-025`（`SUMMARY_ONLY`，直開當時失敗），另 `notion-ux-research-and-10-lens-review-2026-10-25.md` 中 `N15`；**不是新增來源**。
- 本輪獨立閱讀識別：`AUTO38-R01-R1-TEXT`；此次原文可讀，完整走查正文「Create a database」「Full-page vs. inline databases」「Duplicate a database」「Add and open database pages」「Item options」「Customize database pages」「Collaborating in a database」「Can edit content」「Lock views」。原始圖片、影片、真實權限與跨角色測試未完成；僅將過去 SUMMARY_ONLY 提升為本輪 `R1_MAIN_TEXT_ALL_SECTIONS+C1`，不將先前摘要當完整R1，也不計本次為完整R2。
- 可核實機制：資料庫每列為頁面；Full-page/Inline 有不同入口與視覺操作；頁面屬性可 always show、hide when empty、always hide；「Can edit content」能建立/修改資料頁與屬性值，但不能修改**原資料庫**的 properties/views/filter/sort；官方另註明此角色仍可建立 linked database 並編輯**該 linked database 的 views/sorts/filters**。資料庫 Lock view 主要防意外操作，具編輯權者可以切換，**不是權限隔離保證**。
- 本次新增反證 `C1`：若把某個 linked view 的「只看本期」篩選當作補助資料的權限邊界，使用者可能仍可透過來源或其他 linked view 接觸其原本有權查看的資料；即使將原資料庫 lock 也不能視為不可修改的法規/安全管控。另一方面，若因資訊多就把「期別」「資格未核對」欄位 Always hide，雖然畫面精簡，可能造成錯誤收費判斷；需要區分可隱藏的非關鍵資訊與業務必看資訊。**此為根據官方能力提出的風險推論，不代表已在治療所權限實測證實**。
- 來源核對：https://www.notion.com/help/intro-to-databases；2026-10-27 當次讀到上述全部正文小節。

## 獨立性、限制與進度

- 本輪新 canonical URL 候選：**1**（S01）；已登錄來源重新成功閱讀正文：**1**（R01，舊摘要升級）；主要正文獨立閱讀：**2篇各1次**；本輪新反例：**2**；既有來源完整十次深讀新增：**0**。
- **FULL_DEEP_PASS_10_OF_10：本輪0，累積可核實0／10,000篇**。沒有任何一篇已具備10次相互獨立、含必要視覺/互動/反證的完整閱讀證據。搜尋命中、同篇兩個面向、已登錄來源升級，不冒稱新篇或10次閱讀。
- 未驗：原圖逐張、嵌入影片、可展開互動、Marketplace模板內容、Notion實際頁面/DB/Schema/View/公式、角色權限、手機UX、載入秒數、補助核定規則與歷史收費公式真值；全庫跨檔/同文不同URL精確去重仍待完成。
- 安全邊界：本輪僅GitHub研究檔及索引/決策/驗收進度記錄；**未修改Notion任何頁面、資料庫、Data Source、View、Formula、Relation、權限、真實業務資料或正式GAS/Cloud Run/Session/部署**。10,000篇×10次尚未完成，**不進入Notion重新設計**；每小時與手動「繼續」各自執行，寫入前 Fetch 最新 main/blob SHA，衝突不覆蓋其他流程。
