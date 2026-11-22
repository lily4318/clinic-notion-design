# AUTO-127｜Retrieve a block 官方 API 針對性研究（2026-11-22 14:38 Asia/Taipei）

- Trace: AUTO-127-20261122-1438-RETRIEVE-BLOCK-READONLY
- 來源標題：Retrieve a block — Notion Docs
- 原始 URL / canonical identity: https://developers.notion.com/reference/retrieve-a-block / notion-dev:reference/retrieve-a-block
- 來源性質：Notion 官方 API reference；原始發表日期未核；查閱 2026-11-22。
- 研究證據：官方頁面當次可讀，主文第319–340、557–561、576–595及回應型別603–674行；範例、錯誤碼與契約部分閱讀。未完整核讀所有 block subtype 結構、外鏈、示意與實機，因此 **PARTIAL**，不計嚴格完整 R1。
- GitHub去重：本輪 sources.md 精確網址比對0次命中；全歷史同文異址及其他研究文件語義去重未完成，僅記新候選1，不認列全域唯一新增。

## 已核對事實與應用邊界

1. GET /v1/blocks/{block_id} 取得指定 block 物件；若 has_children=true，須另以 Retrieve block children 取得其下內容；單次取得父block不能視為整頁完整備份。
2. 要讀某頁內容，可將 page ID 當作 block_id 呼叫 children 端點，而非假定 retrieve block 已展開頁面全部內容。
3. 需要 read content capability；缺少能力可回403；404同時可能表示不存在或整合沒有權限，不能單靠404判斷刪除。
4. Notion-Version 是必要標頭；當次官方參考顯示 2026-03-11。
5. 官方回應型別包含 synced block、child database、column、table、unsupported 等多種結構；未知型別不可靜默丟棄。
6. 400/429 與請求限制相關；其他 409/503/504/529 亦列於可能錯誤清單；不能把非200都轉成「資料不存在」。

## 待驗反例（研究假說，不代表本所缺陷）

- CE01：只讀父block就宣稱已備份全部 Session 工作台內容。
- CE02：has_children=true 卻未追 children，導致折疊區內警示/說明遺漏。
- CE03：將403當作不存在，誤刪 GitHub 研究清冊內既有映射。
- CE04：將404當作已刪除，忽略整合未被分享至該區塊。
- CE05：解析器只支援 paragraph/heading，忽略 synced block/child database/unsupported。
- CE06：將 page ID 與 block ID 的查詢語意混淆，產出空白頁面備份。
- CE07：未固定 Notion-Version，將不同API契約回應誤判為資料異動。
- CE08：讀取部分區塊失敗仍標記整頁備份 PASS，造成回復能力虛假保證。

## 計數與界線

- NEW_SOURCE_CANDIDATE=1；GLOBAL_DEDUP_CONFIRMED_NEW=0（待全歷史稽核）。
- PARTIAL_TARGETED_READ=1；FULL_R1=0；FULL_R2_TO_R10=0；FULL_DEEP_PASS_10_OF_10_THIS_RUN=0。
- 累積嚴格10/10可核實基準仍為0/10,000篇（尚未重新完成全歷史稽核）。
- 未實際測試本所 Notion API、真人UX、角色權限、原生公式、效能或備份回復；未修改 Notion、GAS、Cloud Run、Session或正式部署；不進入重新設計。
