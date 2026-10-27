# Notion 深度學習｜AUTO-46｜2026-10-27（公開官方文件複讀；非Notion變更）

- 唯一執行軌跡：`AUTO-46-20261027-1339-RESEARCH`；2026-10-27 台灣時間；自動研究軌道，與手動「繼續」獨立。
- 範圍：只讀 GitHub 最新 main 規範、來源索引與可取得的官方原文；僅寫 GitHub 研究／進度。**沒有存取或修改 Notion 正式／TEST 業務資料，沒有操作 GAS、Cloud Run、Session 或部署。**
- 開始前 Fetch：根 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、decision-log.md、acceptance-status.md、research/README.md；另核對 AUTO-45、MANUAL-01、AUTO-05、AUTO-28、batch-02/03及十面向研究清冊。sources.md可解析到52個 research 文件連結；嘗試批量逐檔取得時遇工具呼叫上限，**不能宣稱52/52完整重新掃描**。本輪兩篇均已有明確歷史登錄，故不計新URL。
- 去重：`https://www.notion.com/help/database-buttons` 在十面向研究 N12 及 batch-03 已登錄；`https://www.notion.com/help/database-automations` 在 MANUAL-01-02 已登錄。語系鏡像不重算新篇。兩篇皆屬**既有來源本輪獨立針對性複讀**，而非嚴格完整第二遍。
- 計量：新 canonical URL **0**；主要文字針對性複讀 **2**；新的交叉反證 **2組**；`FULL_DEEP_PASS_10_OF_10` 新增 **0**，累積可稽核完成仍 **0／10,000篇**。

## AUTO46-R01｜Database buttons（既有N12；本輪針對性複讀）

- 官方原文：https://www.notion.com/help/database-buttons
- Canonical：`notion-help:database-buttons`；標題 Database buttons；Notion Help，原文未標示確定發布日期，查閱2026-10-27。
- 獨立閱讀軌跡：`AUTO46-R01-TARGETED-REREAD-TEXT-CONFIRMATION-PERMISSION-C1`。
- 實際重讀官方可取得正文的「Who can use」「Create」「Database button actions」「Send mail」「Define variables」「Mentions and formulas」「Errors」：有 Full access／Can edit 才能建立或編輯 DB 按鈕；Full access／Can edit／Can edit content 均可點擊；但編輯目標頁仍需有目標權限。按鈕支援 Edit property、Add page、Edit pages in、Show confirmation、Open page/URL、通知與變數。Gmail／Webhook 等動作另有付費限制。公式只能用於動作，不能用於觸發；部分動作不支援公式。缺少資料庫／欄位或外部連線失效可能使動作出錯。
- **新交叉反例 C1（修正先前能力不確定描述）**：AUTO-40 只記「不能假設 Notion 原生能自訂確認框」。此篇官方現行正文**明確列有 Show confirmation 按鈕動作**，故「完全沒有原生確認能力」不是可接受結論；但不能推論所有操作／資料庫更新都有可自訂確認、或確認可檢驗補助資格。若行政人員點「確認」卻未檢查服務日期、Price Plan 期別、人工資格證據，仍可能把錯價寫入歷史 Session。確認視窗是防誤觸而非業務審核或不可逆動作的回滾保證。
- **新交叉反例 C2（權限鏈）**：具有 Can edit content 的人可點按鈕，不代表能安全執行跨資料庫的所有動作；若目標來源受限，按鈕可能失敗，若具寫入權又可能影響多筆。不得以「能點」或「顯示確認」當作成功交易、角色隔離、單一方案期別範圍或去重保障。
- 限制：只重新閱讀主要文字及圖說，未逐張查看原圖、未測免費/付費工作區、不同角色或點擊後失敗/部分完成情況；本輪不算完整 `DEEP_PASS_R2`。

## AUTO46-R02｜Database automations（既有MANUAL-01-02；本輪針對性複讀）

- 官方原文：https://www.notion.com/help/database-automations
- Canonical：`notion-help:database-automations`；標題 Database automations；Notion Help，原文未標示確定發布日期，查閱2026-10-27。
- 獨立閱讀軌跡：`AUTO46-R02-TARGETED-REREAD-TEXT-TRIGGER-ERROR-C1`。
- 實際重讀「Who can use」「Triggers」「Actions」「Variables」「Errors」「FAQs」：一般 DB automation 需付費與 full access；Free Slack 例外與 Slack 動作付費描述在同篇仍有張力，保留未解。多個 edited 條件若要同時成立，約需在3秒窗口內發生。Automation **不能由另一 automation 觸發**，但使用者點擊 Button action 可以觸發 automation。Automation 可針對全庫或特定 View；View 篩選變更會改變作用集合，觸發後不符合 View 篩選亦可能不執行。公式/Webhook 錯誤可能不通知，出錯暫停後須手動恢復；空日期 dateAdd 及 Locked database 也列為風險。
- **新交叉反例 C1（人員按鈕→自動化的安全錯覺）**：原生 Button 允許一鍵修改欄位，並可能觸發後續 DB automation；但 automation 再引發另一 automation 的鏈條不會照預期連續執行。治療所若把「補助待核→按鈕標確認→後續計數」設想成原子流程，可能只完成前段，讓工作台顯示確認但計數未同步；也可能因 View 期別篩選變更導致原本符合的歷史紀錄不被處理。官方功能描述**沒有提供交易原子性、完整回滾或業務一致性保證**。
- **新交叉反例 C2（錯誤可觀測性）**：未收到錯誤通知不代表成功；官方明示某些公式/Webhook錯誤可能無通知。若把「沒有告警」等同「週回報／補助用量已更新」，可能漏記。另一方面，對每次編輯都設強制確認或通知也可能造成疲勞。須區分操作成功、資料真值、稽核與必要告警，不能以 UI 便捷性取代。
- 限制：只重新閱讀主要文字及圖說，未觀看頁首影片、未操作觸發器、未實際測試 Free/付費權益與角色、3秒窗口、View改動或錯誤恢復；本輪不算完整 `DEEP_PASS_R2`。

## 跨來源校正、保留假說與硬界線

1. 與 AUTO-40「確認對話框」研究校正：**Notion Database button 確有官方記載的 Show confirmation 動作**，但不是任意資料庫編輯都自動有確認，也不等於資格核准或原子回復。應將早先「原生能力未驗」細分為「文件能力已確認／本所可用性與實帳行為未驗」。
2. 與 MANUAL-01 的來源內部衝突保持一致：Free Slack automation 的例外描述與 Slack 動作方案限制仍需官方/實帳核驗，不能選擇性聲稱免費功能 PASS。
3. 這些是**研究推論與反例**，不是提出或授權實作按鈕、自動化、View、欄位或改版。尤其現行個案×方案期別用量、心理師方案額度、歷史 Session 金額不得因本輪研究更動。
4. 尚未逐張驗證原圖、影音、互動、真人操作、手機、權限、速度、歷史金額／補助公式真值；全庫跨路徑及同文異址去重未完成。僅可稱「既有來源的兩次針對性文字複讀＋兩組新交叉反例」，不能稱完整深讀或第二次全文。
5. **NO NOTION / SYSTEM WRITE**：本輪僅 GitHub 研究與進度記錄，未修改 Notion 頁、DB、Data Source、View、Formula、Relation、權限、個案/財務資料或 GAS／Cloud Run／Session／部署。未達10,000篇各10次及使用者確認，不進入 Notion 重新設計。
