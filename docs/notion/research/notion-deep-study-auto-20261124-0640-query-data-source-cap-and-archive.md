# AUTO-166｜2026-11-24 06:40｜Query a data source 大型結果截斷與歸檔範圍複讀

- 來源：Query a data source｜Notion Developers
- Canonical URL：https://developers.notion.com/reference/query-a-data-source
- 去重身份：notion-developers:reference/query-a-data-source；既有 AUTO-124 同URL，因此**新增唯一來源0**。
- 本輪讀取：官方可讀頁約1322行；針對 Overview、Archived pages、Pagination limit、Performance、Permissions、Formula/Rollup limitations、Errors 各段獨立核讀（約806–1098行）。**獨立針對性部分複讀1次，非完整逐篇深讀，不計10/10**。與 AUTO-124 端點及一般游標契約的閱讀重點不同。
- 查核日期：2026-11-24（台灣時間）；官方 API 版本範例：2026-03-11。
- 證據定位：官方頁 843–857 歸檔選擇；861–875 10,000筆上限與 request_status；879–902 filter_properties；1064–1097 權限、公式限制及503重試。
- 既有來源記錄：docs/notion/research/notion-deep-study-auto-20261122-1142-query-data-source-contract.md。

## 本輪新辨識的官方契約

1. `archive_status` 可選 `active`（預設）、`archived`、`all`；不包含垃圾桶，也不擴張連線權限；跨分頁需保持相同選擇。
2. 單次查詢最多可分頁取得10,000個結果；到上限時即使 `has_more=false`，仍可能因 `request_status.type=incomplete` 而截斷。必須每頁檢查 request_status，不得把游標結束等同全量完成。
3. 超過上限的完整掃描可按 created_time 時間窗分割，但分割查詢仍需處理重複、邊界與並行更新；這是研究衍生驗證條件，不是官方提供快照一致性保證。
4. `filter_properties` 可以減少大型 Formula/Rollup/Relation 回應負擔，但未回傳欄位不是空值；需要再取個別頁面或屬性。
5. Relation 超過25筆時，依賴 Relation 的 Formula 可能只計入25筆；多層 Relation 的 Formula/Rollup 亦可能不正確。這不是對治療所現有計數已出錯的實證。
6. 未分享父資料庫給 Integration 可能回404；缺讀取能力回403；503可依 additional_data 採指數退避、縮小頁數或收窄條件。

## 反例／待驗情境（均未在正式治療所系統測試）

1. 10,000筆結果最後一頁 has_more=false，但 request_status=incomplete；若直接宣告完整盤點，產生假陰性漏資料。
2. 將 archived 排除後的「有效筆數」誤稱全部歷史資料；必須記錄 archive_status。
3. 使用 archive_status=all 誤以為包含 Trash；仍漏垃圾桶。
4. 將 filter_properties 未回傳的補助欄位當作 NULL 或0，造成錯誤額度。
5. 依 Relation 超過25筆的 Formula 值判定個案已用次數，可能低估。
6. 分割 created_time 時間窗時使用不一致的包含邊界，漏掉臨界時間戳資料。
7. 503逾時後無退避無限制重試，造成負載與失敗放大。
8. 404被誤當作資料來源已刪除，而未查父資料庫分享權限。

## 計數及限制

本輪新增唯一來源0、部分獨立複讀1次、完整深讀0次、待驗反例8項；本來源仍未有可稽核的10次完整深讀。全歷史逐篇去重及10/10盤點未完成，**累積可核實完成10/10保守記0／10,000**。本紀錄僅供研究；不授權 Notion、GAS、Cloud Run、Session 或權限修改。

研究軌跡：AUTO-166-20261124-0640-query-data-source-cap-archive。