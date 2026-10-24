# 2026-10-24｜B1～B3 獨立 TEST 預覽與狀態驗證｜整批設計預覽及活動狀態回歸測試

## 實際產出（已建立並回查）

- **TEST 整批 UX 預覽頁**：https://app.notion.com/p/4038ca66aa4d814297a2dbe27e8d054d
  - 上層：既有「TEST 行政管理」（不取代原10模組）。
  - B1 包含活動狀態判定與隔離 TEST 連結；B2 一次整理帳務、活動團體、心理師／薪資及會議專案的任務導航；B3 保留新詢問、個案／歷程、會談、空間、任務及文件的原始入口。
  - 沒有黃色警示。不把 TEST 預覽冒稱已取代原行政頁面。
- **獨立驗證 Data Source**：Notion DB https://app.notion.com/p/39f6c1322dd44106b32760a58246860e ，Data Source `collection://5864ca97-2ceb-4727-a52c-9b7cf749dcd9`。
  - Schema 僅四欄：「名稱」TITLE、「狀態」STATUS、「預期報名中」CHECKBOX、「預期進行中」CHECKBOX；已 Fetch 確認**無 Relation**、不指向啟用的 Events、Sessions、Staff、Billing、Cases 或 Price Plans。
  - 建立完全合成的五筆資料，各狀態「籌備中／開放報名／已額滿／已取消／已結束」一筆，沒有真實個案、電話、收據、薪資或會談。
  - 以三個獨立 saved Views 實際查詢並比較：

| TEST View | View ID | 正確條件 | 預期 | Notion 回傳 | 結果 |
|---|---|---|---:|---:|---|
| 可報名 | `view://4038ca66-aa4d-8128-9c01-000c5a1d52b2` | 狀態 = 開放報名 | 1 | 1 | PASS |
| 進行中 | `view://4038ca66-aa4d-8195-b024-000c073de3a8` | 狀態 ∈ {開放報名,已額滿} | 2 | 2 | PASS |
| 全部狀態 | `view://4038ca66-aa4d-81af-bf26-000c67fcdf50` | 無狀態篩選 | 5 | 5 | PASS |

三項 `query_data_sources(mode=view)` 均 `has_more=false`，名稱均為合成「[TEST] 狀態驗證」記錄（Notion fetch 會以反斜線跳脫中括號）。結果也已寫回 TEST 預覽頁，Fetch 查核保留獨立 DB 子頁與原結構。

## 原 Events View：已確認未修改

- `view://3b08ca66-aa4d-8216-8abf-08275d9b29bb`「報名中」**仍是** status_is_not 開放報名；原業務邏輯尚未套用 TEST 通過條件。
- `view://9768ca66-aa4d-82d2-8284-8840f61fd407`「進行中活動」**仍是** status_is_not Complete 群組；尚未套用 TEST 版精確狀態集合。
- 原行政 Events/Groups 頁 https://app.notion.com/p/d578ca66aa4d8303bebf017bdcf7904d 仍有 15 個原 linked database blocks，最近內容未被本回合修改。
- Notion 原 Events 狀態 Schema 當次查得：籌備中（to_do）、開放報名與已額滿（in_progress）、已取消／已結束（complete）。B1 TEST 採相同五個 option 名稱和群組，避免用未核實的假選項測試。

## B2／B3 設計比較（已呈現，尚未套用原頁）

| 分類 | 舊頁存在的風險 | 整批預覽改善 | 原頁仍不變 |
|---|---|---|---|
| 帳務 | 「待處理收據」分待審與人工確認；「待建立收款」有 Session 和 Event Registration，表面名稱易混 | 先區分待審、需人工確認、會談建立收款、活動建立收款、待收款、補助請款、營收 | 14區塊不刪不改 |
| 活動與團體 | 團體要先建場次、場次才建立 Session，與活動報名不同工作流 | 先待處理、再報名、進行中及管理與歷史，B1 狀態模型明確 | 原15區塊、原 View 不改 |
| 人員薪資 | 待建立薪資含 Staff 待處理、Payroll 待拆、PDF 待產 | 明確分成「資料 → 拆單 → PDF → 確認」；排班與請假另外導覽 | 原14區塊、薪資敏感資料不複製 |
| 會議與專案 | 「本週會議」和「全部專案」容易混淆 | 分成會議與專案進度兩類 | 原頁不改 |
| 行政其餘功能 | 特定情境 ALL 實為有限篩選；舊功能已有既定操作路徑 | 各自保留直接入口，後續只修改已證實誤導的名稱 | 原 Intake/Cases/Sessions/Rooms/Tasks/Documents 均未修改 |

預覽不讀取／複製任何真實個案、病歷、財務或薪資列；**但它有導航連結指向既有頁面，View 和顯示範圍不是 Notion 權限隔離**，使用者的原存取權限仍需按 Workspace 設定驗證。

## 驗收範圍、效能及回復

- **PASS**：新 TEST 預覽頁與獨立 DB 已建立、回讀，四欄 Schema 和零 Relation 可核對，五筆合成資料有三組 View 結果 1／2／5 PASS。原兩組 Events View 讀回仍是原條件。
- **PARTIAL**：B2/B3 只完成一次性任務導航預覽，尚未真人試用；B1 通過的是獨立 TEST Data Source，不是原 Events 的真正業務列。
- **PENDING**：00.config_notion 全域映射尚未取得、原行政頁並行變更／實際載入延遲／權限驗證、原始五種狀態的業務定義確認、其他十模組 B 級批次發布、10,000 篇文獻研究。
- **資料及權限**：原 23 個業務 Data Sources、76個原嵌入區塊、177個原 View、Schema、Formula、Relation、角色權限沒有任何寫入。未涉及正式 GAS／Cloud Run／Session／部署。
- **效能**：新增一個 TEST 頁、一張獨立4欄資料庫與5筆合成資料，不改原十頁載入方式；不宣稱量測效能改善。TEST 預覽只有連結，非新權限層。
- **備份與回復**：原頁未修改，已由原 Notion 實際 Fetch 當成比較基準。若決定撤銷這次預覽，**需先核對新 TEST 頁與獨立 DB 是否仍只有五筆合成測試記錄，經使用者同意再封存這兩個 TEST 資源**，不影響原管理頁；不得對真實來源或原 View 執行刪除、清篩選等操作。

## 下一個實作門檻

先完成原始工作流使用者核准與最小備份，確認 B1 在真實 Events 上「報名中」就是只含開放報名、「進行中」是否含已額滿；B2/B3 先比較原/新導航的日常步驟與實際範圍，再一次套用所有經確認的 B 級 View／頁面改動。核心 Schema／公式／Relation／薪資／個案資料改動屬 C，依現有專案指示另需明確批准。
