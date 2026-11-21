# AUTO-113｜Notion Database automations 官方文件針對性閱讀（2026-11-22 00:42 Asia/Taipei）

- 執行軌跡：AUTO-113-20261122-0042-database-automations；僅研究及 GitHub 記錄，不觸碰 Notion。
- 標題：Database automations；來源：Notion Help；canonical URL：https://www.notion.com/help/database-automations
- 去重鍵：notion-help:database-automations（語系鏡像不另計）；docs/notion/sources.md 已含此 URL，故屬既有來源複讀；全歷史語義稽核仍未完成，不認列新篇。
- 本次證據：2026-11-22 查得可讀官方英文正文，閱讀觸發條件、動作、權限、錯誤、FAQ 等文字段落；未檢視所有影片／圖片與實際產品行為，故標為「獨立文字針對性部分閱讀 1」，不是完整深讀 1/10。
- 來源版本：線上文件未提供可驗證的固定版本號；未證實更新日。後續重讀需重新查核。

## 官方可讀內容及限制
1. 資料庫 automation 由 trigger + action 組成；支援 page added、property edited、週期觸發；可選 any/all 條件。
2. 多個 is edited 觸發若需同時成立，變動約需在三秒內；不能把分時人工操作假設成單次原子事件。
3. Database automation 不會由其他 automation 觸發；使用者按 button 可以觸發。週期觸發不可與其他類型 trigger 混搭，且不能用 Edit property 動作。
4. 權限受限頁面可能不被操作；跨資料庫動作必須有適當編輯權限。以 View 作範圍時，View filter 改變會影響觸發集合。
5. 既有 automation 出錯可能暫停；部分 webhook 或公式錯誤不一定通知；修復後可能需要人工重新啟用。空日期上的 dateAdd 可能失敗。
6. 付費方案與角色權限影響建立／編輯能力；guest 即使對資料庫 Full access 仍不可建立 automation。以上是文件說明，不是本所帳號的實測結論。

## 反例與本所研究假說（未驗證缺陷）
- R1：Session 狀態先改、方案期別稍後填寫，兩個 is edited 觸發不在三秒內，導致額度同步未啟動。
- R2：假設一個 automation 建立補助用量後會自動串接另一個 automation，實際第二層不觸發。
- R3：以 View 篩選當作資料存取或交易一致性保證，狀態變更後資料退出 View，後續處理被略過。
- R4：個案頁限制權限，跨庫動作無法寫入卻被誤判為「無需回報」。
- R5：日期空值使公式動作失敗並暫停，管理者未收到可見通知，造成未同步紀錄。
- R6：把 automation 視為原子且恰好一次的財務記帳機制，未另設唯一鍵與讀回去重，可能重複或漏記。
- R7：把「guest Full access」誤當作能維護 automation，導致人員交接後無法修復。
- R8：週期 trigger 被誤設成可與 property edited 合取，產生錯誤業務期待。

## 本輪認列與界線
- 新全域去重篇數：0（既有 sources.md 已列此 URL）；既有來源部分文字複讀 1；新反例 8；完整深讀 0。
- 累積達成 10/10：沿用既有可核實基準 0/10,000；本輪未重新稽核全歷史。
- 不將研究推論宣稱為本所實際缺陷，不將官方功能視為已配置。
- 尚未完成：全文全部媒體、真實權限角色與錯誤行為驗證、歷史語義去重及十輪完整閱讀。
- 未修改 Notion 頁面、DB、View、公式、權限、GAS、Cloud Run、Session；未進入重新設計。
