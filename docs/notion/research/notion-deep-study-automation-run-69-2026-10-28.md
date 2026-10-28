# Notion 深度學習｜AUTO-69｜2026-10-28 12:43（研究限定）

- 唯一執行標記：`AUTO-69-20261028-1243-RESEARCH`；Asia/Taipei 2026-10-28 12:43；自動流程與聊天室手動續作獨立。
- **範圍**：僅公開來源閱讀、反例推論及 GitHub 研究進度。沒有讀寫 Notion 業務資料或變更正式／TEST頁面、資料庫、View、Formula、Relation、權限；沒有操作正式 GAS、Cloud Run、Session、部署。
- 本輪開始及寫入前重新 Fetch main：根 README、AGENTS、docs/system/source-of-truth.md、docs/notion/AGENTS.md、sources.md、decision-log.md、acceptance-status.md；另讀 research README、audit checklist、AUTO-68、首批 evidence register。當期 sources 全文未見以下 canonical URL，GitHub code search `patterns/dates`、`patterns/names` 未命中；**尚未逐檔核對所有歷史 AUTO 清冊及全庫同文異址語義去重**，僅標記「已查索引新候選」，不冒稱全庫唯一。
- 直接開啟官方 GOV.UK Design System 原文及可開啟的示例頁；本文與示例的 HTML／Nunjucks 文字已查。沒有實際執行鍵盤、讀屏、手機、真人可用性或 Notion 原生功能測試。

## S01｜Ask users for Dates
- ID：`AUTO69-S01`；canonical URL：https://design-system.service.gov.uk/patterns/dates/；去重身份：`govuk-design-system:patterns/dates`；維護者：GOV.UK Design System team；原文未明列首發日，未推測；查核日：2026-10-28。
- 唯一閱讀事件：`AUTO69-S01-R1-MAIN-TEXT-C1`；**主要正文文字與獨立預覽一次閱讀，非完整深讀 R1**。閱讀覆蓋：日期類型（記憶日期、文件日期、約略日期、相對日期）、日期輸入元件與 HTML/Nunjucks、文件原格式、約略日期、相對日期、選擇日期的日曆、非 JavaScript 唯一輸入、日期格式示例及官方未解研究問題；示例：https://design-system.service.gov.uk/patterns/dates/default/（Day／Month／Year 三欄）。
- 官方要點：日期欄位應依使用者是否知道確切日期及日期用途選擇輸入模式；日曆只適合部分需比較近期日期的情境，且不能作為唯一依賴 JS 的輸入方式；約略日期可在不要求精確的情境接受。
- **反例 A**：治療所 Session 的實際服務日期／時間與補助使用期限通常要求精確；若把「2026年10月左右」當成可計費的精確日期，可能錯計方案期別及額度。反證條件：區分「歷史回憶約略日期」與「計費／核定的確切日期」，不以約略輸入直接執行精確計數。
- **反例 B**：補助期限可能以首次實際服務日、核定期與地方規範為基礎，不一定等於「今天起三個月」；日曆選到合法日期不代表業務資格合格。反證條件：日期格式有效、服務規則符合、核准狀態各自驗證；未知首次服務日不得自動補為今日或開案日。
- **反例 C**：跨民國／西元日期及臺灣常見年月日排序可能使英國式日月年提示誤導行政輸入；例如 115 年不得在未確認紀年制時默認西元115年。反證條件：顯示紀年與日期格式必須明確，匯入與顯示的轉換需雙向核對，未經實測不得宣稱已處理。
- 研究推論：日期輸入的便利性與日期資料的業務可用性是不同層次；不得以 UI 允許輸入推定核定期別與歷史用量正確。

## S02｜Ask users for Names
- ID：`AUTO69-S02`；canonical URL：https://design-system.service.gov.uk/patterns/names/；去重身份：`govuk-design-system:patterns/names`；維護者：GOV.UK Design System team；首發日未明列；查核日：2026-10-28。
- 唯一閱讀事件：`AUTO69-S02-R1-MAIN-TEXT-C1`；**主要正文與兩種獨立預覽一次文字閱讀，非完整深讀 R1**。覆蓋：是否需要姓名、欄位長度與字元、多欄／單欄、常用姓名與證件姓名差異、中間名、autocomplete、spellcheck=false、避免強制稱謂、姓名更改、錯誤提示與 HTML/Nunjucks；預覽：https://design-system.service.gov.uk/patterns/names/default/index.html 及 https://design-system.service.gov.uk/patterns/names/error/index.html。
- 官方要點：只在服務必要時索取姓名；不能假設所有姓名均符合 first/last name 格式；單一欄位容納範圍較廣，但無法可靠分拆；需要支援多種字元、更新姓名，且姓名不宜被拼字檢查誤判。
- **反例 A**：治療所若以顯示姓名而非不可變的 Cases/Staff 內部識別碼建立關聯，同名或改名可能錯接 Session、Billing 或補助用量。反證條件：顯示姓名僅供辨識，跨庫關聯與歷史對帳使用經核實的穩定 ID；不能用「姓名相同」自動合併個案。
- **反例 B**：強制英語 first/last 分欄或限制字元，可能破壞中文姓名、複姓、原住民族姓名及其他合法姓名寫法；但單欄姓名也不保證可以無誤生成法律文件。反證條件：證件姓名、常用稱呼與必要行政用途分開評估，保留原始合法文字，必要時人工確認，不擅自拆分。
- **反例 C**：姓名自動填入或變更後直接覆寫所有歷史財務／同意文件的姓名，可能導致審計或文件身分對應問題。反證條件：分辨現行顯示名稱、法定證件姓名及歷史交易快照的必要性；僅在合法且授權範圍內處理更正，未經核對不批次覆寫。
- 研究推論：易用的姓名欄位不等於唯一身分識別或歷史文件一致性；保護個資、權限與更名流程須另核對。

## 去重、進度與限制
- 本輪「已查來源索引」新候選 **2 篇**；主要正文文字閱讀 **2 篇各一次**；首次獨立反例 **2 組、6 情境**；既有來源完整複讀 **0 次**。
- **完整深讀 R1=0、R2–R10=0；本輪 FULL_DEEP_PASS_10_OF_10=0；累積可核實 0／10,000 篇。** 預覽頁與 HTML/Nunjucks 不另計文章或複讀次數。
- **NOT_TESTED**：全儲存庫歷史清冊逐檔及同文異址語義去重、原始圖片像素/實際互動、鍵盤/讀屏/手機、Notion 真人操作、日期民國西元轉換、身份識別、角色權限、公式、歷史收費金額、Session/Billing 真值、補助資格及效能。研究假說不構成任何重新設計或實作核可。
