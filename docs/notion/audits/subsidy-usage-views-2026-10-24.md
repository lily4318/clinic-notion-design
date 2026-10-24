# 2026-10-24｜政府補助使用額度 Views：Notion TEST 實作與驗收

## 使用者要求與偏離修正
使用者明確要求建立「看使用額度的 View」，此前追查 Billing 屬於工作方向偏離。本輪只修改 Notion TEST 工作台中的 View 及一行入口，不改收款、Price Plan 業務資料、Care Episodes／Sessions、Staff、Formula、Relation、Schema、權限或 GAS。青壯資格依使用者已確認流程人工核對，再於 Care Episodes 選正確核定方案實例；不得新增額外資格清單及黃色提醒。

## 原現況與改動
1. 原工作台 https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf 的 Price Plans 來源原有 View「01｜政府方案與核定期別」，可看核定總額度、已占用及剩餘，但沒有分開呈現原有「已完成、已預約、待確認」三類使用組成。
2. 在原 Price Plans linked database 中建立新 View「02｜政府補助使用額度（完成／預約／剩餘）」：https://www.notion.so/3f68ca66aa4d8156bccfcc28f75cbb9a?v=4038ca66aa4d81278430000cd581b5e7。View ID view://4038ca66-aa4d-8127-8430-000cd581b5e7。只選收費類型=補助 AND 服務類型=政府方案（不寫死青壯115）；依方案開始日排序，顯示名稱、方案識別、期間、核定總額度、已完成、已預約、待確認、已占用、剩餘及額度狀態。原01頁籤不動。
3. 在 TEST 工作台頁尾追加原 Care Episodes 的 inline linked View「個案使用額度｜依服務歷程／方案篩選（待核對）」：https://www.notion.so/3f68ca66aa4d81cca3b4ee43b4bd8dcf?v=4038ca66aa4d81a3ab1a000ca3244dce，view://4038ca66-aa4d-81a3-ab1a-000ca3244dce；新 inline DB URL：https://app.notion.com/p/4038ca66aa4d8163b08ac5efb0d8a427。Quick Filter 預選實際青壯115 Price Plan URL，日後可換方案；呈現歷程名稱、方案、狀態、個案方案上限、歷程已完成與已預約、他處是否確認、個案補助剩餘及狀態。資料層級是「服務歷程」，不宣稱已驗證同個案跨歷程總額度。
4. 原心理師週額度 View（青壯115專用）已含本週有效占用、他處使用顯示、週上限、額度狀態，不建立重複 View、不變更其2名在職臨床心理師的原篩選。URL：https://www.notion.so/c698ca66aa4d826baa8f8773b5c2cfe6?v=3f78ca66aa4d817581c9000c3420b577。
5. TEST 工作台「② 政府方案與核定期別」下新增一行快速入口，說明到原表第02 View、個案新 View、③心理師週額度。個案新資料表因 create_view 的 parent_page_id 行為追加在頁尾、原雙欄之外；未重排既有版面或增加黃色提醒。此版面位置需要真人 UX 驗收。

## 完成的唯讀讀回／驗收限制
- Price Plans 新 View Fetch、linked DB 同時列舊01與新02兩頁籤、saved-view query 均通過，回傳目前青壯115方案 1筆、has_more=false；必要展示欄位存在。
- Care Episodes 新 View Fetch、工作台 Fetch 的 linked DB／快速入口回查通過，預選青壯115篩選回傳22筆、has_more=false。
- Google Docs「青壯方案額度管理｜跨年度資料模型與 UX 規格 v3.4」已追加本次第十六節並在 revision guard 下回讀驗證：https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit。
- 未取得 Notion Formula／Rollup 原生數字，僅能看到 formulaResult／rollupResult 參照；因此 View 欄位及資料範圍通過 ≠ 真正已完成、已預約、已占用或剩餘的數值計算 PASS。外部未知≠0；跨歷程累計、跨方案／期別通用性、10/25週換週、角色權限、真人操作步數與頁面載入效能都仍未通過。
- 新建兩個 View 無原始資料、Schema、Formula、Relation、分享權限及業務資料寫入。00.config_notion 精確權威設定檔本回合未獨立定位，實作使用當次重新Fetch的工作台原 linked database 和直接取得的 Data Source Schema／Relation／View，不把 GitHub 當即時 schema。

## 回復與查驗
回復前重新讀最新工作台／View 並核對他人改動；只從 TEST 工作台精準刪除本輪新建的 Price Plans 第02頁籤、新 Care Episodes inline linked View 及那一行入口，不刪原始 DB 或原業務列。此連接器目前未提供 View 刪除工具，回復刪除需由有權限者在 Notion UI 精準執行。Google Docs／GitHub 的本輪新增段落可在保留並行更動前提下撤回。

使用者在 TEST 工作台②切換第02頁籤應看到核定／已完成／已預約／待確認／已占用／剩餘；點個案額度入口預設應看到22筆青壯115歷程；③維持原心理師週額度。

## 2026-10-24｜使用者更正：青壯一案一歷程、到期結案；原View精準更新與讀回

### 重要業務決策（覆蓋此前跨歷程疑慮）
- 使用者指出：在汐予同一個案**一次 Care Episode**即完成青壯；**超過衛生局核定時間就結案**，本所**不會為同一個案再接第二筆青壯**。因此青壯正常使用額度的來源應直接是此 Care Episode，**不需要跨歷程合計**；不能將個案跨歷程計數當成青壯方案必要功能。此規則只限汐予青壯，不影響其他補助或其核定期別/官方跨機構總次數查核。
- 舊通用「已逾期而開案中不能自動隱藏或自動關案」應區分**行政應結案**與**自動變更業務資料**。本回合新增的結案要求是行政流程確認，並**未授權無人工核對的狀態批次寫入**；若仍在進行中且已超期，保持可見等待處理，正式核定期限不寫死在通用邏輯。

### 改動前備份（View獨立還原資訊）
- 原View ID `view://4038ca66-aa4d-81a3-ab1a-000ca3244dce`，原名「個案使用額度｜依服務歷程／方案篩選（待核對）」；`simpleFilters` 有1筆 `💲收費方案` Relation Contains 當期青壯115實際Page URL，**沒有 advancedFilter**；排序開案日DESC；原顯示欄：`名稱`,`💲收費方案`,`狀態`,`個案方案上限_帶入`,`本歷程已完成_帶入`,`本歷程已預約_帶入`,`他處使用已確認`,`個案補助剩餘_自動`,`個案補助狀態_自動`。寫前實際重新 Fetch View、工作台、Care Episodes Schema與Price Plan，確認所需欄位存在。
- 原工作台②快速入口全文：「額度檢視：本表切換『02｜政府補助使用額度』查看治療所用量；[個案使用額度（按服務歷程／方案篩選）]({{個案inline DB URL}})查看個案用量；下方③查看心理師週額度。」（此處僅示意文案，未隨本次複製個資或其他區塊）

### 最小實作
- 對**同一個已建立View**原地更新（不新建來源DB/View、不修改別的View）：名稱為「青壯115｜個案使用額度（單一歷程）」；`CLEAR QUICK FILTER "💲收費方案"`、新增固定`FILTER "💲收費方案" = "https://app.notion.com/p/c748ca66aa4d83909393815a05b6030a"`，保留原方案實例範圍、避免可任意切換其他補助但標題仍為青壯；SHOW新增`開案日期`、`結案日期`，保留原額度欄；開案日排序不變。
- 原[補助工作台TEST](https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf)②只改**一段入口文案**及新增一段青壯單一歷程、核定期後應結案、既有重複紀錄人工待核的純文字說明；原方案02額度View、心理師週額度及所有原歷史資料區塊不動，不增加黃色警示。
- [本次View永久URL](https://www.notion.so/3f68ca66aa4d81cca3b4ee43b4bd8dcf?v=4038ca66aa4d81a3ab1a000ca3244dce)；新增欄位只是顯示原有`開案日期`、`結案日期`，不新增資料欄位／公式。

### 本輪驗收（及特別小心的TEST例外）
- **[VIEW CONFIG PASS]** 修改後重新Fetch View：新名、固定Relation FILTER 115實際Page URL、Quick Filter已清除、起結案日期已顯示；Saved View Query 返回**22筆**，`has_more=false`，22筆全部匹配青壯115實際Page ID；沒有隱藏其他補助原 View。
- **[WORKBENCH PASS]** Fetch工作台：新入口、單一歷程結案文字均存在；原方案 linked DB、心理師週額度 linked DB、新 Care Episodes linked DB都保留，未恢復黃色警示。
- **[DATA EXCEPTION / NO FIX]** 22筆青壯115 Care Episodes，按`😶 個案` Relation 去重為**21名不同個案**，1名個案同時連兩筆青壯歷程；**兩筆名稱皆有測試標記**，且皆連啟用115 Price Plan（沒有證據顯示真實收案重複）。兩筆歷程各有1或2筆關聯Session且都處於進行中、沒有填寫開案或結案日期；**[TEST] 名稱不代表隔離**，不因本次規則改動而自動刪改。全部22筆在查詢當下均為`進行中`，結案日期均未填；目前Price Plan欄位顯示2026-01-01至2026-12-31，依本輪本地日期2026-10-24**尚未到2026-12-31**，不能用這條行政規則誤批次結案。
- **[FORMULA / AUTH / UX NOT TESTED]** Formula、Rollup只讀到結果指標，不可宣稱確切本歷程使用／剩餘次數PASS；未實測真人讀取權限、帳號或頁面速度，且尚未取得所有地方核定文件來證實每例具體截止日。更新未影響Notion業務資料、Relation、Schema、Formula、其他View、權限、Billing或正式系統，沒有新增公式效能負擔。
- Google Docs[青壯UX v3.4](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)已透過revision guard追加第十七節，寫後重新讀回確認內容及原第十六節仍保留。

### 回復
若須回復，本次只需核對最新View與TEST工作台內容（保留並行修改），將原View名、9個原顯示欄、Quick Filter「💲收費方案」含當期Page URL、清除本次固定AdvancedFilter恢復原設定；工作台刪除／恢復本次改動的入口及規則說明。不得刪除資料列或原始DB，也不可動人員週額度及方案總額度View。Notion「結案」並未做任何業務資料寫入，故**無業務資料回復需求**。

## 2026-10-24｜青壯額度 Views 續作唯讀回歸（15時）
- **[LIVE VIEW / SOURCE PASS]** 重新 Fetch「補助方案管理｜TEST」頁、Price Plans / Care Episodes / Sessions Data Source Schema（30／50／67欄），及治療所、青壯單歷程、心理師週額度3個原生 View。首頁仍保留「人工核對→Care Episodes 選方案」、單一歷程／期滿行政結案說明、原資料庫入口及無黃色提示。治療所 View 專用「補助＋政府方案」、青壯 View 固定115方案實例 Relation、心理師 View 在職臨床心理師篩選均未變。
- **[VIEW ROWS PASS]** 當次原生 Saved View 查詢：政府方案1筆、青壯115 Care Episodes 22筆、心理師週額度2筆，三者均 has_more=false；22筆皆「進行中」，依個案Relation去重21位，其中1位重複兩個青壯歷程，保留待人工核對；22筆結案日皆空白。當前Price Plan表列開始2026-01-01、結束2026-12-31，不代表每位個案首次服務三個月截止已驗。
- **[DATA DISCREPANCY / INVESTIGATE]** 本次 Saved View 有20／22筆 `開案日期` 非空，與先前同日稽核「全部未填開案日期」的敘述不同；現況優先，不沿用舊空白結論。未逐項確認此差異來源／變更人，不因此更動任何歷程狀態或日期。
- **[NUMERIC BLOCKED]** 同一 Price Plan 的核定總額、已完成、已預約為 `rollupResult://` 參照，已占用／剩餘為 `formulaResult://` 參照；Care Episodes 的完成／預約／剩餘與 Staff 本週有效占用／他處／狀態亦僅返回 Rollup / Formula 結果參照。另用 Price Plans 最小 `rows` 查詢回傳相同參照。無原生可核算數值、公式原碼，不能以22筆歷程或歷史Sessions狀態推定實際額度通過。
- **[SCOPE/NO NOTION WRITE]** 本次僅唯讀驗證，Notion原業務列／Schema／Formula／Relation／View／分享權限、Google Docs、Billing、GAS、Cloud Run／Session／部署完全未改；新增GitHub匿名驗收紀錄。`00.config_notion` 以名稱搜尋仍未精確定位；真人UX、載入效能、角色權限、計數與本地契約逐人截止日尚未實測。GitHub追加文字可由版本紀錄精準撤回，任何 Notion 資料無須回復。
