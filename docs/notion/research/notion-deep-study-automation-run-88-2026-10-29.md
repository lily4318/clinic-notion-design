# AUTO-88｜Notion 深度學習：流程說明與進度指示的反證（2026-10-29）

Trace: `AUTO-88-20261029-0744-PROCESS-STEP-RESEARCH`。研究與 GitHub 紀錄限定；**RESEARCH ONLY / NO NOTION OR SYSTEM WRITE**。本批是獨立自動研究單元，不抵銷聊天室手動續作。

## 前置規範、去重與來源層級
- 2026-10-29（Asia/Taipei）讀取 main：README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、sources.md、decision-log.md、acceptance-status.md；研究目錄99項檔名及研究 README、首批證據清冊、批次02/03/04、MANUAL-01、稽核進度、研究→實作矩陣、long-term-goals、AUTO-86/87。
- 開始前 sources.md 全文（原SHA `1373a51595db5112b66035bf7fc2f0f8504a9bc8`）未見以下兩個 exact URL，GitHub code search 查兩 URL 及 `AUTO-88` 均未命中。**尚未逐一全文比對全部87個AUTO研究檔、同文異址或跨語系內容指紋；只記新來源候選，不宣稱全庫唯一**。寫入共用文件前須再次讀最新 main 與 blob SHA。
- 兩篇均為 USWDS／美國 GSA 官方 HTML 設計元件指引，**不是 Notion 原生功能**。查核日2026-10-29；首次發布日期未核。官方更新表只作歷史版本線索，不當首發日期。
- 同一篇只建立一個本次閱讀事件；輔助 accessibility-tests 頁作為背景，不另算十次深讀或獨立新文章。以下均是主文／選定程式碼與無障礙文字的**部分閱讀**，不是完整的 DEEP_PASS。

## S01｜Process list（候選新來源）
- 標題：**Process list | U.S. Web Design System (USWDS)**；canonical URL：https://designsystem.digital.gov/components/process-list/ ；ID `uswds:components/process-list`；維護者 USWDS/GSA。
- 閱讀事件 `AUTO-88-20261029-0744-PROCESS-STEP-RESEARCH-S01-R1-MAIN-HTML-GUIDANCE-A11Y-PARTIAL`。實際開啟並閱讀定義及三種預覽文字（頁面L188–L228）、有序清單 `<ol>`／`<li>`／標題層級 HTML 範例（L229–L320）、Guidance/適用與替代（L411–L436）、設定/更新表（L441–L506），並查輔助清單 https://designsystem.digital.gov/components/process-list/accessibility-tests/ 的測試摘要與選定條目（L188–L325）。未操作 preview、未逐一完成無障礙測試、未驗證原始 CSS／視覺/手機。**FULL_R1=0**。
- 官方要點：適合**固定順序的高層次步驟說明**，不適合非線性任務、跨多頁的進度回報或當前狀態指示；建議約3–10步、短而平行的標題、正確語意 heading 層級。USWDS 官方6項無障礙測試：2 PASS、4 CONDITIONAL、0 FAIL；有些項目必須在實際專案內驗證，不能外推本所。
- 文檔品質異常（待再核）：Process list 頁的「Using the process list component」下出現 `usa-step-indicator__header`、置中 counter/segment 等 Step indicator 特定語彙（L435–L443），與前面 Process list 使用範圍及 HTML 不一致；**可能是文件混入其他元件說明**，不把該段當作 Process list 可用功能的保證。
- 反例 P1【政府補助資格流程只要畫成三步即可自動完成核准】：固定步驟只描述人工核對順序，不能取代當期資格、首次服務日、核定期別與正式行政核准；**流程說明≠規則驗證/核准**。
- 反例 P2【把 Billing/Session 每次操作都拆成多個步驟頁面】：USWDS 的流程說明不要求拆頁；若迫使高頻行政人員跳頁，反而違反已確認「同類資料同頁、開啟即見」。流程指引可為文字，不能冒充已核准的重設。
- 反例 P3【有順序編號即代表資料已依序保存】：列表不追蹤遠端寫入；補助文件未完成、交易未知、重試重複入帳等都不能由第3步圖示推定為完成。

## S02｜Step indicator（候選新來源）
- 標題：**Step indicator | U.S. Web Design System (USWDS)**；canonical URL：https://designsystem.digital.gov/components/step-indicator/ ；ID `uswds:components/step-indicator`；維護者 USWDS/GSA。
- 閱讀事件 `AUTO-88-20261029-0744-PROCESS-STEP-RESEARCH-S02-R1-MAIN-SELECTED-HTML-GUIDANCE-A11Y-PARTIAL`。開啟定義/5種變體（L188–L242）、預設與置中等選定 HTML（L243–L380，含 `aria-current`／隱藏文字／完成及待辦狀態）、Guidance/使用界線（L732–L758）、variants/測試/更新表（L789–L845）；輔助 https://designsystem.digital.gov/components/step-indicator/accessibility-tests/ 查摘要與一般/放大測試（L188–L328）。沒有完整逐行覆蓋全部重複 HTML 變體，也沒有操作手機/鍵盤/讀屏。**FULL_R1=0**。
- 官方要點：適合**跨頁、至少3個高層次章節且線性**的表單流程；進度條**不是導覽控制**，應另有上一步/下一步；條件分支會改變步數、非線性工作及短表單不適用。需有文字的當前/已完成/未完成狀態，不能僅靠顏色，使用正確 heading 與 `aria-current`。USWDS 9項無障礙測試：7 PASS、2 CONDITIONAL、0 FAIL；不能外推至 Notion。
- 反例 S1【將同頁個案/心理師/機構三區改成第1/2/3步更直覺】：三區可各自獨立查閱，並非線性提交流程；步驟條可能誤導有必填先後且增加點擊，違反同頁直顯需求。
- 反例 S2【顯示已完成 3/5 即代表個案補助核定與交易進度正確】：介面進度不保證底層 Relation、期別、補助資格或 Billing 寫入正確；中途修改、退件、退款後可能不再是線性狀態。**畫面完成≠業務完成**。
- 反例 S3【官方 WCAG Passed 可直接視為 Notion 原生步驟條已驗收】：官方只測其 HTML 元件且2項 conditional；Notion 原生 View/Formula/Status 不保證相同 ARIA、手機呈現或角色權限；若未驗證就套用，可能造成讀屏/放大使用者理解錯誤。

## 交叉反證、成果與邊界
- 對照已記錄的 GOV.UK Task list（AUTO-80）：Process list 是**順序說明**、Step indicator 是**跨頁線性位置**、Task list 可描述**可分次/非線性工作**；三者不等同於 Notion Status 或交易持久化。研究結論：**說明順序／顯示當前步驟／記錄業務狀態／資料真實保存**須分層判斷，不能把一種 UI 元件混作其他功能。只是未核准研究推論。
- 本輪：`NEW_SOURCE_CANDIDATE=2`；`PARTIAL_MAIN_AND_SELECTED_HTML_READ=2`；`COUNTEREXAMPLE_GROUPS=2`（6個）；`FULL_INDEPENDENT_REREAD_EXISTING=0`；`FULL_R1=0`；`FULL_R2_TO_R10=0`；`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`。累積**可核實10/10篇數仍0/10,000**。輔助清單、同篇多角度不另計。
- 待核：完整歷史/跨語系語義去重、全部互動/視覺、手機/鍵盤/讀屏、Notion 原生能力、權限、真人 UX、實際載入時間、Billing/Session/補助/歷史金額資料真值，均 `NOT_TESTED`。
- **NO NOTION/SYSTEM WRITE**：本輪僅外部資料讀取及 GitHub 研究進度紀錄，不修改正式或 TEST Notion 頁面、DB、View、Formula、Relation、權限、業務列，亦不修改 GAS、Cloud Run、Session 或部署。10,000篇各10次門檻未達，不能進入重新設計；兩研究路徑可並行。
