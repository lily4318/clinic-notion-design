# AUTO-158｜Delete a block：Trash 語義與復原邊界（2026-11-23 22:43 Asia/Taipei）

- 執行軌跡：AUTO-158 / 20261123-2243 / delete-block-trash-semantics；研究專用，非 Notion 操作。
- 來源標題：Delete a block — Notion Developers
- 原始 URL／canonical URL：https://developers.notion.com/reference/delete-a-block
- 來源身分：notion-developers:reference/delete-a-block（以 canonical URL 去重）；官方 API 參考；查閱日期 2026-11-23。
- 版本：文件當時列出 Notion-Version 2026-03-11；可能更新，實作前重查。
- 閱讀範圍：端點、官方說明、授權、錯誤、回傳及回復指引；一次獨立**針對性部分閱讀**，不是完整逐篇深讀；不計入 10/10。
- 來源去重：研究目錄檔名未發現 delete-block 專題；未逐一查完所有歷史文件正文 URL，故唯一新增來源正式認列 0，待全歷史去重。

## 官方契約（事實）

1. `DELETE /v1/blocks/{block_id}` 將 Block（包括 page block）的 `in_trash` 設為 `true`；UI 中移到 Trash，仍可能復原，**不是永久清除**。
2. API 復原分別透過 Update a block 或 Update page；不能以 DELETE 成功證明資料已永久消失。
3. 需 update content capability；缺少能力可回 403；404 可能代表物件不存在，也可能是連線無權存取。
4. 參考文件列出 400/429 請求限制；成功回傳 Block 物件。成功回應與完整下游清理驗收不是同一件事。

## 治療所設計研究推論（非現況缺陷）

「否決即清除」的業務驗收須明確區分：日常介面不再顯示、Trash 可復原、真正不可復原刪除；不同語義不得混稱。若刪除的是容器區塊，還需先查依賴、下游引用及資料保留義務。這裡不主張直接清除臨床或財務紀錄。

## 8 個待驗反例（均未於正式系統測試）

1. DELETE 回 200 就宣稱永久銷毀，但資料仍在 Trash。
2. 只驗證日常 View 消失，卻未核對來源資料與其他連結入口。
3. 將 404 視為已刪除，實際是 Integration 失去存取權。
4. 誤將父容器 block 當作單一提醒文字，影響其子區塊可見性。
5. 把 page block 移入 Trash，誤當成資料庫某筆 Session 已合法完成刪除。
6. 對重試中的 DELETE 僅以錯誤碼判定結果，未重新核對遠端狀態。
7. 以「可復原」推定可以安全刪除受法定保存要求約束的紀錄。
8. 刪除舊區塊後宣稱所有連結／公式／檢視依賴已清理，未做依賴盤點。

## 計量與界線

- 本輪可讀官方候選 1；獨立針對性部分閱讀 1；新增待驗反例 8；嚴格完整深讀 0；新增可核實 10/10 篇數 0。
- 累積 10/10 仍保守為 0/10,000；全歷史跨檔去重及獨立輪次稽核未完成。
- 本輪僅研究及 GitHub 紀錄；未操作 Notion 頁面／DB／View／公式／權限，未觸及 GAS、Cloud Run 或 Session。

參考：https://developers.notion.com/reference/delete-a-block
