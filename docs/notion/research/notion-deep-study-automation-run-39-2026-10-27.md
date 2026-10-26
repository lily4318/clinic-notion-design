# AUTO-39｜2026-10-27 06:44 Asia/Taipei｜篩選維度與桌面導航可發現性（僅研究）
Trace: `AUTO-39-20261027-0644-RESEARCH`；只進行外部公開文章閱讀、獨立反例分析、GitHub研究進度紀錄；**Notion/正式系統零寫入**。

## 本輪基準與來源去重
開始時 Fetch main 七項規範：README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md。sources.md 連結的 **45 份研究 Markdown 文件均成功讀取**，逐份檢查本輪兩個 URL slug；兩個 slug 在 sources.md 及這45份已查清冊中均未命中。GitHub code search 亦無命中，但不作為唯一去重依據。仍未取得全庫所有未索引歷史檔及同文不同 URL 的精確去重，故只記為「已查清冊新 canonical 候選2篇」。同一篇文章不因多種分析角度而重複計篇或計輪。

## AUTO39-S01｜Filters vs. Facets: Definitions
- 原文 URL：https://www.nngroup.com/articles/filters-vs-facets/
- canonical 去重ID：`nngroup:articles/filters-vs-facets`；作者 Kathryn Whitenton；2014-03-16；Nielsen Norman Group；2026-10-27 06:44 起本輪取證。
- 閱讀軌跡：`AUTO39-S01-R1-TEXT-C1`，獨立閱讀 **1次主要文字**，包含引言、Filters vs. Facets 全段、食譜檢索的三種比較情境、建置維護成本與結論；原文主要正文可讀。原始五張示意圖片未逐張驗證，未實際操作原案例站台；狀態 `R1_MAIN_TEXT+C1`，**非 FULL_DEEP_PASS、非完整1/10**。
- 可核實觀點：filter 透過條件排除結果；faceted navigation 使用多個內容面向供探索，可讓使用者了解資料有哪些分類，但建置、維護與為每筆資料補齊多面向 metadata 有成本，也增加操作負擔；簡單情境不必使用多面向篩選。
- 首次獨立反例 C1（研究假說）：若治療所為每個補助方案加「年度／期別／心理師／資格／使用狀態／會談狀態」六個篩選面向，卻沒有完整維護各期資料，行政人員可能以為「篩選後零筆」等於「沒有此個案或不需核對」。但反向極端——完全不提供期別維度——也可能混看不同核定期資料。**因此篩選維度的數量不是越多越好，需先確認資料語意、維護成本及實際查詢任務**；View 的可見集合不等於權限、資格或真實業務不存在。這是推論，未在Notion真實驗證。
- 限制：文中食譜網站與圖片是歷史示例，不能直接推定Notion目前有完整 facets、動態計數或任何特定互動；未實測真人、角色、手機、速度。

## AUTO39-S02｜Beyond the Hamburger: How to Make Navigation Discoverable on Desktops
- 原文 URL：https://www.nngroup.com/articles/find-navigation-desktop-not-hamburger/
- canonical 去重ID：`nngroup:articles/find-navigation-desktop-not-hamburger`；作者 Kara Pernice、Raluca Budiu；2016-07-24；Nielsen Norman Group；2026-10-27 06:44 起本輪取證。
- 閱讀軌跡：`AUTO39-S02-R1-TEXT-C1`，獨立閱讀 **1次主要文字**，覆蓋研究樣本/測量、6網站桌面導航差異、可見/隱藏導覽的具體案例、結論與指南。原始圖表、站台截圖未逐張開啟，未查原研究方法附文，狀態 `R1_MAIN_TEXT+C1`，**非 FULL_DEEP_PASS、非完整1/10**。
- 可核實觀點：文章描述179名參與者、6個網站、桌面與手機情境；本文桌面部分關注導覽使用率與找到導覽所需時間。文中 Slate 的導覽使用率17%、桌面總平均42%，作者亦指出網站類型、內容品質、位置與視覺對比等混雜因素；不能把百分比外推為治療所Notion的預期改善。可見、易辨識、符合使用者任務語意的導覽通常較易被找到，但可見導覽若命名含糊、對比不足仍可能表現不佳。
- 首次獨立反例 C1（研究假說）：把「補助額度」「方案期別」「待核對」全部藏入一個只有圖示的折疊導航，雖可減少首頁文字，卻可能讓新進行政人員找不到入口；**反向反例**是把所有10個行政模組的每一個次功能都展開成首頁長清單，同樣造成首屏擁擠。應保留使用者要求的同類資料同頁、開啟即見與必要業務入口，但不據此決定Notion原生導航必須怎樣實作。研究文的使用率不是治療所真人測試結果。
- 限制：2016年一般網站研究，非Notion、非臨床行政、非本所工作者；原圖、真實裝置、Notion工作區、權限/載入/公式未測。

## 研究結論、稽核與界線
- 本輪：已查清冊新 canonical URL 候選 **2**；主要文字獨立閱讀 **2篇各1次**；首次獨立反例 **2次**；既有來源完整複讀 **0**；新增嚴格十次完整深讀達標 **0**。
- **FULL_DEEP_PASS_10_OF_10：本輪0、累積可核實0／10,000篇。** 不把搜索結果、圖說、同篇兩個角度、未檢查的原圖/互動、或不同URL視為獨立完整深讀。全域唯一來源總數尚未完成跨檔與同文異址稽核。
- 尚未驗證原始圖像/影片、互動範例、Notion當前能力與真人操作、手機、角色權限、效能、跨期金額及原生公式真值。
- **NO NOTION/SYSTEM WRITE**：本輪僅GitHub研究、來源索引、決策與驗收紀錄；未更動任何Notion正式或TEST頁面、資料庫、Data Source、View、Formula、Relation、權限、業務資料，亦未更動正式GAS/Cloud Run/Session/部署。研究門檻未達，**不進入Notion重新設計**；手動與每小時排程可各自續作，後續寫入須重新Fetch main/blob SHA，衝突安全合併或停止。
