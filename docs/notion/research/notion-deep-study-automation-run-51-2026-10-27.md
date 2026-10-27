# AUTO-51｜2026-10-27｜GOV.UK Error summary 與 Notification banner：研究文字取證及反例

- Trace：`AUTO-51-20261027-1841-RESEARCH`；本輪獨立執行標記。
- 授權：**只研究及 GitHub 進度紀錄**，不變更 Notion、任何資料庫/View/公式/權限、正式 GAS、Cloud Run、Session 或部署。
- 前置讀取：main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、decision-log.md、acceptance-status.md、docs/notion/research/README.md、AUTO-50 研究紀錄。讀取 sources.md 抽出57個唯一研究 Markdown 引用；嘗試批次取得全部研究文件時遭工具呼叫上限中斷，**未完成57/57逐檔全文查重**，也無法確認所有未被索引的研究路徑。
- 2026-10-27 以公開官方網頁取得可讀原文。sources.md 全文及 GitHub code search 對兩個 canonical 路徑均未見重複；此為「已查索引新候選」，**不宣稱全庫精確去重**。
- 兩篇各只計**一次主要正文文字閱讀與首次反例分析**；並非完整 R1 深讀，未產生任何 R2–R10；同一篇多個分析角度不增加閱讀次數。

## AUTO51-S01｜Error summary
- URL：https://design-system.service.gov.uk/components/error-summary/
- 標題：Error summary – GOV.UK Design System
- 維護者：GOV.UK Design System team；首次發表日期未核實。官方變更紀錄有 2026-06 CSS 修正、2025-02 焦點指引澄清，**不可把修改日期當初版日期**。
- Canonical ID：`govuk-design-system:components/error-summary`；閱讀軌跡：`AUTO51-S01-R1-MAIN-TEXT-C1`。
- 閱讀範圍：用途與何時使用、驗證錯誤時同時顯示頁首摘要與欄位旁訊息、鍵盤焦點、頁面 title、摘要與欄位錯誤文字一致、單欄與複合日期欄位的錨點、checkbox/radio 錨點、放在 main 頂端但 h1 之前、Recent changes；已看主要 HTML/Nunjucks 範例的語意及連結結構，**未逐行核對所有範例程式碼，也未以瀏覽器操作示例/輔助技術驗證**。
- 官方事實：驗證錯誤時提供頁首摘要及各錯誤欄位旁訊息；摘要可將使用者導向有問題的輸入，複合日期欄位連到首個錯誤欄位；焦點管理與一致措辭對鍵盤/讀屏使用者重要。
- 治療所反例 A：跨期 Session 表單可能同時存在「服務日期落在期別外」「歷史價格與期別不一致」「缺少人工資格證據」。如果只在頁頂列一個總錯誤，使用者仍需猜哪個欄位可修正；如果只在欄位旁標紅而無總覽，長表單會漏看。**總覽與欄位訊息應互相對應**，但必須先有可信的資料驗證來源。
- 治療所反例 B：把「資格尚待人工核對」當成可自動修正的欄位驗證錯誤，可能迫使使用者填入不實的「已核准」；此類**業務待核狀態**與可修正的**輸入格式錯誤**不應混淆。反過來，若所有例外都允許忽略，也可能掩蓋跨期金額風險。
- 治療所反例 C：Notion 資料庫視圖並非 GOV.UK 自建表單，不能假定能控制 DOM 錨點、focus、aria-live 或阻止提交。研究是未來設計評估依據，不代表 Notion 原生支援。
- 未驗：示例完整互動、螢幕閱讀器、手機、Notion 原生輸入錯誤行為、實際業務資料及角色權限。

## AUTO51-S02｜Notification banner
- URL：https://design-system.service.gov.uk/components/notification-banner/
- 標題：Notification banner – GOV.UK Design System
- 維護者：GOV.UK Design System team；官方變更紀錄記載 2020-11 引入元件（非整頁最初發表日期）；2021–2022有指引及程式碼調整。
- Canonical ID：`govuk-design-system:components/notification-banner`；閱讀軌跡：`AUTO51-S02-R1-MAIN-TEXT-C1`。
- 閱讀範圍：用途、何時不適用、置於 h1 之前、同頁避免多個、全系統事件與個人期限、前頁操作結果、一般與綠色成功版本、ARIA、無障礙與 Recent changes；已讀主要 HTML 與用途示例，**未實際執行互動或逐行驗證全部程式碼**。
- 官方事實：通知橫幅適合「不是本頁主要任務、但需要知道」的系統或個人訊息；對本頁直接相關的訊息應放主內容；驗證錯誤用 Error summary / Error message 而不是通知橫幅。官方也提醒橫幅可能被忽略、同頁不宜堆疊多個；成功橫幅適用已確實完成的動作。
- 治療所反例 A：如果「補助資格待人工確認」是當前個案作業的核心條件，放在通用頁首 banner 反而可能被略過；應以任務內容直接顯示，而不是為了醒目把每一個欄位狀態都變成橫幅。
- 治療所反例 B：系統儲存 Session 後若立即顯示綠色「補助核准成功」，但其實只是寫入成功、尚未完成資格與歷史金額核對，會製造錯誤的業務承諾。**成功訊息須指向可核實的具體操作階段**，不能混同資料儲存、同步完成及人工核准。
- 治療所反例 C：大量持續 banner 會造成警示疲勞；但完全不顯示跨頁的服務中斷也不安全。應依資訊是否與當前任務直接相關決定位置與優先級，且不把 GOV.UK 元件能力當作 Notion 原生保證。
- 未驗：banner 的真實被注意率、輔助技術、手機/Notion原生顯示與操作、角色權限、效能。

## 去重、進度及界線
- 正規化 URL：去追蹤參數、保留官方 canonical path；兩篇均為 **已查 sources.md 索引的新來源候選**。GitHub code search 零命中不代表已證明所有研究檔不存在同文異址。
- 本輪：新來源候選2；主要正文文字閱讀2；首次反例分析2；既有來源完整複讀0；完整 R1 0；完整 R2–R10 0；`FULL_DEEP_PASS_10_OF_10` 新增0，累積可核實 **0/10,000**。
- NOT_TESTED：全部圖片、原始互動、外部研究全文、真實 Notion、手機、讀屏、權限、原生公式/歷史價格/補助資格、效能。這些設計推論不等於本所業務驗收。
- NO NOTION/SYSTEM WRITE：只記錄公開研究與 GitHub 進度，不開始 Notion 重新設計；與聊天手動續作並行，後續更新共用檔案必須重讀 main 與 blob SHA、衝突不得覆寫。
