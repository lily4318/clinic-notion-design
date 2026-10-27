# AUTO-60｜2026-10-28｜Accordion 與 Tabs：資料可見性、跨區比較及無障礙風險（僅研究）

- 唯一執行軌跡：`AUTO-60-20261028-0345-RESEARCH`；台灣時間 2026-10-28 03:45 起；僅研究及 GitHub 紀錄，未操作 Notion 或正式系統。
- 開始與寫入前讀取 main：README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md、docs/notion/research/README.md；另核對 AUTO-59 與既有研究入口。
- 去重狀態：sources/decision/acceptance 的完整 canonical URL 檢索未命中；GitHub code search 兩個 canonical ID 未命中；本輪**未逐檔讀取所有歷史 research Markdown**，亦未完成同文異址、其他語系、其他 repo 路徑的全庫語義去重，故只列「新來源候選」，不列全庫確認新來源。前次 AUTO-59 曾查 70 份研究檔，但不能代替本輪重新核驗。
- 研究方法：公開原始官方網頁的正文與範例程式、已知問題/研究限制；未直接執行原始互動、鍵盤、螢幕閱讀器、行動裝置或治療所 Notion 操作。以下皆 `R1-MAIN-TEXT`，**不構成完整深讀 R1**，不增加 R2–R10。

## AUTO60-S01｜Accordion – GOV.UK Design System
- 來源：https://design-system.service.gov.uk/components/accordion/；canonical URL 同上；去重 ID `govuk-design-system:components/accordion`；作者/維護 GOV.UK Design System team；原始發布日未核；取證 2026-10-28。
- 閱讀軌跡 `AUTO60-S01-R1-MAIN-TEXT-C1`。閱讀範圍：用途、何時不適用、與 Tabs/Details 的選擇、HTML/Nunjucks 例、無 JavaScript 行為、標題與展開、session storage、已知讀屏問題、2025-04 等變更紀錄。參照網頁第 52–213、590–635 行；範例長程式碼作結構檢視而非實際運行。
- 官方原則：相關多節內容可展開，對反覆使用的 caseworking 任務可能有用；但所有人必看資訊不可預設藏在 Accordion；避免巢狀收合、長摘要及過量內容造成效能問題；官方元件在 JavaScript 不可用時展開全部內容，session storage 可記錄展開狀態；其實作與 Notion Toggle **不是同一產品**。
- 獨立反例 C1：將「補助資格待人工核實、服務日期與期別矛盾、未收款」等必看例外放入預設收合區，可能使行政人員只看到表面正常的總數就做出錯誤判斷。反證：版面短並不等於工作安全；但全部歷史備註常駐也可能拖慢高頻作業，應以任務必要性而非資訊量決定預設可見。
- 獨立反例 C2：把同案跨期歷史資料拆進多層 Accordion，會增加跨區比較與尋找成本；然而一頁全部展開也可能變慢。反證：Accordion 的「同頁」不等於「開啟即見」；不能用折疊代替使用者已確認的直接資料呈現要求。
- 反向限制：官方已提醒語音辨識、讀屏元素清單可能難辨標題按鈕，長 summary line 會增加語音負擔；不能假設 Notion 原生 Toggle 提供相同的鍵盤/讀屏/記憶展開行為。

## AUTO60-S02｜Tabs – GOV.UK Design System
- 來源：https://design-system.service.gov.uk/components/tabs/；canonical URL 同上；去重 ID `govuk-design-system:components/tabs`；作者/維護 GOV.UK Design System team；原始發布日未核；取證 2026-10-28。
- 閱讀軌跡 `AUTO60-S02-R1-MAIN-TEXT-C1`。閱讀範圍：用途、禁忌、與 Accordion/Details 比較、HTML/Nunjucks、JS/小螢幕退化行為、URL fragment、標籤排序、標題/鍵盤/讀屏限制及 2024-08 變更。參照網頁第 52–455、456–488、889–945 行。
- 官方原則：當相關資訊可清楚分段、第一段最常用且使用者不必同時看到各段時，Tabs 可讓高頻使用者快速切換；不適合跨 Tab 比較、依序閱讀或當成跨頁導航；無 JS/小螢幕時官方元件呈現連續內容與目錄，URL fragment 可記錄切換。官方明言該元件**尚未經其自身使用者研究直接驗證**，小螢幕與讀屏使用方式仍需研究；不能把官網指引當成治療所 UX PASS。
- 獨立反例 C1：把 Session、Billing、補助用量分成三個互斥 Tabs，行政人員核對同一案的服務日、收款日及額度時必須反覆切換並記住數字；不同 Tab 的方案期別篩選還可能不一致。反證：視覺上同頁≠同時可見，也不保證跨資料源一致。
- 獨立反例 C2：若第一個 Tab 是低頻維護資訊而日常待處理案件在後方，使用者可能忽略急迫工作；但若為了突出待核而塞滿第一頁，也會降低可讀性。反證：預設 Tab 應以真實工作頻率/任務證據決定，不是由設計者主觀選擇。
- 反向限制：官網的 URL hash、無 JS fallback、手機呈現與 Notion 原生 database view tabs 不是同一機制；未在 Notion 實際測試，不推定同等行為、權限或資料載入策略。

## 跨來源反證與嚴格計數
- Accordion 允許多段同時展開；Tabs 一次只呈現一段。對需要同時核對 Session/Billing/補助用量的情境，兩者都可能產生資訊遮蔽；對低頻補充說明，收合可能減少干擾。**選擇需依業務任務與證據，不因官方示例美觀而自動改版。**
- 本輪新來源候選 2；主要正文文字閱讀 2；首次反例分析 2 篇（各 2 情境），**獨立完整深讀 R1 = 0、R2–R10 = 0**；既有來源完整複讀 0；新增 `FULL_DEEP_PASS_10_OF_10` 0，累積可核實 0／10,000 篇。
- 未逐張檢查示例圖片、未執行範例互動、鍵盤/讀屏/手機測試；無治療所真實角色、效能、金額與公式驗證。此處只是研究假說，**未核准也未執行任何 Notion 頁面、Data Source、View、Relation、Formula、權限、業務資料、GAS/Cloud Run/Session/部署修改**。
