# AUTO-131｜Retrieve a view：讀取契約與錯誤分類｜2026-11-22 18:39 Asia/Taipei

- 執行軌跡：AUTO-131-20261122-1839-RETRIEVE-VIEW；僅外部研究與 GitHub 記錄。
- 標題：Retrieve a view — Notion Docs / Notion Developers
- 原始 URL：https://developers.notion.com/reference/retrieve-a-view
- canonical 去重鍵：notion-developers:reference/retrieve-a-view
- 取證：2026-11-22 取得官方可讀 HTML 文字（頁面約683行），閱讀端點說明、SDK/cURL 範例、回應範例、Connection capabilities、Errors、header、path、response schema；不包括互動式 Try it、實際授權呼叫或 UI 實測。官方頁面閱讀範圍約 L108–129、L206–325、L326–360、L450–678；頁面導航/重複多語程式碼未逐一驗證，因此標記**針對性部分閱讀**，嚴格完整深讀0次。
- GitHub 前置：本輪重新 Fetch main 七份核心規範及 research/README，核對 blob SHA；sources.md 全文未出現本精確 URL，research/README 與 AUTO-130 未見該 URL；全歷史同義/別名去重尚未完成，僅列**候選來源**，不正式認列全域唯一篇數。

## 可核對官方契約

- GET /v1/views/{view_id} 依 View ID 取得 View object；需要 integration 的 read content capability。
- 必須提供 Authorization Bearer 與 Notion-Version；文件頁面當時列最新版本 2026-03-11。200 範例有 object=view、id、parent、type；type 可能是 table、board、list、calendar、timeline、gallery、form、chart、map、dashboard。
- 404 可能表示 View 不存在，**也可能是連線無權存取**；400/429 可能與請求限制有關。文件同時列出 401、403、406、409、500、503、504、529 等錯誤範例，不能只靠 HTTP code 推斷唯一根因。
- 成功取得 View metadata 不等於已查得所有資料列、真人可見性、篩選正確性、操作權限或速度；此為從 API 回應範圍推導的驗收界線，不是官方保證。

## 新的待驗反證（研究假說，非已確認治療所缺陷）

1. 只依 View 名稱定位，兩個同名 View 讀錯設定：應以 View ID 對照 parent 與 type。
2. 404 被當成 View 已刪除而重建：其實可能是 integration 沒被授權，造成重複 View。
3. 讀取 metadata 200 就宣稱工作台清單資料完整：尚未讀取查詢結果及分頁。
4. parent 指向非預期資料庫，卻因 type=table 相同就判為通過：需比對預期 Data Source 與工作台位置。
5. 401 token 錯誤與 403 權限不足混為一談，錯誤處理直接重送而不排查授權。
6. Notion-Version 未固定，升級後 response contract 改變卻沿用舊驗收。
7. 將 GET 回應 200 當作人員有權編輯：read content capability 不等於 update content。
8. 429/503/529 被當作永久遺失 View：應區分暫時性服務問題與資源不存在，避免不必要重建。

## 計量與限制

- 本輪候選來源 1（未完成全歷史語義去重，正式新增唯一來源 0）；官方針對性部分閱讀 1；新增反證假說 8；嚴格完整深讀 0；10/10 新完成 0。
- 累積完成10/10維持最近可核實基準 0/10,000（全歷史稽核未完成）。
- 不將 API 文件的讀取視為 Notion 系統的實際驗收；未修改 Notion 頁面、資料庫、View、公式、權限、正式 GAS、Cloud Run 或 Session；未開始重新設計。
