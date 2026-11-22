# AUTO-137-20261123-0140-buttons-permissions｜Database buttons 權限與失敗語義獨立複核

- 執行：2026-11-23 01:40 Asia/Taipei；研究性唯讀；不涉及任何 Notion/GAS 寫入。
- 原始來源：Notion Help, Database buttons，https://www.notion.com/help/database-buttons
- canonical URL / 去重鍵：https://www.notion.com/help/database-buttons
- 原文範圍：官方可讀正文 Who can use database buttons、actions、mail、variables、errors（頁面行 107–262，2026-11-23 取得）。
- 先前研究：notion-deep-study-auto-20261122-0142-database-buttons-mail-errors.md 已存在，故本輪為既有 URL 的獨立**針對性部分複讀**，不是新增來源或完整深讀。
- 閱讀計量：新增唯一來源 0；獨立部分複讀 1；嚴格完整深讀 0；10/10 完成篇數增量 0。不得將本次多個角度計為多次閱讀。

## 官方內容核對

1. Full access / Can edit 可建立及修改資料庫按鈕；Can edit content 可點擊，但不等於可修改按鈕定義。
2. 按鈕可以 Edit property、Add page to、Edit pages in、Send notification、Send mail、Send webhook、Show confirmation、Open page/URL、Define variables；部分動作受付費方案限制。
3. 按鈕涉及其他頁面或資料庫的編輯，仍需對目標具有權限；成功點擊不保證跨資料庫動作完成。
4. Gmail 寄信動作有連線持有人編輯限制、寄達可能延遲最多兩分鐘；連線失效可能造成先前可用的按鈕故障。
5. Mentions/formulas 用於 actions 而非 triggers；部分動作（插入區塊、開啟頁面/URL、Slack 通知）不支援公式。
6. 建立時的無效設定會阻止儲存；已運作的按鈕可能因目標資料庫、屬性或第三方連線失效而故障。

## 本次獨立反例假說（待隔離測試，非既有系統已發生）

- B137-01：行政人員具有 Can edit content，誤以為能調整按鈕流程；實際僅可按下。
- B137-02：點擊核准按鈕後，目標資料庫缺少編輯權限，未完成預期跨表更新。
- B137-03：Gmail 連線原建立者離職或重新授權後，其他人不能編輯既有寄信設定。
- B137-04：寄信未立即收到，被誤判未執行並再次按鈕，造成重複通知。
- B137-05：用公式動態決定觸發條件，卻誤把 action 的公式支援當作 trigger 支援。
- B137-06：目標欄位改名／移除後，原可用按鈕失效，工作台仍顯示可點擊。
- B137-07：Show confirmation 被誤當角色授權或不可撤回的正式審批紀錄。
- B137-08：一個按鈕連續新增 Session 與更新額度，其中部分動作失敗，卻只以畫面點擊完成當作全流程驗收。

## 專案對應與邊界

與補助方案用量（個案×Price Plan 期別）、心理師方案額度、Session 與角色權限有關；未確認真人 UX／角色權限與跨方案端到端，故不主張已修復、已通過或應直接部署。任何按鈕自動化設計或實作須等研究門檻完成且使用者另行確認。

## 稽核限制

本輪取得的是官方頁面正文，但沒有逐字獨立涵蓋所有頁面外連或示範情境，故僅部分閱讀。歷史全域 URL 語義去重及各來源 10 次完整閱讀尚未完成；最近可核實 10/10 基準維持 0／10,000。只新增本研究紀錄，不修改共享清冊，避免並行覆寫。
