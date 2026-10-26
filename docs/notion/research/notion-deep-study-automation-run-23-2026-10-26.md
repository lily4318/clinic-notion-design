# Notion 深度學習｜AUTO-23｜頁面驗證治理與跨裝置情境（2026-10-26）

> Trace: `AUTO-23-20261026-1436`；僅公開文獻研究與GitHub研究進度紀錄；未讀寫Notion業務資料／頁面／Schema／View／Formula／Relation／權限，也未改GAS、Cloud Run或Session。未開始重新設計。

## 0. 基準、去重與證據限制

- 本輪開始從 `main` 重新讀取 `README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`、`docs/notion/research/README.md`、首批 evidence-register、AUTO-21/22原始研究；亦以來源索引所記AUTO-01～22及歷史批次進行canonical核對。GitHub code search對候選slug無命中，惟索引可能延遲，故以實際取得的 sources.md 全文為主要去重基準。
- `wikis-and-verified-pages` 已於 **AUTO-07** 登錄，**不得計新增篇數**；本輪對它做新的針對性文字複讀 `TARGETED_R2`，非第二次完整深讀。
- 新候選 `guides/verify-knowledge-your-teammates-can-trust-with-page-verification` 與 `nngroup:articles/context-specific-cross-channel` 在本輪讀取的 main 來源索引未見；各只計一篇，不把跨語系網址、段落、角度或搜尋命中另算篇數。
- 閱讀日期 2026-10-26（Asia/Taipei）。Notion兩篇頁面未見可核實發表/修訂日，標 `UNKNOWN`；NN/g明示作者Kim Flaherty，2017-02-26。實讀主要文字內容；未逐張解讀圖片、展開每個互動折疊段、觀看影片或登入實帳操作；因此 **均非 FULL_DEEP_PASS**。

## 1. AUTO23-S01｜Verify knowledge your teammates can trust

- **標題／URL**：Verify knowledge your teammates can trust；https://www.notion.com/en-gb/help/guides/verify-knowledge-your-teammates-can-trust-with-page-verification
- **作者／來源**：Notion Help Guide；canonical `notion-help:guides/verify-knowledge-your-teammates-can-trust-with-page-verification`；類別：知識治理、版本信任、維護責任；日期 `UNKNOWN`。
- **閱讀證據**：2026-10-26開啟網頁正文行106–214，閱讀「Which pages should I verify?」「Three ways your organization can leverage page verification」「Create a verification rhythm and strategy」「View all your verified pages」。行151–153、165–177與191–195有未展開的互動區塊；部分示意圖未逐張檢視。狀態 `R1/MAIN_TEXT+COUNTEREXAMPLE_1`。
- **原文主張**：優先驗證高頻、高風險、影響決策、具權威性的文件；驗證標記有助搜尋辨識；可以指定Owner、定期失效提醒或選擇無期限；設定頁集中查看已驗證頁。
- **假設**：只要行政文件顯示已驗證藍勾，當期補助資格、額度、跨期規則就自然是正確且最新的。
- **反例A**：某文件去年驗證並設為「無期限」，今年核定辦法已改，藍勾仍可能存在；標記是內容治理訊號，**不是**官方法規、業務資料或公式真值的保證。
- **反例B**：具有編輯權的人可操作驗證；組織內部的正式核准人、Notion頁Owner與政府核定者未必相同。若不另訂責任分工，勾選動作不能等同正式核准。
- **更新認識**：可把「驗證」視為文件信任提示的研究候選，但不能當成補助資格/額度通過或權限隔離；且需與官方Help的Business/Enterprise限制交叉核對。**不提出已核准新功能**。
- **待核**：全部展開區、圖片、Notion工作區方案權益、角色權限、失效後搜索表現、真實文件治理流程；第2–10次獨立完整深讀未做。

## 2. AUTO23-S02｜Optimizing for Context in the Omnichannel User Experience

- **標題／URL**：Optimizing for Context in the Omnichannel User Experience；https://www.nngroup.com/articles/context-specific-cross-channel/
- **作者／日期**：Kim Flaherty，Nielsen Norman Group，2017-02-26；canonical `nngroup:articles/context-specific-cross-channel`；類別：跨裝置工作流程、情境式UX。
- **閱讀證據**：2026-10-26開啟正文行40–147，閱讀「What Makes Up Context of Use」「Channel Strengths」「Desktop/Laptop Channels」「Mobile-Phone and Tablet Channels」「Optimization vs. Consistency」「Optimized for Context」。頁面內各例子的圖片未逐張檢視；原文為一般跨通路UX研究，不是Notion功能文件。狀態 `R1/MAIN_TEXT+COUNTEREXAMPLE_1`。
- **原文主張**：桌機較適合複雜資料比較、長表單與多工；手機偏向短時、易中斷的微任務；應維持核心資訊與操作的一致性，但可依裝置調整布局與優先順序。
- **假設**：治療所桌機工作台若可看見全部資料，直接把相同密集欄位堆在手機就一定達成跨裝置一致。
- **反例A**：心理師用手機只需快速核對本週回報狀態，若首屏須橫向捲動數十欄，可能無法在中斷情境迅速完成；但反向地，**把關鍵額度藏在多層頁面**也會違反使用者要求的同頁直顯。
- **反例B**：把桌機的完整核定期比較縮成手機一個單一「可用」徽章，會掩蓋未知、未確認0與超額風險；裝置適配不能犧牲重要狀態與同源數值。
- **更新認識**：跨裝置一致性應優先是**業務真值、狀態語義與關鍵操作可達**，不等於版面像素一致。是否需要差異布局須待真人任務測試，不能把NN/g一般原則當作Notion可自訂行動版布局的能力證據。
- **待核**：示意圖片、真實Notion手機/桌機工作流程、角色差異、可用性與操作時間；第2–10次完整深讀未做。

## 3. AUTO23-R01｜Wikis & verified pages（AUTO-07既有來源針對性複讀）

- **URL**：https://www.notion.com/en-gb/help/wikis-and-verified-pages；canonical `notion-help:wikis-and-verified-pages`；原始登錄AUTO-07，**非新增來源**。
- **本輪複讀範圍**：正文行106–246，包含Wiki建立/撤銷、三種預設檢視、驗證到期通知、wiki與一般頁/DB驗證、移除驗證與已驗證頁管理。標 `TARGETED_BODY_REVIEW_R2 + NEW_COUNTEREXAMPLE`，不是完整第二輪深讀。
- **新的反例A**：官方說Wiki由獨立頁轉換且需Full access，並非把任一現有業務資料庫直接轉成Wiki；若為了「已驗證」標記重構現有補助資料來源，可能改變使用路徑且無授權，不能推導為必要措施。
- **新的反例B**：官方明示非Wiki一般頁與一般資料庫的驗證功能限Business/Enterprise；指南中的「幾下點擊即可驗證」不能外推為所有方案皆有。將文件驗證標籤當作個案資格或政府核銷核准亦不成立。
- **待核**：已註記示意圖片、實帳權益、角色操作與不同頁面類型，尚未完整實測。

## 4. 交叉反證、計數與安全界線

- **跨文獻結論**：文檔驗證是內容治理，不能取代政府規則核實與資料計算；跨裝置一致是業務狀態和可完成任務的一致，不能用美觀的單一徽章遮蔽未知或過期。兩項均只是研究假說，不授權修改現有Notion。
- 本輪新去重候選：**2篇**；新來源可讀主要正文+首次反例：**2次**；既有來源針對性複讀：**1次**；新完成10/10嚴格深讀：**0篇**；可核實累積10/10仍 **0/10,000篇**。全域唯一來源總數尚未完整機器稽核，不虛構精確值。
- 嚴格未驗：圖片、互動區塊、真人角色/手機/效能、Notion方案權益、公式與政府資料；本輪Notion及正式系統零變更，未進入重新設計。自動與手動研究維持雙軌，寫入GitHub需最新SHA條件與寫後讀回核驗。
