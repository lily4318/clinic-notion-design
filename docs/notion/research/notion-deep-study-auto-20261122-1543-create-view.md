# AUTO-128｜Create a view｜2026-11-22 15:43 Asia/Taipei

- 軌跡：AUTO-128 / create-view / 20261122-1543；研究限定，無 Notion 寫入。
- 標題：Create a view — Notion Developers
- canonical URL：https://developers.notion.com/reference/create-view
- 去重鍵：notion-developers:reference/create-view；主要 sources.md 當次未見精確 URL；全歷史語義去重未完成，正式新增唯一來源計數 **0**。
- 取證：2026-11-22 網頁搜尋提供可讀的官方端點正文及參數、錯誤節；未取得全頁逐段完整閱讀，故僅記 **針對性部分閱讀 1 次**，完整深讀 0 次，10/10 新完成 0 篇。
- GitHub 前置：重新讀取 main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md，及 research 目錄清冊；目標採新獨立檔，避免覆蓋並行增量。

## 官方端點摘要（部分正文）
POST /v1/views 建立 database view 或 dashboard widget；須指定 database_id、view_id、create_database 三者恰好其一，並提供 data_source_id、name、type。支援 table/board/list/calendar/timeline/gallery/form/chart/map/dashboard 等型態。建立需要 insert content 及 update content capabilities。filter/sorts/quick_filters 與顯示配置可分別設定；sorts 上限 100。Notion-Version 為必填，搜尋所得頁面列出 2026-03-11。404 可由資源不存在或連線無權限造成；400 可能來自定位欄位互斥錯誤；400/429 可能為請求限制。

## 本輪新反例假說（待驗，非既有系統缺陷）
1. 建立 View 只傳 database_id 而忘記 data_source_id，造成 400。
2. 同時指定 database_id 和 view_id，互斥條件錯誤。
3. 只有 read content 權限，建立 View 遭拒，不能歸因於資料不存在。
4. 404 被當成刪除而重建資料庫，實際可能只是連線權限不足。
5. 把 View filter 當作個案資料授權邊界，造成角色資料暴露風險。
6. 新 View 沒有複製必要篩選，讓跨期補助記錄混列。
7. 在 dashboard widget 和資料庫 tab 之間使用錯誤的 placement/position，操作入口不符合預期。
8. 429 後無節流直接重送，與其他流程競爭共享額度。
9. 只驗證 POST 成功而未讀回 View 配置，錯誤篩選未被發現。

## 研究判定
本輪僅外部文獻研究，無真實 Notion、GAS、Cloud Run、Session 修改；未取得完整正文，嚴格深讀 0 次。累積完成 10/10 以最近可核實基準 0/10000 篇暫列，須全歷史稽核才能更新。後續應在完整正文可讀時獨立深讀並與現有研究 URL 清冊去重。
