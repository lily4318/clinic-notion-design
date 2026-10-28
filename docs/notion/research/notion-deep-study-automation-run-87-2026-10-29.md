# AUTO-87｜Notion 深度學習：大量選項與字數限制的反例（2026-10-29）

Trace: `AUTO-87-20261029-0643-COMBO-CHAR-RESEARCH`。執行界線：RESEARCH ONLY；只讀外部官方文獻與GitHub，允許 GitHub 研究紀錄寫入；禁止 Notion／GAS／Cloud Run／Session／正式部署任何寫入。

## 基準、來源與去重
- 2026-10-29（Asia/Taipei）開始時重讀 main 的 README、根 AGENTS、docs/system/source-of-truth、docs/notion/AGENTS、sources、decision-log、acceptance-status；並讀 research/README、audit-checklist、首批證據清冊、批次02/03/04、manual-01、research-to-implementation-matrix、long-term-goals 與 AUTO-86。
- 在寫入前再次讀取最新 sources、decision-log、acceptance-status blob SHA；精確 canonical URL 在當期 sources 全文均未出現，GitHub code search 搜尋 `components/combo-box` 與 `components/character-count` 均未命中。未完成所有歷史 AUTO 文件逐檔比對、同文異址與跨語系語義指紋去重；故**僅新來源候選**，不能宣稱全庫唯一。
- 來源均為 U.S. Web Design System（USWDS；美國 GSA）官方 HTML 元件文件，不是 Notion 原生功能、也不是治療所現況。查核日 2026-10-29，文章首次發表日未核；版本更新日期不能冒充首發日。

## S01｜Combo box（候選新來源）
- 標題：**Combo box | U.S. Web Design System (USWDS)**；URL：https://designsystem.digital.gov/components/combo-box/；canonical `uswds:components/combo-box`；作者／維護：USWDS/GSA。
- 閱讀事件：`AUTO-87-20261029-0643-COMBO-CHAR-RESEARCH-S01-R1-MAIN-CODE-GUIDANCE-A11Y-PARTIAL`。實際開啟官方頁，讀元件定義、果物列表 HTML 選定範例（L188–L270）、Guidance/可用性/無障礙/設定（L342–L414）、更新表（L419–L458），並讀輔助無障礙清單 https://designsystem.digital.gov/components/combo-box/accessibility-tests/ 的狀態與部分測試條件。長列表程式碼未逐行比對兩個重複範例；沒有實際操作 Preview、鍵盤、讀屏或手機。**FULL_R1=0**。
- 來源事實：官方建議在選項超過15個或空間有限時考慮 combo box；選項少時可用 select/radio。建議熟悉的標籤、避免相依選項及選取即自動提交；已選預設值也需清楚。官方列16項 WCAG 測試：13 PASS、3 CONDITIONAL、0 FAIL；**同一官方頁仍明示輔助科技使用者的可用性疑慮，建議考慮 Select**。官方2026-08-18 v3.14.0 更新修正容器溢出，非首發日。
- 反例 C1【所有方案期別用一個可搜尋選單就不會選錯】：同一方案有多核定期別、金額不同；僅依模糊名稱過濾，仍可能選到舊期或錯誤方案。需要清楚辨識「方案＋有效期」並以資料層驗證當次適用性；搜尋便利不等於期別正確。
- 反例 C2【選取個案或方案時自動提交即可省步驟】：使用者可能仍在更正選項；若選取即建立 Billing/Session，可能產生錯帳或重複紀錄。選項選定、正式確認、後端保存與交易驗證須區分。
- 反例 C3【USWDS WCAG Passed 即可當 Notion 無障礙已通過】：官方明示輔助科技疑慮與3項 conditional；USWDS HTML/JS 元件不等於 Notion Select/Relation 原生操作，不能據此宣稱 Notion 的讀屏/鍵盤/手機已驗收。

## S02｜Character count（候選新來源）
- 標題：**Character count | U.S. Web Design System (USWDS)**；URL：https://designsystem.digital.gov/components/character-count/；canonical `uswds:components/character-count`；作者／維護：USWDS/GSA。
- 閱讀事件：`AUTO-87-20261029-0643-COMBO-CHAR-RESEARCH-S02-R1-MAIN-CODE-GUIDANCE-A11Y-PARTIAL`。開啟官方頁，讀定義/預覽文字（L188–L204）、HTML input/textarea maxlength/aria-describedby 範例（L205–L289）、使用時機/替代方案/JS降級（L290–L317）、9項測試摘要與已知問題（L318–L344）、更新表（L349–L389）；輔助清單 https://designsystem.digital.gov/components/character-count/accessibility-tests/ 僅作背景，未完整逐項操作。未實測 Preview、JS/無JS、手機或讀屏。**FULL_R1=0**。
- 來源事實：只有必要簡潔或法規字數限制時才建議顯示字數；若後端上限造成常見困擾，應優先評估提高上限。HTML 使用 maxlength、aria-describedby、無JS時備援文字。官方9項測試：7 PASS、1 PASS WITH EXCEPTIONS、1 CONDITIONAL；官方記錄讀屏及螢幕放大使用者難以辨識超限情況。2026-08-18 v3.14.0 有 iOS VoiceOver 宣告時機及初始化修正。
- 反例 T1【所有治療紀錄與個案主訴都限制120字，介面較整齊】：短字數可能截斷臨床必要事實或合法留存內容；UI 整潔不能凌駕完整性與資料保護。此研究**不建議變更臨床欄位**。
- 反例 T2【輸入框顯示尚可輸入N字就保證正式收據備註合規】：不同平台對中文字、emoji、組合字元及 UTF-16/Unicode 計數可能不同；USWDS HTML maxlength 不代表本所 Notion 或核銷系統實際限制，需以正式系統規則驗證；字數通過也不代表財務資料正確。
- 反例 T3【動態字數剩餘為綠色即人人可理解】：官方列1例外及1 conditional，已知讀屏/放大鏡超限提示問題；不能以顏色或前端動態訊息取代可理解錯誤與保存狀態確認。

## 交叉反證、界線與後續證據
- 介面「可搜尋」與「可限制字數」是輸入輔助，不是期別正確性、交易已保存、法定紀錄完整性或權限隔離的保證。對治療所應區分 **輸入候選→人工確認→資料層規則→成功持久化→後續核對**；但這是**未核准的研究推論**，不是 Notion 設計變更。
- 待核：Notion 原生 Relation/Select 搜尋及不同期別標籤、中文與組合字元計數、實際保存結果、手機/鍵盤/讀屏、角色權限、真人 UX、Session/Billing/Price Plan 歷史資料與效能；全部 NOT_TESTED。
- 本輪新來源候選2、主要正文/選定HTML與輔助無障礙文字部分閱讀2、反例2組6情境；完整獨立複讀0；`FULL_R1=0`、`FULL_R2_TO_R10=0`、`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`；**累積可核實 0/10,000 篇**。不把搜尋、兩組觀點或輔助清單計成多篇十次深讀。
- **NO NOTION/SYSTEM WRITE**：未改 Notion 正式/TEST 頁面、DB、View、Formula、Relation、權限或業務列；未改 GAS、Cloud Run、Session、部署。研究門檻未達，等待全部達標及使用者確認才進入重新設計；手動與排程研究可獨立並行。
