# AUTO-59｜2026-10-28｜Notion Dashboard view 的跨來源篩選、權限與效能反例（純研究）

- 執行軌跡：`AUTO-59-20261028-0240-RESEARCH`；台灣時間 2026-10-28 02:40 起。僅公開設計研究與 GitHub 進度記錄。
- 開始及寫入前重讀 main：README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md、research/README.md，並檢視當期 research 目錄及其研究清冊。
- 去重：當期 research 目錄共 70 個 Markdown；12 個非 AUTO 研究清冊與 58 個 AUTO 批次均取得全文，另檢查 sources.md 全文；以下完整 canonical URL 在這些已查紀錄中未出現。不同語系同文不另計。其他未索引 repo 路徑、同文不同網址與未來同步寫入仍有去重風險。
- 本輪候選排除：Notion [Unique ID](https://www.notion.com/help/unique-id) 已見 MANUAL-01；[Database settings](https://www.notion.com/help/customize-your-database) 已見 batch-02；[Forms](https://www.notion.com/help/forms) 已見 AUTO-01；[Data sources](https://www.notion.com/help/data-sources-and-linked-databases) 已見 AUTO-07；[Layouts](https://www.notion.com/help/layouts) 已見 batch-02。**以上均不算新增來源、複讀或本輪完整閱讀。**

## 本輪唯一新增來源候選：AUTO59-S01

- 標題：[Dashboard view databases in Notion | Notion Help](https://www.notion.com/help/dashboards)
- canonical：`https://www.notion.com/help/dashboards`；去重 ID `notion-help:dashboards`；發布者 Notion Help；首次發表日期未核實；2026-10-28 擷取。
- 閱讀軌跡：`AUTO59-S01-R1-MAIN-TEXT-C1`。本輪實際閱讀網頁主要正文（約第 106–402 行）：用途與 Business/Enterprise 方案門檻、建立與 Agent、widget 上限、調整大小、view 與 edit、全域篩選、原始 View 變更傳播、權限、效能、dashboard 與 inline views 的比較、三種版面案例、FAQ。頁面導航/頁尾不當成獨立材料。
- 官方產品事實：Dashboard view 需要 Business/Enterprise；最多 12 widgets、每列最多 4 個；全域篩選**只作用於包含相應屬性的 widget**；View 模式中的篩選排序預設為本地狀態，需有權限並選 Save for everybody 才會共用；widget 所使用的底層 View 修改可能影響其他引用該 View 的頁面；Dashboard 遵循底層資料庫權限；官方警告大量 widget/未篩選表格可能降低效能。以上是官方文字，不等於已實測此治療所帳號、方案、角色或 UI。
- 獨立反例 C1（跨來源全域篩選的不完整一致性）：如果首頁把 Sessions、Billing、補助方案用量放入同一 Dashboard，使用者選擇「某方案期別」後，**缺少對應屬性的 widget 可能仍顯示全量**。畫面看似同一篩選條件，實際數據母體不同，可能讓收款或補助用量核對錯誤。反證：不能把「全域篩選」名稱當作跨資料庫關聯正確性的證明；需逐 widget 確認屬性與有效範圍。
- 獨立反例 C2（個人篩選 vs 共用狀態）：行政人員在 View 模式切到「本週」可能只是個人暫時顯示；其他人仍看到原視圖。反向地，改了底層 View 的設定可能影響其他工作台。反證：不能把個人所見視為所有角色的同一工作狀態，也不能把 dashboard 的 Edit/View 模式當成版本管理與資料凍結。
- 獨立反例 C3（權限與方案限制）：Dashboard 是視覺容器，不會創造獨立的資料權限隔離。若某角色不應看到個案資料，不能靠把 widget 隱藏或縮小來保密；若目前方案不是 Business/Enterprise，不能把 Dashboard view 當成無條件可用的改版選項。
- 獨立反例 C4（同頁直接可見與效能的張力）：Dashboard 限 12 個 widget，且官方建議過濾大表；但使用者先前已否決把日常資料改成只有連結的入口。不能為了 dashboard 美觀，把高頻核對資料藏在點擊後才看得到的頁面；也不能為了同頁而無限制載入大型視圖。未來需先做實際任務/速度/權限比較，且必須取得使用者確認才設計。
- 跨文獻比較：先前 GOV.UK Table/Pagination/Task list 的資料可見性原則，可作為本輪反例背景，但**不構成那些舊來源的新閱讀輪次**。
- 本輪閱讀限制：原始圖片未逐張視覺核對；未觀看影片；未執行 Notion Dashboard 實際操作、角色權限、手機、跨來源公式或載入速度測試。因此標記 `R1-MAIN-TEXT`，**不是完整深讀 R1**，也沒有 R2–R10。

## 嚴格計數與邊界

- 新來源候選：**1**（經 sources.md + 70 個 research Markdown 全文查重，未作同文異址全庫語義查重）。
- 主要正文文字閱讀：**1**；獨立首次反例：**1 篇、4 個情境**；本輪既有來源完整複讀：**0**。
- 本輪完成 10/10 完整深讀：**0 篇**；累積已可核實 `FULL_DEEP_PASS_10_OF_10`：**0／10,000 篇**。
- 僅 GitHub 研究記錄。**未修改** Notion 正式/TEST 頁面、資料庫、Data Source、View、Formula、Relation、權限、業務資料，亦未修改正式 GAS、Cloud Run、Session 或部署。未獲使用者確認前，不開始 Notion 重新設計。
