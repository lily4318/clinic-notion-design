# AUTO-91｜Notion 深度學習：資料庫全域設定與欄位權限例外（2026-10-29）

執行軌跡：`AUTO-91-20261029-1042-DB-SETTINGS-PROPERTY-ACCESS`。範圍：**僅公開文件研究與 GitHub 研究紀錄；沒有 Notion 正式／TEST、GAS、Cloud Run、Session 或部署寫入**。此批次與聊天室手動續作各自獨立；同 URL／同一閱讀事件不重複計算。

## 前置與去重證據

- 2026-10-29 Asia/Taipei：先 Fetch main 的 `README.md`、根 `AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`decision-log.md`、`acceptance-status.md`；另檢查 `docs/notion/research/` 目錄（當時 102 個項目）、研究 README、首批 evidence-register、audit-checklist、AUTO-90 研究記錄。main 在本輪預檢為 `4589323218cec4a0a935231df79ac6bd77207e0e`。
- S01 官方 URL `https://www.notion.com/help/customize-your-database` 在當期 `sources.md` 全文無精確 URL，GitHub code search 未見結果；只可列 **新來源候選**，不代表已完成全部歷史／同文異址／跨語系語義去重。
- R01 官方 URL `https://www.notion.com/help/database-property-access` 已於 2026-10-24 首批證據登錄 `N07`，當時只有搜尋摘錄。**本輪取得並查核正文，屬既有來源取證升級，不得當新來源，也不得稱已完成完整獨立第二遍**。
- 兩份皆為官方公開 HTML，實際閱讀範圍列於下方；沒有查完全部圖片、原生互動、手機／鍵盤／讀屏、真人 Notion 或角色登入操作。未核實首次發布與更新日，只記 2026-10-29 查核日。

## S01｜Database settings（新候選，主要正文部分閱讀）

- URL： https://www.notion.com/help/customize-your-database
- 標題：**Database settings**（頁面標題 Customize your Notion database settings）；維護者 Notion Help Center／Notion Labs；canonical ID `notion-help:customize-your-database`。
- 閱讀事件：`AUTO-91-20261029-1042-DB-SETTINGS-PROPERTY-ACCESS-S01-R1-HTML-MAIN-SECTIONS-PARTIAL`。
- 官網正文約 L107–L141：資料庫設定需要 `Can edit` 以上權限；**設定作用於整個資料庫，不只單一 View**（L114–118）。`Lock database` 鎖住 View/屬性變更，**仍可輸入資料**（L122–125）。其他設定包含 Edit properties、Automations、Sub-items、Dependencies、Sprints、Connections、Customize page layout（作用於所有資料庫頁面）、Turn into Tasks／Undo（L125–137）。
- 反例 S1【把正式 Sessions 資料庫鎖定即可阻止錯誤的 Session 修改】：官方說鎖定後仍能輸入資料；此設定不是業務列唯讀、審核或角色權限保證。未對本所做操作測試。
- 反例 S2【為某個 View 調整 Database settings 不會影響其他檢視】：官方明言全資料庫適用；更動欄位／Sub-items／Layout 可能影響同源其他頁面與行政工作流程。不得擅自實作。
- 反例 S3【將政府補助資料庫 Turn into Tasks 是純視覺改善】：Task DB 有狀態、負責人、截止日等任務語義（另需查對 Task DB 原文），可能使業務核定期別與行政任務混淆；未核實現行 schema，不得視為安全等價替換。
- 取證界線：主要文字可讀；未操作全頁設定、圖片或原生 UI。嚴格 `FULL_R1=0`。

## R01｜Manage database property access（既有 N07；正文取證升級）

- URL： https://www.notion.com/help/database-property-access
- 標題：**Manage database property access**；維護者 Notion Help Center／Notion Labs；canonical ID `notion-help:database-property-access`（既有 `N07`）。
- 閱讀事件：`AUTO-91-20261029-1042-DB-SETTINGS-PROPERTY-ACCESS-R01-N07-HTML-ALL-MAIN-SECTIONS-VERIFIED-PARTIAL`。
- 官網正文約 L107–L225：欄位權限**僅 Business/Enterprise**，需資料庫 `Full access` 設定；web/desktop 設定、mobile 生效但不能設定（L116–126）。最多可對 **20 個不同屬性**設定權限；必須在原始資料庫 Table View 而非 Linked View 設定，支援預覽使用者權限（L129–146）。
- 權限等級區分 `Inherit`、可改屬性及值、只改值、只看欄名、看欄名及值、完全無權限（L147–160）。以 Person 欄位設定例外不會自動授予其他列的值（L162–169）。
- **關鍵例外**：資料庫 `Full access` 永遠不受欄位限制；欄位權限不授予原本無法開啟的頁面；對多個例外採**最寬鬆**權限；其他分享路徑也可能擴大存取（L170–182）。受限欄位參與篩選／排序／分組時，某些 View 可能無法開啟；舊版資料庫還原會保留**目前**的欄位權限設定（L174–182）。
- 不可限制的欄位包含 Title、ID、建立/修改者與時間、部分同步屬性及子項目／父項目關聯；Wiki 不支援；多條欄位權限規則可能降低載入效能（L183–206）。若 Button、Automation、Formula 或 Rollup 失效，官方建議以可見欄位者測試，判斷是否權限相依（L207–225）。
- 反例 R1【在 Linked View 隱藏個案金額即可保密】：Linked View 不是欄位權限規則入口，且 View 隱藏不代表其他檢視或共享權限不可見。須先確認方案層級、原始資料庫及角色實際權限。
- 反例 R2【對心理師欄位設定 No access 就能限制所有人】：Full access 角色永遠不受此欄位限制，其他例外採最寬鬆；使用管理員帳號測試得到「可見」不能證明一般角色權限錯誤，反之亦然。須使用非 Full access 身分逐角色驗證。
- 反例 R3【只限制財務欄位不會影響原有 View／公式／效能】：若 View 篩選排序使用受限欄位，可能無法開啟；公式、Rollup、Button、Automation 亦可能因權限失效，且大量規則可能增加載入時間。未對本所正式資料庫做任何測試。
- 本次將 N07 由「僅搜尋摘錄」升級為「官方 HTML 主要正文逐節查核」，**不是十次深讀中的完整 R1/R2**；圖片、權限 Preview 原生互動、不同帳號、手機與無障礙測試皆未完成。

## 交叉反證與保守結論

- `Lock database`（限制更動 View/屬性）、`Property access`（特定欄位存取，僅部分付費方案）、`Page access`（是否能開頁）是不同機制；三者都不能自動證明政府補助核准、歷史收費快照、交易持久化或醫療資料的合規性。
- **不提出任何本輪採用或修改建議**；若未來獲准設計／測試，需先重查 Notion 實際方案、原始 DB 與角色權限，再評估全域設定對其他 Views/公式及效能的相依影響。

## 嚴格計量及未完成項

- `NEW_SOURCE_CANDIDATE=1`（S01，未完成全歷史語義去重）；`NEW_PARTIAL_MAIN_TEXT_READ=1`；`EXISTING_SOURCE_EVIDENCE_UPGRADE=1`（N07，由搜尋摘錄→正文逐節查核）；`COUNTEREXAMPLE_SCENARIOS=6`。
- `FULL_R1=0`、`FULL_R2_TO_R10=0`、`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`；累積可核實 **0／10,000篇**。同一篇或同一次分析不多次計數。
- **PENDING**：所有歷史來源的 canonical/跨語系語義去重；原始圖片、影片、互動；手機、鍵盤、螢幕閱讀器；真人 Notion 權限與 View/Formula/Rollup/Button/Automation 行為、角色隔離、真實載入速度；正式業務與歷史價格核對。
- **NO NOTION/SYSTEM WRITE**：只研究並記錄 GitHub；沒有修改 Notion 正式/TEST 頁、DB、View、Formula、Relation、權限、業務列，也沒有修改 GAS、Cloud Run、Session、部署。研究門檻未達，未經使用者完成確認不得進入重新設計。
