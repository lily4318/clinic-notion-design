# AUTO-90｜Notion 深度學習：Notion Agent 功能界線與 Forms 既有來源獨立複讀（2026-10-29）

Trace：`AUTO-90-20261029-0939-NOTION-AGENT-FORMS-RESEARCH`。**研究及 GitHub 進度紀錄 ONLY；NO NOTION／GAS／CLOUD RUN／SESSION WRITE**。本自動批次與聊天室手動研究並行，但不得把兩者同篇同次分析重複計量。

## 前置來源、去重與證據等級
- 2026-10-29（Asia/Taipei）開始前從 main 讀取 README、根 AGENTS、docs/system/source-of-truth、docs/notion/AGENTS、sources、decision-log、acceptance-status；檢查 research 目錄、README、evidence-register、audit-checklist、research-to-implementation-matrix、long-term-goals，以及 AUTO-01、AUTO-74、AUTO-89 與手動研究紀錄。每次共享檔寫入前再 Fetch 最新 main 與 blob SHA。
- **S01** `https://www.notion.com/help/notion-agent` 在本輪 main sources.md 全文及已抽查研究清冊未見精確 canonical；GitHub code search 不足以證明全庫唯一，故列**新來源候選**。不同語言頁或相同內容不另計。
- **R01** `https://www.notion.com/help/forms` 已在 AUTO-01 以 `AUTO01-01` 登錄，AUTO-74 再明確提及，**不算新來源**；本輪從官方原文獨立針對性複讀，不能將一次針對性複讀標成完整第2遍。
- 來源官方頁均為公開 HTML 可讀文字，並非真人操作、影片、原始截圖、手機／鍵盤／讀屏或本所 Notion 實測。首發及最後修訂日期未核實，僅記檢索日 2026-10-29。

## S01｜新來源候選：Notion Agent（官方 Help）
- 標題：**Notion Agent**；URL：https://www.notion.com/help/notion-agent；canonical ID：`notion-help:notion-agent`；來源／維護者：Notion Help Center／Notion Labs。
- 閱讀事件：`AUTO-90-20261029-0939-NOTION-AGENT-FORMS-RESEARCH-S01-R1-HTML-MAIN-SECTIONS-PARTIAL`。
- 實際讀取範圍：官網可讀正文 L107–L362，重點逐節 How to work、What can do、What can't do、Personalize、FAQs。包含影片連結，但**未播放影片、未檢查原始圖片、未操作任何 Agent**，不符合嚴格 FULL_R1。
- 官方明示：Agent 沿用操作者可存取權限（L124–126）；可查詢工作區資料、建立／修改頁面、資料庫、View、Relation（L146–195）；但不能新建資料庫 Automation、Template、Page Layout、Formula／Rollup／Button 等進階屬性，亦不能修改分享權限（L257–279）。同頁另稱可「Create, edit, and evaluate formulas」（L257），與「can't create ... advanced properties like formulas」（L264）存在**文字層級界線未明**：可能區分公式運算式與新建公式欄位，但不能在未實測前自行斷言。
- 官方亦說個人化指令頁若其他人可編輯，其更動會改變 Agent 回應（L280–310）；這不是權限隔離或資料完整性保證。
- 反例 A1【Agent 可修改 View，因此可一鍵安全建立跨期補助 Formula】：官方明示新建進階屬性受限，且 Formula 計算與實際業務真值不同；不能把自然語言生成視為對 Price Plan／Session／Billing 的驗證或修改授權。
- 反例 A2【Agent 跟隨登入者權限，所以共用管理員帳號可安全處理所有個案】：權限繼承不會替操作者做最小權限分工；若高權限帳號能讀取敏感資料，Agent 的可讀範圍也可能擴大。沒有本所角色實測，不得把其回答當權限審計。
- 反例 A3【把管理規則寫進多人可編輯的 Agent 指令頁，所有流程就會長期一致】：官方承認他人可修改指令時會影響行為；指令不等於版本化業務規則、授權或可回復交易。GitHub 決策與業務真值仍需分離；本輪未建立指令頁。

## R01｜既有來源獨立針對性複讀：Forms（不計新篇）
- 標題：**Forms**；URL：https://www.notion.com/help/forms；canonical ID：`notion-help:forms`，已在 AUTO-01 登錄。
- 閱讀事件：`AUTO-90-20261029-0939-NOTION-AGENT-FORMS-RESEARCH-R01-INDEPENDENT-TARGETED-REREAD-FORMS`。
- 本輪重新開啟官網 L107–L255，針對建立與既有資料庫、表單題目／欄位同步、分享權限、匿名、填寫與回應、匯出限制；其餘末段自動化只依當前搜尋文字參考。**非整篇所有媒體完整複讀**，不能算 FULL_R2。
- 官方明示：既有資料庫建立 Form 需要 Full access（L141–154）；表單問題預設與資料庫欄位名稱同步，關閉 `Sync with property name` 可讓顯示題目不同（L168–189）；公開連結可讓非工作區成員填寫，公開回應自動匿名，工作區內回應可設不同提交後權限（L196–235）；Form View 無法直接匯出，可從 Table View 匯出（L243–255）；複製他人模板的 Form 未另建可能把回應送至原作者（L237–238）。
- 反例 F1【把正式 Billing／Session 現有欄位直接轉成表單問題，只是美化文字】：預設題目改名會同步更動資料庫屬性名稱，可能影響其他使用者、View、外部整合的辨識；不能當純前端文案調整。未實測屬性 ID／公式引用是否自動保持，不宣稱必然斷裂。
- 反例 F2【公開 Form 自動匿名，所以適合所有個案／補助資料收集】：匿名不等於資料最小化、身分確認、合法告知或個資保護；用於匿名滿意度與需對帳的補助資格是不同目的，不能共用相同核驗假設。
- 反例 F3【填完表單且顯示成功，就代表資料可備查、可匯出、已獲核准】：Form View 本身不能直接匯出；回應進入資料庫也不代表核准、保存年限、對帳與存取權限已驗收。若複製外部模板未核對回應目的地，還有回覆流向錯誤風險。
- 與 AUTO-01 不同的本輪新增交叉重點：**Form 問題文案同步可能造成資料來源屬性命名副作用；Notion Agent 雖可建立／修改 View，卻不能因此假定能安全建立完整表單、公式、權限或臨床資料流程**。僅為研究風險，不授權新建表單或改 Schema。

## 嚴格計量、限制及不變事項
- `NEW_SOURCE_CANDIDATE=1`（Notion Agent，尚未全歷史語義去重）；`NEW_PARTIAL_MAIN_TEXT_READ=1`；`EXISTING_TARGETED_INDEPENDENT_REREAD=1`（Forms，不計新篇）；`COUNTEREXAMPLE_SCENARIOS=6`；`FULL_R1=0`；`FULL_R2_TO_R10=0`；`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`；累積可核實達標 **0／10,000篇**。
- 缺漏：全歷史同文異址及跨語系語義去重、全部原圖／影片／互動、手機、鍵盤、讀屏、真人 Notion、角色權限、Form 目的地／提交重複、實際 Formula、歷史費率與效能。不能把同一次分析的六個反例充當六遍閱讀。
- 本輪**沒有**修改任何正式／TEST Notion 頁面、資料庫、View、Formula、Relation、權限、業務資料，亦未更動正式 GAS、Cloud Run、Session 或部署；未達10,000篇×10次門檻，不開始重新設計。使用者未確認完成前不得改版。
