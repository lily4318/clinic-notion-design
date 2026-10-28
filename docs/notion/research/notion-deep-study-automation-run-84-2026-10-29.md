# AUTO-84｜Notion 深度學習：USWDS 表格與同頁導覽（2026-10-29）

Trace: `AUTO-84-20261029-0343-USWDS-RESEARCH`｜僅外部研究與 GitHub 記錄，**NO NOTION/SYSTEM WRITE**。

## 前置、來源與去重範圍
- 開始前從 GitHub `main` 讀取根 README、AGENTS、docs/system/source-of-truth、docs/notion/AGENTS、sources、decision-log、acceptance-status、research/README、audit-checklist-and-research-progress、research-to-implementation-matrix、long-term-goals 與 AUTO-83 紀錄。最新來源索引 `sources.md` 已全文檢查，兩個 `designsystem.digital.gov` canonical URL 均未登錄；檢查 AUTO-84 目標檔案當時不存在。未完成全歷史每個 AUTO 文件全文比對、同文異址與語義去重，因此只記 **2 篇新來源候選**。
- 2026-10-29 查閱美國政府 **U.S. Web Design System（USWDS）** 官方頁面。兩頁有可讀正文、組件示例與程式碼、無障礙測試摘要、版本更新紀錄；本輪實際讀取主要指引與選定示例，**沒有**逐一啟動全部 preview、測試真實手機／鍵盤／讀屏，也沒有驗證 Notion 原生實作。不能算完整 R1。

## S01｜Table（新候選）
- URL: https://designsystem.digital.gov/components/table/
- Canonical ID: `uswds:components/table`；標題：**Table | U.S. Web Design System (USWDS)**；維護者：U.S. Web Design System / GSA；查核日：2026-10-29；頁面列出最近相關更新 2026-08-18（USWDS v3.14.0；非推定文章首次發表日）。
- 唯一閱讀事件：`AUTO-84-20261029-0343-USWDS-RESEARCH-S01-R1-MAIN-GUIDANCE-SELECTED-EXAMPLES-PARTIAL`；已讀頁面概述、standard/striped/sticky 等示例之部分文字、Guidance 的 When to use/consider else、Usability、Accessibility、Using、variants、latest updates，網頁約 L188–L380、L2712–L2845；中段全部長篇原始 HTML 與每一個可點預覽未逐項完整查驗。
- 官方可核重點：表格適合一致欄列的結構化資料；欄標籤清楚、單位一致、數字右對齊、標題及更新來源可用 caption；長表可排序但需考慮手機橫捲／堆疊；可排序數值應以真正排序值而非展示格式為依據；排序的 aria-live 與可聚焦橫捲容器需專案實測。USWDS 自身的 sticky-header 變體與 scrollable/stacked 變體並不相容（該框架限制，**不是** Notion 已驗證限制）。
- 反例 T1【看見當前費率表即認定歷史收費正確】：若 Session／Billing 只是動態引用 Price Plan 目前金額，表格排版再清楚仍可能把歷史交易金額重算；**表格呈現≠交易時點保存**，需另外查核資料歸屬與快照，不能據此提議修改現有公式。
- 反例 T2【格式化金額／日期直接按字串排序】：顯示「2,000」「800」或不同日期格式時，若底層為文字而非正確數值／日期，排序結果可能誤導核銷順序；USWDS `data-sort-value` 是 HTML 組件做法，**不能假定 Notion 原生 View 能直接使用該屬性**。
- 反例 T3【所有欄都放進同一張超寬表】：使用者雖要求同頁直接看資料，但若補助額度、歷史方案、收款、個案敏感欄位全攤開，手機閱讀、橫捲焦點、角色可見範圍與效能可能惡化。精簡顯示需保留任務所需欄位，不能用 View 隱藏當作權限。

## S02｜In-page navigation（新候選）
- URL: https://designsystem.digital.gov/components/in-page-navigation/
- Canonical ID: `uswds:components/in-page-navigation`；標題：**In-page navigation | U.S. Web Design System (USWDS)**；維護者：USWDS / GSA；查核日：2026-10-29；頁面最近列出 2026-08-18 v3.14.0 的 JavaScript／無障礙更新，非首次發表日。
- 唯一閱讀事件：`AUTO-84-20261029-0343-USWDS-RESEARCH-S02-R1-MAIN-GUIDANCE-SELECTED-EXAMPLES-PARTIAL`；已讀概述、部分 HTML 樣例、Guidance 的 When to use/consider else、Usability、Accessibility、Using/settings、14項無障礙測試摘要、latest updates，網頁約 L188–L215、L1299–L1455；大量 lorem ipsum 範例及獨立 Demo 未逐一實際互動。
- 官方可核重點：適合三個以上明確區段或超過三個 viewport 的長頁；短頁、缺標題階層與無限捲動不適用。USWDS 以 `h2/h3` 生成同頁導覽，標籤對應標題、保持焦點與鍵盤可用；官方 14 項無障礙測試摘要為 10 通過、4 條件式，**不代表每個採用網站或 Notion 通過**。
- 反例 N1【用同頁錨點取代直接可見的日常資料】：使用者要求「同類資料同頁、開啟即見」；錨點只是跳到同頁其他位置，若首屏只有導覽而沒有必要的額度與 Session 資料，仍可能不符合已確認的 UX。
- 反例 N2【新增導覽即可改善 20 多個 Linked Views 的載入】：同頁導覽不會自動減少資料庫查詢、公式依賴或載入量；對大量 inline DB 的效能效果仍須實際計時，不能用導覽的存在宣稱變快。
- 反例 N3【把 USWDS 的 JS 自動標題／焦點行為視為 Notion 原生】：USWDS 依特定 DOM、Intersection Observer、鍵盤焦點與錨點運作；Notion 頁面與 linked database 是否能提供同等行為未驗證。若導覽重複顯示含個案資訊的標題，亦可能增加敏感資訊可見面；需按角色權限和可見性查核。

## 交叉反證、採用界線與後續可驗證問題
- 可轉用的**設計原則**：同頁依任務分區、保留清楚的表格欄標籤與數值單位、必要時使用段落定位；但「同頁直顯」不等於全量攤開，也不等於同頁導覽必然改善效率。
- 必須分開檢驗：①已知/未知/確認0的業務語義；②歷史 Billing/Session/Price Plan 金額是否固定；③View 欄位與實際權限；④鍵盤/讀屏/手機；⑤載入時間與任務步數。這些都不是本輪已完成的測試。
- 兩頁均為**外部前端設計規範**，不是 Notion 功能規格、不是使用者核准的改版。採用狀態：`RESEARCH_ONLY / NOT_APPROVED / NOT_TESTED`。

## 嚴格計量
- `NEW_SOURCE_CANDIDATE=2`；`MAIN_GUIDANCE_AND_SELECTED_EXAMPLES_PARTIAL_READ=2`；`INDEPENDENT_COUNTEREXAMPLE_GROUPS=2`、共 6 情境；`FULL_INDEPENDENT_REREAD_EXISTING=0`。
- `FULL_R1=0`；`FULL_R2_TO_R10=0`；`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`；最新可核實累積仍 **0/10,000 篇**，沒有把同文異址、搜尋命中或部分閱讀計為十遍。
- **NO NOTION/SYSTEM WRITE**：未修改任何正式／TEST Notion 頁、資料庫、View、Formula、Relation、權限或業務列；未修改正式 GAS、Cloud Run、Session 或部署；尚未達研究門檻，**不開始重新設計**。
