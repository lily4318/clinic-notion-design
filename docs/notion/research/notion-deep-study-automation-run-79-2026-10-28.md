# AUTO-79｜Notion 深度學習：非預期故障與計畫性停用的介面語義（2026-10-28）

Trace: `AUTO-79-20261028-2244-RESEARCH`｜自動研究｜僅公開文獻閱讀＋GitHub研究紀錄｜NO NOTION/SYSTEM WRITE

## 本輪基準、來源與去重
- 研究開始及新建檔案前重新讀取 main：根 README/AGENTS、docs/system/source-of-truth.md、docs/notion/AGENTS.md、sources.md、decision-log.md、acceptance-status.md、research/README.md、audit-checklist-and-research-progress.md、research-to-implementation-matrix.md；遵守使用者 2026-10-25 雙軌並行及只研究、不改Notion的界線。
- 已在 sources.md 全文、三份主要研究清冊與 GitHub code search 查兩個完整 slug，均未發現；但未能完成全部歷史 AUTO 檔逐篇全文及跨語系/同文異址語義去重，故僅 `NEW_CANDIDATE`，不宣稱已全庫唯一。先排除本輪最初選中的 Check answers、Error summary、Error message：sources.md 已分別在 AUTO-53、AUTO-51、AUTO-58 登記，**本輪未重算、未計為獨立複讀**。
- 來源維護者：GOV.UK Design System team；可讀網頁檢索日 2026-10-28；頁面未核實首發或最後編修日，不能推測。兩篇均屬公眾服務設計指南，不是 Notion 原生功能規格或臺灣法規。

## AUTO79-S01｜Service unavailable pages — GOV.UK Design System
- URL: https://design-system.service.gov.uk/patterns/service-unavailable-pages/
- Canonical ID: `govuk-design-system:patterns/service-unavailable-pages`
- Reading event: `AUTO79-S01-R1-MAIN-TEXT-20261028`；官方可讀頁正文約L51–L516，閱讀適用時機、How it works、一般頁、已知恢復時間、替代服務、季節性關閉、永久停用與研究限制，並核對HTML/Nunjucks文字範例。**文字主體一次，不是完整R1**；未開獨立互動預覽、原始圖片、鍵盤/讀屏/手機。
- 可核來源：此頁用於「有意關閉」服務（例如預定停用、永久關閉），與非預期故障分流；說明何時可恢復、已填資料是否保留、聯絡/替代管道。官方頁範例同時有「已保存30天」與「未保存、需重填」兩種相反狀態，**是不同示例情境，不是系統自動保存保證**。研究曾測5位使用者，仍列需更多研究。
- 反例1／假停用：Notion單一Billing View無法載入，若顯示「整個治療所系統已停用」，可能誤導仍可使用的Session或其他資料源；**反證**：停用範圍、受影響作業與替代途徑須由實際監測與權威狀態核對，不能從單一頁面失敗推論全域停用。
- 反例2／資料保留誤告：未驗證Notion自動儲存、離線同步或後端提交狀態就寫「資料已保存30天」，可能使人員以為收款已入帳或Session紀錄已提交；**反證**：只有取得交易/同步成功的可核實證據，才可說明保存範圍及期限，不能照抄UK示例。
- 反例3／期別誤套：把政府補助某期結束寫成「整個服務永久關閉」，可能遮蔽其他核定期別或自費方案；**反證**：業務方案核定期間、可預約日期、額度與平台可用性是不同狀態，不可混用。

## AUTO79-S02｜There is a problem with the service pages — GOV.UK Design System
- URL: https://design-system.service.gov.uk/patterns/problem-with-the-service-pages/
- Canonical ID: `govuk-design-system:patterns/problem-with-the-service-pages`
- Reading event: `AUTO79-S02-R1-MAIN-TEXT-20261028`；官方可讀頁正文約L51–L319，閱讀意外故障、短期處理、資料保留、替代管道、HTML/Nunjucks範例、研究缺口；**主要文字一次，非完整R1**。未執行實際錯誤注入、Notion斷線/復原、讀屏/手機。
- 可核來源：用於「非預期故障」，須記錄錯誤、盡快修復，若無法短時間修復才轉為有意停用的頁面；簡潔告知重試與聯絡方式、當前輸入是否保留。示例有「已保存30天」與「未保存」兩種情境，需依真實服務狀態決定。來源明言只測5位使用者且仍有研究缺口。
- 反例1／重試重複扣款：Billing已成功寫入但前端回應逾時，畫面若僅說「請再試一次」，重試可能重複新增付款或占用額度；**反證**：使用者提示不能取代交易冪等、回讀核對與重試前檢查；Notion原生是否具備必要控制未測，不可假定。
- 反例2／假定暫存成功：在Notion或外部同步服務失敗時，若一律聲稱「已儲存」，可能掩蓋尚未成功的資料列/附件；**反證**：故障提示必須區分已確認寫入、未知、失敗，並說明安全下一步，不能將未知當成功或當零。
- 反例3／誤判使用者責任：方案期別未核准、角色權限不足、欄位輸入格式錯誤與真正服務端故障不是同一問題；**反證**：分流處理並避免用通用故障頁隱藏實際授權/資格狀態，不能讓使用者無限重試。

## 交叉研究與下一輪可驗證問題
- **故障（unexpected）≠計畫性停用（intentional）≠業務方案失效（eligibility/period）≠交易結果未知（unknown commit）**。這是跨來源與本專案情境推論，並非Notion已提供此分類、或使用者已核准新UI。
- 兩篇共通要求說明輸入資料保存與恢復方式，但官方示例並非產品承諾。若未來取得設計授權，需先唯讀取得實際Notion/GAS資料流與失敗模式，再研究狀態告知與重試；不得在本研究階段改介面或新增警示。
- 來源限制：兩篇均為英國政府服務指南，示例中的聯絡電話、恢復時間、30天保存期限不能移植；無法從文件推論Notion離線/同步/權限或臨床資料保護合規性。

## 嚴格計量與安全
- `NEW_CANDIDATE=2`；`MAIN_TEXT_READ=2`；`INDEPENDENT_COUNTEREXAMPLE_GROUPS=2`（6情境）；`FULL_INDEPENDENT_REREAD_EXISTING=0`；`FULL_R1=0`；`FULL_R2_TO_R10=0`；`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`；累積可核實 `FULL_DEEP_PASS_10_OF_10=0/10000`。
- 尚未驗證：全部歷史檔精確/語義去重、原始圖與獨立互動示例、鍵盤/讀屏/手機、Notion正式/TEST即時Schema、權限、真實Billing/Session/政府方案期別/Formula、故障復原、資料一致性、真人UX及效能。
- **NO NOTION/SYSTEM WRITE**：本輪只進行公開資料研究與GitHub進度記錄，不修改Notion正式或TEST頁、DB、View、Formula、Relation、權限或業務資料；不修改正式GAS、Cloud Run、Session或部署；10,000篇各10次未完成，未開始Notion重新設計，手動與自動研究維持獨立並行。
