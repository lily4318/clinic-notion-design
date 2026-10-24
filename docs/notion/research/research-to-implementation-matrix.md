# 研究結果 → 設計 → Notion 實際狀態｜可追溯對照

基準日期：2026-10-24。研究來源 ID 依 [16 筆歷史證據登錄](evidence-register-2026-10-24.md)。歷史紀錄中 N03、N07 僅有搜尋摘要，**不作為已全文精讀**。本表只對應既有成果與本回合實際讀回，不增加研究篇數。

| 研究／設計規則 | 來源 ID | 對應文件／決策 | 本輪之前／本輪 Notion 實作 | 尚未核實 |
|---|---|---|---|---|
| 常用任務優先、進階明細收合 | U01, U02 | `workbench-ux-principles.md` | 本輪 [行政任務 TEST v2](https://app.notion.com/p/4038ca66aa4d814297a2dbe27e8d054d) 四區任務路由＋3個收合檢視 | 真人使用者步數與操作時間 |
| 名稱應預告實際任務 | U03, U02 | `audits/b1-b3-legacy-batch-2026-10-24.md` | 帳務收據／活動收款／薪資階段明確分名；TEST 入口使用任務名稱 | 操作誤選率 |
| 避免高流量首頁大量同時開 DB | N01 | `performance-permissions-free-plan.md` | TEST v2僅保留1個獨立測試資料庫作附錄，不重複嵌入十模組76區塊 | 真實開頁延遲 |
| 一個來源可有不同 Views，但各自設定 | N02, N03 | `workbench-vnext-2026-10-24.md` | B1新增2個正確 View、舊版停用；補助參與分不同 View | 個別來源讀取資料是否符合預期、無全域同步方案篩選 |
| 保留原資料與來源關聯，不以年度複製 Cases | D01, D02, N04 | `government-subsidy-architecture.md` | TEST補助工作台沿用 Price Plans／參與紀錄／Sessions／Staff，未重建個案核心表 | 跨政府方案與核定期別真實規則 |
| 參與記錄以個案×方案實例區別 | D01, D02, N04 | `government-subsidy-architecture.md` | 已定候選唯一鍵；未見 Notion 原生複合 UNIQUE 保證 | 重複鍵、Relation 和跨期額度 |
| 避免多層 Formula／Rollup 及 Formula 篩選 | N01, N05 | `database-design-principles.md`、十模組稽核 | 23個 Data Source／636欄歷史結構盤點，未擅自刪公式 | 原生計算結果、依賴深度與延遲 |
| 設計需兼容 Notion 免費版限制 | N06, N07, N08, N10 | `performance-permissions-free-plan.md` | TEST v2只用基本連結、欄位、列視圖、折疊／兩欄，不依賴付費 Dashboard 全域篩選 | 工作區目前方案與所有角色權限 |
| 不靠隱藏 View／欄位執行角色授權 | N06, N07 | `docs/notion/AGENTS.md` | 沒有新增對敏感資料的分享權限，原頁權限不變 | 角色帳號實測 |
| Database Template 不應意外預設關聯到正式頁 | N09, N11 | `database-design-principles.md` | 本輪未建立含真實 Relation 的新模板或欄位 | 模板逐套實測 |
| 活動「報名中」及「進行中」條件要與 Status 相符 | N02, U02 | `audits/b1-b3-legacy-batch-2026-10-24.md` | 隔離五狀態測試1／2／5 PASS；原管理 View 新版條件正確、真實查詢0筆 | 真實活動案例可用性 |
| 非必要不動其他已確認功能 | U01, U02, N04 | `docs/notion/AGENTS.md` | 這輪只重整 TEST 任務預覽內容，不動十個原頁、Scheme/Session 等原資料 | 未來各頁真實需求評估 |

## 先前學習資料的完整性結論

- **已有**：資料庫正規化、Relation／Formula／Rollup、Notion Free／效能／權限、UX 理論、政府補助跨期設計、十模組結構稽核、B1～B3 回歸測試、GitHub 更新記錄及備份路徑；已建立這份可追溯連結矩陣。
- **缺少**：大量 Notion 模板逐套原型截圖／比較、個別研究文章的逐節深讀記錄、每一真實使用者任務完成率、每個角色的權限驗證、補助當期的公式與規則實值證據。
- **不可宣稱**：所有歷史網頁都已通篇精讀、1,000或10,000篇研究達標、免費版支援真正全域同步期別篩選、所有補助公式已正確、任務工作台已經受過真人可用性驗收。

## 回查規則

每次 Notion 進一步實作時，優先查此矩陣、最新 `long-term-goals.md`、`decision-log.md` 及 `acceptance-status.md`，再 Fetch Notion 真實 Schema／View、最近版本與當期官方規則；在同回合更新**實作證據**而不是只修改「已完成」字樣。
