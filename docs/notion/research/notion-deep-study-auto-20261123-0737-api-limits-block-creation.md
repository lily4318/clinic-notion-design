# AUTO-143｜Notion API 限流、寫入不確定性與免費工作區區塊限制

- 執行標記：AUTO-143 / 2026-11-23 07:37 Asia/Taipei / 僅研究
- 官方來源一：Request limits — https://developers.notion.com/reference/request-limits
- 官方來源二：Workspace block limits — https://developers.notion.com/reference/workspace-block-limits
- 去重鍵：canonical URL 各自獨立；尚未完成所有歷史研究文件的語義去重，**不認列全域新增唯一篇數**
- 閱讀深度：來源一已取得254行官方頁，閱讀限流、重試、503、參數限制等段落；來源二已取得73行官方頁，閱讀適用範圍、寬限期、背景模板、端點與錯誤段落。此為各1次針對性結構化閱讀，**非10/10完整深讀**。
- 研究日期：2026-11-23；頁面當次可讀；不推定最後更新日期。

## 可核對的官方規則

1. API 同時有 connection 與 workspace 層級的限流；一般方案每 connection 180 requests/min，Business/Enterprise 為600 requests/min；data source query 另約3 requests/sec/connection。429 的 Retry-After 必須遵守，workspace 共用限制可能超過60秒。
2. 529 service_overload 與部分 429 可依 Retry-After 重試；對 500/502/503/504 的非冪等寫入不可盲目重送。官方明示503可能已寫入成功但回應逾時，需讀回物件及 retry_guidance；建立物件可能提供 committed_resource_id。
3. API 單次請求限制包括100個relation頁面、100個block陣列元素、1000個block elements/500KB總payload；單次100個relation限制不等於該屬性最多只能保存100個關聯。
4. 多成員 Free workspace 1000 lifetime blocks 限制；刪除不恢復容量。付費與單成員 Free 不受該限制；特定連線受限，personal access tokens/部分 OAuth 不適用，MCP 另有政策。到達限制後有三天寬限，之後建立區塊可能403 restricted_resource；不能把403一律當作缺權限。
5. 背景模板即使建立請求成功，也可能因執行時的block限制而只完成部分內容；沒有公開 template job-status endpoint，也沒有 template-failure webhook。需讀回子區塊，不可自動重新套用而造成重複。

## 治療所情境反例（待驗證，不是已確認缺陷）

1. 批次讀取 Sessions 時遇 workspace 層級429，誤把部分資料當作完整會談數。
2. GAS/Notion 同步寫入收到503即重送，導致同案同期方案用量重複建立。
3. 以每秒3次固定節奏假設所有 workspace/connection 都不會429，忽略共用配額。
4. 將403一律歸因於心理師權限不足，實際可能是免費工作區block限制。
5. 定期模板頁建立成功但內容未完成，行政人員誤認週回報已完整產生。
6. 為了釋放免費容量刪除舊頁，卻因 lifetime block 規則仍無法建立新頁。
7. 一次更新超過100個 Relation 目標，遇validation_error後將既有關聯錯誤判成只有100個。
8. 對未完成的模板再次套用，重複建立子區塊，產生多筆額度／週報表象。

## 反證邊界與研究結論

上述情境僅供未來測試設計；官方限制並不證明目前治療所工作區使用Free、已達1000 blocks、使用特定Notion API版本，或存在上述故障。必須先查真實連線方案、錯誤內容、寫入後讀回及當期版本；目前禁止進入任何實作。

## 計量與安全

- 本輪官方可讀候選來源2；針對性閱讀2；待驗反例8；嚴格獨立全文深讀0；完成10/10來源0。
- 全域唯一來源增量保守認列0（尚未全歷史語義去重）；累積可核實10/10暫採0/10,000。
- 本輪僅GitHub研究紀錄；Notion、GAS、Cloud Run、Session皆未修改。
