# AUTO-99｜2026-11-21｜Notion database automations 失效邊界研究

Trace: AUTO-99-20261121-0642-DB-AUTOMATIONS-FAILURE-MODES

## 來源與去重
- 既有官方來源：[Database automations | Notion Help](https://www.notion.com/help/database-automations)；canonical `notion-help:database-automations`；Notion Labs；2026-11-21 查閱；頁面未見明確發布/更新日。
- 寫入前核對 `docs/notion/sources.md`：精確 URL 已存在，故 **NEW_UNIQUE_URL=0**；本次只記既有來源的獨立針對性正文複讀，與 AUTO-98 欄位權限不同來源/議題。
- 讀取公開HTML全文462行；研究正文 L107–371，含功能、方案、觸發條件、動作、郵件、變數、錯誤處理、FAQ；影片、圖片、外部技巧鏈結及實機操作未完整閱讀，不計嚴格完整R1–R10。

## 原文核對與反例
1. L133–151：受限頁面不執行；資料庫automation不能觸發另一個automation，但人工Button可觸發。反例CE1：新增Session的自動化再建立Billing頁，不會自動觸發Billing庫的第二段automation，流程看似成功卻漏後續處理。
2. L169–188：多個edited觸發條件若要求全部成立，約3秒窗口；週期觸發不能與其他觸發混用，亦不支援Edit property動作。反例CE2：行政分兩次補完方案與狀態，第二次超過3秒，核對提醒未執行。
3. L189–207：跨資料庫編輯、寄信、webhook均為可能動作，且需目標權限。反例CE3：只確認來源庫可編輯卻忽略目的庫權限，造成部分跨庫更新失敗；不能據此認定Session/Billing已對帳。
4. L315–339：執行錯誤可暫停；公式或webhook問題未必通知，修復後仍需人工重新啟用；空日期運算及View篩選可失敗。反例CE4：日期為空導致dateAdd失敗而沒有可見通知，管理者誤以為補助期限已更新。
5. L351–371：View filter影響automation作用範圍，資料變更後不再符合篩選可能不觸發；鎖定資料庫也可能阻止觸發。反例CE5：改狀態瞬間移出「待處理」View，後續通知/動作被跳過。
6. L212–240：Gmail郵件可能延遲至2分鐘、寄件帳號編輯權屬建立者。反例CE6：把郵件送達或顯示成功當成個案已收到提醒、已同意或財務入帳，缺少獨立回執與對帳。

## 證據界線
- 本輪 `NEW_UNIQUE_URL=0`; `EXISTING_SOURCE_TARGETED_TEXT_REREAD=1`; `COUNTEREXAMPLE=6`; `FULL_R1=0`; `FULL_R2_TO_R10=0`; `NEW_10_OF_10=0`。既有來源先前閱讀事件未在本輪全面重建；不可假稱完整R2。歷史跨語系/同文異址去重仍待稽核，累積嚴格10/10達標依現有驗收紀錄為0/10000。
- 上述均為官方規則及研究推論，未查本所實際automation、Notion原生執行日誌、權限、真實Session/Billing/Price Plan、郵件、Webhook、手機/讀屏/效能，不能認列業務PASS。
- **RESEARCH ONLY**：無Notion頁/資料庫/View/Formula/Relation/權限/業務資料修改；無GAS/Cloud Run/Session/部署修改；未開始重新設計。手動與排程研究可並行。
