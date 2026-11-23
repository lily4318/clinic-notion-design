# AUTO-150｜Append block children：位置、非冪等追加與回讀風險

- 執行軌跡：AUTO-150 / 2026-11-23 14:45 Asia/Taipei / GitHub-only research
- 官方標題：Append block children — Notion Docs
- Canonical URL：https://developers.notion.com/reference/patch-block-children
- 來源機構：Notion Developers；查核日期：2026-11-23；API 文件即時版本，未固定版本號
- 去重身份：canonical URL 完全一致判定；本輪核對 docs/notion/research 目錄與首批來源登錄；全歷史文件正文尚未完成全面語義去重，因此只列候選，不正式增加唯一來源總數。
- 閱讀深度：官方正文針對性部分閱讀 1 次；不是全文深讀，更不是 10/10。沒有執行 API 寫入。

## 可核對正文與推導

1. 官方端點是 PATCH /v1/blocks/{block_id}/children，作用是向指定父區塊追加子區塊；父項可為 block、page 或 database。不能誤認為覆寫現有子區塊。
2. 請求包含 children 陣列；範例另有 position.type=after_block 與 after_block.id，表示位置可以明確指定。對頁面排列順序不能只依賴客戶端預期。
3. 成功範例回傳 list/results 與 has_more/next_cursor；不能以單次回應列出的子項推斷父區塊完整子項數，完整盤點需使用讀取子區塊端點並完成分頁。
4. 文件列出 409、429、503、504、529 等錯誤；追加是產生新區塊的操作，逾時後盲目重試可能造成重複區塊。這是工程風險推論，需另以狀態碼文件確認重試細則。
5. 本端點只說明追加區塊，不代表可用來原子修改 Relation、Session 計數或資料庫 schema。

## 八個待驗反例（均非實測缺陷）

1. 追加補助操作提示遇 503 後重送，導致兩份相同提示。
2. 並行使用 after_block 插入，實際順序與原先視覺預期不同。
3. 只看 PATCH 回應 results，誤判工作台其他子區塊已消失。
4. parent block ID 指向舊版頁面，提示被加到錯誤工作台。
5. 使用者已刪除舊入口，背景流程仍以過期父 ID 重建。
6. 遇 429 不遵守 Retry-After，造成批次部分完成、重試重複。
7. 將區塊追加成功錯認為 Session 資料列或方案用量已成功更新。
8. 只比對子區塊文字、不核對 block ID，將既有相同提示誤當本輪新增。

## 計量與限制

- 本輪官方可讀候選 1 URL；針對性部分閱讀 1 次；新增待驗反例 8 項；嚴格完整深讀 0 次；新認列唯一來源 0 篇（全歷史去重未完成）。
- 累積逐篇 10/10 完成數暫維持保守 0 / 10,000，待跨批次逐篇稽核。
- 不採用、不修改任何 Notion/GAS/Cloud Run/Session；僅為日後設計審查保存假說。
