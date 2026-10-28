# AUTO-86｜Notion 深度學習：檔案上傳與即時驗證的反例（2026-10-29）

Trace: `AUTO-86-20261029-0536-FILE-VALIDATION-RESEARCH`。僅公開設計文獻研究及 GitHub 進度記錄；**RESEARCH ONLY / NO NOTION OR SYSTEM WRITE**。

## 開始前基準與去重
- 2026-10-29 重新讀取 GitHub main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、decision-log.md、acceptance-status.md，以及 research README、首批 evidence-register、audit-checklist-and-research-progress、research-to-implementation-matrix、long-term-goals 與 AUTO-84／AUTO-85 研究紀錄。
- 研究清冊 `sources.md` 的當期全文未包含 `components/file-input` 或 `components/validation` 兩個 USWDS 精確 canonical URL；GitHub code search 各精確 URL／ID 無結果，且本輪檔案寫前不存在。**未完成全部歷史 AUTO 檔案逐一全文比對、跨語系或同文異址內容指紋去重**，故僅標記兩篇「新來源候選」，不是全庫已證唯一。
- 來源是 USWDS/GSA 外部 HTML 設計元件，不是 Notion 原生功能文件；原始互動 preview、手機／鍵盤／讀屏、Notion 角色權限與真實業務資料未操作，不能算完整 R1。

## S01｜File input：新來源候選
- 標題：**File input | U.S. Web Design System (USWDS)**；URL：https://designsystem.digital.gov/components/file-input/；canonical `uswds:components/file-input`；維護者 U.S. Web Design System / GSA；查核日 2026-10-29，首次發表日未核。更新表列 2026-08-18 v3.14.0 手機提示、初始化及色彩更新，不能當成文章首次發表日期。
- 輔助原始清單（**不另計已深讀來源**）：https://designsystem.digital.gov/components/file-input/accessibility-tests/ 。
- 閱讀事件：`AUTO-86-20261029-0536-FILE-VALIDATION-RESEARCH-S01-R1-MAIN-SELECTED-CODE-ACCESSIBILITY-TEXT-PARTIAL`。已讀主文 L188–L215、HTML file input 的單檔／多檔／accept／image／錯誤示例 L218–L386、Guidance L387–L451、更新紀錄 L456–L542，以及無障礙清單主文／選定測試 L188–L483。未實際點選、拖曳、傳送任何檔案；未逐一執行15項無障礙測試，**FULL_R1=0**。
- 可核實官方重點：文件必要時才要求上傳；選填文件不宜變成強制；此元件不支援非同步上傳（隨表單提交 POST），避免大檔與有限網路的負擔；提示檔案格式/大小，優先單一輸入欄位一個檔案；`accept` 限制與 UI 錯誤提示是 USWDS 元件行為。15項官方無障礙測試 13 PASS、2 PASS WITH EXCEPTIONS；原測試清單仍記錄焦點合併與讀屏錯誤提示例外。USWDS 自身的測試不能視為 Notion 或本所通過。
- 反例 F1【附件預覽成功就標示正式已收到收據／證明】：USWDS 會顯示檔名及預覽，但其元件文件明確表示非非同步上傳，可能尚未提交；**選取／預覽≠遠端持久化／可開啟／人工核對／正式收據成立**。對 Billing、申報與附件須另辨識保存狀態與關聯。
- 反例 F2【強制每一筆 Session 都上傳文件】：若業務情境不需要附件，強制上傳會增加行政負擔與敏感個資蒐集；「只在必要時索取」比多一個漂亮上傳區更重要。上傳檔案的資料保護、保存期間及角色權限仍須獨立查核。
- 反例 F3【依 USWDS 的 accept／拖曳行為推定 Notion 已防堵不合法檔案】：檔案類型提示或前端限制不是伺服器端的安全檢驗；手機與讀屏的選檔方式不同，不能直接把 HTML 元件或 WCAG 標記視為 Notion 原生支援。

## S02｜Validation：新來源候選，含官方停用警示
- 標題：**Validation | U.S. Web Design System (USWDS)**；URL：https://designsystem.digital.gov/components/validation/；canonical `uswds:components/validation`；維護者 USWDS/GSA；查核日 2026-10-29，首發日未核；官方更新表列 2025-03-26 v3.12.0 的 deprecation 說明。
- 閱讀事件：`AUTO-86-20261029-0536-FILE-VALIDATION-RESEARCH-S02-R1-MAIN-EXAMPLE-ISSUES-TEXT-PARTIAL`。已讀官方主文 L195–L214、HTML/JS 驗證範例 L215–L275、Guidance/known issues L276–L305、版本表 L306–L349；並查看官方 issue https://github.com/uswds/uswds/issues/5750 的標題/狀態作交叉線索，**未對該 issue 完整深讀**。未實際操作 preview、輔助科技或驗證後端，**FULL_R1=0**。
- **重要反證**：USWDS 官方在此頁明確警告其 Validation 元件有重大可用性與無障礙問題，規劃自 v3.12.0 後停止支援並在未來版本移除；頁面仍保留可用示例與使用說明，**「文件仍有範例」不等於「推薦新系統採用」**。已知問題包括讀屏／放大鏡使用者不易察覺狀態變化，以及部分使用者不理解驗證元件的用途。其即時驗證發生於前端，官方要求伺服器端另行驗證。
- 反例 V1【看見綠色勾選就視為補助資格核准】：即時 checklist 只表示特定輸入規則在前端通過，不代表政府補助的方案期別、個案資格、付款狀態或歷史金額已經人工核實。**格式驗證≠業務規則驗證≠核准**。
- 反例 V2【因為有官方範例就照搬到 Notion 或 GAS】：官方已宣告此元件停止支援／待移除；套用範例可能引入可用性問題。即使採其他驗證方法，前端檢查亦不能取代資料層驗證、權限與重複交易保護；此研究不授權修改任何前台。
- 反例 V3【只靠顏色／動態勾選顯示欄位正確】：讀屏與放大鏡可能無法感知狀態變化；若未提供清楚錯誤文案與可恢復路徑，可能讓工作者誤以為 Session 或 Billing 已保存。即時提示與實際寫入結果須分開呈現。

## 交叉反證與未採用邊界
- **文件上傳狀態、前端輸入驗證、遠端保存結果、業務資格核准是四個不同層次。** 不能以檔案預覽、綠勾或官方 WCAG 標籤當成真實資料已保存、已核准或本所無障礙驗收。
- 對本所可供未來評估的原則：只要求必要文件、清楚說明格式／上傳狀態、降低多檔誤操作、避免過時或停用元件、錯誤訊息可被不同輔助科技理解。**僅研究推論；未核准 Notion 設計，也沒有對現況提出寫入。**
- 待核：Notion 當前附件屬性／實際上傳流程、存取權限、保存／備份、附件與 Billing/Session 的關聯、真人使用性、手機/鍵盤/讀屏、資安與載入效能。全部 `NOT_TESTED`。

## 嚴格計量與安全界線
- `NEW_SOURCE_CANDIDATE=2`；`MAIN_TEXT_AND_SELECTED_CODE_PARTIAL_READ=2`；輔助 accessibility 清單及 GitHub issue **不另計已深讀**；`INDEPENDENT_COUNTEREXAMPLE_GROUPS=2`，共 6 個反例；`FULL_INDEPENDENT_REREAD_EXISTING=0`。
- `FULL_R1=0`、`FULL_R2_TO_R10=0`、`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`；累積可核實 **0/10,000篇**。同一閱讀事件沒有拆成十遍。
- **NO NOTION/SYSTEM WRITE**：沒有修改正式或 TEST Notion 頁面、DB、View、Formula、Relation、權限或業務資料；沒有修改正式 GAS、Cloud Run、Session 或部署。10,000篇各10次尚未完成，不開始重新設計；手動與每小時研究可並行。
