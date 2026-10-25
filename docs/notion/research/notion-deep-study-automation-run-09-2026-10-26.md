# Notion 深度學習｜排程獨立研究批次 AUTO-09（2026-10-26）

> 研究軌跡：`AUTO-09-20261026-0041-ASIA-TAIPEI`。本批僅讀公開官方文件、更新 GitHub 研究清冊；**不修改任何 Notion 頁面、資料庫、View、Formula、Relation、權限、業務資料或正式 GAS/Cloud Run/Session**。使用者要求10,000篇唯一來源各10次獨立完整深讀；本批是可稽核的首次分析，**不是完整深讀十次，也不是開始設計的授權**。

## 1. 查核、去重與閱讀證據

- 2026-10-26 00:41（Asia/Taipei）開始本次排程研究。先讀取GitHub `main` 的 `README.md`、根 `AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`；並讀取首批16篇清冊、第二/三/四批、十面向研究、AUTO-01～08及MANUAL-01研究檔。
- 與上列研究紀錄中URL slug逐一核對，本批下列3篇均**未見登錄**；對 `/en-gb/help/suggested-edits` 以英文區域語系為現有可讀來源，但其唯一文章身分按slug `suggested-edits`，不把 `/help/suggested-edits` 另計篇數。新來源各只計1篇；若並行工作另有同slug新增，全球唯一清冊仍需合併、不可雙算。
- 實際透過官方網站讀取全部可取得的主要文字小節與FAQ，分別涵蓋Comments頁約L106–285、Suggested edits約L106–150、Links & backlinks約L106–213。網頁動態圖片/影片未逐一開啟、官方頁可能隨時更新，未做實際帳號角色/行動裝置測試。故三篇的級別為 `MAIN_TEXT_SECTIONS_READ + ANALYTICAL_PASS_1`，**嚴格 `FULL_DEEP_PASS` = 0**。未驗證正式發表/修訂日期，不猜測版本號。
- 研究不是病歷或臨床資料查核，沒有取得/提交任何個資或 raw Notion records。

| Source ID | 官方標題／唯一文章URL | 已讀主要段落 | 實讀狀態 | 10次深讀 |
|---|---|---|---|---|
| AUTO09-01 | [Comments, mentions & reactions](https://www.notion.com/help/comments-mentions-and-reminders) | 頁面/行內/資料庫/屬性留言、留言面板與Resolved、@人/頁/日期、通知、Reactions、FAQ | `MAIN_TEXT_SECTIONS_READ; ANALYTICAL_PASS_1` | `0/10 FULL` |
| AUTO09-02 | [Suggested edits](https://www.notion.com/en-gb/help/suggested-edits) | Suggesting模式、Can comment門檻、支援的文字Block類型、限制、接受/拒絕 | `MAIN_TEXT_SECTIONS_READ; ANALYTICAL_PASS_1` | `0/10 FULL` |
| AUTO09-03 | [Links & backlinks](https://www.notion.com/help/create-links-and-backlinks) | @mention/[[/+/Link to page、Block anchors、Web mentions、Backlinks權限與FAQ | `MAIN_TEXT_SECTIONS_READ; ANALYTICAL_PASS_1` | `0/10 FULL` |

## 2. 首次分析與獨立反例

### AUTO09-01｜留言、提及與反應

- **初始假設**：只要在某筆補助核定紀錄的資料庫屬性留下評論並@負責人，就代表該核定欄位已完成覆核，相關人員也一定會收到提醒。
- **原文證據**：留言可針對頁面、行內文字、資料庫頁及資料庫屬性；Resolved的留言仍可在留言面板篩選及重新開啟；@mention人員、頁面與日期用途不同；在對方**無權存取**的頁面@提及，不會通知該人。Notion開啟狀態亦影響推播/郵件路徑。
- **反例**：某個案額度資料在私人頁面被@提及，對方因無權存取不會收到通知；即使收到並將討論串標Resolved，欄位仍可能保持未核對或數值有誤。評論解決狀態與正式核定狀態不是同一資料來源。
- **修正理解**：溝通事件（留言/@提及/Resolved）≠可稽核的業務審核、角色授權或補助額度真值；單靠留言不可取代業務欄位、人工核定流程及存取權限驗收。沒有授權在現有頁面新增留言規則。
- **交叉來源**：AUTO-04 通知中心與設定顯示推播受客戶端狀態影響，這與本篇無權存取頁面不通知是兩個獨立阻斷點；不能由通知中心無通知推論不存在待辦。
- **待驗證**：真實Free/Plus方案、Guest與Member的評論/通知差異、對不同角色的私人頁面通知、評論歷史留存及法規稽核要求。第2–10次**未執行**。

### AUTO09-02｜建議修改

- **初始假設**：讓只有評論權限的人使用Suggested edits，就能安全提出資料庫欄位、公式、補助期別與額度的修改草稿，經核准後再寫入。
- **原文證據**：至少`Can comment`才可提議；頁鎖或權限不足可能無法提議；可建議文字、待辦、標題、項目符號/編號清單；**不支援 inline database、database properties 或 peek view中的頁面**。接受建議會修改頁面文字，拒絕則移除提議。
- **反例**：要更正個案額度Formula或Relation，Suggested edits根本不能在相關資料庫屬性上形成待批准的變更；若改為在旁邊寫一段「建議改成X」，只留下說明文字，無法保證實際業務資料正確或權限受到約束。
- **修正理解**：Suggested edits是文件協作審稿工具，不能當成資料庫Schema、業務核定或公式變更的正式approval workflow。接受提議也不等於執行過真值驗收或備份。
- **交叉來源**：AUTO-03的`Can edit content`及AUTO-05 Buttons各有不同操作/權限語意，不能因「有審核介面」便推論擁有資料層級審批；也不應擅自在現有Notion增加流程。
- **待驗證**：不同頁面鎖定狀態、Suggested edits的版本歷史與完整追溯、是否支援手機、權限/方案實帳差異。第2–10次**未執行**。

### AUTO09-03｜連結與反向連結

- **初始假設**：只要將行政文件頁放進Link to page並有Backlinks，就能建立可供所有人使用、完整且安全的跨頁索引，還可依Backlinks清單判斷頁面是否無引用可刪除。
- **原文證據**：@mention、`[[`、`+`可以插入頁面引用；`Link to page` block會讓連結頁出現在側邊欄，類似子頁導覽；每個Block可複製anchor link；@mention頁面會自動建立Backlink；Backlinks顯示受**查看者可存取權限**限制，私人頁可能顯示`Private`或不顯示，無權者不能藉Backlink打開該頁。
- **反例**：管理員檢查某舊版工作台時看不到任何Backlink，可能只是目前帳號沒有權限看另一處引用，並非真正沒有依賴；因此不能只憑「Backlinks=0」就刪除原始資料源或同步區塊。反向連結也不是正式Data Source Relation，不能依它推算補助計次。
- **修正理解**：導覽連結、反向連結、資料庫Relation與權限是四種不同語意。Backlink是方便查找的**部分可見索引**，不能單獨作為無引用/可刪除的依賴證明；這一輪不做任何刪除或調整Sidebar。
- **交叉來源**：AUTO-07側邊欄搬移權限風險、AUTO-08 Hide不等於Delete，以及第三/四批Synced blocks共同引用風險：任何「舊設計清理」仍需獨立檢查所有引用及資料保存，不能因Backlink畫面空白就認定安全。
- **待驗證**：跨角色Backlinks顯示與Private標籤、不同連結種類的引用可發現性、已封存頁面的Backlink行為、實際可稽核的依賴盤點方法。第2–10次**未執行**。

## 3. 本批跨來源檢驗

1. **評論Resolved≠資料核定**：協作狀態不可代替公式、核定期別與計次真值。
2. **Suggested edits≠資料庫審批**：能提出文件文字變更，不代表能提議或審核Schema/Formula/Relation。
3. **Backlinks缺席≠沒有引用**：顯示受權限影響，不能用來宣告無依賴而直接刪除。
4. **可見UI≠權限/資料真值**：三篇官方文件分別說明溝通、文件審稿、導航三個層次，均未提供資料庫級交易一致性或正式審核保證。

## 4. 可稽核結果與硬界線

| 指標 | 本輪真實值 |
|---|---:|
| 已核對去重的新官方文章URL | **3** |
| 本輪可取得的主要文字章節閱讀 + 一輪反例分析 | **3** |
| 本輪逐張圖片/嵌入影片與實帳操作 | **0** |
| 本輪嚴格完整深讀Pass | **0** |
| 累積完成每篇10次完整深讀篇數／目標 | **0 / 10,000** |
| Notion Page/DB/View/Formula/Relation/權限/業務資料/GAS/Cloud Run/Session變更 | **0** |

只有真正的10,000篇每篇10次獨立且可稽核完整深讀完成，才能報告使用者等待確認；未確認不能進入Notion重新設計。雙軌執行時同slug不重算；每次GitHub寫入前重讀main與blob SHA、衝突重讀合併，寫後回查commit與完整內容。沒有真人/效能/權限/補助真值測試。研究檔若需回復，精準revert本批Commit，不影響並行工作線。
