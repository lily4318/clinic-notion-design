# Notion 深度學習｜AUTO-19｜2026-10-26（僅研究）
- 執行軌跡：`AUTO-19-20261026-1042`；來源編號 AUTO19-S01～S03（新候選）、AUTO19-R01（舊來源獨立複讀）。
- 嚴格範圍：只研究公開文件並寫 GitHub 研究清冊；**沒有授權、沒有執行任何 Notion 頁面／資料庫／View／Formula／Relation／分享權限、GAS、Cloud Run 或 Session 變更**，不進入重新設計。
- 開始前重新取得 main：根 README、AGENTS、docs/system/source-of-truth、docs/notion/AGENTS、sources、decision-log、acceptance-status、research/README、首批 evidence-register、第二至第四批、MANUAL-01、AUTO-01～18（逐檔核對本輪三個候選slug）；GitHub搜尋可能不完整，以直接讀取清冊為準。已發現初選的 charts、database-templates、forms、synced-blocks、customize-your-database、collaborate-within-a-workspace 早已在其他批次登錄，**全部排除本輪新增計數**。
- 網頁實際閱讀日：2026-10-26 臺灣時間；原文出版及最後修訂日期未核實。Notion 官方 canonical ID 採 `notion-help:{slug}`，語系、追蹤參數、重導向不得另計篇數。
- 本輪新增3個經已讀清冊去重的官方URL，各完整閱讀可取得的主要**文字**章節與FAQ、各做一次獨立反例分析；圖片、影片、真人帳戶、跨角色、行動裝置及實際資料操作**未完整核驗**，所以本輪均只計 `BODY_MAIN_AND_FAQ_R1`，不計 `FULL_DEEP_PASS`；R2～R10尚未進行。

## AUTO19-S01｜Map view
- URL：<https://www.notion.com/help/maps>；標題：Map view；來源：Notion Help；canonical：`notion-help:maps`；本輪閱讀 `R1/BODY_MAIN_AND_FAQ`。
- 閱讀覆蓋：Place property、地址搜尋第三方、Place欄位建立及文字欄轉換、建立/加入Map view、100筆限制、地圖操作、Place文字篩選排序、切換Place欄位、FAQ。2026-10-26網頁正文約第106–204行。
- 官方資訊：地圖最多顯示100個項目；地址搜尋由第三方處理，地區覆蓋與品質有差異；建立Map view可能新增Place欄；多個Place欄位時需選擇正確來源；目前不支援兩地距離計算。
- **原假設**：把服務據點／轉介地點顯示在地圖就能直接判斷全部據點分布、距離及覆蓋率。
- **反例**：超過100筆可能只顯示部分；地址格式不完整、Place欄位選錯或第三方定位不準，均可使圖釘缺失；沒有距離運算，不能把地圖視為完整名冊或地理核定依據。
- **修正結論**：地圖是輔助導航而非行政資料完整性驗收；如未來真有地址業務需求，應保留表格查詢、總筆數對帳、資料最小化與第三方地址處理的資安評估。此為研究風險，不代表需要新增Map欄位或功能。
- 未驗：地圖圖像、台灣地址定位準確率、第三方資料處理合約、100筆以上實測、手機版與權限。

## AUTO19-S02｜Task databases & sprints
- URL：<https://www.notion.com/help/sprints>；標題：Task databases & sprints；來源：Notion Help；canonical：`notion-help:sprints`；`R1/BODY_MAIN_AND_FAQ`。
- 閱讀覆蓋：Task DB轉換與復原、Status/Assignee/Due date、My tasks、ID與ID URL、Sprint建立、Sprint board及Sprints DB、規劃與完成、1–8週設定、開始日、未完成任務處理、自動Sprint、停用後刪除關聯；網頁正文約106–239行。
- 官方資訊：啟用Sprint會新增看板及Sprints DB；更改週起始日會改變目前Sprint日期；關閉Sprint功能會**永久刪除**Sprints DB、看板及任務關聯；任務ID不因刪除頁面而重用，且不是業務複合唯一鍵。
- **原假設**：每週行政／補助工作只要設Sprint便可自動安全延續，改週起始日也只是視覺設定。
- **反例**：更改週起始日會改變現行Sprint日期；未完成任務可能被搬至下期、backlog或留原期；關閉Sprint功能會移除資料結構與關聯，並非無害的停用。
- **修正結論**：Sprint屬專案工作節奏工具，不等於政府補助的週日～週六核定週、跨期業務規則或核銷紀錄；未來若考慮須另測週期、歷史與回復。**不提議**對現行補助資料庫啟用Sprint。
- 未驗：實際新增/關閉、資料復原、週期跨時區、真人角色、畫面與影片。

## AUTO19-S03｜Style & customize your page
- URL：<https://www.notion.com/help/customize-and-style-your-content>；標題：Style & customize your page；來源：Notion Help；canonical：`notion-help:customize-and-style-your-content`；`R1/BODY_MAIN_AND_FAQ`。
- 閱讀覆蓋：•••選單與權限差異、文字/Markdown、字型/小字、色彩、全寬、頁面討論、資料庫頁面共用布局、Callout、圖示/Emoji、封面、FAQ；網頁正文約106–314行。
- 官方資訊：資料庫頁面的Discussion布局變更可套用到該庫**所有頁面**；Callout中的標題可進入目錄；手機不支援部分字級/全寬操作；自訂Emoji不會呈現在mobile widgets；頁面封面會隨視窗裁切，沒有固定比例；目前不能將Full width設為全域預設。
- **原假設**：調整顏色、縮小文字、加入封面及多個Callout就能讓工作台更直覺，且改動只影響當前頁。
- **反例**：縮小文字可能降低可讀性，裝飾性封面擠壓首屏；Discussion布局套用全庫影響其他頁；手機與桌面呈現不一致，Callout標題還可能增加目錄噪音。
- **修正結論**：未來的視覺設計評估必須先以工作者「開頁即見資料」與文字辨識為準，檢查套用範圍及手機版；研究並非對Notion頁面做任何變更的授權。
- 未驗：全部截圖與影片、視覺對比/無障礙、手機、真人操作。

## AUTO19-R01｜既有 Synced blocks 的第三次針對性文字複讀（非嚴格完整深讀）
- 原來源 <https://www.notion.com/help/synced-blocks>，canonical `notion-help:synced-blocks`；已在第三批 NEW02 首讀、第四批記錄 ANALYTICAL_REVIEW 2/10，**不是新來源**。
- 本輪重新讀取Sync、Edit、Unsync、FAQ全部可讀文字，重點為「Unsync單一副本後內容成為獨立版本，內部頁面連結仍有效」與原區塊存取權。網頁正文約106–168行。標記 `R3/TARGETED_BODY_REVIEW`，不計 FULL_DEEP_PASS。
- **與前兩輪不同的新反例**：當管理員修正某個共用行政提示後，某個已被Unsync的舊副本不會同步更新，雖然仍保留可點的原頁連結；因此「原始同步區塊已更新」不保證各頁沒有過期指示。前輪聚焦誤刪原始造成連帶刪除，本輪聚焦解除同步後的**內容漂移**。
- **修正結論**：日後若做內容治理，必須區分目前仍同步的副本、已解除同步的舊副本、原始來源權限與內容版本；只改原始區塊不足以證明全頁一致。此處沒有清理任何實際頁面。
- 未驗：實帳解除同步後各副本狀態、超過10副本刪除與Undo、圖片及角色權限。

## 交叉反證、計數與未完成
- Map 100筆上限與Chart 200群組限制、Sprint自動週期與政府週額度、Style的Callout/縮字與使用者首屏需求，分別是**不同文件與不同功能**，不把交叉討論當作新URL或額外閱讀次數。
- 本輪：候選新增官方canonical 3；正文與FAQ主節閱讀3；首次獨立反例3；已登錄來源針對性複讀1；嚴格10/10完成新增0。
- 累積可稽核「每篇10次獨立完整深讀」合格數仍 **0／10,000篇**。全域唯一來源精確累計尚未跨所有檔案做機器去重，不能用批次數直接相加。
- 本輪所有來源發表／更新日期未核實；無逐圖、影片、實帳、角色、效能、臨床資料或資安驗證；不把官方功能介紹當成現況已落地或適合本所的決策。
