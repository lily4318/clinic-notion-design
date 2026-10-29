# AUTO-92｜Notion 深度學習：Accordion 與 Breadcrumb（2026-10-29）

執行軌跡：`AUTO-92-20261029-1142-ACCORDION-BREADCRUMB`；Asia/Taipei 2026-10-29 約11:42。**範圍僅公開 UX 文件研究與 GitHub 研究紀錄；沒有操作任何 Notion 正式或 TEST 頁面、資料庫、View、Formula、Relation、權限、Session、GAS、Cloud Run 或部署。**

## 前置與去重
- 本輪開始已讀 main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、decision-log.md、acceptance-status.md；檢視 docs/notion/research 目錄（當時截至 AUTO-91）及研究 README、首批 evidence-register、稽核清單、MANUAL-01、AUTO-90/91。以本輪最新 sources 全文精確 URL/canonical 查核，並以 GitHub code search 查兩個 URL，未見命中；但**未逐一語義比對全部歷史 91 份研究全文及跨語系鏡像**，故僅列「新來源候選」而非已全域去重唯一。
- 研究來源維護者：U.S. Web Design System（USWDS）／U.S. General Services Administration；查核日 2026-10-29；官方更新表有 2026-08-18 v3.14.0，**這是元件更新日，不冒稱文章首次發表日**。
- 來源是可讀公開 HTML；閱讀了選定程式碼、指南、無障礙摘要及更新表。未逐一操作預覽、下載/執行原始程式、手機/鍵盤/螢幕閱讀器或真人 Notion；嚴格完整深讀 R1=0。

## S01｜Accordion：摺疊資訊的操作成本
- 標題：**Accordion | U.S. Web Design System**；URL：https://designsystem.digital.gov/components/accordion/；canonical ID `uswds:components/accordion`；閱讀事件 `AUTO-92-20261029-1142-ACCORDION-BREADCRUMB-S01-R1-MAIN-GUIDANCE-SELECTED-CODE-A11Y-PARTIAL`。
- 已查核原文：頁約 L187–255 為 borderless、bordered、multiselectable 三種預覽的文字呈現；L256 起部分 HTML 示例，使用 button、aria-expanded、aria-controls 與內容 id；L866–897 的適用情境、認知負擔、鍵盤/讀屏要求、預設開啟與多選屬性；L914–948 官方 23 項 WCAG 2.1 AA 測試摘要（21 通過、2 項依情境驗證），以及 2026-08-18 v3.14.0 圖示位置更新。
- 原文結論：當使用者只需少數內容、版面有限可考慮摺疊；若需要看到大部分資訊或內容很少，摺疊增加選擇與點擊成本，應改用清楚格式化正文。這是 USWDS 元件指引，**不是 Notion 原生 Toggle 已通過測試**。
- 反例 A1【將治療所每日個案餘額、期限、心理師本週回報全部收進 Toggle 就更簡潔】：日常必讀資訊需額外展開，違反本專案「同頁開啟即見」的已確認要求；收合只是隱藏，不能代替清楚直顯。
- 反例 A2【把敏感 Billing/Session 欄位收合即可保密】：視覺收合不是資料庫、頁面或欄位權限；具有存取權的使用者仍可能從其他 View/搜尋看到資料。不得把收合當存取控制。
- 反例 A3【USWDS Accordion 23項測試摘要足以證明 Notion Toggle 可供所有使用者操作】：不同產品、ARIA 實作、裝置與讀屏支援均未實測，外部元件測試不可直接外推。
- 未完成：原始互動 Demo、所有 HTML 變體完整逐行檢查、鍵盤/讀屏、手機與 Notion 真人操作。

## S02｜Breadcrumb：階層位置不等於操作流程
- 標題：**Breadcrumb | U.S. Web Design System**；URL：https://designsystem.digital.gov/components/breadcrumb/；canonical ID `uswds:components/breadcrumb`；閱讀事件 `AUTO-92-20261029-1142-ACCORDION-BREADCRUMB-S02-R1-MAIN-GUIDANCE-SELECTED-CODE-A11Y-PARTIAL`。
- 已查核原文：頁約 L188–314 的一般、RDFa、截斷示例及部分 HTML；L427–455 使用時機、例外、行動版長標題、語意 nav/ol/aria-current；L475–508 官方14項無障礙測試摘要（11通過、3依情境驗證）及 2026-08-18 v3.14.0 改成**預設換行**、單行截斷改為 opt-in 的 breaking change。
- 原文結論：Breadcrumb 表示網站階層位置，幫助從搜尋或外部連結進入內頁的使用者；不適合當線性流程指示，淺層網站/首頁或與側欄重複時可能不需要。
- 反例 B1【把補助資格→收費→Session→收據當作 Breadcrumb 即表示完成各步驟】：這是業務狀態/交易程序，不是頁面階層；導覽文字不證明資格核准、入帳或保存。
- 反例 B2【首頁已有清楚同頁三區，仍必須額外加入 Breadcrumb 才算好 UX】：對淺層工作台或已具側欄的介面可能重複且占空間，不能只因外部模板有就強加。
- 反例 B3【將長標題強制截斷一行可維持整齊且沒有副作用】：可能遮住核定期別/方案辨識資訊；官方2026-08-18版本改預設換行，手機視角/長中文標題須另驗證，且不能推定 Notion 原生可套 USWDS CSS。
- 未完成：原始預覽實際點擊、行動裝置、ARIA/讀屏測試及治療所真實頁面操作。

## 交叉反證與狀態
- Accordion 回答「哪些內容需要預設展開」；Breadcrumb 回答「使用者在頁面階層的哪裡」。兩者都**不能代替資料直顯、權限隔離、資料持久化或補助資格審查**。
- 研究推論：治療所已確認高頻核心資料「開啟即見」；僅低頻補充說明可能適合折疊。此處**不提出或批准任何版面修改**；需未來使用者明確核准、真人 UX/權限/效能測試後才可決定。
- 計量：`NEW_SOURCE_CANDIDATE=2`、`PARTIAL_MAIN_AND_SELECTED_EXAMPLES_READ=2`、`INDEPENDENT_COUNTEREXAMPLE=6`；`FULL_R1=0`、`FULL_R2_TO_R10=0`、`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`，累積可核實完成 **0／10,000篇**。輔助無障礙測試連結未另計已讀來源。**只寫 GitHub 研究紀錄，不修改 Notion/正式系統；未達門檻不得進入重新設計。**
