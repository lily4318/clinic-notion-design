# Notion 深度學習｜排程獨立研究批次 AUTO-07（2026-10-25）

> **狀態：研究增量已完成；10,000篇×每篇10次嚴格完整深讀仍未完成。** 本批僅閱讀公開官方來源、記錄反例、更新GitHub研究清冊；**沒有改Notion、業務資料、正式系統或開始新設計**。執行標記：`AUTO-07-20261025`；日期為台灣2026-10-25，非來源發布日期。

## 1. 研究範圍、去重與證據級別

- 作業開始前重新取得`main`的`README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`sources.md`、`decision-log.md`、`acceptance-status.md`，以及研究目錄下2026-10-24首批、2026-10-25第二～四批、AUTO-01～06、MANUAL-01、十面向研究及其餘研究文件；使用官方help slug與URL查重。
- **新來源3篇**：`simple-tables-vs-databases`、`navigate-with-the-sidebar`、`wikis-and-verified-pages`。`/nl/`、`/en-gb/`只是頁面語系，不因語系版本額外計數。三篇均成功取得並查閱官方**可讀文字主節**，逐一提出新反例；沒有逐張檢查所有圖片、影片、實際帳號權益與操作，**不記嚴格FULL_DEEP_PASS**。
- **舊來源2篇獨立重新研讀，不算新來源**：`https://www.notion.com/help/data-sources-and-linked-databases`（舊N04）及`https://www.notion.com/help/tables`（舊N11）在既有十面向研究已登錄。本批再讀可取得文字主要章節，產生下列新反例；標為`TARGETED_REVIEW_NEW_ANALYSIS`，不把它冒稱第2次完整深讀或多個新URL。
- 本批**3篇新來源、3次首次文字主節分析、2篇舊來源有新增的針對性分析**。本輪可核實完成十次完整深讀的篇數**0**；全域嚴格10/10合格**0/10,000**。並行工作線以最新main檔案與SHA判定重複；不能直接把所有歷史「候選數」相加作為精讀數。

## 2. 新來源逐節閱讀證據

| ID | canonical URL／官方文件 | 本輪閱讀範圍（文字） | 分級／未驗證 |
|---|---|---|---|
| AUTO07-01 | [The best ways to use simple tables in your Notion pages (and when not to)](https://www.notion.com/nl/help/guides/simple-tables-vs-databases) | 何時使用簡單表格、文件/摘要呈現、討論與腦力激盪、何時轉成資料庫、何時直接建立資料庫（正文約lines 106–229） | `MAIN_TEXT_READ + ANALYSIS_PASS_1`；未逐張檢查示意圖，未實作轉換/復原 |
| AUTO07-02 | [Navigate with the sidebar](https://www.notion.com/help/navigate-with-the-sidebar) | 基本架構、Home/分頁/搜尋/Inbox/快捷入口、Private/Shared/Teamspace/Favorites、巢狀頁、拖曳/刪除/回收桶、FAQ（正文約lines 106–380） | `MAIN_TEXT_READ + ANALYSIS_PASS_1`；未實際測帳號權限、手機版/個人化預設 |
| AUTO07-03 | [Wikis & verified pages](https://www.notion.com/en-gb/help/wikis-and-verified-pages) | Wiki建立/撤銷、三個預設Views、Owner/驗證、一般頁及DB驗證的方案限制、驗證到期/管理（正文約lines 106–246） | `MAIN_TEXT_READ + ANALYSIS_PASS_1`；未測各方案、Owner可見性、驗證流程或版本時效 |

### AUTO07-01｜簡單表格不等於可維護的業務資料

- **初始假設**：將補助額度和方案期別改成一張簡單表格，視覺更清楚也不需複雜資料庫。
- **官方文本**：Simple table適合固定文字、摘要、會議筆記、未定案的初稿；當需要filter/sort、typed properties、Relation/Rollup/Formula、不同View、每筆頁面時，Database才提供這些能力。文字頁還說明可從簡單表格轉成DB。
- **反例**：用靜態表格人工列出「已用/預約/剩餘」可能很漂亮，但不會自動追蹤跨期別、已取消預約、心理師比例等來源更新，產生**漂亮但過期的第二份真值**；在編輯簡單表格時合併儲存格，官方另有被覆蓋儲存格清空的操作風險（此點以既有Columns/Headings文章交叉核對，未實測）。
- **修正理解**：簡單表格是**表達文字資訊的載體**，不是權威業務紀錄。這不是主張立即新增或替換任何表格；須尊重使用者「同類資料同頁、開啟即見」及未核可設計的限制。**第2～10次完整深讀未做**。

### AUTO07-02｜側邊欄調整可能影響權限與資料，不只是美化

- **初始假設**：把舊頁面移進Private、把不常用的項目藏起來，只是個人導航偏好。
- **官方文本**：Favorites、釘選DB View與快捷入口是導航便利；隱藏/收合section不等於刪除。**從共享區拖曳頁面至Private會使其他人失去存取**；拖曳頁面到Trash可能同時刪除其下子頁及DB items。新Sidebar的Home是tab內區塊而非舊式獨立全頁，與早期UI教學可能不同。
- **反例**：以「清理側邊欄」為理由把正在被心理師使用的共用資料移入Private，表面上只是收納，實際卻改權限；把含原始Data Source的父頁丟到Trash，可能傷及歷史紀錄。相反，從sidebar移除捷徑或收合section不表示來源已刪。
- **修正理解**：要分辨**個人導覽偏好、分享/繼承權限、資料刪除**三層。這次只學習，不整理實際側邊欄，也不動任何舊頁。**第2～10次完整深讀未做**。

### AUTO07-03｜Verified知識文件≠可核實的業務計次

- **初始假設**：將治療所工作台轉Wiki並標Verified，即可同時保障規則最新與補助額度正確。
- **官方文本**：僅standalone且具Full access的頁面可轉Wiki，預設Home/All pages/Pages I own；一般頁面或一般資料庫的Verification功能，官方明列**Business/Enterprise**，DB Verification會同時新增Owner property。Owner與到期提醒可協助內容再審。
- **反例**：將現有資料庫轉Wiki不符合官方「只能轉頁面」條件；為了Verified新增Owner欄是**實際Schema變更**而非純標章；已驗證說明文件可能仍含錯誤公式/過期補助政策，且並未證明Free方案可用一般頁驗證。
- **修正理解**：**文件版本/責任人/驗證週期**與**每筆業務紀錄、公式、角色權限**分層。研究沒有授權轉Wiki、加Owner、改方案或對Notion頁面進行驗證。**第2～10次完整深讀未做**。

## 3. 既有來源再研讀：不新增URL、不冒稱嚴格完整Pass

### N04：Data sources & linked databases（已登錄來源）

- 本次重新查閱建立/管理/Linked/FAQ各主節。新發現：在`Manage data sources`中，`Sources`下的`Move to Trash`與`Linked`下的`X`移除連結，是不同作用域；**Linked View的filter/sort/group可獨立，但修改來源title/property/page會回寫原資料源**。移動來源時View可留在原處變成Linked Views，故畫面看似未消失不等於原來源未移動。
- **官方文件內部張力**：`Add a data source`段寫`Can edit`可移動來源；`Manage data sources`段寫僅`Full access`可移動來源。標記`SOURCE_INTERNAL_TENSION`，可能因「新增/連結/跨位置移動」動作範圍不同，**不能未實測就挑其中一種當權限真值**。
- 分級：`TARGETED_REVIEW_NEW_ANALYSIS`，未實測，不作新的完整深讀Pass；舊URL不重算。

### N11：Table view（已登錄來源）

- 本次重新查閱建立/多筆bulk edit/欄位計算/FAQ。新發現：Table可對多筆列進行**批次屬性修改**，且`Count unique values`只是在所選欄位的顯示資料上計數不同值，不等於後端複合唯一約束；`Count all`也不是依方案/期別的可核實額度。
- 反例：將某一欄選為批次修改，可能把多個服務紀錄狀態一次覆蓋；將`Count unique`當「個案×方案實例唯一」會誤判。這是對舊十面向「表格可比較三指標」的補充，**不能從表格計算功能推論業務計次真值**。
- 分級：`TARGETED_REVIEW_NEW_ANALYSIS`；舊URL不重算，不主張新增任何表格/批次編輯。

## 4. 跨來源反證與未驗證範圍

1. **N04 × AUTO07-02**：Linked View的顯示設定與原資料源分離；Sidebar移動頁面又可能改分享/刪除範圍。不能將所有「只整理UI」當無副作用。
2. **N11 × AUTO07-01**：Simple table和Database Table外觀近似，但一者純文字，一者具業務屬性/批次編輯能力；兩者風險方向不同（靜態資料過期 vs 誤改多筆）。
3. **AUTO07-03 × AUTO-01 Page Verification**：官方驗證機制可促進文件知識維護，**不是**補助額度/權限/Formula正確性驗收；一般頁驗證有付費限制，與Wiki內驗證須分別判讀。
4. **無實帳證據**：沒有執行Notion TEST/正式權限、角色、跨裝置、效能、刪除復原、Data Source移動、實際計次公式或臨床資料測試；任何功能與方案權益都需在未來獲核可後重新核對。

## 5. 本輪嚴格進度與邊界

| 指標 | 本輪可稽核結果 |
|---|---:|
| 新增與當期研究清冊逐URL去重的官方來源 | **3** |
| 新來源讀取可得主要文字並作首次反例分析 | **3** |
| 舊來源有新增反例的針對性再研讀（不新增URL） | **2** |
| 完成任一篇10次嚴格完整深讀 | **0** |
| 累積完成10/10篇數／目標 | **0／10,000** |
| Notion/業務資料/權限/正式程式寫入 | **0** |

本批未逐張驗圖、觀看嵌入影片或實機驗證，**不將文字主節分析記為嚴格FULL_DEEP_PASS**。來源為2026-10-25查閱的當時頁面，未能驗證其實際發布/修訂日期，不推測版本時間。研究檔寫入後需重Fetch比對Commit/blob SHA及內容；共用索引更新亦需先重取最新main SHA、寫後回讀。任何並行衝突不能覆蓋其他研究。**尚未完成10,000×10，未經使用者確認不得進入Notion重新設計**。
