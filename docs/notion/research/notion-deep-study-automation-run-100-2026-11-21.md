# AUTO-100｜2026-11-21｜Database buttons 權限與失效邊界（研究限定）

Trace: AUTO-100-20261121-0740-DATABASE-BUTTONS-BOUNDARIES

## 來源與去重
- 官方來源：[Database buttons | Notion Help](https://www.notion.com/help/database-buttons)；canonical `notion-help:database-buttons`；Notion Labs；2026-11-21 查閱；未見明確發布日期。
- 最新 main 的 `docs/notion/sources.md` 已包含此精確 URL，故新增唯一來源 **0**。此輪是獨立的既有來源正文針對性複讀，不計完整 R1/R2 或新增來源。與 AUTO-99 的 database automations 不同頁面。
- 閱讀公開頁 349 行中的主文 L107–262，涵蓋可用方案、權限、操作、跨資料庫動作、Gmail、變數、公式與失效處理；圖片、影片、連出文件、實機與完整跨來源追查未讀，嚴格完整深讀計 0。

## 官方規則與新反例（未在本所實測）
1. L116–122：所有方案可用資料庫按鈕，建立/編輯須 Full access 或 Can edit；Can edit content 可按下但不等於可編輯按鈕配置。CE1：行政人員能按「核准」卻無權修復按鈕規則，不能把可點擊當作完整管理權。
2. L143–159：跨資料庫新增/編輯要求目標權限，Private/Shared 目標可能使動作失效。CE2：Session 按鈕修改 Billing 或方案用量時，來源可按卻因目標權限失敗；不能視為對帳成功。
3. L152：通知最多 20 名工作區成員或 People 欄位指定對象。CE3：大量收件群組被當成無上限廣播，部分應通知人員未被覆蓋；必須另行核對收件範圍。
4. L166–175：Gmail 連線者獨有編輯權，郵件可能延遲兩分鐘且受 Gmail 限制。CE4：原設定者離職/連線失效，其他人可按卻無法修復郵件動作；寄送觸發也不等於即時送達。
5. L210–225：公式與提及僅用於按鈕動作、不能用於觸發；部分動作不支援公式。CE5：將動態日期公式放在不支援的開啟 URL 或 Slack 通知動作，無法實現預期動態導航/提醒。
6. L245–262：目的資料庫/欄位刪除、Gmail/Slack 連線失效均可能破壞既有按鈕。CE6：方案期別欄位重命名/刪除後未做依賴核對，歷史流程按鈕失效；僅看 UI 上仍有按鈕不代表執行正常。

## 嚴格計量與界線
- `NEW_UNIQUE_URL=0`; `EXISTING_SOURCE_TARGETED_TEXT_REREAD=1`; `COUNTEREXAMPLE=6`; `FULL_R1=0`; `FULL_R2_TO_R10=0`; `NEW_10_OF_10=0`。
- 累積可核實 10/10 依目前 GitHub 驗收基準仍為 **0/10,000**；跨歷史語義去重及逐篇十輪深讀未完成。本輪的針對性複讀不得冒稱完整獨立深讀。
- 官方產品規則與推論不等於本所按鈕、角色、資料、原生公式、通知、速度或業務流程驗收通過。
- **RESEARCH ONLY**：不更動 Notion 頁面、資料庫、View、公式、Relation、權限、正式 GAS/Cloud Run/Session 或部署；不進入重新設計。雙軌研究並行，不覆寫既有紀錄。
