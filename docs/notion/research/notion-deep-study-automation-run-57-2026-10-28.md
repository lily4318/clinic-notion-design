# AUTO-57｜2026-10-28｜日期輸入與長選單的操作風險（純研究）
- Trace：`AUTO-57-20261028-0045-RESEARCH`；台灣時間 2026-10-28 00:45 起；工作範圍僅公開資料閱讀與 GitHub 研究進度。
- 先重新取得 main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md、docs/notion/research/README.md；並取得 research 目錄清單（開始時 68 份 Markdown）。已查 sources.md 完整內容與 repo code search（date-input、components/select）均未命中兩個 canonical URL；**未完成全部歷史研究文件逐檔全文比對與同文異址查重**，僅登錄「已查索引新來源候選」，不宣稱全庫精確去重。
- 取證方式：實際開啟 GOV.UK Design System 官方原文、閱讀主文段落、HTML/Nunjucks 範例、錯誤狀態與 Recent changes；並各做一次獨立反例分析。沒有逐張驗證圖片、實際操作範例、鍵盤/讀屏、真實 Notion 或第三方延伸影片，因此是 `R1_MAIN_TEXT_PARTIAL`，**不是完整 R1，也不是 R2–R10**。

## AUTO57-S01｜Date input – GOV.UK Design System
- URL：https://design-system.service.gov.uk/components/date-input/
- Canonical：`govuk-design-system:components/date-input`；標題：Date input；維護者：GOV.UK Design System team；原始首發日期未核實；本輪存取日期 2026-10-28；閱讀記號：`AUTO57-S01-R1-MAIN-TEXT-C1`。
- **實際覆蓋**：頁面「When to use/not use」指出適合使用者知道或容易查得的日期，不適合不知道精確日期的事件；三欄 day/month/year 的 fieldset/legend 與例子、同頁多問題時 heading 區別、不可自動跳焦點；生日 autocomplete 的三個 bday 屬性；整體日期/單欄錯誤的 HTML/Nunjucks 範例；缺漏、非法日期、過去/未來及與另一日期的前後/區間關係錯誤文案；接受月份全名/縮寫的研究與變更紀錄（頁面顯示 2026-07 元件更新）。原文主體約第52–606行。
- **反例A：日期欄位的形式正確，不等於業務時序正確**。歷史 Session 服務日可以是過去，但該筆輸入日期是否落在某補助核定期、是否符合首談後期限或是否與已預約/實際服務日一致，須由正式業務規則與原始記錄核對；單靠日期格式或一般「不可選過去」的提示可能錯誤拒絕合法補登。
- **反例B：英國範例的日/月/西元年拆欄，不等於台灣行政作業的最佳格式**。民國/西元轉換、時區、日期與時間分離、跨午夜服務可能引入新錯誤；不能直接要求 Notion 原生 Date 屬性改為三欄，也不能假設 GOV.UK 的錯誤阻擋或 aria 行為能在 Notion 原生欄位重現。
- **新推論（非設計核准）**：應分別核對輸入是否為有效日期、該日期是否為真實服務日期、是否符合相應核定期規則；三種驗證不應互相冒充。原圖、真實互動、台灣日期輸入使用者測試未完成。

## AUTO57-S02｜Select – GOV.UK Design System
- URL：https://design-system.service.gov.uk/components/select/
- Canonical：`govuk-design-system:components/select`；標題：Select；維護者：GOV.UK Design System team；原始首發日期未核實；本輪存取日期 2026-10-28；閱讀記號：`AUTO57-S02-R1-MAIN-TEXT-C1`。
- **實際覆蓋**：頁面「When to use/not use」稱公共服務應盡量避免 select，先嘗試縮小選項；設定可有預設值，但問答不應預選；HTML/Nunjucks 的排序範例、提示文字、未選擇錯誤狀態、無障礙描述；不建議 `<select multiple>`；研究所述的焦點/已選混淆、手機縮放、看不到更多選項、無法關閉清單等問題；Recent changes 包括 2025-03 ID 預設、2024-10 hint 更新。原文主體約第52–393行。
- **反例A：縮短方案清單可能反而隱藏合法歷史期別**。若只列「目前啟用」方案，補登舊 Session 時可能找不到當期正確 Price Plan；但無限制展開所有歷年期別又會增加錯選與搜尋成本。必須區分當前作業與歷史補登的查找範圍，並保留原始方案實例 ID 與日期可稽核性。
- **反例B：設定用預設值不等於收費決策可預設**。排序方式預設「最近更新」通常可撤銷，但自動帶入最新收費期別或金額可能直接改變歷史計費；不應以 Select 的 UI 便利性當成正確業務期別的證據。未知/未確認不能自動轉為首個有效選項。
- **新推論（非設計核准）**：資料搜尋與唯一選擇、選擇的業務有效性、保存歷史快照分屬不同責任；GOV.UK HTML Select 不等於 Notion Select/Relation 的能力，需後續另行驗證。未觀看外連使用者研究影片、未測手機/讀屏/Notion 實帳。

## 計量、限制與安全
- 本輪在已查索引下的新來源候選2篇；主要正文文字閱讀各1次；獨立首次反例分析各1組；完整 `DEEP_PASS` 0、獨立 R2–R10 0、`FULL_DEEP_PASS_10_OF_10` 新增0，累積可核實 **0／10,000篇**。不可把正文各章節、HTML/Nunjucks兩種寫法或反例多角度當成多次閱讀。
- 原始圖片、互動、輔助技術、真實 Notion 日期/Relation/Formula/歷史金額、角色/權限/效能及全庫精確去重未驗。不得據此新增/刪除/改動 Notion 頁面、資料庫、View、Formula、Relation、權限、業務列；不得修改正式 GAS、Cloud Run、Session、部署。
- 本次只允許 GitHub 研究紀錄，沒有開始 Notion 重新設計。使用者手動續作與既有每小時排程可獨立並行；共用清冊更新採 main 最新 blob SHA 條件寫入。
