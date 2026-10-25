# Notion 深度學習｜獨立批次 AUTO-03（2026-10-25）

> **僅官方資料唯讀研究＋GitHub紀錄。** 使用者設定「每小時自動排程與手動『繼續』雙軌並行」，本批以獨立檔案保存，不能覆蓋手動研究。研究總目標10,000個去重來源、各10次獨立且可稽核的全文深讀；**未達標，不能開始Notion新版設計**。研究日：2026-10-25，Asia/Taipei；未核定網頁發佈日期。批次唯一標記 `AUTO-03-20261025`。

## 1. 本輪閱讀、去重與嚴格計數

- 在研究前讀取GitHub `main` 最新 `README.md`、根 `AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`decision-log.md`、`acceptance-status.md`，以及2026-10-24首批、2026-10-25第二/三/四批、十面向研究、AUTO-01、AUTO-02、MANUAL-01的現有研究紀錄。
- 新增**3個不同canonical slug**，已逐檔比對上述清冊：`/help/guides/assign-custom-database-permissions`、`/help/guides/tasks-manageable-steps-sub-tasks-dependencies`、`/help/feeds`。其中兩篇使用`/nl/`、`/en-gb/`語系URL，**語系版本不當新篇**。同一研究主題已有其他官方參考文件（例如`/help/sharing-and-permissions`）不代表這篇新GUIDE被重算；仍需以全域canonical slug去重。
- 3篇都實際開啟官方頁面並閱讀**全部可取得的文字主章節**，各寫一輪獨立假設、反例、交叉驗證與待測問題，標記 `MAIN_TEXT_READ + ANALYTICAL_PASS_1`。未觀看嵌入影片、未逐張檢查所有截圖，亦未在Notion TEST/正式環境實機驗證；因此**0次嚴格FULL_DEEP_PASS**，且不是每篇完成10次。這一輪不複製任何模板，不用搜尋摘錄充作全文。
- 本輪來源皆Notion官方，取閱日2026-10-25；文章可能持續更新，來源顯示2026版面但不代表2026發佈或實際產品版本。

| ID | 官方來源（canonical） | 本次閱讀主節與範圍 | 證據等級 |
|---|---|---|---|
| AUTO03-01 | [Assign custom database permissions](https://www.notion.com/nl/help/guides/assign-custom-database-permissions)（canonical `/help/guides/assign-custom-database-permissions`） | 控制資料庫結構；Can edit content 可改哪些內容；保護Select選項；linked database個別視圖；page-level access；約文字主節106–175行 | `MAIN_TEXT_READ + ANALYTICAL_PASS_1`；無角色實測 |
| AUTO03-02 | [Sub-tasks and dependencies](https://www.notion.com/en-gb/help/guides/tasks-manageable-steps-sub-tasks-dependencies)（canonical `/help/guides/tasks-manageable-steps-sub-tasks-dependencies`） | 子任務自我Relation、父子欄位、Timeline依賴、呈現、其他用途；約文字主節106–201行 | `MAIN_TEXT_READ + ANALYTICAL_PASS_1`；無實際DB/Timeline測試 |
| AUTO03-03 | [Feed view](https://www.notion.com/en-gb/help/feeds)（canonical `/help/feeds`） | 用途、建立新Feed、現有DB加Feed、Property visibility；約文字主節106–142行 | `MAIN_TEXT_READ + ANALYTICAL_PASS_1`；短篇但非10次深讀 |

## 2. 逐篇第一輪反例分析

### AUTO03-01｜Can edit content與角色權限

- **初始假設**：將心理師或行政人員改成`Can edit content`，便能防止誤刪重要業務紀錄及避免非本人讀取敏感列。
- **正文支持的較窄事實**：這個角色可新增/刪除**資料庫頁列**、修改列值、套用既有模板，但不能改主資料庫的屬性結構、Select選項或主要Views/Filters/Sorts。文章也提到Linked Database上的個人檢視與依Person欄位設定page-level access。
- **反例**：一位只有`Can edit content`的使用者仍能**刪除整筆服務紀錄**，因此不能拿它當防刪保護或個案保密的完整方案；某人建立`@me`過濾的個人View，也不能據此斷言其沒有來源DB其他列的存取權。權限分層與視圖篩選是不同的保護機制。
- **交叉查證**：已登錄的官方[Sharing & permissions](https://www.notion.com/help/sharing-and-permissions)說明page-level access只在Business/Enterprise，且更寬廣的分享權限會優先；[Manage database property access](https://www.notion.com/help/database-property-access)亦明列Business/Enterprise，且有Full access者不受欄級限制。**不能因本篇GUIDE提到page-level access就假定Free可用**。
- **修正理解**：`Can edit content`是「避免Schema誤改」而不是「避免列刪除」或「自動隔離病歷」；付費功能的能力與當前工作區是否具備、操作者實際權限須另查。**不在本輪修改任何權限**。
- **未驗證**：免費/付費實帳、Notion當前UI權限繼承、Linked View分享、外部人員能否看到隱藏資料、刪除與恢復、2026實際角色行為。第2–10次未執行。

### AUTO03-02｜Sub-items與Dependencies

- **初始假設**：把補助方案各期的服務紀錄都改成Sub-items，能自動解決年度、核定期與多方案計次；把某服務列設成另一列的Dependency會禁止先完成後面的服務。
- **正文支持的較窄事實**：`Sub-items`建立自我關聯的Parent/Child屬性，並以Table或Timeline呈現；`Dependencies`也以自我Relation表達項目先後依賴，在Timeline可視覺連線。
- **反例**：Relation只標示關係，文章沒有聲稱它能自動核對「補助資格、每期額度、週報、跨治療師計次」或阻擋業務錯誤。依賴連線也不等於交易層級強制禁止更改狀態；把不同期別的服務紀錄強行收為父子可能扭曲原始歷史記錄的平行性。
- **修正理解**：`Parent/Child`是階層式任務結構；`Dependency`是流程依賴標記；`核定期/個案/方案`是業務實體與複合約束。三者不是同一種資料模型。**不能以漂亮的層級UI推論自動算對**。
- **未驗證**：是否所有檢視都顯示同樣的子項、Relation與現有公式依賴、移動父子列的寫入副作用、免費版能力、效能。第2–10次未執行。

### AUTO03-03｜Feed View

- **初始假設**：將首頁38筆服務歷程轉成Feed卡片，就能讓使用者更快判讀本期剩餘額度與最後一次補助候選。
- **正文支持的較窄事實**：Feed是線性堆疊卡片，適合團隊更新、公告、評論、追蹤瀏覽，並可選擇顯示或隱藏卡片屬性；文章沒有證實其能提供跨列數值對照、週期計算或更低載入時間。
- **反例**：需要同時比較「治療所總額度／心理師額度／個案額度」時，逐張卡片滑動可能比表格更難比對，也可能增加捲動量。隱藏屬性是顯示設定，**不等於撤銷該欄位資料存取權**。
- **交叉對照**：早期NN/g資料表研究指出比較相鄰數值與掃描行列的重要性；官方[Views, filters, sorts](https://www.notion.com/help/views-filters-and-sorts)可調整不同View，但「能顯示」不等於「對所有任務更好」。**不因此新增Feed或調整首頁**。
- **未驗證**：Feed在目前方案下的權益、真實手機操作、閱讀速度、跨列數值比較、效能、卡片留言的隱私。第2–10次未執行。

## 3. 跨來源結論、不可外推之處

1. **權限 ≠ View Filter**：有內容編輯權的人仍可刪業務列，過濾/隱藏屬性也不等於安全隔離。免費方案不能直接套用付費的page-level/property-level功能。
2. **自我Relation ≠ 補助計次邏輯**：父子關係與依賴連線都不保證額度計算、核定期、法規或稽核正確。
3. **卡片化 ≠ 可用性提升**：Feed適合閱讀/互動型內容，但對密集數值比較可能是反例。此為研究假說，沒有實測UX與效能。
4. 三篇的文字閱讀與第一輪分析**只計3個來源、各1個分析輪次**；無法把主題分成數個小節當多篇，或把引用的舊官方文件算本輪新來源。

## 4. 本輪驗收、資料安全與後續門檻

| 指標 | 本輪 |
|---|---:|
| 新增已與現有清冊比對的canonical URL | **3** |
| 已讀可取得全部文字主節＋有反例的第一輪分析 | **3** |
| 任一來源嚴格10次完整深讀 | **0** |
| 累積嚴格10/10完成篇數／總要求 | **0 / 10,000** |
| Notion Page/Database/Views/Formula/Relation/Permissions/業務資料修改 | **0** |
| GAS/Cloud Run/Session修改 | **0** |
| 真人UX、跨裝置、效能、角色權限測試 | **未執行** |

本批與AUTO-01/02、MANUAL-01研究證據分檔，僅可同步GitHub `sources.md`、`decision-log.md`、`acceptance-status.md`之研究索引。任何共享檔修改前需重Fetch最新`main` blob SHA、用條件更新、衝突重讀合併不重複增量；寫後重Fetch核驗Commit/SHA與內容。未達10,000篇各10次真正獨立深讀前，不開始Notion改版。