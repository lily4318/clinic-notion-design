# Notion 深度學習｜AUTO-68｜2026-10-28 11:37（研究限定）

- 唯一執行標記：`AUTO-68-20261028-1137-RESEARCH`；Asia/Taipei 2026-10-28 11:37；自動研究流程，與聊天手動續作獨立並行。
- **唯一授權範圍：公開來源研究與 GitHub 研究進度記錄。** 未操作 Notion 正式／TEST 頁面、DB、Data Source、View、Formula、Relation、權限、業務資料；未操作正式 GAS、Cloud Run、Session 或部署。
- 本輪開始及建立研究紀錄前重新讀取 main：根 README、AGENTS、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md；另讀 research/README、audit-checklist、AUTO-67、首批 evidence-register、batch-02/03/04、manual-01、十面向研究清冊，列舉研究目錄79份 Markdown。來源索引與已查非自動清冊未見下述兩個 canonical URL，GitHub code search 亦無命中；**未完成79份逐檔全文及同文異址語義去重，故僅列新來源候選**。曾考慮的 Check answers 已在 AUTO-53 登記，已排除，不重複計算。
- 研究的主要正文由 GOV.UK Design System 官方網站直接開啟、核對；HTML/Nunjucks 示例文字和圖片替代文字不代表實際互動、真人可用性或 Notion 原生能力。

## S01｜GOV.UK Design System — Check a service is suitable
- ID：`AUTO68-S01`；canonical URL：https://design-system.service.gov.uk/patterns/check-a-service-is-suitable/；去重身份：`govuk-design-system:patterns/check-a-service-is-suitable`；作者/維護者：GOV.UK Design System team；官方頁面未明示首次發表日，不推測；查核日：2026-10-28。
- 唯一閱讀事件：`AUTO68-S01-R1-MAIN-TEXT-C1`；**主要正文一次文字閱讀**（官方頁面約189行，含選單與程式碼）：何時使用/不使用、複雜資格條件、成本與時間、避免重複詢問、結果頁應告知原因與替代路徑、結果頁 HTML/Nunjucks、示例圖的文字說明及舊名稱「Check before you start」。原圖像素/互動流程未測；**不是完整深讀R1**。
- 官方主張：複雜的資格規則適合先用簡短問題引導使用者了解適用性；若開始頁能說清楚，就不應無故增加問答；結果頁應解釋適用性及必要時的成本、時程、替代方案。官方示例是 Prototype，不能視為正式政府資格判定引擎。
- **獨立反例A**：政府補助是否適用可能需人工查核證明、核定期及其他機構使用紀錄；只回答前端幾題不代表官方核准。反證條件：結果須區分「可初步申請」「人工待核」「已由權責單位核准」；沒有核准證據不可顯示已核准。
- **獨立反例B**：同一個案跨兩個 Price Plan 核定期，服務日期與各期條件不同；如果僅依當前日期/年齡顯示一個「符合資格」結果，可能錯套歷史金額或用量。反證條件：核對以當次實際服務日期與方案期別來源為準，且未知不得當0或合格。
- **獨立反例C**：將原已由治療所人工確認的青壯資格重新設為多步必填問卷，會違反現行「人工確認後直接於 Care Episodes 選方案」的明確決策。反證條件：先比較現有流程的錯誤率、操作步數與例外情境，沒有證據不得新增前置關卡。
- 研究假說：**預先判斷適用性是資訊服務，不等於核定；是否採問答流程須依業務規則與既有使用者決策，不可直接套版。**

## S02｜GOV.UK Design System — Create accounts
- ID：`AUTO68-S02`；canonical URL：https://design-system.service.gov.uk/patterns/create-accounts/；去重身份：`govuk-design-system:patterns/create-accounts`；作者/維護者：GOV.UK Design System team；官方頁面未明示首次發表日，不推測；查核日：2026-10-28。
- 唯一閱讀事件：`AUTO68-S02-R1-MAIN-TEXT-C1`；**主要正文一次文字閱讀**（官方頁面約127行，含選單）：帳號適用/不適用、單次交易參考碼、建立與登入區分、避免重複填寫、降低 CAPTCHA 障礙、英國 National Insurance number 不宜作身分驗證的當地例子、相關外部指引連結；外部連結未作為獨立文章計數。**不是完整深讀R1**。
- 官方主張：需要反覆存取/更新資料的服務可考慮帳號；不必要的帳號會增加阻礙與維護成本；建立帳號與登入的文字及流程須區分；CAPTCHA 對部分使用者不友善；單次交易可能以參考碼提供狀態查詢。
- **獨立反例A**：治療所內部心理師/行政人員反覆接觸敏感個案及財務資訊，若為了降低登入步驟而改成「參考碼＋姓名」就可能欠缺足夠身分驗證與可稽核責任歸屬。反證條件：內部角色應依最小權限、驗證與稽核要求評估；不能照搬公眾單次交易模式。
- **獨立反例B**：新增一個帳號入口不等於 Notion、GAS、Cloud Run、Session 的權限一致；共用 Notion View 隱藏欄位也不代表存取限制。反證條件：逐一查證資料來源、登入身分、權限邊界與撤權生效路徑，未實測不宣稱安全。
- **獨立反例C**：一律要求個案先建立帳號才能提交一次性資料，可能提高放棄率；但完全不驗證身分就開放查詢又可能洩漏敏感資訊。反證條件：按風險分級評估最低必要的驗證方式、可存取資訊範圍及回復流程，不能以單一 UX 原則決定。
- 研究假說：**帳號的必要性、身分驗證強度、資料授權與使用者操作成本應分開評估。** GOV.UK 對公眾服務的模式不等於 Notion 的功能或本地法規要求。

## 去重、計量與未驗證
- 本輪已讀公開主要正文：2篇各1次；新增候選：2篇（**非全庫確認去重**）；首次獨立反例：2組、6情境；已排除已登記 Check answers 1篇；既有來源完整複讀：0次。
- **嚴格門檻：完整深讀R1=0、R2–R10=0；本輪 FULL_DEEP_PASS_10_OF_10=0，累積可核實仍0／10,000篇。** 不把多角度分析、圖片替代文字、HTML示例或搜尋命中計作額外篇次。
- **NOT_TESTED**：全庫79份逐檔全文/同文異址語義去重；原圖、互動、鍵盤/讀屏/手機、真人 Notion、角色/權限、補助資格、Price Plan 歷史金額、Session/Billing 真值、效能、跨系統登入與安全。未進入 Notion 重新設計，研究結論僅為假說，需使用者最終確認。
