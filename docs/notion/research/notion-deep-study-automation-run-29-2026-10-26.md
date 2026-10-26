# Notion 深度學習 AUTO-29｜2026-10-26（僅研究）

- 執行標記：`AUTO-29-20261026-2044-RESEARCH`；軌道：每小時自動研究，獨立於聊天室手動研究。
- 範圍：只允許 GitHub 研究證據與索引更新；不得修改 Notion、正式 GAS、Cloud Run、Session 或部署。
- 起始查核：已重新 Fetch main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、sources.md、decision-log.md、acceptance-status.md；檢查 research 目錄40份文件、首批、批次02–04、十面向、MANUAL-01、AUTO-28，以及 sources.md 的 canonical slug。未在當期 sources.md 或七份主要研究清冊中發現本輪兩個候選 slug。研究目錄其他逐檔完整機器稽核尚未完成，因此新增篇數屬「依已查清冊暫列」而非全庫確證。
- 去重規則：Notion各語系 help 路徑統一為 `notion-help:connected-properties`；NN/g使用 `nngroup:articles/user-mistakes`。同URL、頁內小節、反例角度及搜尋命中均不另計來源或閱讀次數。

## AUTO29-S01｜Notion Connected properties

- 原始 URL：https://www.notion.com/help/connected-properties
- 標題：Connected properties；canonical ID：`notion-help:connected-properties`；未標作者或發表日期；2026-10-26 取得官方可讀主要正文。
- 閱讀證據：`R1_MAIN_TEXT_ALL_FOUR_CONNECTORS+COUNTEREXAMPLE`；已讀前言及 Google Drive、Figma、Zendesk、GitHub PR 四節與方案限制。原頁包含影片、圖片；未播放影片、未逐張檢視圖片、未實際授權任何連線，因此非 `FULL_DEEP_PASS`。
- 內容事實：Google Drive connected property 限 Plus／Business／Enterprise；Figma、Zendesk、GitHub PR connected property 限 Business／Enterprise。Google Drive 文件可在資料庫欄位連結；GitHub PR 屬性會在缺少時新增 Unique ID，並可藉 Notion 任務ID或PR網址關聯。
- 先驗假設：把外部檔案直接放進Notion資料庫欄位，能降低治療所行政人員查詢成本，且免費版可直接使用。
- **反例1（方案）**：官方對上述連線屬性明確限制付費層級；不能以頁面示範推定本所現有方案支援，也不能將其當作免費版既有功能。
- **反例2（權限／來源真值）**：欄位顯示連結不代表登入者一定具有外部檔案的存取權，也不代表外部檔案內容經正式核准、即時同步或可用於補助額度計算。不能將「可見連結」等同「可讀內容」或「已驗證來源」。
- **反例3（隱含副作用）**：GitHub PR connected property 可能自動增加 Unique ID；若未經確認就套用到既有臨床業務資料庫，會產生非預期 schema 變更，且原生 Unique ID 不等於個案×核定期別的業務唯一鍵。
- **未驗限制**：沒有實際付費帳戶、外部服務授權、跨角色測試、敏感資料評估或Notion實作；上述僅是官方文件支援的產品描述與研究推論。

## AUTO29-S02｜NN/g Preventing User Errors: Avoiding Conscious Mistakes

- 原始 URL：https://www.nngroup.com/articles/user-mistakes/
- 標題：Preventing User Errors: Avoiding Conscious Mistakes；作者 Page Laubheimer；2015-09-07發表；2026-10-26 取得可讀正文。
- Canonical ID：`nngroup:articles/user-mistakes`；閱讀證據：`R1_MAIN_TEXT_ALL_HEADINGS+COUNTEREXAMPLE`，已讀「The 2 Gulfs」「Gather User Data」「Follow Design Conventions」「Communicate Affordances」「Preview Results」「Preventing Both Mistakes and Slips」及「Summary」，包含確認、Undo、輸入前提示等子節。示例原圖未逐張檢視，不是完整深讀。
- 內容事實：使用者誤判常來自介面與心理模型不符；減少記憶負擔、讓操作結果可預覽、關鍵刪除前確認、提供可復原能力、及在真正錯誤前給就地提示可降低風險。文章也提醒過多確認視窗可能造成習慣性忽略。
- 先驗假設：所有行政欄位都加「確定？」彈窗就能防止錯誤，或反過來完全移除確認視窗以求速度。
- **反例1（確認疲乏）**：每次查閱／修改低風險欄位都二次確認，工作人員可能習慣性按確定；真正會批次改動方案期別的高風險操作反而難被注意。應區分風險層級，不可單靠確認視窗。
- **反例2（操作前後狀態）**：只在送出後顯示「成功」，不告知變更前後的方案、期別、筆數，使用者無法確認是否誤改他期；但 Notion 原生按鈕未必支援此種完整交易預覽，不可把UX建議冒充既有能力。
- **反例3（復原假設）**：NN/g倡議 Undo，但不等於 Notion 的批次編輯、跨庫自動化或第三方同步都能原子復原；設計階段仍須逐項驗證。未知／待核對／確認為0須保留不同狀態。
- **研究限制**：此文為一般 UX 研究，不能證明本所目前錯誤率、操作速度或 Notion 具備特定復原機制；無真人測試、圖片逐張檢視。

## 本輪計數與硬性限制

| 指標 | 本輪可稽核值 |
|---|---:|
| 當期索引初步去重的新 canonical 文章 | 2（全域精確去重待核） |
| 可讀主要正文的一次閱讀 R1 | 2 |
| 首次獨立反例分析 | 2 |
| 舊來源針對性複讀 | 0 |
| 本輪完成10次獨立完整深讀 | 0 |
| 累積嚴格達標10/10 | **0／10,000篇** |

- 未完整檢視圖片、影片、互動展示、實際 Notion 操作、方案授權、角色權限、效能、跨期公式或補助核定數值，因此兩篇僅 `R1_MAIN_TEXT`，`FULL_DEEP_PASS=0`。
- 沒有對 Notion正式／TEST頁、DB、Data Source、View、Formula、Relation、權限、個案資料或正式 GAS／Cloud Run／Session／部署執行任何寫入；也未開始重新設計。
- 此研究紀錄不是任何新功能實作決議；10,000篇×10次完整深讀與使用者確認均未完成。
