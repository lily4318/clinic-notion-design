# AUTO-62｜File upload／Character count：文件重用與文字限制的業務風險（2026-10-28）

- 唯一執行標記：`AUTO-62-20261028-0537-RESEARCH`；排程自動研究，Asia/Taipei 2026-10-28 05:37 起。
- **授權邊界**：只研究公開來源及寫入 GitHub 研究/進度紀錄；**不修改** Notion 正式/TEST、資料庫/資料列、View、Formula、Relation、權限、GAS、Cloud Run、Session 或部署；未獲准開始重新設計。
- 開始前已讀 main：README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md，以及 docs/notion/research/README.md、AUTO-61 原文。兩個 canonical 在 sources.md 全文未見、GitHub repo code search 未命中；**未完成所有歷史 research 文件逐檔全文與同文不同網址語義去重**，只能稱「新來源候選」。
- 本輪每篇只計 **1 次主要正文文字閱讀＋1 組首次獨立反例**；不是完整 R1，更不是 R2–R10。示例頁面只作輔助，不另計來源或複讀。

## S01｜File upload – GOV.UK Design System

- 官方 canonical URL：https://design-system.service.gov.uk/components/file-upload/
- 去重身分：`govuk-design-system:components/file-upload`；維護者 GOV.UK Design System team；本文首發日期未核。官方更新紀錄包含 2025-03 改良元件引入、2026-02 互動狀態、2026-06 wrapper 與 error state、2026-07 Rails 修正，**更新日期非本文首發日**。
- 閱讀軌跡：`AUTO62-S01-R1-MAIN-TEXT-C1`。已讀 When to use、How it works、reuse uploaded files、HTML/Nunjucks、錯誤訊息類別、改良元件與 HTML attributes、輔助技術限制、Known issues、Recent changes；另開獨立示例 https://design-system.service.gov.uk/components/file-upload/default/ （僅確認可讀頁面；沒有上傳或拖曳實測）。
- 官方原文要點：只有服務真正必要才要求上傳；同一旅程中可考慮重用已上傳檔案，但要考慮隱私與公用裝置；不同失敗（未選檔、類型/大小不符、空檔、病毒、加密、上傳失敗、檔案數量/範本不符）應有具體訊息。改良版本為 opt-in 並處理可及性/翻譯/拖曳提示，但語音操作仍受瀏覽器安全限制；`required` 不會由改良元件的讀屏工具讀出。**這些是 GOV.UK 元件，不是 Notion 附件功能的已證實特性。**
- **反例 A｜重用與最小權限衝突**：補助申請若需兩次使用同一份證明，重用可以減少操作；但若在共用電腦或不同個案間開放預覽/重用，可能誤選他人附件或擴大可見範圍。不能從「重用便利」直接推論應把所有附件放入共用檔案庫。要先確定資料主體、用途、權限與可下載對象。
- **反例 B｜成功上傳不等於文件有效**：畫面顯示「上傳成功」只證明某步驟成功，不證明檔案內容、資格、核定期別或補助核准；失敗時也不能把檔案格式錯誤與後端服務失敗混為一種「請重傳」。尤其不能在未驗證 Notion 實際檔案安全機制時宣稱已掃毒或有特定上限。
- **反證／可推翻條件**：若日後真實工作流證明附件重用能在嚴格個案/角色隔離下減少重複且沒有誤附，才可考慮設計；需檢查 Notion 真實權限、檔案下載、跨個案誤附、版本與保留政策，不能用 GOV.UK 的 HTML 示範取代實測。
- **暫定研究推論**：減少重複上傳與保護敏感文件是兩個需共同驗證的目標；文件「上傳完成／驗證通過／資格核准」應分別表述。

## S02｜Character count – GOV.UK Design System

- 官方 canonical URL：https://design-system.service.gov.uk/components/character-count/
- 去重身分：`govuk-design-system:components/character-count`；維護者 GOV.UK Design System team；本文首發日未核。官方近期變更紀錄含 2026-10 Frontend v6.6.0 新增 `countType` 以改善計數準確性，但**不能推論 Notion 同步具備此功能或已解決所有中文字元計數問題**。
- 閱讀軌跡：`AUTO62-S02-R1-MAIN-TEXT-C1`。已讀 When to use/not、How it works、HTML/Nunjucks、word count、threshold、Error messages、Research、Known issues、Recent changes；另開獨立示例 https://design-system.service.gov.uk/components/character-count/default/ （只讀頁面文字，未鍵入測試）。
- 官方原文要點：應先測試沒有字數限制的流程；只有實際法律/技術/研究理由才限制；若後端限制過小，優先考慮提高限制。此元件在輸入時提示剩餘字數，但**不阻止超額輸入或貼上**，提交時才須提供清楚錯誤；可選字數而非字元計數，亦可在接近上限時才顯示。官方承認部分 emoji/非拉丁字元可能計數不同，特定讀屏/瀏覽器組合有已知問題。
- **反例 A｜臨床/行政必要資訊被硬截斷**：治療所若對 Session 備註或行政異常原因套用過小字元上限，可能迫使刪除對帳、申訴或必要照護交接資訊；「短文案較乾淨」不構成限制資料完整性的理由。若只為首頁摘要精簡，應區分摘要欄與原始記錄，而不是截斷正式記錄。
- **反例 B｜中文字元、表情與後端限制不一致**：同一段中英文混合、換行、emoji、組合字元可能在 UI 計數與後端驗證有差異；若輸入框顯示未超限，但 Notion/外部 GAS 接口拒絕或截斷，使用者可能遺失重要內容。要在真實系統核實 Unicode 計數、複製貼上、儲存及錯誤回復，不能由 GOV.UK 示例外推。
- **反證／可推翻條件**：若未來證據顯示特定外部系統有不可變更的欄位上限，且工作人員常超額，可研究預先提示、保留原文、分欄/附件與明確修正方式；需真人測試不同中文/emoji 輸入與保存回讀。
- **暫定研究推論**：字數計數是預期管理，不是資料品質/業務核定；長文字能否儲存與必要資訊完整性優先於畫面精簡。

## 交叉比較、未解問題與計數

1. File upload 要求不要索取不必要的檔案，Character count 要求不要施加無證據的限制：共同原則是**降低不必要的輸入負擔**，但不能以此刪減必要業務證據。
2. 兩者都有「前端顯示成功/可輸入」與「後端真的接受、正確保存」的差距；Notion/GAS 的真實保存與角色權限不能用其他設計系統的 HTML/JS 說明替代。
3. 使用者已確認同類資料同頁直接可見；此輪不提出任何實際版面、欄位、權限或文件流變更。
4. **NOT_TESTED**：原圖逐張、拖曳/選檔、鍵盤/讀屏、手機、上傳掃毒、Notion 檔案與權限/下載、實際字元/Unicode 計數、公式/跨期金額、真實 Session、效能與真人 UX。
5. **計數**：已查索引新來源候選 **2**；官方主要正文文字閱讀 **2 篇各1次**；首次獨立反例 **2 組（共4情境）**；完整 R1 **0**，獨立完整 R2–R10 **0**，本輪 `FULL_DEEP_PASS_10_OF_10` **0**，累積可核實 **0／10,000 篇**。全庫同文異址去重尚未完成，候選不計為全量已核定。
6. **安全邊界**：只許 GitHub 研究與進度更新，**沒有修改 Notion 正式/TEST 頁、資料庫、View、Formula、Relation、權限、業務資料或正式 GAS/Cloud Run/Session/部署**；研究門檻未達且使用者未確認，不開始重新設計。
