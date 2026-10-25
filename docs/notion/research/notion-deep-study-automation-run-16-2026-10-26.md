# Notion 深度學習｜AUTO-16（2026-10-26）

- **Trace**：`AUTO-16-20261026-0744`；路線：每小時自動研究；與手動研究並行但本次不重用同一次分析。
- **權威基準**：本次開始已讀 main 的 `README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`；另核對研究資料夾與 AUTO-01～15、MANUAL-01、證據批次02～04、十面向研究、研究索引的既有 URL。原 repo 只存匿名研究證據，不存個資。
- **研究方法**：實際開啟官方原文（2026-10-26），依本文各章節及 FAQ 研讀可取得的主要文字，逐篇建立一組獨立「可反駁假設→官方依據→反例→設計風險」；沒有將不同角度算作多次閱讀。未逐張檢查所有圖片、iframe、互動示範，未進行 Notion 實帳/手機/權限/效能測試，因此僅記 `TEXT_MAIN_READ+COUNTEREXAMPLE_R1`，**不記 `FULL_DEEP_PASS`**。原文發表/最後更新日期未核實。
- **URL 正規化**：`https://www.notion.com/help/<slug>`；同一文章的語系、錨點、參數與重新導向不另計。這三個 canonical slug 未見於上述當期研究清冊；若後續全域稽核發現更早來源，改記既有來源的補充閱讀，不能重複增加唯一來源數。

## AUTO16-S01｜Buttons（R1）
- **標題**：Buttons；**URL**：https://www.notion.com/help/buttons；**ID**：`notion-help:buttons`；**類型**：Notion 官方操作文件；**主題**：頁面按鈕、跨庫寫入、權限、通知、第三方連接。
- **閱讀範圍**：Who can use buttons?；Create a button；Button actions；Send mail to；Define variables；Mentions and formulas；Button errors；Edit/delete；FAQ。閱讀日 2026-10-26；R1=1 次主要文字研讀及首次反例，非完整深讀。
- **原文事實**：頁面按鈕所有方案可用但部分動作需付費；建立/點擊通常需要該頁 Full access 或 Can edit；修改另一個資料庫還需該目標資料庫編輯權。可一次執行多動作，含新增/編輯頁面、通知、寄 Gmail、Webhook、開啟頁面、確認視窗與變數。官方列出目標庫/欄位被刪或第三方連接失效造成既有按鈕失敗；用模板新增頁面時，模板欄位值可能覆蓋按鈕指定值。公式不能用於 Insert blocks、Open page/URL、Send Slack 等動作。
- **可反駁假設 H1**：「在首頁放一個按鈕，任何有閱讀權限的人就能安全完成政府補助核定並保證每次只寫一筆。」
- **反例／修正**：有閱讀權不一定可按；跨庫需目標權限；多步驟動作未被本文證明具有交易原子性或業務唯一約束，且模板欄位可覆蓋按鈕值。若使用者連按、權限不足、目標欄位變更，不能把畫面有按鈕當成核定已成功。應把按鈕視為 UI 動作而非補助核定真值/防重機制；本輪**不主張現有按鈕有缺陷**。
- **仍待驗**：實際操作、錯誤處理、執行順序/重試/冪等性、免費方案每種動作、真人權限、郵件傳送、所有插圖/示範。**狀態：TEXT_MAIN_READ + COUNTEREXAMPLE_R1；FULL_DEEP_PASS=NO**。

## AUTO16-S02｜Feed view（R1）
- **標題**：Feed view；**URL**：https://www.notion.com/help/feeds；**ID**：`notion-help:feeds`；**類型**：Notion 官方檢視文件；**主題**：卡片式資訊流、資料庫欄位可見性、行政資訊密度。
- **閱讀範圍**：Create feed view；Display & hide properties；全文主要文字。閱讀日 2026-10-26；R1=1 次主要文字研讀及首次反例，非完整深讀。
- **原文事實**：Feed 將資料庫頁面呈現為線性堆疊卡片，支援瀏覽、留言與查看頁面瀏覽數；可新增檢視，亦可調整可見屬性。
- **可反駁假設 H2**：「Feed 卡片較美觀，因此一定比表格更適合治療所本期、個案及心理師額度的同頁判讀。」
- **反例／修正**：當工作需要同時比較多列的剩餘額度、核定期、未知/已確認0與異常狀態，線性卡片需要更多捲動；若把必要欄位隱藏，操作人員可能無法立即判斷。Feed 官方定位偏向團隊更新，不是密集數值對照。故不能以美觀取代使用者既已確認的「同頁直顯、快速比較」；不據此修改現有 View。
- **仍待驗**：卡片在手機/桌機的實際密度、可見欄位數、載入時間、權限、所有示意圖片。**狀態：TEXT_MAIN_READ + COUNTEREXAMPLE_R1；FULL_DEEP_PASS=NO**。

## AUTO16-S03｜Archive pages（R1）
- **標題**：Archive pages；**URL**：https://www.notion.com/help/archive-pages；**ID**：`notion-help:archive-pages`；**類型**：Notion 官方資料生命週期文件；**主題**：封存、搜尋、父子頁、方案限制與刪除差異。
- **閱讀範圍**：What happens when a page is archived；How to archive；When to archive vs. deleting；Places to view；FAQs。閱讀日 2026-10-26；R1=1 次主要文字研讀及首次反例，非完整深讀。
- **原文事實**：Archive 為 beta、僅 Business/Enterprise；封存後仍可透過原連結、Library、搜尋篩選、資料庫 archived views 存取；封存父頁會連帶封存子頁，預設搜尋隱藏但不是刪除。官方將應保留歷史與連結的內容歸類適合封存，真正可丟棄的測試頁/重複頁則適合刪除。
- **可反駁假設 H3**：「將使用者已否決的舊補助頁封存，就等於真正刪除並已完成清理，且免費方案可直接使用。」
- **反例／修正**：Archive 不刪除、既有連結仍有效且有付費門檻；父頁封存影響子頁。封存可作歷史保留但**不能冒充使用者要求的實際清除**。若牽涉法定/財務歷史紀錄，應先查依賴和保留義務，不得直接批次刪除。本輪僅研究，不實際封存或刪除。
- **仍待驗**：beta 版本變動、各方案真實功能、父子頁/DB 操作、搜尋與分享權限、所有插圖。**狀態：TEXT_MAIN_READ + COUNTEREXAMPLE_R1；FULL_DEEP_PASS=NO**。

## 本輪計數與界線

| 項目 | 可稽核結果 |
|---|---:|
| 新 canonical URL（依本次已讀清冊暫列） | 3 |
| 新來源主要文字研讀 | 3 |
| 新來源首次獨立反例分析 | 3 |
| 既有來源獨立複讀 | 0 |
| 本輪完整10/10深讀通過 | 0 |
| 累積可證明10/10深讀通過 | **0／10,000** |

- **去重風險**：歷史 AUTO-13/14 曾重複計數，故不將各批次新增數簡單相加，不報未完成全域 URL 正規化稽核的累積唯一篇數。
- **無實作授權**：Notion 正式/TEST 頁面、資料庫、Data Source、View、Formula、Relation、Share/權限、業務列、GAS、Cloud Run、Session、部署均**零修改**；沒有開始重新設計。所有反例僅供後續設計評估，非現行系統故障證據。
- **GitHub 並行安全**：本批次使用獨立檔名與 trace；共享索引及決策/驗收紀錄需逐檔重新讀 main SHA、條件更新、寫後驗證。無法安全合併時不得覆蓋並行增量。
