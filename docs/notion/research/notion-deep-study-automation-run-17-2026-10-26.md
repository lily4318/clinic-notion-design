# Notion 深度學習｜AUTO-17｜2026-10-26（08:38 台灣時間）

- 執行軌跡：`AUTO-17-20261026-0838`；模式：每小時排程獨立研究批次；範圍：公開官方來源研讀、研究清冊去重與 GitHub 取證，**不修改 Notion／GAS／Cloud Run／Session**。
- 本輪開始先讀 main 最新 `README.md`、根 `AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`decision-log.md`、`acceptance-status.md`，列出當期研究目錄並比對首批、第二～四批、十面向、MANUAL-01 與 AUTO-01～16 來源 URL。研究目錄中既有來源的重複不再算新增。
- 研究時間：2026-10-26；官方原文發表／更新日未見可驗證值，不推測。去重規則：忽略 `www.`、語系前綴（如 `en-gb/`）、尾端斜線、追蹤參數；以官方 help slug 作 canonical 身分。只統計實際打開可讀正文者，未讀媒體不列完整深讀。

## 本輪新來源（2 篇；均為首次文字研讀與獨立反例分析，不是 FULL_DEEP_PASS）

### AUTO17-S01｜Webhook actions｜notion-help:webhook-actions
- URL：https://www.notion.com/help/webhook-actions
- 作者／類型：Notion Help 官方操作文件；主題：按鈕／資料庫自動化、HTTP POST、跨系統資料外送、方案限制。
- 實讀範圍：正文「Use webhook actions」、「Who can use webhook actions?」、「Send webhook」、「Webhooks limitations」、「Disable webhook actions in a workspace」及本文目錄；原文擷取行106–167，全文頁共251行（含站台導覽）。
- 可核對的原文要點：Webhook action 僅付費方案；傳送 POST；官方寫明不要求認證；可新增自訂 header；資料庫自動化可選欄位作 payload，資料庫按鈕無法選欄位；失敗會自動暫停須手動恢復；每個自動化至多5個 webhook actions；僅傳資料庫頁屬性而非內文；無原生 payload preview；Enterprise 可停用工作區 webhook action。
- 本輪獨立反例：若把個案識別資訊或財務／臨床欄位放進 payload，單靠 Notion 既有頁面權限不能保證對外資料最小化；若 HTTP POST 接收端逾時或錯誤，自動化可能暫停，不能假設補助核定或通知必定送達。修正假設：**Webhook 是有方案、傳輸、失敗與資料外送風險的觸發機制，不是具認證、重試與核定唯一性的交易保證**。日後若要評估，須另行驗證權限、payload、接收端驗證、去重與人工補救；本輪不實作、不測試。
- 反證邊界：文件「不要求認證」是官方 action 的設定說明，不代表所有接收端皆無法自訂驗證；不得將其誇大為「完全無安全機制」。
- 閱讀證據：2026-10-26 公開官方頁面可讀文字；**MAIN_TEXT_SECTIONS_READ + ANALYSIS_1/10**；圖片／實際 webhook／付費帳號與跨系統端點未測，**FULL_DEEP_PASS=0**。

### AUTO17-S02｜Intro to workspaces｜notion-help:intro-to-workspaces
- URL：https://www.notion.com/help/intro-to-workspaces
- 作者／類型：Notion Help 官方入門文件；主題：工作區、Sidebar、共享與私有、權限、跨工作區搬移與方案。
- 實讀範圍：「Workspace basics」、「Sidebar tools」（Tabs、Sections、Favorites、Settings/Trash、Create、Hover）、「Editor tools」（Breadcrumb、Collaborators、Share、menu）、「Team vs. personal workspaces」及 FAQ；原文行106–297，整頁394行（含站台導覽）。
- 可核對的原文要點：Sidebar 將頁面移至 Private 會讓其他人失去存取；Lock database 仍允許輸入資料但阻止調整 View／Property；分享連結本身不授權；不同 Workspace 的付費方案不互相涵蓋；跨工作區移動頂層頁會連帶子頁，官方提示搬移內容可能有問題；Workspace 的 Allowed Email Domains 影響自行加入。
- 本輪獨立反例：若為改善治療所行政導覽而直接將共用頁拖進 Private，操作人員可能立即失去工作入口；若以新增第二個 Workspace 代替分區，可能帶來另一份計費與跨工作區內容搬移風險。修正假設：**Sidebar 視覺整理不等於權限安全，Workspace 分割不等於免費、無損或能解決資料權威來源問題**。
- 反證邊界：本文為入門導覽，不是每種帳號的完整權限矩陣；免費／付費功能細節應另查當期方案文件，不能只據此確定本所帳號現況。
- 閱讀證據：2026-10-26 公開官方頁面可讀主文字及 FAQ；**MAIN_TEXT_SECTIONS_READ + ANALYSIS_1/10**；頁面圖片／嵌入影片／真實工作區操作未測，**FULL_DEEP_PASS=0**。

## 來源清冊更正（本輪確認兩項歷史重複；不刪原始證據）

1. **AUTO16-S01 `/help/buttons` 非新來源**：AUTO-05 已在 2026-10-25 登錄 `https://www.notion.com/en-gb/help/buttons`（AUTO05-01），語系版與 AUTO-16 的 `https://www.notion.com/help/buttons` 是同一 canonical ID `notion-help:buttons`。AUTO-16 的分析證據保留，但「新增」計數須 -1；不自動當作嚴格第2次完整深讀。
2. **AUTO16-S02 `/help/feeds` 非新來源**：AUTO-03 已登錄 `https://www.notion.com/en-gb/help/feeds`（AUTO03-03），與 AUTO-16 同一 canonical ID `notion-help:feeds`。AUTO-16 的分析證據保留，但「新增」計數須 -1；不自動當作嚴格第2次完整深讀。
3. AUTO16-S03 `/help/archive-pages` 依本次當期清冊核對暫仍可列新來源；AUTO-05 的 `duplicate-delete-and-restore-content` 雖談 Archive，屬另一篇文章，不能僅因主題相近合併。AUTO-16 實際**暫列新來源1篇而非3篇**。全域唯一來源數仍須另做機器化跨清冊稽核，不以歷史各輪「新增」相加冒稱總數。
4. 本輪新增的兩篇 `/help/webhook-actions`、`/help/intro-to-workspaces` 在已取得的研究清冊 URL 中未出現；本次各只計一次首次文字研讀。

## 嚴格進度與安全

- 本輪新增 canonical 官方來源：**2 篇**；首次主要文字研讀與新反例：**各1次，共2次**；歷史重複新增更正：**2 筆**；本輪嚴格完整深讀10/10新增：**0篇**。
- **累積可稽核完成10/10篇數：0／10,000篇**。來源有主文字閱讀不等於完整圖片、影片、操作與十次獨立閱讀；不能將同一分析拆成十次。
- 未修改任何 Notion 頁、DB、View、Formula、Relation、權限、正式 GAS／Cloud Run／Session；未開始重新設計；手動續作與排程獨立並行。
- 此檔是研究取證，不代表 Notion 功能或系統安全已在真實工作區實測。
