# AUTO-81｜Notion 深度學習：Question pages 與 Contact a department or service team（2026-10-29）

Trace: `AUTO-81-20261029-0038-RESEARCH`｜公開文獻研究與GitHub研究進度｜**NO NOTION/SYSTEM WRITE**

## 基準、去重與研究範圍
- 本輪開始重新讀取 main 的 `README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`，並閱讀 `research/README.md`、`research/audit-checklist-and-research-progress.md`、`research/research-to-implementation-matrix.md` 與 AUTO-80 紀錄。研究目錄列出92份檔案（含索引），不代表逐檔全文比對完成。
- 在來源索引全文查詢精確canonical URL兩項均未命中，GitHub程式碼搜尋相應slug均0筆。**尚未逐檔檢查全部歷史研究正文、跨語系/同文異址語義去重**，故兩項只能列「新來源候選」，不能宣稱全庫唯一。
- 來源為GOV.UK Design System team之公開設計指南，檢索日期2026-10-29；頁面初次發表/最近更新日期未核實。GOV.UK網站上的HTML/Nunjucks範例**不代表Notion原生功能或臺灣治療所已核准設計**。
- 實際閱讀官方網頁主要正文、選定程式碼範例、適用限制、研究與操作說明；未觀看全部獨立示例、圖片、互動、影片、鍵盤/讀屏/手機實測，因此**兩篇都不能計入完整R1，更不能計入R1–R10完成**。

## AUTO81-S01｜Question pages — GOV.UK Design System
- URL: https://design-system.service.gov.uk/patterns/question-pages/
- Canonical ID: `govuk-design-system:patterns/question-pages`
- 閱讀軌跡：`AUTO-81-20261029-0038-RESEARCH-S01-R1-MAIN-TEXT-PARTIAL`（首次、一次主要文字閱讀與反例分析，非完整深讀）。
- 取證範圍：官方頁面約L51–L215（基本問答頁/必填與選填/未知/返回/避免重問）、L327–L425（欄位標題與hint）、L550–L557（同頁多題例外）、L682–L738（繼續按鈕/進度指示/拖曳式滑桿限制），並核對頁內代表性HTML/Nunjucks表單範例。沒有逐一開啟所有獨立預覽或檢查原圖。
- 原文可支持：每個問題需有實際目的，只收必要資訊；有效的「不知道／不確定」應允許；選填欄位明示optional；預設一頁一題但**高頻切換的內部服務可以依使用者研究把相關問題同頁分組**；已輸入答案盡量重用；返回不可破壞已輸入狀態，付款等不可重複操作要阻止再次提交；冗長說明不塞在hint；進度條須能可靠顯示總數，否則不應憑空標進度。
- 反例A【將一頁一題當絕對規則】：若把治療所Billing、Session、補助用量每個屬性拆成獨立問答頁，行政人員需反覆跳轉，違反已確認「同類資料同頁、開啟即見」。反證：原文自身允許內部高頻工作將相關問題分組，設計必須由工作任務與真人驗證決定。
- 反例B【空白即零或必填】：把他處使用、首次服務日或核定額度的未知/未確認強迫填0，會造成補助資格與歷史費用的錯誤判斷。反證：允許真實未知，不可用表單格式把「未知/不適用/已確認0」合併。
- 反例C【返回重送交易】：使用者在Billing送出後按上一頁、再次按繼續，若沒有交易結果查核/防重處理，可能建立第二筆收款。反證：介面返回與實際寫入冪等是不同責任；本次沒有驗證Notion交易保證。

## AUTO81-S02｜Contact a department or service team — GOV.UK Design System
- URL: https://design-system.service.gov.uk/patterns/contact-a-department-or-service-team/
- Canonical ID: `govuk-design-system:patterns/contact-a-department-or-service-team`
- 閱讀軌跡：`AUTO-81-20261029-0038-RESEARCH-S02-R1-MAIN-TEXT-PARTIAL`（首次、一次主要文字閱讀與反例分析，非完整深讀）。
- 取證範圍：官方頁面約L51–L119（適用與聯絡範例）、L119–L168（順序/費用/服務時間/預期等待）、L169–L258（Inset/Details/HTML與Nunjucks）、L259–L269（研究基礎與待驗證）。原文稱來源研究曾做2輪、共12名參與者；其研究情境為英國政府服務，不可外推臺灣治療所成效。
- 原文可支持：聯絡管道排序依真實需求並跨頁一致；電話、電郵、webchat等需標明服務時段、可能費用與合理回覆等待；公開社群不能分享個人個案資料；大量低優先度聯絡資訊可收合，若只有1–2行則直接顯示；緊急聯絡與已登入使用者情境尚有研究缺口。
- 反例A【承諾不存在的行政服務】：沒有專職行政或實際SLA證據卻在頁面標「即時客服/兩個工作天回覆」，會造成錯誤期待。反證：範例時段與回覆時間不能直接複製；須有真正可履行的聯絡責任人與管道才可對外告知。
- 反例B【方便求助而洩漏敏感資訊】：將個案病歷、收款細節或補助身分引導到社群留言/公開頻道詢問，會擴大個資暴露。反證：公開管道僅適合一般性問題，涉及身分/臨床/財務應另經授權的安全流程。
- 反例C【所有求助入口一律收合】：將急迫的異常收款或錯誤補助核定求助入口藏在深層Details，使用者可能無法即時處理；但把全部支援SOP塞進日常工作台又增加負擔。反證：簡短必要求助資訊就近直接顯示；長說明/非急迫管道才按情境收合，且不能自行新增業務頁。

## 交叉反證與不可移植範圍
- **問題與聯絡資訊的顯示位置由使用者任務/風險決定**，不能僅套用「一頁一題」或「全部收合」。內部高頻操作的同頁直接顯示與清楚短提示是已確認需求；危險交易需分辨表單完成、資料已保存、正式核准。
- 這些是外部UX設計研究假設，不是Notion功能驗證、臺灣法規適用性判定或介面改版核准。若未來進入設計階段仍需核對實際Schema/View/Relation/角色權限、跨期價格快照、使用者操作與效能。

## 嚴格計量、阻礙及安全
- `NEW_CANDIDATE=2`、`MAIN_TEXT_PARTIAL_READ=2`、`INDEPENDENT_COUNTEREXAMPLE_GROUPS=2`（6個情境）、`FULL_INDEPENDENT_REREAD_EXISTING=0`。
- `FULL_R1=0`、`FULL_R2_TO_R10=0`、`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`；累積可核實`FULL_DEEP_PASS_10_OF_10=0/10000`。沒有以搜尋結果、不同角度或重複URL增加十次閱讀。
- 阻礙：全部歷史研究正文/同文異址語義去重未完成；獨立示例與圖片、鍵盤/讀屏/手機、真人Notion操作、角色權限、原生Formula、歷史Billing/Session/Price Plan與效能均未實測。
- **NO NOTION/SYSTEM WRITE**：未修改Notion正式/TEST頁面、資料庫、View、Formula、Relation、權限、業務資料；未修改正式GAS/Cloud Run/Session/部署；未達研究門檻，**不開始重新設計**。手動/排程研究雙軌獨立並行。
