# Notion 深度學習｜AUTO-42（2026-10-27；研究取證，非 Notion 實作）

- 獨立執行標記：`AUTO-42-20261027-0944-RESEARCH`；台灣時間 2026-10-27 09:44 起本輪研究。
- 授權：只讀公開研究、只寫 GitHub 研究與進度；不修改 Notion 正式/TEST、資料庫、View、Formula、Relation、權限、業務資料、GAS、Cloud Run、Session、部署。
- 開始前已重新讀 main：根 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md；讀 research/README.md、AUTO-41 紀錄，並逐檔讀取當期 research 目錄 53/53 份 Markdown 進行兩個候選 slug 比對。sources.md 及 53 份研究文件均未命中 `listbox-dropdown`、`info-tips-bad`。這僅證明**已查索引與研究目錄**無相同 canonical slug；未對其他路徑與不同網址相同文章做全庫語意去重。
- 來源取得：兩篇 NN/g 文章的可讀公開 HTML，依標題、主要段落、比較表、結論與可見圖片說明各做**一次**獨立主要文字閱讀及一次新反例分析；未逐張開啟原圖、影片、操作原型或進行真人測試。以下標記 `R1_MAIN_TEXT+C1` **不等於完整深讀 R1**，更不等於十次完整深讀。

## AUTO42-S01｜Listboxes vs. Dropdown Lists

- URL：https://www.nngroup.com/articles/listbox-dropdown/
- Canonical：`nngroup:articles/listbox-dropdown`；Anna Kaley；2020-04-12；UX / 表單選擇控制。
- 閱讀軌跡：`AUTO42-S01-R1-MAIN-TEXT-C1`；主文七段落/分類表已查：Listboxes（單選、多選、核取方塊、多選雙欄）、Dropdown Lists、兩者實例、listbox優缺點、dropdown優缺點、選擇比較矩陣、Conclusion。圖說可見，但原始圖片未逐張核驗。
- 核心證據：listbox 讓多個選項直接可見、可支援多選但占空間；dropdown 緊湊、常用於單選，但會隱藏其他選項，過長易誤操作；原文建議依選項數、空間、是否多選、是否需要比較及預設值正當性選控制，並把日期/數字按序排列。文章中的「5/15個選項」是一般 UX 判斷框架，**非**治療所經實測的最佳數字。
- C1 新反例：收費方案名稱固定而核定期別逐年變動，若把「最新期別」預設為選中值，歷史 Session 編輯時可能不經察覺地套用新價格；但一口氣把所有歷史期別攤成可見清單，也會增加選錯與閱讀負擔。選項合法 ≠ 按服務日適用；**歷史金額保存與有效期判定是資料邏輯，不能靠選單型態保證**。
- 反證：若工作人員多半只處理當期新 Session，預設或精簡入口可能確實節省操作；但歷史補登與跨期改價屬不同任務，需另外驗證。不能假設 Notion 原生 Relation 選擇器可任意改成 HTML listbox、雙欄控制或自訂選項驗證。
- 狀態：`NEW_CANDIDATE_INDEX_DEDUPED`、`R1_MAIN_TEXT+C1`；`FULL_DEEP_PASS_10_OF_10=NO`。

## AUTO42-S02｜Why So Many Info Tips Are Bad (and How to Make Them Better)

- URL：https://www.nngroup.com/articles/info-tips-bad/
- Canonical：`nngroup:articles/info-tips-bad`；Kate Kaplan；2026-01-23；UX / 情境提示與必要資訊可見性。
- 閱讀軌跡：`AUTO42-S02-R1-MAIN-TEXT-C1`；已讀 What Is an Info Tip?、Representing Info Tips（i / ?）、The Problem、三類 Pitfalls（重複提示、隱藏關鍵資訊、打斷流程）、Conclusion；可見各正反例圖說，未逐張開啟原始圖片。
- 核心證據：info tip 適合簡短、可選的補充說明；重要限制、法律告知、操作必要條件不應藏在 hover/click 才可見的資訊裡。問號更偏向求助，i 更偏一般補充；長文、跳頁或遮蓋操作上下文會妨礙工作。
- C1 新反例：若「補助資格待人工核對」「本次服務日與方案期別衝突」只藏在問號提示內，行政人員可能看到可用額度就誤以為可以核准；但反向把所有跨期模型、設計規則、驗收紀錄都放進工作頁，又違反已確認的**業務頁不放 AI 內部規則**，讓首屏雜亂。應區分「當下必須看見的業務狀態」與「可選補充解釋」，但本輪**不提出實際改版或寫入**。
- 反證：部分專業人員需要更完整背景來判斷例外情境；不代表應將完整背景永久顯示於每筆記錄，也不代表 Notion 原生有可自訂的 hover info tip。必要資訊可能須直接使用現有欄位/短提示，具體設計需等研究門檻及使用者核准。
- 狀態：`NEW_CANDIDATE_INDEX_DEDUPED`、`R1_MAIN_TEXT+C1`；`FULL_DEEP_PASS_10_OF_10=NO`。

## 本輪計量與限制

| 指標 | 本輪可核實 |
|---|---:|
| research 目錄既有 Markdown 逐檔比對 | 53/53 |
| sources.md 索引候選 canonical slug 命中 | 0 |
| 新 canonical 來源候選（限已查清冊） | 2 |
| 主要文字 R1 閱讀 | 2 篇各 1 次 |
| 首次獨立反例 C1 | 2 次 |
| 既有來源完整重讀 R2–R10 | 0 |
| 本輪嚴格 10/10 完整深讀達標 | 0 篇 |
| 累積可核實嚴格 10/10 完整深讀達標 | **0 / 10,000 篇** |

**未驗項目**：全儲存庫其他路徑/同文異址去重、兩篇原始圖片逐張、互動示範、真實 Notion/手機/角色權限/效能/歷史金額與補助公式驗證。2020年文章之介面型態與2026年 Notion 功能不能直接畫等號。只記研究假說，不冒稱正式設計或產品驗收。

## 寫入與安全驗收

- 本檔為本輪唯一新增研究紀錄；共用 sources / decision / acceptance 各自寫入前重讀 main 最新內容與 blob SHA，SHA 條件更新，遇衝突只合併不重複增量。完成後須重新 Fetch 驗證 commit、blob SHA 與內容，未讀回者不得稱 PASS。
- 本輪沒有對 Notion 或正式系統發出任何修改操作；不開始 Notion 重新設計，研究未完成且使用者未確認完成。
