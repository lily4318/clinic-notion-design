# Notion 深度學習｜AUTO-25｜2026-10-26

- 執行軌跡：`AUTO-25-20261026-1736-RESEARCH`；路徑：HOURLY/AUTO；研究日：2026-10-26（Asia/Taipei）。
- **權限邊界**：僅公開研究閱讀與本 GitHub 研究證據記錄；不修改任何 Notion Page、DB、View、Formula、Relation、權限、業務列，也不修改 GAS、Cloud Run、Session、部署。不得開始重新設計。
- 開始前重讀 main：`README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`。另列舉 `docs/notion/research/` 全部 36 個當期文件並逐檔檢查本輪兩個候選 URL，未見已登錄；sources/decision/acceptance 亦未含兩者。GitHub 搜尋索引為補充而非唯一去重證據。
- 去重規則：去掉語系前綴、追蹤參數與結尾斜線；NN/g 文章以 `nngroup:articles/<slug>` 作唯一 ID。本文兩篇為不同 slug、不同文章；搜尋結果不算閱讀，本文同一輪不同分析角度不算多次閱讀。
- 研究範圍：公開原文中可取得的全部主要文字段落與圖說，逐章節核對；未逐張開啟全部圖片、未看錄影或實際操作 Notion，故 **R1=MAIN_TEXT_READ_WITH_COUNTEREXAMPLE；FULL_DEEP_PASS=0**。不得把 R1 當作嚴格完整深讀第1/10輪。

## AUTO25-S01｜目錄導覽設計

- 標題：**Table of Contents: The Ultimate Design Guide**；作者 Huei-Hsin Wang、Maddie Brown；原文日期 2023-10-06；本次讀取 2026-10-26。
- URL：https://www.nngroup.com/articles/table-of-contents/
- canonical：`nngroup:articles/table-of-contents`；新增候選，當期 36 份研究文件＋sources/decision/acceptance 未登錄；閱讀軌跡 `AUTO25-S01-R1-TEXT`。
- 已讀章節：Definition、Benefits（overview/跳轉/底部可發現性/段落分享/搜尋結果）、Considerations、Placement（正文/左右欄、sticky/非sticky、上方/內文）、Styling（垂直/水平/多欄、可點擊辨識、捲動）、Best Practices（標籤一致、短標題、避免外部連結、回頂部、跨頁一致）、Conclusion；讀到文字圖說，但未逐張開啟 70+ 圖例/動畫。
- 原文可核要點：頁內目錄有利長文掃描與直達段落；正文內的非固定目錄通常較不與全域導航混淆；右側欄可能被忽略；水平導覽節省高度卻不易掃描；目錄連結標籤應與目標標題一致，避免把外部頁連結混進頁內目錄。證據：原文 Definition/Benefits/Placement/Styling/Best Practices 各段。
- **假設 H1**：長篇治療所行政頁只要加入頁內目錄，便能改善找資料時間。
- **反例 C1**：如果行政人員最常需要在首頁直接比較多筆額度、待處理清單，新增目錄只會多佔首屏、要求多一次點擊；把工作區導覽和頁內目錄混為一談也會造成預期錯誤。使用者已否決「只能再進資料庫才能看到資料」的模式，目錄不能取代 inline 資料。
- **修正 R1**：目錄僅是長頁輔助導航候選，不能作為精簡內容的唯一方案；在實際改版前須比較「直接可見原資料」與「頁內跳轉」兩種工作任務的點擊數、誤入率、手機可見性，且不得改動資料來源或權限。
- **反證／未證**：文章是一般網站導覽研究，不能推論 Notion 原生 TOC 的固定方式、手機展開、內嵌 linked DB 或錨點行為已符合此模式；需在未來獲授權後另行真人驗收。文章本身並非治療所工作者實測。

## AUTO25-S02｜表單認知負荷與錯誤預防

- 標題：**Few Guesses, More Success: 4 Principles to Reduce Cognitive Load in Forms**；作者 Huei-Hsin Wang；原文日期 2025-07-18；本次讀取 2026-10-26。
- URL：https://www.nngroup.com/articles/4-principles-reduce-cognitive-load/
- canonical：`nngroup:articles/4-principles-reduce-cognitive-load`；新增候選，當期 36 份研究文件＋sources/decision/acceptance 未登錄；閱讀軌跡 `AUTO25-S02-R1-TEXT`。
- 已讀章節：四原則 Structure、Transparency、Clarity、Support；Structure 下的欄位分組、視覺階層、問題排序、單欄、漸進揭露；Transparency 下的前置要求、必填/選填、進度；Clarity 下的白話、正向措辭、單一問題、格式例子、熟悉的表單元件、欄位長度；Support 下的 placeholder 風險、輸入約束、適時就地錯誤訊息；Conclusion。圖例文字可讀，未逐張核對所有圖片或實測表單。
- 原文可核要點：將相關欄位成組、清楚說明必要資料、避免負面或雙重問題、保留持續可見的標籤；只在適當時機呈現錯誤，並靠近錯誤欄位。漸進揭露是減少無關欄位的策略，但不保證任何業務都適合多步頁面。
- **假設 H2**：將行政資料填寫流程拆成多頁、多步驟，就一定比同頁更清楚。
- **反例 C2**：治療所常見「已知個案＋方案」的快速日常作業，若每次必須先跑 wizard，反而增加步驟；如果把未知/待核對/已確認0收成同一個 checkbox 或隱藏說明，會產生錯誤的補助資格與用量解讀。把警示全部提前亮紅也會造成警告疲勞。
- **修正 R1**：優先保留同頁直見關鍵資料；只有不常見、需要條件分支的輸入才評估漸進揭露。狀態語義與資料真值優先於美化；錯誤訊息應就地、可修正且與一般待輸入狀態區別。這是未來設計假設，不是本輪授權實作。
- **反證／未證**：文中單欄建議針對表單完成流程，不可直接外推所有資料庫比較表（比較任務可能需要並排欄位）；Notion 原生 Form、Relation、Formula、免費版條件能力及真人使用尚未驗證。不可將此篇研究等同於補助公式或合規驗收。

## 本輪計數、與歷史成果界線

| 指標 | AUTO-25 |
|---|---:|
| 新 canonical 候選（全研究目錄+來源索引去重） | 2 |
| 取得並閱讀主要文字章節 | 2 |
| 獨立首次反例分析 | 2 |
| 既有文章針對性複讀 | 0 |
| 新增 FULL_DEEP_PASS | 0 |
| 累積可稽核完成 10/10 篇數 | 0 / 10,000 |

- 兩篇皆是 R1 主要文字閱讀與獨立反例，不計任何完整深讀輪次；圖像/互動/實帳/角色/手機/效能/數值真值均 NOT_TESTED。外部資料的網站擷取日期不等於原文修訂日。
- 全域已閱讀來源精確唯一總數仍待依各研究清冊的閱讀等級、重複別名及正文證據做機器核驗；**36份文件未命中這兩個 URL** 不等於已核算全域已深讀篇數。
- 僅新增 GitHub 研究紀錄與來源/決策/驗收索引；沒有 Notion 設計、業務資料或正式系統變更。未達目標，須繼續研究並等待使用者於全目標完成後確認。
