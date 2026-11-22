# AUTO-135｜2026-11-22 22:45 Asia/Taipei｜Notion database automations failure modes

- 執行軌跡：AUTO-135-20261122-2245; scope=research-only; canonical URL=https://www.notion.com/help/database-automations
- 標題：Database automations｜Notion Help
- 去重：既有來源，docs/notion/sources.md 曾記錄同一 URL，且 2026-10-25 MANUAL-01 與 2026-11-22 AUTO-early 已研究；本次 **0 新來源**，不可重複認列。
- 取證：2026-11-22 本輪重新開啟官方完整可讀文字（網頁約462行；正文約107–371行），對觸發鏈、三秒視窗、view依賴、失敗通知和權限作獨立針對性複讀。嵌入影片、示意圖片、實際系統測試未完成，故 **partial reread 1 / full-depth 0 / 10-of-10 0**。
- GitHub前置：已讀 main 根 README/AGENTS、source-of-truth、Notion AGENTS/sources/decision-log/acceptance-status、research目錄及先前同URL索引。未修改既有檔案。

## 官方正文支持的界線
1. 自動化建立的資料列不能再觸發另一個 database automation；使用者按鈕建立頁面則可觸發。
2. 多個「is edited」觸發條件的共同判定視窗約三秒，超出可能不觸發。
3. 自動化可指定整個 database 或特定 view；若資料在觸發時不再符合 view 篩選，可能不執行。
4. Recurring trigger 不可與其他 trigger 配對，且不支援 Edit property action。
5. 某些 webhook/formula 失敗不一定通知；錯誤後可能暫停且須人工重新啟用。
6. 空日期欄位上的 dateAdd 可能失敗；頁面權限受限也可能阻止執行。
7. 本文所述付費方案、Free Slack例外和可編輯權限須按實際方案重新驗證，不推論現有治療所帳號權益。

## 本輪新增待驗反例（研究假說，非已發生）
- R1：Session新增後自動產生額度列，期待第二層自動化再更新週報，卻因 automation-to-automation 不觸發而漏算。
- R2：管理者先改方案期別再改核定狀態，兩個 is-edited 條件跨越三秒，流程不執行。
- R3：狀態修改讓Session離開原View，view-scoped automation不執行，後續補助餘額未更新。
- R4：將每週排程觸發器與資料列修改觸發器合併，設定本身不合法。
- R5：公式 dateAdd 遇到空白首次服務日期失敗，誤當已完成通知。
- R6：Webhook執行失敗未收到通知，行政人員誤判資料已同步GAS。
- R7：修復錯誤後未人工恢復 Active，後續新Session一直不觸發。
- R8：對受限的臨床頁面執行動作遭權限阻擋，誤以為跨角色操作已通過。
- R9：按鈕建立與自動化建立兩種路徑的觸發結果不同，導致同類資料不一致。

## 判定
研究價值：治療所的 Session、補助用量、心理師週回報不能假定原生 Notion automation 具可靠跨資料庫連鎖、全量覆蓋或錯誤告警。未取得 live schema、真人測試與授權，不得宣稱有此缺陷或提出實作變更。

本輪：候選新來源0、既有來源部分複讀1、反例9、完整深讀0、可核實10/10完成篇數沿用保守基準0/10000（全歷史尚未嚴格重算）。未修改Notion、GAS、Cloud Run、Session或權限。