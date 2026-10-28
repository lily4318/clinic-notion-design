# AUTO-85｜Notion 深度學習：日期與時間輸入之錯誤防範（2026-10-29）

Trace: `AUTO-85-20261029-0435-DATETIME-RESEARCH`；範圍：公開設計文獻閱讀與 GitHub 研究記錄；**RESEARCH ONLY / NO NOTION OR SYSTEM WRITE**。

## 開始前基準與去重
- 已重新 Fetch GitHub `main`：根 `README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`，以及 research README、研究稽核／矩陣、AUTO-84 報告。當時 `sources.md` 全文不含兩個本輪 canonical path；GitHub code search 各為 0 結果；目標 AUTO-85 檔案不存在。GitHub code search 非全庫去重證明；未逐檔核對全部歷史 AUTO 檔與同文異址，**僅登記兩篇新來源候選**。
- 查核日：2026-10-29。主要閱讀頁為 USWDS 官方設計系統，輔助閱讀各自的無障礙測試清單。原始 UI preview 未實際操作；測試清單係閱讀其文字，不是本輪執行鍵盤、讀屏或手機測試。

## S01｜Date picker：新來源候選
- URL: https://designsystem.digital.gov/components/date-picker/ ；canonical `uswds:components/date-picker`；標題 **Date picker | U.S. Web Design System (USWDS)**；作者／維護者 USWDS / GSA；首次發表日未核，官方更新表包含 2026-08-18 v3.14.0。
- 輔助閱讀（**不計另一篇深讀**）：https://designsystem.digital.gov/components/date-picker/accessibility-tests/
- 閱讀事件：`AUTO-85-20261029-0435-DATETIME-RESEARCH-S01-R1-MAIN-AND-ACCESSIBILITY-TEXT-PARTIAL`。實際閱讀主文概述、HTML 表單標籤與格式提示、適用情境、手動輸入、鍵盤導覽、禁用與 aria-disabled、日期上下限、已知問題、16 項無障礙測試結果、更新表，以及輔助頁的條件式／例外測試說明。未完成實際 preview 互動、所有外部 issue 原文、讀屏與跨裝置測試，**FULL_R1=0**。
- 可核實原文重點：日曆有助排程及星期資訊重要的日期；熟知日期可改用一般日期欄位；允許手動輸入、明示格式；避免選取即自動提交；限制日期需告知原因。USWDS 16 項測試 13 PASS、1 PASS WITH EXCEPTIONS、2 CONDITIONAL、0 FAIL；其中操作說明仍有例外，不能稱完全無障礙。
- 反例 D1【將生日、補助首談日、核定期起日全部改成日曆選取】：生日等熟知或歷史日期未必需要逐月點選；首次實際補助服務日若被誤用預約日／建檔日，日曆再便利也不能保證資格期限正確。**日期輸入 UI≠日期語義／來源正確**。
- 反例 D2【設定最小／最大日期即認定補助資格已核准】：USWDS 的 `data-min-date` / `data-max-date` 是其 HTML 元件的可選日期限制，不能取代各方案期別、年齡、間隔、週限額與人工審查；Notion 原生日期屬性是否支援相同限制未核。
- 反例 D3【照搬美式 mm/dd/yyyy 與 disabled 規則】：臺灣作業人員若習慣 YYYY/MM/DD 或民國年，直接沿用美式提示可能造成日月顛倒；原生 `disabled` 可能不送出值、`aria-disabled` 則仍送值，兩者不能作為資料是否保存的推論；此為 USWDS HTML 行為，不代表 Notion 實測。

## S02｜Time picker：新來源候選
- URL: https://designsystem.digital.gov/components/time-picker/ ；canonical `uswds:components/time-picker`；標題 **Time picker | U.S. Web Design System (USWDS)**；作者／維護者 USWDS / GSA；首次發表日未核，官方更新表包含 2026-08-18 v3.14.0。
- 輔助閱讀（**不計另一篇深讀**）：https://designsystem.digital.gov/components/time-picker/accessibility-tests/
- 閱讀事件：`AUTO-85-20261029-0435-DATETIME-RESEARCH-S02-R1-MAIN-AND-ACCESSIBILITY-TEXT-PARTIAL`。實際閱讀主文範例 HTML、何時適用與替代、避免相依選單／自動提交、預設值、`data-min-time` / `data-max-time` / `data-step`、無障礙摘要 11 項、2026-08-18 更新與輔助測試頁的概述；未實際操作選單、完整逐項讀屏／鍵盤或使用者研究，**FULL_R1=0**。
- 可核實原文重點：常見固定間隔如 30 分鐘排程適用選時元件，歷史精確時間宜用自由文字；預設步距 30 分鐘、最小 1 分鐘，時間範圍以 24 小時格式設定；避免輸入後立即提交。USWDS 11 項無障礙測試為 9 PASS、2 CONDITIONAL、0 FAIL，仍需在各專案情境自行驗證。
- 反例 T1【預約時段每30分鐘一格便強迫歷史 Session 以30分鐘進位】：預約候選時段與實際開始／結束、改期、延長、遲到、no-show 是不同資料語義；將歷史時間四捨五入會影響時數、計費與查核。**排程選項≠實際執行時間**。
- 反例 T2【選了時間就視為已預約或完成】：USWDS 明確反對選項變動立即提交；前端選時成功不等於 Session 已持久化、時段未衝突、心理師可服務或個案已確認。若重試未知結果，可能重複建立紀錄；不能把 UI 事件當交易確認。
- 反例 T3【固定預設值、相依選單與時間範圍直接套入 Notion】：預設 09:00 可能掩蓋未確認時間；心理師、日期、診間相依選單可能讓使用者誤解選項突然消失；跨午夜、時區與夏令時間屬需另行界定的資料層問題。USWDS HTML 的 `data-step` 不代表 Notion 原生可設。

## 交叉反證、採用邊界
- 日期／時間輸入方便不等於 Session／Billing 的歷史交易快照正確，也不等於補助核定期與資格判斷正確。可借鏡「明示格式、可手動輸入、避免自動提交、區分已知歷史時間與可選排程」等設計原則，但不擅自導入外部 HTML 控件或改動 Notion。
- 尚待驗證：臺灣日期格式與民國年、同頁直顯流程、時間／日期欄位來源、補助期別、手機與輔助科技、Notion 原生支援、角色權限、效能及真人操作。全部 `NOT_TESTED`；設計狀態 `RESEARCH_ONLY / NOT_APPROVED`。

## 嚴格進度
- `NEW_SOURCE_CANDIDATE=2`；`MAIN_GUIDANCE_AND_ACCESSIBILITY_TEXT_PARTIAL_READ=2`；輔助 accessibility 頁 2 個 URL **僅作支持資料，不列為新增已深讀來源**；`INDEPENDENT_COUNTEREXAMPLE_GROUPS=2`、共6情境；`FULL_INDEPENDENT_REREAD_EXISTING=0`。
- `FULL_R1=0`、`FULL_R2_TO_R10=0`、`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`；累積可核實 **0/10,000 篇**。同一閱讀事件沒有拆成十次，搜尋命中、HTML 範例、兩個輔助頁沒有冒充額外十遍深讀。
- **NO NOTION/SYSTEM WRITE**：未改任何正式／TEST Notion 頁面、DB、View、Formula、Relation、權限或資料列；未改正式 GAS、Cloud Run、Session 或部署。未達研究門檻，未開始重新設計。
