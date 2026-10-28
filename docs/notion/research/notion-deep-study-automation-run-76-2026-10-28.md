# AUTO-76｜治療所 Notion 深度學習：客戶專案追蹤與知識工作台（2026-10-28）
Trace: `AUTO-76-20261028-1941-RESEARCH`｜路徑：自動研究｜範圍：公開官方文件閱讀＋GitHub研究紀錄，NO NOTION WRITE

## 基準與去重
- 開始前重讀 main：README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md，以及 research/README.md、research-to-implementation-matrix.md；列舉 research 目錄當時 87 份 Markdown。
- `sources.md` 全文檢查兩個 canonical slug 未命中，GitHub code search 兩個 slug 均 0 筆；已知 AUTO-75 研究 Board/List，AUTO-06 研究 Calendar/Timeline/Gallery，不能把本輪引用的這些舊主題重算。
- 全 87 份研究檔逐檔核對曾嘗試，但因工具呼叫上限中止，**不能宣稱全庫精確去重完成**；不同語系/同文異址語義去重也未完成。以下僅列 **NEW_CANDIDATE**，非已證實全庫唯一文章。
- 來源為 Notion 官方可讀的長篇指南，不是模板目錄、付費摘要或搜尋結果；來源更新日期未取得，檢索/閱讀日期 2026-10-28。

## 來源 AUTO76-S01｜Manage client work in a flexible project tracker
- 原文：https://www.notion.com/en-gb/help/guides/manage-client-work-in-a-flexible-project-tracker
- canonical identity：`notion-help:guides/manage-client-work-in-a-flexible-project-tracker`；語系 URL 正規化後不另外計篇。
- 閱讀軌跡：`AUTO76-S01-R1-MAIN-TEXT-20261028`；本輪**一次**官方主要正文文字閱讀，頁面可讀行 L105–L265，含 One place for managing work、Flexible trackers、Visualize projects、Standardize processes、Work lives in tracker、Tailored client management、End-to-end workflows；文末模板區只作附錄，不算另篇。
- 可核對內容：一來源多種 View、Board 拖曳改 Status、按任務類型使用 database templates、客戶特定 View/Tracker、Forms intake、automation、Chart、Relation、AI與wiki。這是專案管理情境的範例，不是臨床資料授權或 Notion 方案限制的驗證。
- 反例 A：把一般客戶 portal 直接當成心理治療個案 portal，可能暴露會談/收款/個資；共享頁與Relation不等於最低必要權限。**反證結論**：先界定資料敏感性、存取者與最小必要共享；未經授權不得公開或新增 portal。
- 反例 B：把 Board 拖曳狀態當作收款、補助核定或臨床歷程的正式證據；操作方便可能改寫實際 Status。**反證結論**：視覺化工作流不能取代來源單據、人工核准、狀態歷史與回復。
- 反例 C：套用客戶專案模板時預填 Price Plan Relation/當期金額，可能把新 Session 綁到錯誤核定期，或令歷史 Billing 金額隨動態關聯變化。**反證結論**：方案期別與歷史金額需按交易時點及實際來源核對，不能因模板自動預填就認定正確。
- 仍未完成：原圖逐張/影音/實際操作、Windows中文輸入、手機/鍵盤/讀屏、真人 Notion 權限/公式/效能/歷史資料驗證；`FULL_R1=0`。

## 來源 AUTO76-S02｜Organize, connect, and scale your Notion knowledge management system
- 原文：https://www.notion.com/help/guides/organize-connect-and-scale-your-notion-knowledge-management-system
- canonical identity：`notion-help:guides/organize-connect-and-scale-your-notion-knowledge-management-system`。
- 閱讀軌跡：`AUTO76-S02-R1-MAIN-TEXT-20261028`；本輪**一次**官方主要正文文字閱讀，頁面可讀行 L107–L253，含 company home、knowledge beyond handbook、client/project relations、meeting records、AI insights、comments、synced blocks、external embeds、access and sharing。
- 可核對內容：首頁可用資料庫/圖表/快速連結、Relation 連結專案與會議、共用區塊同步更新、外部工具嵌入、Teamspace/guest 共享；此指南為一般企業知識管理建議，不構成醫療資料安全合規結論。
- 反例 A：將所有個案、收款與臨床資料整合進「全員可見公司首頁」會增加敏感資料曝光；**反證結論**：公司知識首頁與受限個案業務資料的權限/資料域應分開，且 View 隱藏不是授權。
- 反例 B：在日常 Session/Billing 頁大量加入 SOP、AI 設計指令與長篇介紹，雖符合知識集中，卻違反使用者已確認「同類資料同頁、開啟即見」。**反證結論**：內部設計/稽核留 GitHub，Notion 業務頁只留必要操作資訊。
- 反例 C：Synced blocks 與跨頁 Relation 讓「更新一次處處可見」，不代表歷史交易快照應跟著修改；**反證結論**：動態共用知識與歷史收款/方案期別快照責任不同，不能將可變來源直接當歷史財務真值。
- 仍未完成：原圖逐張/影片/互動、鍵盤/讀屏/手機、真人角色權限、Notion原生公式與載入、實際臨床工作台驗證；`FULL_R1=0`。

## 跨來源判斷與嚴格進度
- 共同價值：集中搜尋、按工作呈現資料、可重用 View；共同風險：一般商業 CRM/Portal/知識庫建議不能外推到治療所敏感資料、歷史收款或補助資格。
- 研究推論不構成新設計核可；不修改 Notion 正式/TEST、任何 DB/View/Formula/Relation/權限/業務資料，也不改 GAS/Cloud Run/Session/部署。
- `NEW_CANDIDATE=2`；`MAIN_TEXT_READ=2`（各一次）；`FIRST_COUNTEREXAMPLE_GROUPS=2`（共6情境）；`EXISTING_FULL_REREAD=0`；`FULL_R1=0`、`FULL_R2_TO_R10=0`；`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`；依本輪可見最新清冊，累積可核實 `FULL_DEEP_PASS_10_OF_10=0/10000`。
- 只有達成10,000篇各10次獨立、完整且可稽核深讀，並取得使用者明確確認後，才可開始 Notion 重新設計；自動與手動研究繼續並行。