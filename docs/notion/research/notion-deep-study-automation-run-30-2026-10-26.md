# Notion 深度學習 AUTO-30｜2026-10-26（僅研究）
- trace: `AUTO-30-20261026-2235-RESEARCH`；軌道：每小時自動研究，獨立於聊天室手動續作。
- 範圍：只讀公開文獻並記錄 GitHub；未操作 Notion、GAS、Cloud Run、Session、權限或任何業務資料；尚未獲准重新設計。
- 起始及寫入前：重新 Fetch main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、decision-log.md、acceptance-status.md 與研究清冊。逐一核對 sources.md 連結的36份研究文檔（首批、批次02–04、MANUAL-01、AUTO-01～29 等）對兩個新候選的 slug；36/36均未命中；GitHub code search未回傳結果，但不將搜尋零結果單獨視為全庫證明。另發現 Database settings 已在批次02 DS-023 登錄，Property access 已在首批 N07 與 AUTO-14-S03 登錄，因此均**不重算新來源**。本輪兩個新 canonical URL 依已核清冊暫列新增，未做完整全庫URL機器去重。
- 去重：NN/g canonical 去除 query、fragment、結尾斜線；語系與重複命中不另計。同一篇同次分析只計1次R1；已登錄來源之針對性閱讀不算完整R2。

## AUTO30-S01｜Drag–and–Drop: How to Design for Ease of Use
- URL：https://www.nngroup.com/articles/drag-drop/
- canonical ID：`nngroup:articles/drag-drop`；作者 Page Laubheimer；發表 2020-02-23；取得日期 2026-10-26。
- 證據：`R1_MAIN_TEXT_SECTIONS+COUNTEREXAMPLE_1`。實讀主要文字的四步拖曳流程、grabbability圖示、游標、grab/drop即時回饋、磁吸、鍵盤/讀屏可及性、觸控限制及結論（原頁約行40–145）。部分圖片只讀替代文字，影片未播放、未實際操作，不是完整深讀。
- 原文重點：拖曳可提高直接操作感，卻可能不精確、難以辨識可拖動區域，且在觸控螢幕缺乏hover；應在放下前預告結果、提供替代操作及鍵盤可及性。
- 先驗假設：把治療所表格與任務做成「直接拖曳」比表單/選單更快、更直覺。
- **反例1（業務副作用）**：若在 Calendar/Board 拖動項目會改變日期或狀態，使用者可能把視覺整理誤認為不修改資料；需在日後合法設計階段查證 Notion 原生操作實際效果，不能憑此文章認定已安全。
- **反例2（跨裝置）**：桌機的抓取把手與游標提示在手機上不一定可見；手指遮擋與滑動/拖曳衝突，若高風險補助期別修改只能靠拖曳會增加錯誤機會。
- **反例3（可及性）**：只提供滑鼠拖曳而無精確的選單/鍵盤替代，會排除鍵盤及輔助科技使用者；但原生Notion能否提供相應替代需實測。
- 推論：對重要日期/核定期別變動，優先要求可見變更結果與低風險替代路徑；此為研究假說，不是使用者核可的改版方案。

## AUTO30-S02｜Designing for Long Waits and Interruptions
- URL：https://www.nngroup.com/articles/designing-for-waits-and-interruptions/
- canonical ID：`nngroup:articles/designing-for-waits-and-interruptions`；作者 Kate Kaplan；發表 2021-09-05；取得日期 2026-10-26。
- 證據：`R1_MAIN_TEXT_ALL_FIVE_GUIDELINES+COUNTEREXAMPLE_1`。實讀5項主要文字：進度與剩餘步驟、成功訊息帶上下文、使用者備註、最近歷史入口、背景作業及結論（原頁約行40–148）；未逐張看圖、未操作外部例子，非完整深讀。
- 原文重點：長時間等待或被打斷後，明確狀態、結果摘要、原地備註、最近工作入口與背景處理可降低重新進入工作流程的成本。
- 先驗假設：在治療所首頁放大量進度卡片、歷史清單與成功訊息，能改善所有行政操作。
- **反例1（狀態真值）**：Notion頁面載入完成，不等於補助資料已完成核對；「處理完成」需分辨畫面載入、資料同步、人工資格確認及核定額度，不能用同一成功訊息。
- **反例2（首屏負擔）**：大量進度訊息、歷史紀錄與備註會佔據使用者要求的同頁直見空間；應按工作階段/長任務才提供，不能把所有 UX 建議堆進首頁。
- **反例3（背景作業能力）**：原文建議背景運算，不代表 Notion 原生公式、資料庫自動化或外部連線有可供追蹤的背景任務/原子復原；須實際確認方案、權限與失敗回報。
- 推論：在有證據的長時間等待或中斷流程才評估最小必要狀態回饋；真人耗時與中斷頻率尚未測量。

## AUTO30-R01｜既有 Notion Property access 針對性複讀
- URL：https://www.notion.com/help/database-property-access
- canonical ID：`notion-help:database-property-access`；既有 N07 / AUTO-14-S03；本輪只記 `TARGETED_REVISIT_ROLLBACK_SEMANTICS`，**不是**新URL，也**不是**完整R2。
- 新反證：官方「How access rules interact」明言還原較舊資料庫版本仍保留當前 property access 規則；因此「資料庫版本回復＝權限也回復」的假設錯誤。任何未來權限相關回復計畫須另行驗證分享設定與欄位規則，而非僅憑內容版本還原。
- 其他限制：Business/Enterprise 才有欄權限；未在本所帳戶實測，亦未變更任何權限。

## 可稽核計數與限制
| 指標 | 本輪 |
|---|---:|
| 新增候選 canonical 來源（已查清冊去重） | 2 |
| 新來源主要文字 R1 | 2 |
| 首次獨立反例分析 | 2 |
| 舊來源針對性複讀 | 1 |
| 本輪達成逐篇10次完整深讀 | 0 |
| 累積可證10/10完成 | **0／10,000篇** |

- 圖片/影片/互動示範、Notion真實角色/權限/手機、政府方案計算、真人UX、效能皆未實測；嚴格 FULL_DEEP_PASS=0。
- 此文件只記研究，不授權變更 Notion 正式/TEST、資料庫、View、Formula、Relation、權限、正式 GAS/Cloud Run/Session，也不開始重新設計。