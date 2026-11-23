# AUTO-160｜Retrieve a page as markdown：完整性與未知區塊風險（2026-11-24 00:36 Asia/Taipei）

- 執行軌跡：AUTO-160-20261124-0036-retrieve-page-markdown；只讀外部官方文件、只新增 GitHub 研究紀錄。
- 原始來源：Notion Developers, **Retrieve a page as markdown**，https://developers.notion.com/reference/retrieve-page-markdown
- canonical URL：https://developers.notion.com/reference/retrieve-page-markdown
- 去重識別：notion-dev:reference/retrieve-page-markdown；研究目錄176項檔名未見 markdown 主題，但未完成所有歷史檔案正文 URL 比對，**新增唯一來源暫不認列**。
- 取得日期：2026-11-24；來源頁面無可核實發表日期；版本頁顯示 Notion-Version 2026-03-11。
- 閱讀證據：本次取得官方可讀正文，針對 use cases、general behavior、unknown blocks、errors、query parameters、response schema 進行**一次針對性部分閱讀**，不是完整深讀，亦不是 10 次複讀。
- 統計：候選1、已實讀相關段落1、獨立部分閱讀1、完整深讀0、可認列新增唯一來源0、10/10完成0。

## 官方契約核對
1. `GET /v1/pages/{page_id}/markdown` 回傳 `page_markdown`，含 `markdown`、`truncated`、`unknown_block_ids`；不能只看 markdown 字串就聲稱全部內容已擷取。
2. `markdown_version=v2` 是推薦格式；`v1` 已棄用，未來版本會拒絕。API 版本與 Markdown 版本是不同維度。
3. 未知區塊可能源自約20,000區塊截斷、權限不足、或不支援的區塊類型。截斷／權限造成的 unknown IDs 可嘗試逐一讀取；權限不足會回 404；不支援類型須改用 block API。
4. `unknown_block_ids` 不能直接區分截斷和權限，故不能僅憑 unknown 數量推定遺漏原因。
5. `include_transcript` 預設 false；不應把未帶逐字稿的 markdown 當作含完整會議內容。這是可能涉及敏感資訊的能力，未授權不得抓取真實資料。
6. 需要 read content capability；404 也可能代表未共享權限，不一定是頁面不存在。

## 待驗反例（研究假說，非已確認系統缺陷）
1. 只保存 markdown，忽略 `truncated=true`，誤宣稱工作台已完整備份。
2. 遇到 `unknown_block_ids` 一律重試，權限不足的子頁反覆404卻被誤判為不存在。
3. 書籤／嵌入等不支援類型被忽略，造成工作台實際入口盤點遺漏。
4. v1/v2 Markdown 版本混用，格式轉換結果不同卻誤判頁面被改動。
5. 把頁面文字快照當成 Data Source、View 篩選、角色權限或 Session 業務紀錄的完整備份。
6. 未包含 transcript 就宣稱所有會議資訊均已讀取。
7. 以 markdown 字串內的資料庫呈現文字代替對真正 Data Source 的分頁查詢。
8. 將 API 404 判定為頁面刪除而啟動重建，忽略 Integration 存取權差異。

## 對治療所設計的邊界
本次只形成未來**唯讀盤點檢核項**：記錄 `truncated`、未知 ID、unsupported block、權限及內容型別；工作台 markdown 不能替代 Session / Price Plan / 補助用量 Data Source 與 View 的獨立核對。未執行任何 Notion API 讀寫真實個資、未驗證正式工作台；無設計採用或重構授權。

## 未完成
- 尚未逐篇全文十次獨立深讀、尚未全歷史 URL 去重；累積可核實10/10仍保守0／10,000。
- 需後續研究輪次分開記錄完整閱讀證據，不能將本次8個反例冒充8次閱讀。
