# Notion 文件索引

本資料夾服務於 **治療所行政系統 Notion TEST**；所有連結和數據均須於新工作回合重新驗證。

- [政府補助通用資料模型](government-subsidy-architecture.md)：多政府方案／不同年度期別／獨立規則、資料實體與計數歸屬。
- [工作台與 UX](workbench-ux.md)：三層額度、異常優先、原本十個功能頁面最小調整原則。
- [驗收狀態](acceptance-status.md)：歷史 TEST 證據、P0 缺口、安全隔離與後續。
- [決策日誌](decision-log.md)：已確認設計、研究方向、未核可的大變更。
- [資料來源](sources.md)：Notion TEST 實際頁面、Google Docs 最新規格與備份。

資料實體：Price Plans＝核定方案實例；補助參與紀錄＝個案 × 方案實例；Cases＝永久個案主檔；Care Episodes＝臨床歷程；Sessions＝真實服務及占用；Staff／週回報＝心理師及該期週次；補助額度調整＝核定增減與追溯。現況以最新 Schema 及實際 Relation 為準。



## 設計研究知識庫（2026-10-24 首批）

- [Notion／資料庫／UX 研究總入口](research/README.md)：長期研究證據與規格映射。
- [16 筆來源證據登錄](research/evidence-register-2026-10-24.md)：去重、正文／摘要等級與尚未達成 10,000 篇的精確記錄。
- [資料庫模型準則](research/database-design-principles.md)、[工作台 UX 準則](research/workbench-ux-principles.md)、[Free／效能／權限](research/performance-permissions-free-plan.md)、[全面稽核與下一步](research/audit-checklist-and-research-progress.md)。

上述資料是**研究文件，不是 Notion 已實作／已驗收功能**；要修改 Schema、共用公式或舊模組仍須核准。


## 2026-10-24｜十個既有行政模組完整唯讀稽核

已完成十個原行政模組的**唯讀**資料結構與 View 盤點：76個 linked DB 區塊、177個 View 設定、23個去重來源，合計636欄（152 Formula、147 Relation、48 Rollup）。核心問題、十模組表、F-01～F-07風險、一次性 B 類改善方案與回復／限制，見 [完整稽核與整批提案](audits/ten-module-structure-ux-audit-2026-10-24.md)。**尚未修改任何 Notion View 或 Schema，C級更動仍需使用者批准**。


## 2026-10-24｜B1～B3 獨立 TEST 預覽與狀態驗證

已在 Notion [TEST 行政管理] 下建立[十模組 B1～B3 整批操作預覽](https://app.notion.com/p/4038ca66aa4d814297a2dbe27e8d054d)，另建獨立[活動狀態篩選測試 DB](https://app.notion.com/p/39f6c1322dd44106b32760a58246860e)（4欄、0 Relation、5合成資料）。三組 TEST View 期望／實際為1/1、2/2、5/5，均已查詢 PASS。**原十頁和原 Events View 完全未更動；B2/B3 為整批預覽，不是已套用**。完整實作與回復：[TEST B1～B3 記錄](audits/b1-b3-test-preview-2026-10-24.md)。


## 2026-10-24｜B1–B3 行政頁整批 B 級修正與回查

已在 TEST 管理舊頁批次套用可驗證的 B 級改善（帳務／活動／薪資三個頁面任務標籤，任務與文件 View 精確命名）；活動採**2個新 View + 2個保留標停用的舊 View**，因 Notion `update_view` 無法清除原 `simpleFilters` 而未直接覆寫。五個原生頁面備份已回查，原業務資料／Schema／Formula／權限不變。完整 View ID、備份和驗收：[B 級批次修改紀錄](audits/b1-b3-legacy-batch-2026-10-24.md)。

## 2026-10-24｜研究成果完整性核對、TEST 工作台 v2 與長期目標修訂

- [**Notion 長期目標 v2（成果導向／可驗收）**](long-term-goals.md)：將研究數量要求獨立追蹤，不再當作可用性或安全的替代指標；仍保留歷史1,000／10,000篇口徑差異與未完成紀錄。
- [**研究來源 → 設計 → 目前實作對照矩陣**](research/research-to-implementation-matrix.md)：逐項記錄已保存成果、官方依據、落地狀態、未驗收及缺漏；原有16來源不重複灌水。
- [**行政任務工作台 v2 整體改版**](audits/task-workbench-ux-v2-2026-10-24.md)：只重排既有十模組的 TEST 預覽，任務導向且可回復。
- [直接開啟 Notion TEST 工作台 v2](https://app.notion.com/p/4038ca66aa4d814297a2dbe27e8d054d)；原功能資料庫／權限／Formula 未修改。
