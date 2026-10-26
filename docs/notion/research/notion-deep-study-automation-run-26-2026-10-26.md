# Notion 深度學習｜AUTO-26｜2026-10-26｜僅研究

- Trace：`AUTO-26-20261026-1742-RESEARCH`；路徑：每小時自動排程；與手動續作獨立，研究清冊共用。
- 範圍：僅公開原文閱讀、反例分析、GitHub 研究紀錄。**不修改 Notion 頁面、DB、View、公式、Relation、權限、正式 GAS／Cloud Run／Session；不進入重新設計。**
- 前置：重新讀取 main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、sources.md、decision-log.md、acceptance-status.md；核對 sources.md 指向的 32 份研究文件與另已知十面向清冊。當期來源索引未包含以下兩篇新候選。已登錄的 NN/g Data Tables 與 Information Scent 另列舊來源，不重算新篇。
- 計數口徑：canonical 身份去語系／追蹤參數；主要文字 R1 不等於完整圖文／影片／實作的 FULL_DEEP_PASS；同一回合多個分析角度不算多輪。

## 新來源 S01｜Notion 官方：Build the perfect workflow with customizable layouts

- URL：https://www.notion.com/nb/help/guides/build-the-perfect-workflow-with-customizable-layouts
- canonical：`notion-help:guides/build-the-perfect-workflow-with-customizable-layouts`；title：Build the perfect workflow with customizable layouts；發布／修訂日：原文未核實。
- 取證：2026-10-26 直接開啟完整可取得的主要文字節（Getting started with layout builder；Using layouts in your workspace；Central tracking, custom views for every team），包括頁面主區、右側 Details panel、最多四個 pinned properties、property group、modules、共享 DB 的不同檢視用途。原文「Editing layouts with layout builder」含互動展開區塊，本輪未操作，圖像亦未逐張檢視。
- 先驗假設：把次要屬性收進右側詳情，主畫面只留四個重點欄位，能讓治療所工作台更清楚。
- **反例 1**：使用者已明確要求補助餘額、期限、回報設定同頁直接看見。若把待核對或超額狀態放進 Details panel，雖減少首屏欄位，卻增加查看步數，甚至讓人誤以為未顯示即不存在。
- **反例 2**：同一資料庫的 layout 若影響所有記錄頁，將單一角色視為標準可能使其他角色常用資訊變難找；而主頁顯示優先序也不能代替資料存取權限。
- 暫存結論（RESEARCH_ONLY）：屬性置頂應以「日常決策必需」而非外觀整潔排序；若未經多角色／手機實測，不宣稱側欄布局改善效率，也不據此修改現有頁面。
- 本輪閱讀標記：`AUTO26-S01/R1_MAIN_TEXT+COUNTEREXAMPLE`；**不是完整深讀1/10**。

## 新來源 S02｜NN/g：User Intent Affects Filter Design

- URL：https://www.nngroup.com/articles/applying-filters/
- canonical：`nngroup:articles/applying-filters`；title：User Intent Affects Filter Design；作者 Katie Sherwin；原文日期 2016-02-07。
- 取證：2026-10-26 直接閱讀 Introduction、When to Apply the Filters（探索式即時 vs. 已知多條件批次、速度、回饋）、Scrolling the New Results into View、Conclusion。文內動態示範未播放；屬一般網站／電商 UX 原則，非 Notion 原生功能承諾。
- 先驗假設：每改一個條件就即時更新資料，最直覺。
- **反例 1**：工作者一次設定「方案＋核定期別＋待核對」三條件時，若每選一次就刷新或移動焦點，可能使工作中斷；低速網路／手機尤甚。反過來，純批次篩選可能讓探索者無法及時發現零結果，不能一概規定。
- **反例 2**：套用篩選後強制捲到頂端，可能打斷仍在選條件者；完全不移動又可能只剩少量結果卻在畫面外，讓人誤判為空。須按工作者當下意圖與可見回饋判斷。
- **反例 3（業務安全）**：篩選視圖只改呈現，不等於更動補助期別權威資料、授權隔離或核定結果；「查不到」不能推論「資料不存在／額度0」。
- 暫存結論（RESEARCH_ONLY）：研究未來可測「多條件查找」與「探索式篩選」兩種真實情境；不得宣稱 Notion 目前支援文中所有互動機制。
- 本輪閱讀標記：`AUTO26-S02/R1_MAIN_TEXT+COUNTEREXAMPLE`；**不是完整深讀1/10**。

## 已登錄來源的本輪針對性閱讀（不計新來源）

### AUTO26-R01｜NN/g Data Tables: Four Major User Tasks
- URL：https://www.nngroup.com/articles/data-tables/；canonical `nngroup:articles/data-tables`。
- 去重證據：批次02 UX-019 已列 `SUMMARY_ONLY`，批次03 亦明示先前直開逾時且不得新增。
- 本輪首次成功直接開啟可取得的正文：Tables vs Cards、Find、Compare、View/Edit/Add、Single/Batch Actions、Summary。新反例：表格適合跨個案比較，但「單列編輯」若以遮蔽原表格的彈窗處理，可能使工作者無法對照其他記錄；反之讓所有欄位一直展開也會增加誤改風險。研究只支援情境測試，不等於 Notion 支援凍結欄位等文章舉例功能。
- 標記：`AUTO26-R01/TARGETED_BODY_READ`，不算新 URL、不升級成嚴格 FULL_DEEP_PASS；未完整驗圖。

### AUTO26-R02｜NN/g Information Scent: How Users Decide Where to Go Next
- URL：https://www.nngroup.com/articles/information-scent/；canonical `nngroup:articles/information-scent`。
- 去重證據：2026-10-24 evidence-register U03 已登錄。此次直接閱讀定義、標籤、摘要與圖片、頁面脈絡、先前經驗、社會線索、clickbait 各節。
- 新反例：將「額度」「設定」「回報」寫成單字捷徑，熟悉系統者可能理解，新進人員卻不知是個案餘額還是心理師週額度；但把所有入口寫成長句也會使首屏壅塞。資訊氣味依使用者任務與脈絡而變，不能只看標籤字數判好壞。
- 標記：`AUTO26-R02/TARGETED_BODY_READ`，不算新 URL或完整複讀10次；圖片未逐張檢查。

## 嚴格計數與限制

- 新 canonical 候選：2 篇（依當期 sources.md、32份其連結研究文件及另已知十面向文件核對；仍未完成全儲存庫所有未索引檔的機器去重）。
- 新來源主要文字閱讀：2 篇；首次獨立反例：2 次；已登錄來源本輪針對性文字閱讀：2 次；**本輪 FULL_DEEP_PASS_10_OF_10：0**。
- 累積可稽核 10 次獨立完整深讀：**0／10,000 篇**（依目前研究證據；不可把 R1、SUMMARY_ONLY、目錄、圖像說明或一次多角度分析冒充完整深讀）。
- 未檢查全部圖片、動態影片、折疊內容，未複製模板、未操作真實 Notion、未測真人 UX／手機／權限／速度／公式／政府規則。
- 研究假設不等於設計決議，尚未獲得改版許可；保留既有同頁直見與通用跨期資料模型的使用者要求。
