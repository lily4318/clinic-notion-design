# Notion 深度學習｜AUTO-72｜2026-10-28（純研究，PARTIAL）

Trace: `AUTO-72-20261028-1544-RESEARCH`。研究日：2026-10-28（臺灣時間）；範圍僅公開外部資料閱讀、獨立反例分析、GitHub 研究紀錄。禁止修改 Notion／正式系統。

## 基準、來源發現與去重
- 本輪已從 main 重新 Fetch 根 `README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`decision-log.md`、`acceptance-status.md`、`research/README.md`、`research/audit-checklist-and-research-progress.md` 及 AUTO-71 研究紀錄。
- 在 main 的 sources.md 全文與 GitHub repo code search 中查核 `phase-banner`、`exit-a-page-quickly`、`Exit a page quickly`，均未命中；寫入前重新 Fetch sources/decision/acceptance 的最新 blob SHA，且 AUTO-72 檔案不存在。此查核不等於全歷史研究文件逐檔全文、同文異址的精確去重；本輪兩篇僅列**新來源候選**，不是已證明的全庫唯一來源。
- 同 URL 同輪只計一次；以下 supplementary URL 只作同篇脈絡與交叉查核，不額外計篇、計輪次。與 AUTO-71 電郵／銀行資料來源不同。

## AUTO72-S01｜Phase banner – GOV.UK Design System
- URL: https://design-system.service.gov.uk/components/phase-banner/
- Canonical identity: `govuk-design-system:components/phase-banner`；作者／維護者 GOV.UK Design System team；類別：服務階段／狀態訊息；官方元件首次導入：2018-06（change history），最新可見指南變更：2026-07；檢索 2026-10-28。
- 閱讀證據 ID：`AUTO72-S01-R1-MAIN-TEXT-C1`。實際讀官方主文（117行）、[變更史](https://design-system.service.gov.uk/components/phase-banner/history/)（80行）、[Nunjucks options](https://design-system.service.gov.uk/components/phase-banner/nunjucks/)（82行）的可取得文字；**同一次閱讀主文及附件，不算3篇或3次複讀**。此為主要正文與附件文字閱讀，原圖/實際畫面、互動與輔助技術未驗，**非完整深讀 R1**。
- 官方事實：phase banner 表示服務仍在開發，alpha/beta 標籤依服務階段；原則上置於 header 的服務導覽之後，跨服務頁面顯示；2026-07更新回饋元件建議，2026-02修訂 header 位置。Nunjucks `text/html/tag` 可配置，但 HTML 使用需防 XSS。
- 獨立反例 C1：Notion 頁面標 `[TEST]` 或放測試階段提示，不表示該頁已與正式 Data Source／Relation／Session 隔離；若把「TEST」視為資料隔離證明，可能誤動啟用方案。階段標籤不能取代實際資料關聯查核。
- 獨立反例 C2：政府補助資格 `待核` 是個案／方案期別層級的業務狀態，不是整個系統的 alpha/beta；以全域 banner 顯示可能誤導所有案件皆待核，或掩蓋同頁不同個案狀態。
- 獨立反例 C3：為了醒目在每個 Notion 日常工作頁重複放長篇內部設計警語，可能違反使用者已核准的「同類資料同頁、開啟即見」及 AI 內部規則不進日常頁原則。官方服務階段元件並不授權自行加回使用者曾撤回的黃色警示。
- 反證界線：英國政府的服務階段與 live assessment 規範不能直接移植為臺灣治療所的法定狀態或 Notion 原生功能；此處僅供風險辨識，**不提議當下新增 banner**。

## AUTO72-S02｜Exit a page quickly – GOV.UK Design System
- URL: https://design-system.service.gov.uk/patterns/exit-a-page-quickly/
- Canonical identity: `govuk-design-system:patterns/exit-a-page-quickly`；作者／維護者 GOV.UK Design System team；類別：敏感服務／隱私安全／快速離開；個別首發及最後修訂日期未明列，不自行猜測；檢索 2026-10-28。
- 閱讀證據 ID：`AUTO72-S02-R1-MAIN-TEXT-C1`。實際讀官方主文（269行），包含適用/不適用、Exit 按鈕/替代連結/遮罩、預先告知頁、安全指引、HTML/Nunjucks 示範及研究範圍；另讀 [Exit this page component](https://design-system.service.gov.uk/components/exit-this-page/)（227行）作機制交叉核對，**補充元件不另計新來源**。仍是一次正文/附件文字閱讀，**非完整深讀 R1**。
- 官方事實：快速離開模式面向可能因資訊暴露遭受虐待、報復等風險的使用者；按鈕可轉往其他網站、提供輔助技術可用的次要連結，JavaScript 可立即遮住頁面；須告知不會自動清除瀏覽歷史，並說明是否保留輸入或 session。component 說明有 Shift 連按三次捷徑、可能另設 session 清除流程；官方指出主要研究樣本是家暴風險使用者，對其他族群尚缺廣泛實測。
- 獨立反例 C1：心理治療所的個案敏感資料值得保護，但一般內部 Billing／Session 工作台不是必然適用家暴求助的快速離開模式；未評估工作者情境就加緊急退出，可能造成誤按、未儲存工作遺失或操作混亂。
- 獨立反例 C2：即使畫面瞬間遮蔽並跳到其他網站，仍可能留有瀏覽歷史、後退快取、登入 session 或共享電腦資訊；在 Notion 內僅放一個跳轉連結更不能保證真正登出或清除敏感內容。不能將視覺遮蔽宣稱為資料安全 PASS。
- 獨立反例 C3：若強制離開清除未提交的行政資料，可能造成已收款卻未完成 Billing 記錄、或 Session 更新中斷；但若保存敏感草稿又可能增加外洩風險。必須區分隱私緊急處置與交易原子性／恢復策略，並以角色、裝置、風險和實際平台能力驗證。
- 反證界線：GOV.UK HTML/JS 元件不等於 Notion 原生可支援相同 overlay、Shift 快捷鍵、session 清除、後退保護或自訂登入；尚無臺灣心理治療所使用者研究或權限測試。**不提議當下加按鈕或改 Session**。

## 交叉反證與本輪計量
- 交叉結論（僅研究假說）：**服務階段標籤 ≠ 資料環境隔離 ≠ 業務核准狀態；視覺快速離開 ≠ 登出 ≠ 瀏覽痕跡清除 ≠ 交易安全。** 安全/UX 設計不得以標籤或按鈕取代真實權限與資料一致性驗證。
- 新來源候選：2；主要正文與相關官方附件文字閱讀：2篇各1次；首次獨立反例：2組、共6情境；既有來源完整複讀：0；同 URL 重複計數：0。
- 完整深讀 R1：0；完整 R2–R10：0；本輪 `FULL_DEEP_PASS_10_OF_10=0`；累積可核實 `0/10,000`。不可把搜尋命中、附件、示例、反例數冒充獨立完整深讀次數。
- NOT_TESTED：原圖、實際互動、鍵盤/讀屏/手機、真人 Notion、真實角色/權限/環境隔離、session 清除、瀏覽痕跡、效能、歷史收費、公式/補助規則。全儲存庫同文異址精確去重仍未完成。
- NO NOTION/SYSTEM WRITE：本輪僅研究與 GitHub 紀錄，未改 Notion 正式/TEST 頁、資料庫、View、Formula、Relation、權限或業務資料，亦未改正式 GAS/Cloud Run/Session/部署；研究門檻未達，不進入 Notion 重新設計。自動與手動研究保持獨立並行。
