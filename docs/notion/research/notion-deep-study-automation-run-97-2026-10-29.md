# AUTO-97｜2026-10-29 16:36 +08:00｜Notion 效能與分享權限：官方正文針對性研究

- **Trace / lane**: `AUTO-97-20261029-1636-PERF-SHARING` / hourly automation；與聊天室手動續作獨立。
- **權限與邊界**：RESEARCH ONLY；只允許公開來源閱讀與 GitHub 研究紀錄。未授權改動任何 Notion 正式或 TEST 頁面、資料庫、View、Formula、Relation、權限、資料列，也不改 GAS／Cloud Run／Session／部署。
- **本輪前置核對**：重新讀取 main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、sources.md、decision-log.md、acceptance-status.md；查閱 docs/notion/research 目錄（當次108項）及來源索引中既有的 /zh-tw/help/optimize-database-load-times-and-performance。兩篇都不宣稱完成「全文、全部媒體、實機操作」深讀。
- **查核日期**：2026-10-29；兩篇官方頁面原始發表日未確認。原始可讀 HTML 主文以 web.open 取得；圖片、影片與互動尚未操作。

## S01｜新來源候選｜Sharing & permissions settings
- **URL**：https://www.notion.com/help/sharing-and-permissions
- **標題／機構**：Sharing & permissions settings｜Notion Help
- **canonical**：`notion-help:sharing-and-permissions`；精確 slug 在本輪寫入前 sources.md 未見。**僅候選**：未完成全部歷史同文異址、跨語系語義去重。
- **閱讀事件**：`AUTO97-S01-R1-20261029-1636-HTML-SECTIONS-124-389-PARTIAL`；本次逐節查核官方主文 L124–389（分享、General access、權限等級、資料庫頁級權限、繼承／覆蓋、FAQ），並未播放 L109–113 影片、逐張檢查圖片或執行權限測試。
- **可追溯事實**：L182–210 區分公開連結、全工作區分享、Full access／Can edit／Can edit content／Can create；其中 Can create 限 Business／Enterprise 且不允許查看未另外授權的既有列。L233–299 說明 Business／Enterprise 的資料庫頁級權限、必須從來源庫設定、可由 Person/Created by 屬性授權，且不具來源庫存取時可能要靠通知或共享 linked view 進入個別頁面。L295–324 指出多路授權採**最寬鬆**權限，父頁私有化不保證子頁原有授權同步撤回，公開連結亦有間接可達風險。L364–387 FAQ 提醒同組織網域訪客可能被視為付費 member。
- **新反例 A**：在心理師專屬 linked view 設「只看自己個案」的 filter，卻同時給全工作區 Full access；**filter 不是安全邊界**，最寬鬆授權可讓個案資料外洩。
- **新反例 B**：僅把治療所行政首頁移到 Private，以為內層個案子頁都已撤權；官方指出父頁覆蓋不自動清除子頁原授權，須逐級查證，不能宣稱保密已通過。
- **新反例 C**：讓協作心理師具有 Can create 後，以為其必然可在既有 Session 逐筆查看並編輯；該等級原本限制查看既有列，且限特定方案，不能替代實際角色測試。

## R01｜既有來源的獨立針對性複讀｜Optimize database load times & performance
- **URL**：https://www.notion.com/help/optimize-database-load-times-and-performance
- **標題／機構**：Optimize database load times & performance｜Notion Help
- **canonical**：`notion-help:optimize-database-load-times-and-performance`。來源索引既有繁中 `/zh-tw/help/optimize-database-load-times-and-performance`，**英文同篇不算新來源**。
- **閱讀事件**：`AUTO97-R01-20261029-1636-INDEPENDENT-TARGETED-HTML-117-219-PARTIAL`；重新取得英文官方正文，獨立針對性能、上限、刪除風險閱讀 L117–219。這是**針對性複讀**，非完整 R2，也未檢視圖片、操作介面或測速。
- **可追溯事實**：L117–146 指出大量可見欄位、複雜 Formula/Rollup 鏈與排序／篩選、同頁多個 inline 資料庫會拖慢效能；單個 linked database 切換來源 View 一次只啟用一個 View 可減少負擔，但必須和使用者同頁直接看見的需求權衡。L149–219 列 500 欄、250,000 rows、單頁屬性資料 2.5MB、資料庫屬性結構 1.5MB 等上限；刪除欄位會刪其值，永久刪除後無法復原；超過部分容量／關聯限制會造成保存或反向同步失敗。**這些是官方產品限制，非本所已觸及的實測結果**。
- **新反例 D**：為了官方建議的單一 linked view，把個案餘額、心理師本週摘要及治療所本期額度改成必須切 tab 才能看到；可能改善負載，卻違反使用者已確認的「同頁開啟即見」需求。不得直接採用，須在授權後做前後測。
- **新反例 E**：以「隱藏欄位改善速度」推定隱藏 Billing 收費、個案資料即可防止其他人看到；隱藏是介面設定，不是分享權限。
- **新反例 F**：因為文件建議刪除無用頁／欄以減少負擔，就刪除舊期 Price Plan、歷史 Billing、Session 或原生公式依賴欄位；可能破壞跨期金額與法定紀錄且永久刪除不可復原。此建議不能作為本所清理授權。

## 交叉反證與未核准假設
效能與保密應分別驗證：減少同頁活躍 View 可能降低負載，但不代表真人高頻操作更快；View 隱藏、Filter、資料庫 Lock 均不等於最小權限。臨床／財務歷史正確性優先於以刪除方式追求速度。若日後獲准設計，須保留同頁直接呈現、核定期別隔離、歷史金額不可回溯變動等已確認需求，並以真人任務、載入秒數、不同角色實際權限及回復測試驗收；本輪**不設計、不實作**。

## 嚴格統計與缺口
- `NEW_SOURCE_CANDIDATE=1`；`PARTIAL_READ_NEW=1`；`EXISTING_SOURCE_TARGETED_INDEPENDENT_REREAD=1`；`COUNTEREXAMPLE=6`。
- `FULL_R1=0`；`FULL_R2_TO_R10=0`；`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`。依當期已核實狀態，累積嚴格完成 **0/10,000篇**，不是全部歷史來源的全面重算。
- **PENDING**：歷史 canonical/同文異址/跨語系去重；原始影片、圖片、互動；真人 Notion、手機、鍵盤、讀屏、角色權限、實際計時、Formula／Rollup／跨期交易、備份與復原。
- **NO SYSTEM WRITE**：未操作 Notion、GAS、Cloud Run、Session 或部署；研究記錄不能視為 Notion 功能驗收 PASS。雙軌研究可獨立並行；10,000×10 未達，未經使用者確認不得進入重新設計。
