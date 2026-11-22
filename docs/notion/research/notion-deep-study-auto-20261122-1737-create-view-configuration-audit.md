# AUTO-130｜Create a view：顯示配置與可觀測性獨立核讀｜2026-11-22 17:37 Asia/Taipei

- 軌跡：AUTO-130 / create-view-configuration-audit / 20261122-1737；僅外部研究與 GitHub 進度紀錄。
- 來源：Create a view — Notion Developers
- canonical URL：https://developers.notion.com/reference/create-view
- 去重鍵：notion-developers:reference/create-view
- 先前相同來源：AUTO-128（15:43）、AUTO-129（16:45）；本輪不新增唯一來源，不將任何部分閱讀當完整深讀。
- 取證方法：2026-11-22 重新取得搜尋系統回傳的官方可讀正文（API、必填欄位、配置選項、錯誤、權限及回應），與前兩輪紀錄分別核對；未逐段取得全頁，僅認列獨立針對性部分閱讀 1 次、完整深讀 0 次。直接開啟其他 Notion 官方頁面失敗。
- GitHub 前置：重新讀取 main 的 README、根 AGENTS、source-of-truth、Notion AGENTS、sources、decision-log、acceptance-status，以及 research/ 與 research/runs/ 清冊；比對 AUTO-128、AUTO-129；寫入前重新 Fetch 七份核心檔案 blob SHA 並確認此獨立新路徑不存在。

## 本次與先前不同的閱讀焦點：配置／回應契約

官方端點 POST /v1/views 的 body 除 data_source_id、name、type 外，包含 filter、sorts、quick_filters、configuration；configuration 的 type 必須與 View type 一致。支援 form、chart、map、dashboard 等多種 type，但不等於每一類型都具有相同顯示欄位與能力。建立回應包含 object=view、id、parent、type；HTTP 200 只證明請求成功，不能證明工作者看到的版面、篩選與權限符合需求。sorts 上限 100。建立操作要求 insert content 和 update content。這些是 API 契約，不是現有治療所已實測的結果。

## 新反證情境（均待驗，不得冒稱系統已出錯）

1. View type 選為 calendar，configuration.type 卻是 table：需驗證是否遭拒或無法得到預期顯示，不假定 API 自動轉換。
2. chart、form、map 與一般 table 的可配置屬性不同：若直接複製同一套 configuration，需逐類型驗證合法性與實際顯示。
3. POST 200 且回傳 View ID，但使用者開啟工作台未看到正確 tab：需分開驗證 API 建立、頁面掛載與真人可見性。
4. 只保存 View 名稱而未保存回傳 id，日後同名 View 無法可靠區分：研究應將 id 當追蹤鍵，而非名稱。
5. 回應的 parent 是資料庫，卻把它當成 dashboard widget 的父層：需核對 parent 與指定建立位置的一致性。
6. 快捷篩選是互動式顯示控制，不能代替伺服端業務資料權限或跨期隔離：需以角色授權獨立驗證。
7. 使用多達 100 個排序條件雖符合陣列上限，但並不代表合理操作體驗；需要以實際工作任務驗證排序策略。
8. API 版本改變後，既有 View configuration 可能需要重新驗證：應固定 Notion-Version，且不能將舊版成功結果自動外推到新版。

## 研究計量與邊界

- 本輪新來源：0；同一 canonical URL 的獨立**部分**複讀：1；新增反證假說：8；嚴格完整深讀：0；新完成10/10：0。
- AUTO-128、129、130 是同一來源三次部分研究，**不是**三篇來源，也不是第3/10次完整深讀。
- 累積可核實完成10/10仍暫採最近基準 **0／10,000**；全歷史語義去重與十輪證據尚未完成。
- 未操作 Notion 頁面、資料庫、View、公式、權限、GAS、Cloud Run、Session；未開始重新設計。
