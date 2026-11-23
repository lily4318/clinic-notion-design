# AUTO-157｜Move a page：父層型別與跨資料來源搬移風險（2026-11-23 21:36 Asia/Taipei）

- 研究軌跡：AUTO-157 / move-page-parent-type / scheduled；與 AUTO-156 不同 URL。
- 官方標題：Move a page — Notion Developers
- Canonical URL：https://developers.notion.com/reference/move-page
- 取證：2026-11-23，已取得官方文件正文，核對 endpoint、Authentication、Path parameters、Body parameters、兩種 parent 範例及回應；**針對性部分閱讀 1 次，非全文完整深讀，不計 10/10**。
- 去重：本輪研究目錄檔名未發現 move-page 主題，但未完成所有歷史文內 canonical URL 跨檔稽核；正式新增唯一來源暫認列 0。

## 可直接核對的官方契約

1. `POST /v1/pages/{page_id}/move` 移動既有一般頁面，不能用於移動資料庫或其他區塊。
2. 新父層可以是 `{type:"page_id",page_id:"..."}` 或 `{type:"data_source_id",data_source_id:"..."}`；搬入資料庫應使用 **data_source_id**，不是 database_id。
3. 單一 data source 資料庫存在將 database_id 填入 page_id 的有限相容例外，但日後新增第二個 data source 可能產生 HTTP 400；不可把例外當通用規則。
4. Integration 對新父層需要編輯權限；成功回傳 page 物件不代表治療所所有既有 Relation、View、公式、角色可見性均已驗證。
5. 文件示例採 Notion-Version 2026-03-11；實際部署前仍需核對版本相容與最新官方說明。

## 8 個獨立待驗反例（非系統實測）

1. 將 database_id 當 data_source_id：跨資料來源搬移失敗或錯誤判斷。
2. 單來源資料庫的兼容例外在新增第二來源後失效：先前可用操作回傳 400。
3. 移動非一般頁面（例如 database）：API 不支援，不能將失敗解讀為刪除成功。
4. 來源頁面可讀但新父層無編輯權限：搬移失敗；不得自動改權限規避。
5. 以為搬移後仍在原 Linked View：篩選可能不再顯示；需另查來源與 View，而非誤認資料遺失。
6. 以為搬移後補助方案歸屬會自動更新：Price Plan / 用量關聯應獨立核對，不可用父層推定業務資格。
7. 將搬移作為刪除或隔離測試資料的替代：搬移不是刪除，TEST 標籤也不是隔離證明。
8. 逾時後直接重送搬移：先重新讀取 page parent 與目標，避免在不確定狀態下覆蓋另一操作者後續搬移。

## 邊界與後續

本輪僅官方契約與反例研究，**沒有呼叫 Notion Move API**，沒有修改頁面、資料庫、View、公式、權限、GAS、Cloud Run 或 Session。仍須跨歷史來源與閱讀軌跡去重；完整 10/10 來源維持可核實 0／10,000，未取得重設計授權。
