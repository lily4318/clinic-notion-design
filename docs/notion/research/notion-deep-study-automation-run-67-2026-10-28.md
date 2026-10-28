# Notion 深度學習｜AUTO-67｜2026-10-28 10:42（研究限定）

- 執行軌跡：`AUTO-67-20261028-1042-RESEARCH`；Asia/Taipei 2026-10-28 10:42；執行通道：排程，與聊天手動研究互不抵銷。
- **授權範圍：僅外部研究與 GitHub 研究進度。** 本輪沒有對 Notion 正式／TEST 頁面、資料庫、View、Formula、Relation、權限、業務資料或 GAS／Cloud Run／Session／部署發出寫入；研究推論不是 Notion 功能驗收、設計核准或實作指令。
- 開始及建立本檔前重新 Fetch main 的根 README/AGENTS、source-of-truth、Notion AGENTS、sources、decision-log、acceptance-status、research README、audit-checklist；基準 blob SHA：`README.md`=`51c750119a207e195b675f0613f43cbde9956d67`；`AGENTS.md`=`e541f9d79fcb7a28126f70ebafe290ad0bc349b6`；`docs/system/source-of-truth.md`=`a26ac4c914f3e5e853464d9f0515033f2e3d62c0`；`docs/notion/AGENTS.md`=`c0fe2c5eadd92877643d8ef1c06574115729cd01`；`docs/notion/sources.md`=`9534e2fc5d3d70135a68dc7221514ace10845822`；`docs/notion/decision-log.md`=`eecd7dedf79b4e51f75d9d5822e523986fbee01b`；`docs/notion/acceptance-status.md`=`ae03cd151d61db595a19f91f57759735b3c6202e`；`docs/notion/research/README.md`=`103e2a9268d993c5063f7bb2be3b454d12638370`；`docs/notion/research/audit-checklist-and-research-progress.md`=`83902e17df686a77beb339d950105305f8a3aeb6`。亦讀 AUTO-66 原始紀錄。來源索引全文中兩個下列 canonical URL 未見；GitHub repo code search 對兩個完整 URL、此 trace 均無命中。**未完成全研究目錄逐檔及同文異址語義去重**，故只標「新來源候選」。
- 研究準則衝突處理：較舊 audit-checklist 的「10,000篇不作單一發版關卡」不能覆蓋使用者 2026-10-25 最新明確授權的「10,000篇×每篇10次完成、經使用者確認後才可重新設計」；本輪嚴格採最新要求。

## S01｜GOV.UK Design System — Recover from validation errors
- ID：`AUTO67-S01`；canonical URL：https://design-system.service.gov.uk/patterns/validation/ ；去重身份：`govuk-design-system:patterns/validation`；官方維護者 GOV.UK Design System team；頁面未明列發表／更新日，不推測；查核日2026-10-28。
- 唯一閱讀事件：`AUTO67-S01-R1-MAIN-TEXT-C1`。**已實際閱讀**原頁全部主要文字段落：When to use/not to use、無效/歧義/缺漏、可忽略多餘字元、保留輸入與錯誤摘要/欄位錯誤、觸發時點、client/server validation、關閉 HTML5 原生驗證、研究缺口；對照具體例子：月份13應拒絕、姓名可含撇號/重音、前後空白可容忍、不要在使用者尚未完成輸入時立即報錯。原頁文字約166行；不是實際 Notion 操作，也沒有進行鍵盤/讀屏驗證。
- **官方主張（來源事實）**：輸入驗證針對不可使用的輸入，**不是**拿來判定資格或授權；若有錯應保留原答案、於頁首與欄位旁指出並移動焦點；即使有前端驗證仍需伺服器端驗證；HTML5 novalidate 是此設計系統的特定建議，**不是**普遍所有網站或 Notion 的必須設定。
- **獨立反例1／反證**：行政人員輸入民國年或歷史 Session 日期，日期格式合法，但收費期別未對應；把「方案尚待核對」標成欄位格式錯誤會誤導使用者更改真實日期。反證條件：只有在資料本身無法解析、歧義不可消除時才屬格式驗證；業務期別不符須另由可核對來源判斷，並保留原值。
- **獨立反例2／反證**：若在中文輸入法組字過程即對姓名或備註報錯，可能增加誤觸與輸入中斷；但完全不即時檢查超長文字，又可能造成儲存時截斷。反證條件：不同欄位應用實際可觀察的錯誤率、完成率與儲存一致性比較觸發時點，不能一律主張即時或延後。
- **獨立反例3／反證**：Notion Formula/Relation 的顯示檢查不等於不可繞過的後端強制驗證。即使 UI 顯示「已核對」，也無法據此推定補助資格核准或歷史金額鎖定。反證條件：需有實際資料寫入路徑、權限與後端/平台規則驗證；本輪未做。
- 結論（研究假說）：**格式、業務資格、存取授權、系統故障四類問題需分開描述與驗證**。此結論不授權新增欄位/頁面或修改 Notion。

## S02｜GOV.UK Design System — Complete multiple tasks
- ID：`AUTO67-S02`；canonical URL：https://design-system.service.gov.uk/patterns/complete-multiple-tasks/ ；去重身份：`govuk-design-system:patterns/complete-multiple-tasks`；維護者 GOV.UK Design System team；頁面未明列發表／更新日，不推測；查核日2026-10-28。
- 唯一閱讀事件：`AUTO67-S02-R1-MAIN-TEXT-C1`。**已實際閱讀**長交易適用條件、重返交易時顯示、動詞任務名稱、最少狀態、未開始/進行中/不能開始/已完成/有問題、不可啟動時不連結、錯誤紅色限制、分組/可彈性順序、使用者自行標記完成、重返修改及其 HTML/Nunjucks 示例文字。原頁超過1100行（含大量程式碼與示例）；**沒有**將不同示例當作獨立文章或複讀，原始視覺示例與互動尚未逐項操作。
- **官方主張（來源事實）**：此模式限較長、可能跨多次使用的交易；應先簡化流程，否則未必需要任務清單。狀態越多越難記；若任務需先決條件才可啟動，示例以無連結的 Cannot start yet 呈現；有錯誤時應盡可能在錯誤發生處處理；部分任務可由使用者自行宣告完成並允許回去修改。
- **獨立反例1／反證**：將治療所每天高頻的 Session→Billing 核對變成多頁任務清單，可能違反已確認「同類資料同頁、開啟即見」，增加切換而非降低成本。反證條件：若未經真人計時與錯誤率測量證明多頁優於同頁，不能因官方有 Task list 就拆頁。
- **獨立反例2／反證**：行政人員勾選「補助核對完成」可能只是本人完成資料檢視，**不等於**方案期別正確、政府資格核准、實際服務完成或 Billing 已收款。反證條件：狀態須可追溯到權威資料、責任角色與時間；不能用單一 Completed 標籤跨越業務責任。
- **獨立反例3／反證**：對待人工資格確認的個案顯示 Cannot start yet 並完全移除操作入口，可能阻礙合法補件或歷史補登；但允許直接核准也有風險。反證條件：區分可安全補充證據的工作與不可提前核准的工作，不得只靠單一停用狀態推定。
- 結論（研究假說）：**長交易任務進度、日常同頁核對、業務核准與收款狀態不可混同**；不建議直接套版，需另有真實工作流程與角色測試後由使用者決定。

## 去重、計量、未驗證
- 本輪：已查索引新 canonical **候選2**；官方主要正文閱讀 **2篇×各1次**；首次獨立反例 **2組，共6情境**；既有來源完整複讀 **0次**；**完整深讀R1=0、R2–R10=0、本輪FULL_DEEP_PASS_10_OF_10=0、累積可核實0／10,000篇**。
- 尚未完成：全儲存庫逐檔與同文異址去重；原始視覺/示例逐張檢查、真實互動、鍵盤/讀屏/手機、真人可用性、Notion原生實帳/角色/Formula/歷史金額/效能；這些均不得標 PASS。文字閱讀不能冒稱完整深讀。
- 參照連結：[Validation pattern](https://design-system.service.gov.uk/patterns/validation/)；[Complete multiple tasks pattern](https://design-system.service.gov.uk/patterns/complete-multiple-tasks/)；以上兩頁皆是公開可讀的正文，不是搜尋結果、模板目錄或付費介紹。
- 後續只允許接續研究與安全的 GitHub 研究紀錄；未達10,000篇各10次及使用者確認前，不進行 Notion 重新設計。
