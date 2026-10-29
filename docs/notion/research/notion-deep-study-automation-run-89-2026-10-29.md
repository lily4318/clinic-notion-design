# AUTO-89｜Notion 深度學習：警示訊息與確認對話框的適用邊界（2026-10-29）

Trace: `AUTO-89-20261029-0838-ALERT-MODAL-RESEARCH`。範圍：**RESEARCH ONLY / NO NOTION OR SYSTEM WRITE**。本次為自動研究獨立單元，不取代聊天室手動續作。

## 開始前檢核與去重
- 2026-10-29 08:38–08:4x（Asia/Taipei）讀取 main：README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、sources.md、decision-log.md、acceptance-status.md、research/README.md、audit-checklist-and-research-progress.md、evidence-register-2026-10-24.md、research-to-implementation-matrix.md、AUTO-88研究紀錄，並檢視研究目錄與來源索引。
- sources.md 精確 URL 未出現下列兩筆；GitHub code search 查兩個 URL 未命中。這**不是**全歷史研究檔逐一全文比對、同文異址、跨語系語義去重的證明；僅列「新來源候選」，不宣稱全庫唯一。每篇本次僅一個部分閱讀事件，不把相同頁的不同分析角度當作多次閱讀。
- 來源均為美國 GSA 維護的 **U.S. Web Design System (USWDS)** HTML 元件指引，**非 Notion 原生功能**。查核日 2026-10-29，首發日期未查核；版本更新表不可當作首發日期。兩份無障礙測試清單僅作輔助證據，未另計篇數。

## S01｜Alert（新來源候選，文字與選定 HTML 部分閱讀）
- 標題：**Alert | U.S. Web Design System (USWDS)**；canonical URL：https://designsystem.digital.gov/components/alert/；ID `uswds:components/alert`；作者／維護者：USWDS／U.S. General Services Administration。
- 閱讀事件：`AUTO-89-20261029-0838-ALERT-MODAL-RESEARCH-S01-R1-MAIN-SELECTED-HTML-GUIDANCE-A11Y-PARTIAL`。
- 讀取範圍：官方頁定義/資訊、警告、成功、錯誤、緊急及簡化變體的選定 HTML（網頁約L188–L383）；Guidance 的適用與替代（L384–L401）；Accessibility 的警示類別、文字優先及 `role=alert/status/region` 差別（L402–L427）；變體與官方測試摘要（L442–L472）；版本更新表（L477–L489）；另查看輔助 https://designsystem.digital.gov/components/alert/accessibility-tests/ 的官方測試資料頁。沒有完整操作所有預覽、實際讀屏或手機測試；**FULL_R1=0**。
- 原文重點：Alert 用於系統狀態、欄位驗證與操作回饋；長表單仍應有欄位旁錯誤；不可逆刪除宜考慮明確確認；警示標題簡短並提供下一步；過多通知會降低注意；不能只靠顏色或圖示。 `role="alert"` 針對急迫重要訊息，`status` 為一般狀態，`region` 為可找回的非打斷資訊。官方9項無障礙測試3 PASS、6 CONDITIONAL、0 FAIL；並非本所測試。2026-08-18官方更新了警示類型文字優先的指引。
- 反例 A1【每個補助個案都常駐紅色警告最安全】：若把未確認、已確認0、期別已結束、真正阻塞錯誤都塗成紅色，將造成警示疲乏與誤判；需要可理解的分類及適當優先級，不得自動推定補助不合格。
- 反例 A2【選取 Price Plan 後顯示綠色成功即代表補助核准／Billing入帳】：Alert 是呈現狀態的介面，不驗證方案資格、Session 實際寫入、收款或後端持久化；成功訊息必須有對應的已驗證業務事件，不可用 UI 顏色代替交易證據。
- 反例 A3【把每筆個案錯誤詳情放在共用首頁警示最容易發現】：同頁警示若直接暴露敏感個案/收費內容，可能跨角色洩漏；隱藏/收合 Alert 也不是權限隔離。只可研究最小必要訊息與角色可見性，尚未核實 Notion 權限。
  
## S02｜Modal（新來源候選，文字與選定 HTML 部分閱讀）
- 標題：**Modal | U.S. Web Design System (USWDS)**；canonical URL：https://designsystem.digital.gov/components/modal/；ID `uswds:components/modal`；維護者：USWDS／U.S. General Services Administration。
- 閱讀事件：`AUTO-89-20261029-0838-ALERT-MODAL-RESEARCH-S02-R1-MAIN-SELECTED-HTML-GUIDANCE-A11Y-PARTIAL`。
- 讀取範圍：定義與預覽文案（網頁L188–L224）；一般、大型及強制選擇三種選定 HTML（L225–L389，包含 `aria-labelledby`、`aria-describedby`、`data-force-action`）；使用/替代/可用性與鍵盤焦點指引（L554–L604）；無障礙測試摘要與版本修正（L620–L657）；另參照 https://designsystem.digital.gov/components/modal/accessibility-tests/ 。未實際操作瀏覽器 Modal、鍵盤、讀屏或手機，未測 Notion 原生能力；**FULL_R1=0**。
- 原文重點：Modal 暫時封鎖背景內容並強制聚焦；應少用，尤其避免多步驟與複雜表單。不可逆操作可用明確確認；一般欄位錯誤/成功/警告更適合頁面內訊息。操作按鈕需清楚說明結果；不應任意自動跳出。焦點應限制在對話框，關閉後背景內容不應意外重新載入。官方14項測試13 PASS、1 CONDITIONAL、0 FAIL。2026-08-18 v3.14.0修復關閉後背景仍對讀屏隱藏、讀屏重複朗讀等缺陷；官方修復不代表本所 Notion 已支援。
- 反例 M1【每次編輯 Session、修改 View 或選方案都彈出強制確認最安全】：高頻且可回復操作若反覆中斷，增加負擔、使人機械點選；真正高風險或不可逆的操作才需評估是否中斷，不能把確認視為後端資料完整性檢查。
- 反例 M2【使用者按下「我同意」就等於取得法定同意或核准補助】：Modal 的確認按鈕不是可稽核的知情同意、角色授權或核定期資格證明；缺乏身分、內容版本、時間及業務規則的核實，不得把 UI 點擊當正式紀錄。
- 反例 M3【跳出「即將逾時／未儲存」就保證資料不會遺失】：對話框不會自行保存草稿；若開啟按鈕消失、焦點管理失敗或關閉後重載，可能使使用者無法操作或遺失工作；官方2026年仍修復相關無障礙缺陷，不能推論 Notion 原生 Modal 或保存行為等同USWDS。

## 交叉反證與結論（研究推論，非核准設計）
- Alert 是**傳遞已知狀態與復原下一步**；Modal 是**要求使用者聚焦決定**；兩者都不是權限隔離、交易保存、業務核准或歷史費率快照。先辨識「資訊提示／可復原錯誤／真正不可逆操作／交易結果未知」，不能一律採紅色 Alert 或強制 Modal。
- 與既有 AUTO-83 GOV.UK Interruption 研究屬相近議題，但**來源 canonical URL 不同**，本次只記新文件的部分閱讀，不重複計入 AUTO-83 的閱讀輪次。
- 後續驗證門檻：先有使用者明確核准且研究10,000×10完成後，才可評估實際 Notion 可否支援相當行為；需角色權限、手機、鍵盤/讀屏、警示疲乏、真人任務時間、歷史 Billing/Session/Price Plan 資料真值與效能證據。當前全為 `NOT_TESTED`。

## 嚴格計量與安全
- `NEW_SOURCE_CANDIDATE=2`；`PARTIAL_MAIN_TEXT_AND_SELECTED_HTML_READ=2`；`COUNTEREXAMPLE_GROUPS=2`（共6情境）；`FULL_INDEPENDENT_REREAD_EXISTING=0`；`FULL_R1=0`；`FULL_R2_TO_R10=0`；`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`；累積可核實完成 **0／10,000篇**。沒有將無障礙測試清單或同篇多角度另計來源。
- 未完成：全部歷史/同文異址/跨語系語義去重、完整原圖/互動、手機/鍵盤/讀屏、Notion實機、角色權限、歷史金額、Formula、載入效能與真人 UX。
- **NO NOTION/SYSTEM WRITE**：本輪只研究與更新 GitHub 記錄，未修改正式或 TEST Notion 頁面、資料庫、View、Formula、Relation、權限、業務列，也未改正式 GAS、Cloud Run、Session 或部署。10,000篇各10次門檻未達，不開始重新設計；自動與手動研究路徑獨立並行。
