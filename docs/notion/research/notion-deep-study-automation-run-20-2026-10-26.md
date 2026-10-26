# Notion 深度學習｜AUTO-20｜2026-10-26（僅研究）

- 獨立軌跡：`AUTO-20-20261026-1137`；本輪新候選 `AUTO20-S01`～`S03`，既有來源針對性複讀 `AUTO20-R01`。
- 權限界線：僅讀公開資料、寫入 GitHub 研究/索引/決策/驗收記錄；**不更動 Notion 頁面、DB、View、Formula、Relation、分享權限、任何業務資料或 GAS/Cloud Run/Session**；未開始重新設計。
- 開始前從 main 重新讀根 README、AGENTS、docs/system/source-of-truth、docs/notion/AGENTS、sources、decision-log、acceptance-status、research/README、首批16筆、批次02～04、十面向、MANUAL-01、AUTO-01～19 的當期研究紀錄，對下列三個 canonical slug 逐批比對。已登錄的 `/help/database-templates` (N09)、`/help/charts` (N08)、`/help/views-filters-and-sorts` (N02)、`/help/guides/using-database-views`（十面向）**不重複算新篇**。
- 讀取日：2026-10-26（臺灣時間）；文章發表/最近更新日期未核實。canonical ID 按文章 slug，不因 `/en-gb/`、`/nl/` 語系或搜尋參數重算。下列來源為不同 URL、不同正文的獨立官方指南，但其內容與原 Help doc 有重疊，**不把不同分析角度當作額外來源**。
- 讀取證據：本輪實際打開官方頁並讀取可取得的文字主要章節；圖片未逐張視覺核對、嵌入影片未觀看、外部模板未複製或實測，故只標 `BODY_MAIN_R1 + COUNTEREXAMPLE_R1`，**不是** `FULL_DEEP_PASS` 或「十次完整深讀」。

## AUTO20-S01｜Using database templates（新增官方指南）
- URL：<https://www.notion.com/help/guides/using-database-templates>；標題：Using database templates；來源：Notion Help Guide；canonical `notion-help:guides/using-database-templates`；本輪 `R1/BODY_MAIN_TEXT`。
- 實讀範圍：導言、用途（重複結構與預填屬性）、建立/編輯/複製/刪除、既有新頁套模板、會議紀錄與個人使用情境、模板目錄導流；網頁正文約106–153行。**此指南核心是3分鐘影片加短文字清單，影片未看；不可冒稱影片內容已讀**。
- 初始假設：既有行政表單只要複製模板就能一致、正確建立各期資料。
- 反例：指南證明的是**結構與預填值重複利用**，不是對核定期、個案+Price Plan複合唯一、歷史關聯或資料完整性的保證。若模板預設 Relation 指向舊期，新增頁可能繼承錯誤關聯；該風險由已登錄 N09 `/help/database-templates` 的 Relation 警示補充，不能冒稱本短指南本身有寫此細節。
- 修正結論：將模板視為輸入便利性，而非驗證/核准機制；對高風險預設欄位需要獨立查核。研究未授權建立/修改模板。
- 未驗：3分鐘影片、範本內容、實際套用與刪除、免費版與權限、手機。

## AUTO20-S02｜When to use each type of database view（新增官方比較指南）
- URL：<https://www.notion.com/en-gb/help/guides/when-to-use-each-type-of-database-view>；標題：When to use each type of database view；來源：Notion Help Guide；canonical `notion-help:guides/when-to-use-each-type-of-database-view`；本輪 `R1/BODY_MAIN_TEXT`。
- 實讀範圍：跨團隊不同 View 的用途、資料庫容器可納入不同 Source、Table/Board/Timeline/Calendar/List/Gallery 各節的適用任務、拖曳行為與外部模板連結；網頁正文約106–306行，未實測展開互動/影片/模板。
- 初始假設：把十個行政模組合併成一個漂亮的多來源容器或改成看板/日曆，就能更快速且安全操作。
- 反例A（資料寫回）：指南明確指出 Calendar 將卡片拖到另一日會改動原始資料日期；Timeline 拖曳也用於改動時間範圍。對法定截止日、核定起訖與預約時段，**視覺操作可能是資料修改**，不能視為純顯示。
- 反例B（資訊量與權限）：Table 適合跨多欄比對，Gallery 強調圖像、List偏精簡文件；使用者需要開頁即見補助用量，不等於Gallery或只留連結適用。各View是同源資料的呈現，**不是列級存取控制**；不同來源容器也不自動完成關聯、欄位語義或跨期驗證。
- 反例C（文件時效）：此指南Board群組列舉Select/Multi-select/Person，其他新版本官方Board Help另談Status；其示例不應作為2026年唯一有效的欄位相容性清單。正式採用前應回查當期產品文件與實帳。
- 修正結論：依任務選View，區分「查看」與「拖曳會寫回」；多來源容器與日常首頁設計需另做真人步數、權限、效能及資料正確性驗證。此處**不提出實作變更**。
- 未驗：所有截圖/影片、容器實際 Source/權限、拖曳、跨裝置、載入時間。

## AUTO20-S03｜Use charts to visualize data and track progress directly in Notion（新增官方情境指南）
- URL：<https://www.notion.com/nl/help/guides/charts-visualize-data-track-progress-in-notion>；標題：Use charts to visualize data and track progress directly in Notion；來源：Notion Help Guide；canonical `notion-help:guides/charts-visualize-data-track-progress-in-notion`；本輪 `R1/BODY_MAIN_TEXT`。
- 實讀範圍：圖表與原DB、Donut/Bar/Line用途、以`/chart`組合多張圖、OKR/roadmap/content情境、synced DB/AI autofill/外部圖表嵌入、圖表範本導流；網頁正文約106–228行。
- 初始假設：圖表會隨資料自動更新，於是可直接取代行政清冊與政府補助核定數值對帳。
- 反例A：這篇是專案管理/行銷用途的設計指南，並未提供本所「核定期別、未確認/0、不適用、會談狀態」等正確性保證；若來源公式或分類錯，圖表只是將錯誤可視化。N08官方 `/help/charts` 明定群組上限與免費版張數，亦不能因本文說可組合多圖就推定Free可不限量使用。
- 反例B（跨版本）：本指南介紹4種圖表布局（圓環、橫/直長條、折線）；2026年另一本官方Charts Help列出 `Number chart`，因此指南的「4種」可能是舊版本描述，不可據此斷言目前只有4種。
- 反例C（安全）：外部嵌入與AI自動標籤不是資料驗證，可能增加權限、資料外送或誤分類的檢查負擔；此為風險推論，**不表示本所已有資料外洩**。
- 修正結論：圖表可輔助趨勢判讀，不取代直接可見的原始額度列、例外狀態與人工核對。研究不授權新增圖表或外部整合。
- 未驗：全部圖像、嵌入影片、實際圖表與免費版限制、外部嵌入安全、手機與效能。

## AUTO20-R01｜既有 N02 Views, filters, sorts & groups（獨立針對性文字複讀）
- URL：<https://www.notion.com/help/views-filters-and-sorts>；canonical `notion-help:views-filters-and-sorts`；首批 N02 已登錄且查閱相關段落；本輪重新開啟可取得的 Filters、Advanced filters、Sorts、View settings、Search 等文字，標 `TARGETED_BODY_REVIEW_R2`，**不是第二次完整深讀**，不計新增URL。
- 本輪新的反例：個人未按 `Save for everyone` 的篩選/排序與全員共用的設定不同；同一工作者畫面看到「本期」不代表其他人看到同一條件，亦不代表底層DB只剩這些列。與先前主要討論View獨立設定不同，本輪聚焦**個人視角與共同業務狀態混淆**。
- 修正結論：若未來設計核定/異常清單，需分別驗證共享View預設、個人臨時篩選、實際資料權限與底層完整總數；此處不改任何View。
- 未驗：實際兩角色篩選差異、同帳多裝置、各語系UI與性能。

## 交叉反證與計數
- 本輪新canonical官方指南 **3**（各R1可取得主要文字及獨立反例）、既有N02針對性複讀 **1**；不同官方指南即使討論相同產品，也按不同完整文章URL登錄，但不能把短影片指南當已觀看影片。
- `/help/guides/using-database-views` 在2026-10-25十面向研究已出現，本輪**排除新增**；`/help/charts`、`/help/database-templates`、`/help/views-filters-and-sorts` 亦已在首批N08/N09/N02登錄。
- 新來源各尚缺圖/影片/實帳/真人/跨角色/效能驗證，嚴格 `FULL_DEEP_PASS` **0**；本輪與歷史累積可核實各10次完整深讀合格仍 **0／10,000篇**。全域精確唯一URL總數尚未完成跨檔機器去重，不相加報虛數。
- 無 Notion 或正式系統變更；研究成果未經使用者確認前不進入重新設計。
