# Notion 深度學習｜AUTO-47｜2026-10-27（研究限定；未修改 Notion）

- 執行標記：`AUTO-47-20261027-1436-RESEARCH`；台灣時間 2026-10-27 約14:36；自動研究軌，與聊天手動續作獨立。
- 範圍：公開可讀的 UX 原文、GitHub 規範與研究清冊；只允許 GitHub 研究及進度紀錄。**Notion、GAS、Cloud Run、正式 Session 與部署零寫入。**
- 開始及寫入前讀取 main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、sources.md、decision-log.md、acceptance-status.md、research/README.md。依 sources.md 解析並實際逐份 Fetch 53/53 份已索引研究 Markdown，針對兩篇 canonical URL／標題比對，均無命中；sources.md 也無命中。GitHub code search 非完整保證；**其他未索引路徑、不同網址相同文章及外部鏡像的全庫精確去重仍未完成**。
- 嚴格計量：新增已查索引去重的候選來源 **2篇**；本輪各一次**主要正文文字閱讀**與首次獨立反例分析；既有來源完整複讀 **0**；完整 R1–R10 深讀達標新增 **0**，累積 `FULL_DEEP_PASS_10_OF_10` **0／10,000篇**。不把多章節、不同分析角度或搜尋命中當成多次閱讀。

## AUTO47-S01｜Wizards: Definition and Design Recommendations

- 原始 URL：https://www.nngroup.com/articles/wizards/
- Canonical：`nngroup:articles/wizards`；Raluca Budiu，Nielsen Norman Group，2017-06-25；閱讀日期2026-10-27。
- 獨立軌跡：`AUTO47-S01-R1-MAIN-TEXT-C1`；主要正文依序閱讀「What Is a Wizard?」「Dynamic Form or Wizard?」「Wizards Show Less Information on the Page」「Shortest Path for Each User」「Disadvantages of Wizards」「Recommendations for Designing Usable Wizards」（八項）及結論；閱讀原文圖說，未逐張打開原始圖片。
- 原文重點：Wizard 適合低頻、陌生或需依先前答案分支的流程，減少同頁不相關欄位；高頻專業資料輸入卻可能因更多點擊、跨步比較不便、遮蔽背景資訊及中途退出無法恢復而更慢。作者建議顯示步驟位置、清楚前後操作、允許中斷保存、單步自足，並審慎使用上次選擇作預設。
- **新反例 C1（常態工作 vs. 低頻設定）**：治療所每日大量建立／核對 Session、補登歷史收費資料，如果強迫行政人員逐步經過「選個案→選方案→確認期別→確認金額」Wizard，可能比同頁直接顯示與比較更慢，也違背使用者已確認的「同類資料同頁、開啟即見」。然而低頻新增核定期別或初次設定，分步檢查可能降低遺漏；不能一概否定 Wizard。
- **新反例 C2（沿用上次值的風險）**：原文建議可考慮重用上次選擇，但對跨年或補登歷史 Session，預設上次方案期別可能把現行金額套進歷史資料。若要利用預設，須先由服務日期與有效期別核對，而非以近期操作取代業務真值。這只是待驗證假說，不是已授權設計。
- **反證條件**：若真實行政流程低頻且不同方案有大量條件分支，或新進人員錯誤率高於多步操作成本，Wizard 可能更合適；須以不同角色實測錯誤率、耗時、中斷復原與期別正確性。
- **限制**：只核對主要正文與圖說；未打開所有原始圖、未進行真人 Notion 操作／手機／權限／效能測試；Notion 原生是否能實作完整分支、儲存與回復未核實，故不是完整深讀 R1 PASS。

## AUTO47-S02｜Reset and Cancel Buttons

- 原始 URL：https://www.nngroup.com/articles/reset-and-cancel-buttons/
- Canonical：`nngroup:articles/reset-and-cancel-buttons`；Jakob Nielsen，Nielsen Norman Group，2000-04-15；閱讀日期2026-10-27。**年代較久，適用性須依現代產品重新驗證**。
- 獨立軌跡：`AUTO47-S02-R1-MAIN-TEXT-C1`；閱讀全文「Reset: Don't Use」「Make All Form Entries Undoable」「Exception: Use Reset for Repeated Form-Filling and for Revert-to-Default」「Cancel: Use Sparingly」「Remove Button in Shopping Carts」「Clarification: When Cancel Is Necessary」與開頭使用者控制／Undo 論述。
- 原文重點：一般表單的 Reset 容易誤觸、清掉輸入並增加決策負擔；例外是重複填寫且各次差異大，或將複雜設定回復安全預設。Cancel 在多步操作或可能已提交部分變更時仍有價值；瀏覽器返回並不保證撤回已執行的操作。作者區分 Cancel／Reset 與停止耗時動作。
- **新反例 C1（清空欄位不等於撤銷業務紀錄）**：治療所若將「重設」放在收費或補助確認附近，使用者可能誤以為只清空本次表單，實際卻誤刪歷史資料。反過來，禁止所有清除也可能阻礙重複輸入錯誤的復原。應明確區分「未儲存表單的清除」「取消未提交操作」「已儲存資料的更正」及需要正式稽核的歷史帳務變更。
- **新反例 C2（返回≠回滾）**：按下 Notion Database button、跨來源自動化或資料列更新後，使用者按返回或關閉頁面，不保證變更回復。AUTO-46 已指出按鈕確認與自動化鏈不是交易原子性證據；不能把 Cancel／Back 視為完整交易撤銷，也不能把 GitHub 備份視為 Notion 真實業務紀錄的撤銷能力。
- **反證條件**：若在完全隔離、無業務資料的設定表單中反覆重設至安全預設能顯著減少錯誤，保留 Reset 可能合理；但須實測操作語意、影響範圍與可回復性。2000 年的網頁返回行為不應不加驗證直接推論 2026 Notion。
- **限制**：此文主要為文字，已讀主要全文；未重查其連結的其他研究、現代介面或 Notion 原生操作，不計完整深讀。

## 跨篇校正與硬界線

1. Wizard 的「可返回上一步」和表單 Cancel／Reset 都是介面概念，**不是資料庫交易回滾**；若已寫入 Session／Price Plan／用量，應獨立確認資料真值、權限、歷史證據及更正程序。
2. 兩篇分別說明「分步減少單頁負擔」與「不必要控制增加認知成本」，彼此並不矛盾；適用性取決於**低頻複雜設定**或**高頻同頁核對**的任務差異。
3. 與使用者已確認「同頁直顯、方案期別與歷史金額安全」相符的部分僅列為研究假說，**不代表決定新增 Wizard、Reset、Cancel 或按鈕**。
4. 原始圖片、外部研究全文、實際 Notion 操作、角色權限、手機、載入效能、Formula、跨期補助與歷史金額均未驗證；無任何本所業務 PASS。
5. **NO NOTION / SYSTEM WRITE**：只建立本 GitHub 研究紀錄並同步研究清冊、決策及驗收進度；未改任何 Notion 頁、DB、Data Source、View、Formula、Relation、權限、個案或財務資料，未改 GAS、Cloud Run、Session、部署；未達10,000篇×10次及使用者確認，不開始 Notion 重新設計。
