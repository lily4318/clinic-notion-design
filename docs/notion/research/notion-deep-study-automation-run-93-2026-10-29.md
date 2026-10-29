# AUTO-93｜Notion 深度學習：備份、刪除、版本回復的可恢復性界線（2026-10-29）

執行軌跡：`AUTO-93-20261029-1245-BACKUP-DELETE-RESTORE`；Asia/Taipei 2026-10-29 約12:45。**僅公開官方文件研究及 GitHub 研究進度寫入；沒有修改 Notion 正式/TEST 頁面、資料庫、View、Formula、Relation、權限、業務資料，也沒有修改 GAS、Cloud Run、Session 或部署。**

## 前置、去重與證據層級
- 開始先讀 main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md、docs/notion/research/README.md 與 AUTO-92 研究紀錄，核對 10,000篇×10次要求與研究/正式系統隔離；寫入前再 Fetch 最新 SHA。
- 兩個 URL 在當時最新 sources.md 全文精確匹配均為0；研究目錄所有歷史文件尚未逐一全文語義比對，跨語言鏡像及同文異址也未完成，故**僅列新來源候選2篇**，不聲稱全域唯一。
- 可讀官方 HTML 主要文字、FAQ、相關段落與對應回復限制已查核；沒有完整檢視全部圖片、原始互動、帳號操作、手機/鍵盤/讀屏、恢復演練，因此兩篇均為**部分文字閱讀**，嚴格完整 R1=0。
- 發布日期未在所讀正文確認；取證日 2026-10-29，勿將網站版權2026當發表日期。

## S01｜Back up your data：匯出不等於完整可回復的系統備份
- 標題：**Back up your data | Notion Help**；原文：https://www.notion.com/help/back-up-your-data ；canonical ID `notion-help:back-up-your-data`；作者/維護者 Notion Help；閱讀事件 `AUTO-93-20261029-1245-BACKUP-DELETE-RESTORE-S01-R1-EXPORT-RESTORE-FAQ-PARTIAL`。
- 原文取證：網頁 L107–186。L120–150：可匯出 HTML/Markdown/CSV、附件；匯出者無權查看的私人頁面不包含，某些 Teamspace 設定也可能排除；工作區匯出只在桌面/網頁端操作；郵件下載連結7日到期；**重新上傳匯出檔不能立即重建工作區**。L131 說工作區 PDF 匯出在 2026-08-31 前分批下架，此為官方文件描述的排程，未以本所帳號實測是否完成。L151–163：垃圾桶預設30日、頁面版本回復及支援復原途徑。L170–186：大型工作區匯出可能失敗，官方提供分批匯出替代；原生定時自動備份當時FAQ稱尚未提供。
- 反例 A1【下載 CSV 就能完整還原 Billing、Session、Relation、Formula、View 與角色權限】：官方明言匯出不可立即重建工作區；資料可攜性 ≠ 原生結構、連結與權限的可恢復性。跨期金額、歷史快照的正確性須另核。
- 反例 A2【有雲端每分鐘備份，所以不用測回復、也能隨時精準回到任何時間點】：官方內部備份不等於客戶可指定時間的全工作區還原點；仍要有明確可用的垃圾桶、版本、匯出及回復測試，不能承諾 RPO/RTO。
- 反例 A3【全工作區匯出一定包含所有個案頁與附件且可無限期下載】：私人頁/Teamspace 限制可能排除內容，連結7天失效，且大工作區匯出可能出錯；不能把按下匯出當作完成備份驗收。
- 尚未查核：實際帳號權限/方案、匯出包內容與重新匯入結果、附件與關聯完整性、資安保存合規、回復所需時間；**不要求或執行任何正式資料匯出**。

## S02｜Delete & restore content：頁面/屬性/資料庫的回復語義不同
- 標題：**Delete & restore content | Notion Help**；原文：https://www.notion.com/help/duplicate-delete-and-restore-content ；canonical ID `notion-help:duplicate-delete-and-restore-content`；維護者 Notion Help；閱讀事件 `AUTO-93-20261029-1245-BACKUP-DELETE-RESTORE-S02-R1-TRASH-VERSION-DB-PROPERTIES-PARTIAL`。
- 原文取證：網頁 L117–170 為區塊與頁面刪除、垃圾桶預設30日；L171–205 為 Archive（Beta、Business/Enterprise，隱藏搜尋但連結仍可存取，**不是刪除**）；L207–264 為版本紀錄（Free 7天、Plus 30天、Business 90天、Enterprise不限天數，非Enterprise較少細節；版本歷史只顯示主要變動，不能保證每項變更都記錄）；L253–264 明言恢復資料庫可恢復資料庫頁及其屬性，但**資料庫頁內文不會隨之恢復**，必須逐頁另行恢復，且可能影響 View；L276–296 為已刪除欄位可在 Deleted Properties 復原，從該區永久刪除則無法復原。
- 反例 B1【將已否決的舊青壯額度 View/頁面 Archive 或 Toggle 收起來就算清除】：Archive 仍保留可存取內容與連結；與使用者要求「真正移除」不同。此為研究反證，不授權本輪刪除任何實際資料。
- 反例 B2【恢復整個資料庫版本會連同每筆個案頁正文、所有 View 與歷史關聯完全回到原狀】：官方明示資料庫頁正文需要逐頁復原，View 可能受影響，版本歷史也不是逐項完整稽核；不能以資料庫回復成功冒稱個案內容/權限/交易狀態皆PASS。
- 反例 B3【刪掉欄位後，永久清除也可以隨時按一下還原】：Deleted Properties 有可恢復與永久刪除兩階段，永久刪除不能直接復原；對仍被公式/Relation/歷史報表引用的欄位，先查依賴與備份，不因名稱舊而擅刪。
- 尚未查核：本所方案層級、實際版本差異、欄位回復後 Formula/Rollup/Relation 與 View 依賴、權限繼承、保留期、真人操作；**不操作垃圾桶、不恢復/刪除資料**。

## 輔助交叉核對（不另計新來源/閱讀篇數）
- https://www.notion.com/help/custom-data-retention-settings：官方稱自訂 Trash 與刪除後保留期僅 Enterprise，預設各30日，可依管理權限設定；企業管理員恢復原位置可能重新開放原權限。僅作旁證，未計本輪第3篇。
- https://trust.notion.com/：官方 Trust Center 文字區分服務端備份與客戶可自行指定時點的 Workspace restore point，並提醒匯出不會重建原權限/設定/完整組態。此處只作交叉核對，未計新來源。
- 交叉結論：**匯出可攜性、服務端備份、頁面垃圾桶、版本歷史、欄位回復、完整業務恢復是六個不同概念**。不以任何單一機制推論跨期收費、個案保密或業務回復已通過。

## 嚴格計量與安全邊界
- `NEW_SOURCE_CANDIDATE=2`、`PARTIAL_TEXT_READ=2`、`COUNTEREXAMPLE=6`、`FULL_R1=0`、`FULL_R2_TO_R10=0`、`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`，累積可核實完成 **0／10,000篇**。同URL、同一分析不重計；第三方/輔助官方連結不冒充新篇。
- **NOT_TESTED**：所有圖片、完整互動、手機、鍵盤、讀屏、真人 Notion、正式方案與權限、真正的匯出/回復、資料一致性、效能、歷史交易與合規。
- **RESEARCH ONLY / NO NOTION OR DEPLOYMENT WRITE**：未達10,000篇各10次可稽核深讀，不進入 Notion 重新設計；自動排程與聊天手動續作維持獨立並行。
