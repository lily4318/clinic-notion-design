# AUTO-111｜2026-11-21 22:40 Asia/Taipei｜Retrieve a block 官方文件針對性閱讀

- 執行軌跡：AUTO-111-20261121-2240-retrieve-block；僅研究與 GitHub 進度，不操作 Notion。
- 來源：Notion Developers, Retrieve a block，https://developers.notion.com/reference/retrieve-a-block
- canonical URL／去重 ID：https://developers.notion.com/reference/retrieve-a-block
- 擷取時間：2026-11-21 22:40（台灣時間）；官方頁面在本次網頁工具可讀，總 693 行。
- 本輪實際核讀範圍：L105–128、L205–318、L319–358、L443–561、L575–688。重複程式語言範例與全部互動範例未逐一實測。
- 閱讀等級：官方文字針對性部分閱讀一次；**不認列完整深度閱讀、不認列10/10**；是否全域新 URL 仍待完整歷史語義去重。

## 直接可核對的文件事實

1. GET /v1/blocks/{block_id} 讀取單一 Block object；它不是取得整個頁面所有子內容的操作（L319–338）。
2. 回傳 has_children=true 時，須另外呼叫 Retrieve block children；頁面內容亦以頁面 ID 作為 block_id 查子區塊（L557）。
3. 此端點需 read content capability，缺少能力回傳403（L558）。
4. 404 既可能表示區塊不存在，也可能表示連線無存取權；不能僅靠404判定已刪除（L559–561）。
5. API 要求 Notion-Version header；當次文件列最新 2026-03-11（L575–586），須按正式版本再確認。
6. 回應可能有多種 Block 類型，包括 synced block、child database、table、image、file 等（L595–673）；不能假定皆為純文字段落。

## 新的反證／邊界案例（研究推論，非本所已確認缺陷）

1. 只 retrieve 頁面頂層 block 就宣稱已完整備份行政操作說明：若 has_children=true，實際漏掉子區塊。
2. 把404直接當作頁面遭刪除而觸發清理：實際可能是 integration 未被分享。
3. 用只支援 paragraph 的 parser 解析補助管理頁：table、synced block、child database 或其他類型可能被忽略。
4. 把 read content 403 當作網路故障無限重試：能力設定問題不會因單純重試解決。
5. 讀取單一 block 成功就推論所有 Linked View 資料列已完整讀取：block 與 data source query 是不同的資料路徑。
6. 未記錄 API 版本便把舊 JSON 結構套用到新版：可能誤讀類型或權限差異。

## 計量及限制

- 新候選來源：1（不保證全歷史唯一）；本輪針對性文字閱讀：1；新反例：6；嚴格完整深讀：0；新增完整10/10：0。
- 累積可核實完成10/10：沿用最近可核實基準 0 / 10,000；未完成全歷史逐篇十輪稽核。
- 未測 API 實際連線、未看所有互動與媒體、未做真人 UX、未更動 Notion/GAS/Cloud Run/Session。
