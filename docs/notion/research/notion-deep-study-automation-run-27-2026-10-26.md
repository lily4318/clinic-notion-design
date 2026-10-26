# Notion 深度學習｜AUTO-27｜2026-10-26｜研究紀錄（未開始設計）

- Trace：`AUTO-27-20261026-1841-RESEARCH`；執行線：每小時排程，與聊天室手動續作獨立並行。
- 僅准研究與 GitHub 研究進度紀錄；未取得重新設計許可，不修改 Notion 正式／TEST Page、Database、View、Formula、Relation、Share／權限、業務資料或 GAS／Cloud Run／Session。
- 本輪開始重新 Fetch main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md；另讀 docs/notion/research/README.md、首批 evidence-register、AUTO-26 詳報；查 sources.md 與 GitHub slug 搜尋。全域所有未索引研究檔尚未完成完整機器稽核，故新來源計數標「依當期清冊暫列」。
- 來源去重身份採主域名＋文章 slug，移除語系／追蹤參數；同一 URL 不因 FAQ、案例、反例角度而多算篇數，同次閱讀不多算輪次。
- 閱讀方式：2026-10-26 直接開啟可讀的官方／NN/g 原文，逐節檢視主要正文與文字圖說。圖片像素內容、影片與真實產品操作均未完整驗證，**不計完整深讀1/10，更不計10/10**。

## AUTO27-S01｜Notion 官方：Table view

- URL：https://www.notion.com/help/tables
- Title：Table view；作者／發布日期：官方 Help Center，頁面未明示日期；讀取日期：2026-10-26。
- Canonical：`notion-help:tables`；來源類型：Notion 官方功能說明；暫列新 canonical 文章；閱讀標記：`AUTO27-S01/R1_MAIN_BODY_FAQ+COUNTEREXAMPLE`。
- 實讀範圍：Create a table view、Add table view to a database、Bulk edit multiple rows、Customize your table（Rearrange columns and rows／Wrap cell content／Calculations）、FAQ（conditional color、Name/Title、Open pages in、simple tables、inline/full page）。
- 原文可核功能：每個資料庫 Table row 可開為頁面；inline Table 可直接嵌在頁內；多選列後可批次修改屬性；欄可移動／調寬／換行；依屬性型別可做 count、empty、sum、average 等欄底統計。Simple table 不等於具有資料庫篩選、排序及屬性功能的 Database Table。
- 先驗假設：在補助工作台直接顯示 Table 並用欄底 Sum，就能可靠取代方案額度總覽。
- **反例 A（篩選範圍）**：若 Table View 僅顯示「當期、待核對」紀錄，欄底 Sum 反映該檢視的計算範圍，不能未經核實當成跨方案／跨期的官方剩餘總額；空值、未確認與已確認0也不能只用 Sum 判定。
- **反例 B（誤改）**：多選列 Bulk edit 是寫入操作，若同時選中不同方案期別或個案，可能將同一狀態／關聯批次套用錯對象；不能因 Table 便於比較就視為唯讀安全。
- **反例 C（介面與資料）**：Inline Table 支援同頁直見，但過多欄位／換行可能增加首屏高度；Simple table 只是文字表格，不能取代已有 Relation/Formula。拖曳排序或視圖顯示不代表歷史核銷紀錄改寫。
- 暫存研究結論：日常查閱可保留同頁直接比較的 Table；若未驗證來源期別、過濾條件、原生計算、操作權限及手機可用性，不將 Table 底部彙總視為政府核定值。**僅研究假說，未提出／執行改版。**
- 未完成：官方嵌入 Table 影片、所有示意圖片、實帳的批次修改／手機／效能／角色權限及公式原生值。

## AUTO27-S02｜NN/g：Designing Empty States in Complex Applications: 3 Guidelines

- URL：https://www.nngroup.com/articles/empty-state-interface-design/
- Title：Designing Empty States in Complex Applications: 3 Guidelines；作者 Kate Kaplan；發表 2021-09-19；讀取 2026-10-26。
- Canonical：`nngroup:articles/empty-state-interface-design`；來源類型：UX 原則；暫列新 canonical 文章；閱讀標記：`AUTO27-S02/R1_MAIN_BODY+COUNTEREXAMPLE`。
- 實讀範圍：導言與空狀態案例、Use Empty States to Communicate System Status、Provide Learning Cues、Provide Direct Pathways for Key Tasks、Conclusion，及可讀的圖片文字說明。
- 原文要點：真正沒有結果、尚在載入、查詢出錯不能以同一空白區域或「No records」混淆；空狀態可用簡短狀態說明、就地提示及與任務相關的直接操作入口。文章舉 ERP 警示、最近檔案、Loggly 初始資料等例，並非 Notion 原生產品規格。
- 先驗假設：補助清單空白就代表目前沒有待核對／異常紀錄，並可顯示「0筆」。
- **反例 A（非空而尚未載入）**：大型 linked View 讀取尚未完成時，若先顯示「沒有待核對」，工作者可能誤以為已核對完畢。只有資料成功載入、篩選條件可知且查詢完成後，才能合理解釋「目前檢視0筆」。
- **反例 B（權限／篩選）**：不同心理師、不同方案期別或權限範圍的 View 可能沒有顯示某筆資料；「本檢視無結果」不能推論整個資料庫沒有紀錄、個案不符合或政府剩餘額度為0。
- **反例 C（提示負擔）**：NN/g 建議空狀態提供引導，但在本所使用者已否決冗長操作說明的前提下，不能把每張空表都改成大篇教學或黃色警示；只有與當下工作有關且不混淆真實錯誤的簡短提示才值得後續驗證。
- **反例 D（可行性界線）**：文章展示可點擊建立按鈕與載入中狀態，但不能因此推論 Notion 原生 Linked View 可自訂所有空狀態或載入訊息；須在將來合法實作階段核對產品能力，不可直接新增額外元件。
- 暫存研究結論：研究後續需分辨「載入中／真0筆／篩選0筆／查詢失敗／權限不足／未確認」，而非只看表格有無資料。這是業務風險假說，不是已核准的 UX 設計。
- 未完成：全部圖片原像素核對、實際 Notion 行為、真人 UX、手機／角色權限／效能測試。

## 本輪計數與安全邊界

| 指標 | 本輪 |
|---|---:|
| 暫列新增 canonical 來源（依當期清冊） | 2 |
| 可取得主要正文閱讀 | 2 |
| 首次獨立反例分析 | 2 |
| 既有來源獨立複讀 | 0 |
| 完成10次嚴格完整深讀 | 0 |
| 累積可稽核10/10完成 | **0／10,000** |

- 無法把文字閱讀、FAQ、案例、圖片說明或多個反例視為多次完整深讀；全域去重總數仍待完整跨檔核算。
- 未實測 Notion 頁面、View、Formula、Share、手機、速度、真實人員操作或政府核銷真值；沒有開始重新設計。
- 本輪唯一允許的寫入：此 GitHub 研究紀錄與 sources／decision-log／acceptance-status 的非敏感研究索引。與手動續作共享 main，寫入前須重新 Fetch／SHA 條件更新，寫後重 Fetch 驗證。
