# AUTO-114｜Database buttons：郵件、變數與失效情境針對性複讀

- 執行標記：AUTO-114-20261122T0142+0800；研究批次獨立於手動流程
- 研究來源：Notion Help，Database buttons，https://www.notion.com/help/database-buttons
- 去重鍵：notion-help:database-buttons；已在 docs/notion/sources.md 的 AUTO46-R01 登錄，**新增唯一來源 0**；本次為不同章節及反例的獨立針對性複讀，非全文深讀
- 本次讀取：2026-11-22 01:42 台灣時間；可讀官方正文 L107–262，特別聚焦 L162–209 郵件與變數、L210–262 公式限制與錯誤
- 深度：TARGETED_REREAD_TEXT_PARTIAL；完整深讀 0 次，10/10 完成 0 篇。未實測 Notion 按鈕或 Gmail 寄送

## 官方文字核讀結果

1. 資料庫按鈕可由有 Full access / Can edit 的人建立或編輯；Can edit content 亦可點擊，但按鈕寫入其他目標仍需相應權限（L116–122、L143–150）。
2. Send mail to 須連接 Gmail，屬付費方案動作；連接該 Gmail 的人才能編輯此郵件自動化，其他人可使用；郵件可能延遲兩分鐘（L152–175）。
3. 寄件者、收件者、主旨、訊息、回覆地址可透過相關人員或欄位配置，Gmail 寄送數量另有限制（L175–195）。
4. Define variables 可以使用 mentions/formulas 供後續按鈕動作引用（L196–209）；公式只能用在動作，不能用於觸發條件，且不支援插入區塊、開啟頁面/URL、Slack 通知等指定動作（L210–224）。
5. 已經可以運作的按鈕，若目標資料庫或屬性遭刪除、第三方 Gmail/Slack 授權失效，可能後續失敗（L245–262）。

## 新的反證／待驗情境（研究推論，非本所已發生）

- R1：按鈕點擊成功，但 Gmail 郵件延遲；不得將點擊完成當成個案已收到通知。
- R2：Gmail 連接者離職或授權失效，既有按鈕仍顯示但無法完成郵件動作；需獨立驗證第三方連線健康。
- R3：一般編輯者可按按鈕，不等於其具備目標資料庫的跨庫編輯權；不得以按鈕存在推論會談狀態已寫入。
- R4：按鈕動作變數計算與按鈕觸發混為一談，可能錯以為公式變動就會自動重新執行。
- R5：把按鈕寄信作為補助申報或收費核准的唯一證據，忽略 Gmail 限流及寄送失敗，會造成不可稽核的狀態。
- R6：刪除/改名目標屬性後沿用舊按鈕，可能在執行時失效；需在獨立隔離環境驗證錯誤及人工回復。
- R7：將 Show confirmation 視為已經完成業務複核；確認對話框不提供外部資格核准、跨表交易原子性或不可抵賴證據。

## 計數與界線

- 本次新增去重來源：0；既有來源不同重點針對性文字複讀：1；新反證情境：7；嚴格完整深讀：0；10/10 達標新增：0。
- 歷史累積10/10：沿用最近已核實基準0／10,000；未完成全歷史語義去重及逐輪稽核，不能宣稱已驗證所有紀錄。
- 本次僅 GitHub 研究紀錄；不修改 Notion 頁面、DB、View、Formula、權限、GAS、Cloud Run、Session 或正式環境。
- 寫入前 main SHA：27c09191e40a97c074c26747681a0409d894cdd2；核心文件讀取 blob SHA：README.md=51c750119a207e195b675f0613f43cbde9956d67; AGENTS.md=e541f9d79fcb7a28126f70ebafe290ad0bc349b6; docs/system/source-of-truth.md=a26ac4c914f3e5e853464d9f0515033f2e3d62c0; docs/notion/AGENTS.md=c0fe2c5eadd92877643d8ef1c06574115729cd01; docs/notion/sources.md=4cb54a075ad9243054d899ec715ca2a68140dd80; docs/notion/decision-log.md=6c56f39c37c79421c8f5689d50d045793be86627; docs/notion/acceptance-status.md=f1cfc159492f119d95753230c7e91e4d702ef13b。
