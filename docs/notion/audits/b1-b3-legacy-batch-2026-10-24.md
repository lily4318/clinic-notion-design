# 2026-10-24｜B1–B3 行政頁整批 B 級修正與回查

**狀態：Notion TEST 行政管理下既有頁面已進行有限範圍 B 級批次修改；頁面／View 結構讀回通過；原業務資料與真實活動業務情境未更動、未全面驗收。**

## 問題與決策

前次10模組稽核發現：Events 兩個活動 View 的狀態篩選與標示不一致；Billing 的同名收據與收款區塊其實屬不同資料流；Staff 三個薪資區塊分屬不同處理階段；Tasks 與 Documents 的 `ALL` 不是真正全部。使用者要求不要零碎逐項調整，採**一次盤點、備份、集中套用已核實 B 級變更**，對不符事實的舊稽核結論修正後保留原頁。

前次 F-03「本週會議混入全部專案」判斷**需要更正**：重新 Fetch 原 Projects & Meetings 頁證實 `<h3>本週會議</h3>` 下是 Meetings 區塊，後有獨立 `<h2>專案</h2>` 及 Projects 區塊；**本輪完全沒有修改該頁**。請勿根據舊 F-03 直接改寫專案／會議頁面。

## 原生頁面備份（完成後已逐頁回讀）

| 原頁 | 備份 Page URL | 備份保留的 linked DB block 數 |
|---|---|---:|
| Billing | https://app.notion.com/p/4038ca66aa4d8145a3eec4c49740744f | 14 |
| Events & Groups | https://app.notion.com/p/4038ca66aa4d81a890cacc9a997c6d91 | 15 |
| Staff | https://app.notion.com/p/4038ca66aa4d81f58ffccad644e27a78 | 14 |
| Tasks | https://app.notion.com/p/4038ca66aa4d81249ff4d6b96f2ca812 | 3 |
| Documents | https://app.notion.com/p/4038ca66aa4d81778fb9c13cc809fa85 | 5 |

備份是 Notion 原生頁面複本（有原 Linked DB 的檢視內容），**不是將業務來源另行複製一組獨立資料庫**。實際回復前需再次 Fetch 原頁／備份頁，避免覆蓋期間的並行修改。

## B1｜Events 兩個真實 View 的修改界線

- 來源 Data Source：`collection://2ab8ca66-aa4d-83bd-894f-87531b7fc587`；原 Linked Database block：https://app.notion.com/p/1278ca66aa4d833c9bd501d9606e1abf
- **平台限制：** 嘗試對原 View 使用 `CLEAR FILTER; FILTER ...` 時，Notion 仍留下舊 `simpleFilters`，卻增加新 `advancedFilter`，會形成相反條件。單獨 `CLEAR FILTER` 仍無法移除舊 `simpleFilters`。因此不宣稱原 View 已原位修正，而是取消新增錯誤的 advancedFilter、保留原簡易篩選，將舊 View 改名標記停用，同時在同一個原 Linked DB 內建立兩個新的正確 View。
- **新 View A：** `view://4038ca66-aa4d-81fd-bb28-000c6f1f92fa`「可報名｜開放報名」，唯一 advancedFilter：狀態=開放報名；依活動時間 ASC；可見原欄位「＋活動報名／類型／名稱」。Fetch 確認**沒有殘留 simpleFilters**。
- **新 View B：** `view://4038ca66-aa4d-819d-9082-000c961b50f5`「進行中｜開放報名與已額滿」，唯一 advancedFilter：狀態 ∈ 開放報名／已額滿；依活動時間 ASC；可見「狀態／類型／名稱」。Fetch 確認**沒有殘留 simpleFilters**。
- **保留舊 View（停用）：** `view://3b08ca66-aa4d-8216-8abf-08275d9b29bb` 現名「舊版｜反向報名篩選（停用）」，仍保留 `status_is_not 開放報名`；`view://9768ca66-aa4d-82d2-8284-8840f61fd407` 現名「舊版｜過寬進行中篩選（停用）」，仍保留 `status_is_not Complete`。**因工具未提供刪除 View 的功能，舊兩個頁籤仍在，務必選擇新版兩個頁籤。**
- 已實作過的完全隔離 TEST Data Source `collection://5864ca97-2ceb-4727-a52c-9b7cf749dcd9` 用五種合成狀態驗證：可報名1／進行中2／全部5筆 PASS；本次實際原來源的新 View 均查回 **0筆、has_more=false**，沒有真實活動案例可驗證實際涵蓋性。這只是結構與篩選配置 PASS。
- Events 管理頁：https://app.notion.com/p/d578ca66aa4d8303bebf017bdcf7904d，將活動管理標題調整為「活動管理｜新版『可報名／進行中』檢視」，避免舊頁籤混淆。原15個 block、導覽保留。

## B2｜三個頁面的工作階段標示

透過最小 `update_content`，只在既有 linked DB 之前插入 H4 任務標籤，**沒有移動、複製或刪除原資料庫 block**：

| 頁面 | 新增任務標示 | 原數量／讀回 |
|---|---|---|
| Billing | 收據待審核、收據需人工確認、會談待建立收款、活動報名待建立收款 | 14 / 14 |
| Events | 團體場次待建立會談Sessions、團體待建立場次、團體治療報名中、一般活動報名中 | 15 / 15 |
| Staff | ①人員待建立總覽、②薪資確認單待拆明細、③薪資確認單待產生PDF | 14 / 14 |

原資料來源與 View 的條件、排序、資料列、權限不變；僅 Events 指定兩個新 View 如 B1。

## B3｜僅顯示名稱，條件未改

- Tasks Linked View `view://ef28ca66-aa4d-8250-8728-8814cc9a8fc5`：`ALL` → **全部未完成｜依任務類型**。原 `Done = false` 篩選及依類型分組仍存在，讀回查詢3筆。
- Documents Linked View `view://4758ca66-aa4d-8386-9690-087cf2535764`：`ALL` → **待更新＋草稿｜總覽**。原「狀態=待更新或草稿」簡易篩選仍存在，讀回查詢4筆。
- 原 Tasks 頁3個、Documents 頁5個 linked DB block 未變；未改資料原值。

## 驗收、效能、安全、回復及未完成項目

- **已回查**：以上原3個版面、原 Events block 包含2個新版／2個停用舊版、預覽頁最新狀態、所有5份標為 BACKUP 的原生複本及各 View 條件／查詢。
- **保持不變**：所有核心資料來源的資料列、Schema、Relation、Rollup、Formula、權限；Notion 其他5個舊行政頁、GAS／Cloud Run／Session／正式部署均未修改。並未新增使用者已拒絕的黃色提醒。
- **權限**：改名及 Linked View 篩選不等於真正角色權限隔離；沒有權限測試，不得據此允許存取原本無權限的資料。
- **效能**：Events 在既有 Linked DB 增加2個 View 頁籤，原頁 block 數不變；未量測真實載入時間，不宣稱改善速度。
- **回復**：在核對當時最新原頁／備份與 View 設定後，撤銷 H4 新標籤與活動管理標題；Tasks、Documents 分別改回 `ALL`；Events 兩個舊 View 名稱改回「報名中」「進行中活動」，它們的舊篩選原本就保留。新增兩個正確 View 如需要撤回可改名「停用／待移除」，真正刪除需有人在 Notion UI 執行（當前連接工具無 delete_view）。**不得刪原資料來源或修改業務列**。
- **未驗收**：真實活動正確進出條件（當前0筆）、真人 UI／使用者操作時間、10模組所有細部名稱、00.config_notion 全域映射、Notion Free 真實權限隔離、公式真值／載入效能、10,000篇外部文獻研究。B1/B2/B3 僅完成本文件列明的**可安全實施部分**，不是全部需求功能已完成。

Notion 整批預覽頁已新增「部分套用與回查（最新現況）」節：https://app.notion.com/p/4038ca66aa4d814297a2dbe27e8d054d，覆蓋歷史「原活動 View 尚未修改」敘述。