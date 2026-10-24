# 2026-10-24｜行政任務工作台 TEST v2：整體 UX 改版與回查

## 原因、目標、來源

原 [十模組 B1～B3 預覽](https://app.notion.com/p/4038ca66aa4d814297a2dbe27e8d054d) 按技術修正階段排列，並混用「原 Events View 尚未修改」等已過時文案；實際使用者不易按一天工作順序找到入口。本輪依此前研究成果的漸進揭露、資訊氣味、任務優先、減少同屏 database 負載原則，**將整張 TEST 預覽改版成任務型工作台**。

參考研究來源：`../research/research-to-implementation-matrix.md`（U01/U02/U03, N01/N02/N03），以及 [Notion Linked Views](https://www.notion.com/help/notion-academy/lesson/linked-views)、[效能說明](https://www.notion.com/zh-tw/help/optimize-database-load-times-and-performance)。

## 修改與備份

- 原頁：https://app.notion.com/p/4038ca66aa4d814297a2dbe27e8d054d
- 新標題：「[TEST] 治療所行政任務工作台｜整體 UX v2」，icon「🧭」保留。
- 改版前 Notion 原生複本：https://app.notion.com/p/4038ca66aa4d81389417ca0faadf3492 ，現名「[BACKUP] 十模組 B1–B3 預覽｜完整改版前 2026-10-24」。
- 複本連原先獨立 TEST 資料庫也複製出一份新 DB（其資料源與原 DB 不相同）。**此備份用於回復版面文字，不應混入原活動資料，也不應當成正式會談或營運來源**。
- 修改目標只有原 **TEST 預覽頁內容與標題**，不是原行政首頁、十個原行政頁或任何業務資料庫。

## 一次性版面設計

1. **① 今天先處理**：預約會談、Intake、Tasks、Rooms。
2. **② 接續處理業務**：Cases/Care Episodes、Billing/Receipt、跨方案補助 TEST、Events/Groups。
3. **③ 人員、協作與管理**：Staff（薪資分階段）、Meetings/Projects、Documents、返回原首頁。
4. **④ 測試／研究／回復**：三個原生收合區分別容納採用原則、活動五狀態測試（1/2/5 PASS）、安全邊界與回復；原獨立測試 DB 完整保留。

不新增黃色 Callout；保留原 TEST 資料庫 tag：`collection://5864ca97-2ceb-4727-a52c-9b7cf749dcd9`。用原十模組的 Notion 頁面 mention 直接導覽，不重複在入口複製76個 block。

## 實作與讀回驗收

- **PASS：Notion Fetch 結構**：標題修改成功；頁面包含四個主要 `##` 工作區及4個兩欄分支、3個原生 toggle、1個原獨立 TEST 資料庫，沒有黃色警示；原子資料庫 page ID 完全保留。
- **PASS：前後可比**：改版前備份存在且包含舊的 B1、B3 預覽及一個獨立 TEST DB 複本；實際修改沒有觸及其他頁。
- **PASS：原來源不變**：未建立新會談／收費／個案資料來源，未更改既有行政10頁 Schema、Formula、Relation、View、權限或資料列。
- **PENDING：實際可用性**：未由真實負責人／行政／心理師身份完成「找待辦、查預約、處理收據、跨期補助」的任務路徑操作；未量測手機／桌機可讀性、點擊次數、開啟時間及角色可見性。
- **PENDING：補助計算**：跨政府方案期別隔離、原生計算及方案最新正式規則不在本輪完成，不能從首頁入口推論計算驗收。
- **安全／效能**：這是 TEST 導覽，連結依舊受原 Notion 分享權限限制；用較少嵌入資料庫是設計策略，**尚未量測實際效能**。

## 回復與版本

若使用者決定恢復：先重新 Fetch 原 TEST v2 頁及改版前 BACKUP 頁，確認無並行更新；只將原 TEST 預覽頁任務導航、文字及標題還原為舊版，保持原獨立 TEST 子資料庫 ID 不變。**不可直接用備份的新複製 DB ID 替換目前測試 DB**、不可刪除原業務資料、也不得依舊狀態覆蓋同事新修改。

需同步：`docs/notion/README.md`、`decision-log.md`、`acceptance-status.md`、`sources.md`、`research/README.md`、`AGENTS.md`，及 `long-term-goals.md`。
