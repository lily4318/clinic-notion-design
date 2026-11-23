# AUTO-156｜Update a block：欄位完整取代與子區塊邊界

- 執行軌跡：AUTO-156 / 2026-11-23 20:36 Asia/Taipei；研究限定，不執行 Notion 寫入。
- 來源標題：Update a block — Notion Developers
- Canonical URL：https://developers.notion.com/reference/update-a-block
- 去重鍵：notion-developers:reference/update-a-block；本輪候選1，因全歷史跨檔去重未完成，正式新增唯一來源暫記0。
- 取證：2026-11-23 讀取官方可讀正文，頁面約963行；聚焦API契約第733–745行、請求與回應範例、支援型別清單，**一次針對性部分閱讀**，不是完整深讀，也不認列10/10輪次。

## 官方明確契約

1. PATCH /v1/blocks/{block_id} 依區塊型別更新內容；**已提交的欄位值整體取代**，省略的欄位保持不變。
2. child_page 的標題應使用 Update page；child_database 的標題應使用 Update database。
3. 不能透過 Update a block 直接修改 children；新增子區塊須使用 Append block children。
4. 成功回傳200與更新後 Block；需要 update content capability。404涵蓋不存在、垃圾桶或無權限；400可由型別或欄位輸入錯誤造成。
5. 文件示例採 Notion-Version 2026-03-11；本研究沒有檢查現有正式整合使用版本。

## 反例分析（待驗，非系統已存在缺陷）

1. 並行編輯同一段 rich_text：以過期完整陣列 PATCH，另一人新增文字被覆蓋。
2. 誤以為更新 caption 陣列是追加，導致舊備註遺失。
3. 企圖用 PATCH 更新 children，收到錯誤後錯誤判定為已新增成功。
4. 對 child_page 直接改區塊標題，未使用頁面更新端點。
5. 對 child_database 直接改區塊標題，造成錯誤或無預期結果。
6. 404直接判定區塊已刪除，忽略權限或垃圾桶情況。
7. 200成功僅證明該區塊更新，不證明嵌入的 Session 資料、View 或統計值同步正確。
8. 以舊API版本推定新欄位支援，未比對當前整合版本與Block型別。

## 對治療所的研究推論與界線

行政工作台文字、嵌入區塊與資料庫頁面屬不同更新契約。未來若獲得改版授權，需先辨識Block ID與頁面／資料來源ID，讀取現有欄位全值、確認並行修改、精準更新並回讀；此處**只提出風險檢查，不實施設計**。

## 計量

- 官方可讀候選1；本輪部分閱讀1；新增待驗反例8；嚴格完整深讀0；可核實10/10完成篇數仍採保守0/10000。
- 不將同URL搜尋、同次分析八個角度算成八次閱讀。歷史來源語義去重與獨立閱讀輪次稽核仍待完成。
- 官方來源：https://developers.notion.com/reference/update-a-block
- GitHub基準：README、AGENTS、docs/system/source-of-truth、docs/notion/AGENTS、sources、decision-log、acceptance-status、research/README及研究目錄已於本輪查閱；共享清冊不覆寫。
