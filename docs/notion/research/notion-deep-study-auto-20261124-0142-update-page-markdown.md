# AUTO-161｜Notion Markdown 更新 API：部分閱讀與反例研究
- 執行標記：AUTO-161 / 2026-11-24 01:42 Asia/Taipei / 獨立研究
- 官方來源標題：Update a page's content as markdown
- Canonical URL：https://developers.notion.com/reference/update-page-markdown
- 去重 ID：notion-dev-reference-update-page-markdown
- 來源類型：Notion 官方 API 參考；2026-11-24 讀取公開正文
- 閱讀深度：**一次針對性部分閱讀**，核對 Use cases、General behavior、Requirements、Errors；未逐節驗證所有參數與全部範例；**完整深讀 0/10**。此記錄不是十次閱讀。
- 跨清冊狀態：本輪已核對 sources.md、research/README.md、audit-checklist-and-research-progress.md、evidence-register-2026-10-24.md 及研究目錄；尚未完成全歷史每份文件正文 URL 語義去重，故正式新增唯一來源計 **0（待查）**。
- 僅研究／GitHub 記錄，沒有呼叫 Notion 寫入 API。

## 可核對的官方契約
1. `PATCH /v1/pages/{page_id}/markdown` 支援 `update_content` 以 old_str/new_str 精準替換；`replace_content` 會替換整頁內容，`insert_content` 與 `replace_content_range` 屬仍可用但不建議的新專案主要方式。
2. 同步結果回傳 page_markdown，包含 truncated、unknown_block_ids、warnings；`allow_async:true` 回 202 async_task，須另行查任務狀態，且非同步回應不提供 warnings。
3. `markdown_version:v2` 為建議版本；v1 已棄用。更新需要 update content capability，否則可能 403。
4. 未命中的 old_str 可能導致 validation_error；若同批至少一筆有變更成功，其他未命中可進 warnings。多處匹配且未指定 replace_all_matches 會報錯。
5. 預設防止刪除 child pages/databases；明確設 `allow_deleting_content:true` 才允許此類刪除。頁面過大時即使小範圍更新也可能無法處理。
6. 同步回應成功不能在未檢查 warnings、truncated、unknown_block_ids 時當作完整內容比對通過。

## 八個獨立待驗反例（研究推論，非治療所已發生）
1. 以 replace_content 改工作台一段文字，意外清除其他人新增的段落。
2. 同批三項 old_str 僅一項匹配，回應成功但另外兩項警告被忽略。
3. 以 allow_async:true 收到 202 便宣布 Notion 寫入完成，未追蹤 async task。
4. 同一 old_str 在兩個業務區重複，沒有 replace_all_matches 造成 validation_error。
5. 設 allow_deleting_content:true 後意外刪除子頁或資料庫入口。
6. v1/v2 Markdown 格式差異造成文字、表格或結構轉換後不一致。
7. 回傳 truncated=true 卻只比較可見片段，漏掉頁尾的必要操作入口。
8. 多人同時編輯時舊快照的搜尋替換雖匹配，卻覆寫其他人的語義修訂。

## 對治療所的研究意義（未核准實作）
日後若需調整行政工作台文案，應先讀最新頁面、確認精準替換目標與子頁保護、考慮非同步完成及 warnings，再獨立核對完整內容與必要操作入口。此處只提出候選驗證條件，**不得據此修改任何 Notion 頁面／資料庫／View／公式／權限或正式 GAS、Cloud Run、Session**。

## 本輪計量
- 取得官方正文來源：1 個候選；正式新增去重來源：0（未完成全歷史核對）
- 針對性部分閱讀：1；嚴格完整深讀：0；新增待驗反例：8
- 累積可核實完成 10/10 篇數：保守 0 / 10,000
