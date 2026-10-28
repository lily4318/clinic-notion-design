# Notion 深度學習｜AUTO-74｜2026-10-28｜純研究
- Trace：`AUTO-74-20261028-1741-RESEARCH`；台灣時間2026-10-28 17:41起始；**只准公開資料研究及GitHub記錄，不准修改任何Notion／GAS／Cloud Run／Session**。
- 開始及寫入前重新讀取 main 七項規範（README、根AGENTS、source-of-truth、Notion AGENTS、sources、decision-log、acceptance-status）及 research 目錄85份Markdown（73份AUTO、12份非AUTO）；對本次新候選精確slug逐檔檢查85/85，當時未命中；sources及GitHub code search亦未命中。這是**精確字串／canonical路徑去重**，不代表已完成所有同文異址、翻譯版或內容指紋語義去重。
- 本輪不是把舊 `/help/forms`、`/help/layouts` 或 `/help/database-templates` 重新算作新篇：`/help/forms` 已在AUTO-01、`/help/layouts` 已在DS-018及其他批次、布局指南已在AUTO-26登記。重複候選已排除。
- 計數：**新來源候選1篇**（獨立編輯指南）、該篇主要文字閱讀1次、已登記來源獨立針對性複讀1次、跨來源差異核對1組；**嚴格完整深讀R1–R10仍均未達標，FULL_DEEP_PASS_10_OF_10新增0，累積可核實0/10000**。單一分析多個反例不能充作多次閱讀。

## S01｜新增候選：Use forms to collect, organize and act on responses right in your Notion workspace
- 原文：https://www.notion.com/help/guides/use-forms-to-collect-organize-and-act-on-responses-in-notion
- canonical：`notion-help:guides/use-forms-to-collect-organize-and-act-on-responses-in-notion`；來源／作者：Notion官方Help Guides；標示8 min read，首發／修訂日期頁面未核實；取證2026-10-28。與AUTO-01的參考手冊 `/help/forms` 是**不同編輯頁面**，但重疊主題不等於多次深讀同一篇。
- 閱讀軌跡：`AUTO-74-20261028-1741-RESEARCH-S01-R1-TEXT`；實際逐節讀取官方可取得的文字：Create forms from scratch or existing databases（新表單、既有來源、linked source不能直接加Form）；Customize forms（匿名、描述、必填、提交頁）；Use forms to build end-to-end workflows（自動指派與Slack/email通知）；Connect multiple forms to a unified database（多來源入口寫入同一DB）；Transform responses into insights with database views（Chart、Board、Calendar、Timeline）。讀取的外部文本範圍約官方頁面L106–L253；未打開所有折疊互動、原始圖片或影片。
- 可核實產品文字：表單可從原始資料來源建立，多表單可指向同一資料庫；表單回覆與資料庫欄位相連；文章以一般請求與回饋管理舉例，非醫療資料的安全認證或法規保證。功能與權限仍須以參考手冊及實際方案核對。
- 反例A（資料模型）：將「個案首次接洽」「補助資格」「收款問題」三張表單全部導向同一來源DB，雖有統一入口，可能混合不同法定保存、存取角色與資料生命周期；跨流程共庫**不等於**相同資料實體或安全的單一真相。
- 反例B（敏感資訊）：官網示範匿名回饋，若治療所使用匿名問卷處理補助資格或會談收費，缺少可驗證的個案ID及授權可能導致無法正確對帳；但一律要求身分也可能不適合一般匿名滿意度回饋。應先依用途分流，不能直接套模板。
- 反例C（自動化）：示例自動把表單內容寄送Slack/email適合一般工作請求，不代表可以寄送心理治療相關敏感資料；表單送出成功、工作者收到通知與正式補助核准／Billing入帳是不同狀態。
- 反例D（欄位）：在既有資料庫新增Form，若問題名稱／欄位型別直接映射正式欄位，可能影響其他View與Formula。使用者已要求不可擅改現有正式欄位，因此本輪不建立表單、也不提案直接接正式Session。
- 暫時推論：表單可以降低收集摩擦，但若缺少資料來源、權限、重複提交、同意與保存驗證，便利性可能放大錯誤。此推論非功能核准或實測。

## R01｜既有來源獨立針對性複讀：Build the perfect workflow with customizable layouts
- 原文：https://www.notion.com/help/guides/build-the-perfect-workflow-with-customizable-layouts
- canonical：`notion-help:guides/build-the-perfect-workflow-with-customizable-layouts`；已於AUTO-26 S01登錄，**本輪新篇數0**；本輪獨立軌跡：`AUTO-74-20261028-1741-RESEARCH-R01-TARGETED-REREAD`。閱讀官方主文Getting started with layout builder、Using layouts in your workspace、Central tracking, custom views for every team，特別檢查固定主區、可收合Details panel、Pinned、Property group及集中資料庫的範例。不是完整R2/R3。
- **新增跨文件反證（與AUTO-26不同）**：此指南文字仍說Pinned properties「up to four」，但同日官方最新參考文件 https://www.notion.com/help/layouts 的Heading & pinned properties節明示「up to 15」。**官方同域不同文件規格互相衝突**；不得以舊指南的4或新參考的15直接宣稱治療所實際UI可用數量，須在未來獲授權TEST環境核對版本、裝置與方案。這是研究中的證據衝突，不是本輪已修復的系統錯誤。
- 反例E：若按「最多四個」設計補助工作台，可能錯誤排除必要的個案餘額、期別、回報期限與警示；反之即使可放15個，全部置頂也可能造成橫向捲動，並不符合開啟即見。可見性需依實際螢幕與角色工作任務驗證。
- 反例F：共用DB的layout對所有頁面生效，不能用來假設不同角色或不同期別各有獨立欄位權限；Property group藏起來仍不等於保護敏感資料。此輪只記錄風險，不更改layout。

## 可稽核去重／品質與未完成
- 逐檔精確比對：研究目錄當時85份（73 AUTO＋12非AUTO）＋main sources全文；發現 `/help/forms` 已在AUTO-01、`/help/database-templates` 已在N09與批次03/04、layout指南已在AUTO-26；這些都**不算新篇**。新Forms Guide精確slug未命中上述已檢查文件，仍標**候選**而非全庫語義去重PASS。
- 本輪 **NEW_CANDIDATE=1，MAIN_TEXT_READ=1，TARGETED_REREAD_EXISTING=1，NEW_COUNTEREXAMPLE_SCENARIOS=6，FULL_DEEP_PASS_10_OF_10=0，CUMULATIVE_VERIFIED_10_OF_10=0/10000**。不把已讀章節、交叉文件、圖片替代文字、搜尋命中或一次分析當十遍完整深讀。
- 未驗：原圖、影片與折疊互動、鍵盤/讀屏/手機、真人Notion操作、表單匿名性與權限、正式個資法規合規、實際資料庫/Formula/歷史金額、真實效能。Notion及正式系統**零寫入**，沒有開始重新設計。完成10000篇各10次後仍須使用者明確確認才能進入設計。
