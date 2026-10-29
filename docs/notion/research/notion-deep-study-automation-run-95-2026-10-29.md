# AUTO-95｜WCAG 2.2 狀態訊息與重要資料提交防錯：官方文獻部分閱讀（2026-10-29）
- Trace: `AUTO-95-20261029-1438-WCAG-STATUS-ERROR-PREVENTION`; execution lane: hourly automation; batch: W3C-STATUS-ERROR-PREVENTION; repository: `lily4318/clinic-notion-design`; target: research-only.
- 研究開始前讀取 main: `README.md`、根 `AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`、`docs/notion/research/README.md`、`docs/notion/research/audit-checklist-and-research-progress.md`、`docs/notion/research/research-to-implementation-matrix.md`、`docs/notion/long-term-goals.md`。查核當期來源索引全文與 GitHub code search 精確 URL，兩來源未見重複；全歷史逐檔/同文異址/跨語系語義去重仍待完成，故均僅為「新來源候選」。
- 查核日期：2026-10-29（臺灣）。W3C WCAG 2.2 規範來源 `https://www.w3.org/TR/WCAG22/`（Recommendation 頁面標示 2024-12-12），兩篇 Understanding 為 **informative、非規範性** 解說；原始 Understanding 發表日期未核實。W3C Recommendation 僅作交叉依據，不額外計一篇深讀。
- 本輪計量：新來源候選2；官方解說正文與選定例子、技巧部分閱讀2；獨立反例2組共6情境；完整獨立 R1=0、完整 R2–R10=0、10/10完成0篇；累積可核實 **0/10,000篇**。沒有以同一次閱讀冒充多遍。

## S01｜Understanding SC 4.1.3: Status Messages (Level AA)
- 原文 URL: https://www.w3.org/WAI/WCAG22/Understanding/status-messages.html
- canonical identity: `w3c:wcag22:understanding:4.1.3:status-messages`; title: Understanding Success Criterion 4.1.3: Status Messages; publisher: W3C WAI; author/date: 個別作者與首次發布日未核。
- 閱讀事件 `AUTO-95-20261029-1438-WCAG-STATUS-ERROR-PREVENTION-S01-R1-INTRO-INTENT-EXAMPLES-TECHNIQUES-PARTIAL`。查核主文約L20–L61（規則、目的、成功/錯誤/忙碌/進度案例）、L69–L103（非文字提示、狀態消失、元件變更與對話框排除、避免過度播報）、L104–L144（role=status、role=alert、live region、失敗模式）；與 WCAG Recommendation §4.1.3 交叉核對。
- 取證重點：(a) 對不移動焦點的狀態訊息，應可由輔助科技以角色/屬性辨識；(b) 查詢結果清單本身不等於「查到5筆」狀態訊息；(c) 僅把「3」更新可能失去「3筆」語境；(d) busy 提示消失不一定讓讀屏者知道已結束；(e) 取得焦點的對話框及 Tab/Accordion 展開不必直接視為此準則所稱 status message；(f) 本準則不強制憑空新增每一種狀態訊息。
- 反例 S01-CE1：Session 搜尋結果表更新而只顯示「2」的動態數字，對讀屏者可能缺乏「符合條件的會談2筆」語境；**設計假設**是完整狀態語義應可被理解，不能推論 Notion 原生 aria-atomic 已正確實作。
- 反例 S01-CE2：Billing 畫面顯示綠色「已完成」但僅代表本地表單驗證或資料列已建立，並不代表款項入帳、對帳或補助核准；成功文案須與實際持久化/業務階段分離。
- 反例 S01-CE3：每次欄位輸入、滑動、篩選都以高優先警示播報，會造成警示疲乏及讀屏干擾；重要錯誤、一般狀態、焦點切換應分層，不能把所有更新一律當成緊急警告。
- 尚未測試：Notion 原生資料庫篩選、Toast/提示是否存在/實際ARIA、鍵盤、螢幕閱讀器、手機、中文朗讀、真人操作；沒有任何 WCAG PASS 聲明。

## S02｜Understanding SC 3.3.4: Error Prevention (Legal, Financial, Data) (Level AA)
- 原文 URL: https://www.w3.org/WAI/WCAG22/Understanding/error-prevention-legal-financial-data.html
- canonical identity: `w3c:wcag22:understanding:3.3.4:error-prevention-legal-financial-data`; title: Understanding Success Criterion 3.3.4: Error Prevention (Legal, Financial, Data); publisher: W3C WAI; author/date: 個別作者與首次發布日未核。
- 閱讀事件 `AUTO-95-20261029-1438-WCAG-STATUS-ERROR-PREVENTION-S02-R1-CRITERION-INTENT-EXAMPLES-TECHNIQUES-PARTIAL`。查核約L21–L52（條文、意圖、購物/金融案例）、L53–L79（充分/建議技巧），交叉核對 Recommendation §3.3.4。
- 取證重點：涉及法律承諾、財務交易、使用者可控制資料的修改/刪除、測驗提交時，需至少有一項：可撤回、輸入錯誤檢查並可修正、提交前可檢視確認並修正；**不是三者全部必備**。解說明言重點是防止重大資料損失，不要求每次一般文件儲存都跳確認。刪除資料的恢復/確認、交易的檢視/取消等為例示技巧，非保證符合臺灣法規或 Notion 原生已具備。
- 反例 S02-CE1：每次新增或修改 Session 一般備註都跳不可略過的確認視窗，反而使高頻行政流程疲乏；規範並未要求每次一般儲存都確認。真正重大刪除/不可逆財務提交另評估風險。
- 反例 S02-CE2：歷史 Billing 金額、方案期別或收據被覆寫，僅靠「可以返回上一頁」或顯示一個確認按鈕，不能證明可回復正確歷史交易；需另驗證實際可撤回/修正機制、審計軌跡與原始值保留。
- 反例 S02-CE3：刪除補助用量資料前顯示確認對話框，但沒有檢查 Relation 依賴、備份及法定保留義務，仍可能造成不可回復或違規資料損失；WCAG防錯合規 ≠ 業務授權、保留年限或資料庫交易一致性。
- 尚未測試：Notion 原生回復/確認/版本歷史、權限角色、跨期方案計費、Billing/Session 實際資料完整性、法規與補助核准流程、真人鍵盤/讀屏；無任何系統修改。

## 交叉結論與嚴格反證
- 4.1.3 關心「狀態如何被無障礙感知」；3.3.4 關心「高風險提交如何避免重大錯誤」。兩者不能相互替代：一個可讀屏的成功提示不證明交易正確；一個有確認步驟的交易也不保證動態狀態可被輔助科技理解。
- 設計推論僅供未來評估：依風險區分一般編輯、資料刪除、財務提交；將「儲存成功」「收款入帳」「補助核准」分開；必要狀態訊息不以顏色/數字獨自承載。**不授權任何 Notion 或 GAS 修改**。
- 證據層級：W3C 規範/解說正文部分閱讀；無原圖/全部外鏈技巧逐篇完整閱讀、無互動、手機、鍵盤、讀屏、真人 Notion 操作、公式/效能/角色實測；不得將部分閱讀計為完整 R1，亦不得計成 R2–R10。
- 遵守本輪界線：僅 GitHub 研究文件與來源/決策/驗收進度；沒有修改 Notion 正式或 TEST 頁面、資料庫、View、Formula、Relation、權限、業務列，也沒有修改 GAS、Cloud Run、Session 或部署。10,000篇各10次尚未達成，**不得開始重新設計**。
