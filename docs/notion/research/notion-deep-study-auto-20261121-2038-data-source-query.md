# AUTO-109｜Notion API Data Source Query｜2026-11-21 20:38 Asia/Taipei

- 執行軌跡：AUTO-109-20261121T2038-DSQUERY；只新增本研究紀錄，不修改任何 Notion 或正式系統。
- 來源：Notion Developers，**Query a data source**，https://developers.notion.com/reference/query-a-data-source
- 去重鍵：canonical:https://developers.notion.com/reference/query-a-data-source（去 fragment / query）；本輪在 docs/notion/sources.md、docs/notion/decision-log.md、research/README.md 與首批 evidence-register 中未發現精確網址；未逐一核對所有歷史研究紀錄的內文，因此**全域唯一性未證實，候選1篇，不正式計入唯一新增**。
- 取證日期：2026-11-21；來源頁面由網頁工具成功取得，總計1322行，僅核讀 API 概覽、請求示例、狀態碼與回應片段（主要 L110–185、L310–356、L445–489、L671–718、L806–810），不是全文十遍深讀。
- 閱讀次數：本次獨立針對性文字閱讀1次；完整深讀0次；10/10達標新增0篇。
- GitHub 起始 main SHA：a459949e28e07101705ee39db5bda4663ba9e785；寫入前再取 main 以確認並行更新。已閱讀 README、根 AGENTS、source-of-truth、Notion AGENTS、sources、decision-log、acceptance-status、研究索引及首批來源清冊。

## 官方原文核讀（僅針對性）
1. Query endpoint 為 POST /v1/data_sources/{data_source_id}/query，支援 filter、sorts、start_cursor、page_size；SDK 範例以 dataSources.query 查詢。
2. 概覽明言回傳可能少於 page_size；若有 next_cursor，必須按分頁規則繼續。
3. 範例回應有 has_more、next_cursor、results，亦展示 request_status 及 incomplete_reason；不能把單頁回應等同全量。
4. API 文件列示 400、401、403、404、406、409、429、500、503、504、529 等狀態碼；不能把各種失敗都當作空結果。
5. Wiki 的資料來源子項可能不是一般 page，文件特別提及 result_type 篩選 page/data_source；不能假設結果全部為 Session 頁面。

## 六項反證／待驗假說（研究推論，非現況缺陷）
1. 只讀第一頁，has_more=true 卻直接計算補助會談總數：應測試跨頁完整性。
2. results.length < page_size 被誤判「查完」：應依 next_cursor/has_more，而非筆數判定。
3. 把 403/404 當作零筆 Session：應區分權限/來源 ID 問題與真正空集合。
4. Query filters 指向不同核定期別而程式仍沿用舊 cursor：應固定查詢契約並核對跨頁條件。
5. Wiki 來源回傳 data_source 物件卻當成會談 page 計數：應檢查 object/result_type。
6. request_status 提示查詢結果上限，卻仍將目前累計視為全量：應標記不完整並停止核准性統計。

## 限制與後續
- 本輪未做 Notion API 實際請求、角色權限、原生公式、資料量/載入測試；未觀看所有互動區塊、完整核對整頁文件或所有連結。
- 本輪新增：候選來源1、部分閱讀1、反例6、完整深讀0、可驗證10/10新增0。累積10/10沿用最近可核實基準 **0/10,000**，未完成全歷史語義去重，不能當作重新全量稽核後的精確統計。
- 不進入 Notion 重新設計，待全部研究達標及使用者確認。
