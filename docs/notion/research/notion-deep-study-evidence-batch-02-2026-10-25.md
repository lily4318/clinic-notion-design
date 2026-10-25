# Notion 設計深度學習｜第二批來源證據與閱讀進度（2026-10-25）

> 狀態：**研究進行中／未達使用者門檻／未進入 Notion 設計階段**。此文件只記錄本次可回溯的查閱、閱讀層級及反思，不記臨床個資，也不授權更動 Notion、GAS、View 或資料模型。

## 一、目標、計數、閱讀定義

使用者指定：**至少 10,000 篇個別 Notion 設計相關材料，且每篇深度重複學習至少 10 次；全部完成並確認後才進行 Notion 設計。** 材料可包括 Notion 官方教學、官方/第三方模板、使用者研究、資料庫/權限/效能文件等；不同語系的同一文章不得重複計數。

嚴格級別：
- `CANDIDATE`：只有搜尋索引/模板目錄；**不算讀過**。
- `SUMMARY_ONLY`：已讀公開摘要/搜尋引言，但原文章打開失敗或付費模板內部不可見；**不算深讀**。
- `BODY_SECTIONS`：實際開啟且檢核正文至少一段關鍵章節，記錄適用界線；可算**一輪重點閱讀**，但**不算全文逐篇深讀**。
- `DEEP_PASS`：通讀單篇完整可用正文、保存觀點/反例/與其他材料衝突/限制/具體實務證據；每篇十個`DEEP_PASS`須是**十個獨立可追溯的查閱與分析過程**，不能用單回合「十個面向」取代。

**本次新增的計量（僅本批，不累加未逐URL去重的歷史數值）：**
- 唯一來源URL在下表登錄：**14**。其中 **10** 個網頁開啟且針對正文關鍵章節查閱（`BODY_SECTIONS`）、**4** 個為搜尋長文/公開摘要（`SUMMARY_ONLY`）；可獨立核實每頁10次深入完整深讀的達標篇數 **0**。
- 本批`DEEP_PASS`總量：**0／至少100,000次**，`DEEP_PASS_10_OF_10`篇數：**0／10,000**。上述10個BODY_SECTIONS只是一般首次重點閱讀，**不可**計為每篇深讀的第一遍。此文件不能證明以前或其他回合未登錄來源的累計已讀數。
- 同來源不同語系與帶`?nxtPslug`網址未重複列；目錄中「70,000+ templates」也不計為已讀70,000。
- 前批來源檔：[2026-10-25十面向研究](notion-ux-research-and-10-lens-review-2026-10-25.md)。前批「十面向」不是十遍、且未有`DEEP_PASS`，故兩批合併至少`10_OF_10=0`。
- 檢索/段落核對日期：2026-10-25（台灣）；實際頁面更新日若未標明，記為`未核實`。錯誤/Cache miss如實標示。

## 二、實際閱讀與來源清冊（14 unique URLs）

| ID | 主題/作者 | URL | 取得級別 | 本輪核對到的明確內容 | 尚未完成的深讀條件 |
|---|---|---|---|---|---|
| DS-017 | Notion官方：資料庫效能 | https://www.notion.com/zh-tw/help/optimize-database-load-times-and-performance | BODY_SECTIONS | 資料筆數、可見屬性、文字/Formula/Rollup篩選與多inline DB影響；建議簡單屬性篩選和在大量來源時使用不同Data Source Views | 未逐段通讀、未驗官方建議在本案的性能真值 |
| DS-018 | Notion官方：Customize layouts | https://www.notion.com/help/layouts | BODY_SECTIONS | 原生Layout套用該來源所有頁，而非某筆或某View；有固定properties配置；改Layout非純局部美化 | 尚未完整讀全部操作章節、未測手機/桌面 |
| DS-019 | Notion官方：Views/Filters/Sorts | https://www.notion.com/help/views-filters-and-sorts | BODY_SECTIONS | 分檢視設定、複合篩選、Freeze column；欄位固定適用寬表，篩選不等於資料變更 | 未通讀全文、未對每種類型做實例實驗 |
| DS-020 | Notion官方：Mobile | https://www.notion.com/help/notion-for-mobile | BODY_SECTIONS | 手機多欄會變單欄，無hover；手機與桌面控制差異 | 未用實機逐項驗證 |
| DS-021 | Notion官方：Sharing & permissions | https://www.notion.com/help/sharing-and-permissions | BODY_SECTIONS | Business/Enterprise方有資料庫row/page-level access；設計不能以View篩選冒充角色隔離 | 未完整研究免費版各種混合分享情境 |
| DS-022 | Notion官方：Database properties | https://www.notion.com/help/database-properties | BODY_SECTIONS | 新版Conditional color依各View設定、與Property/Row背景顯示有差異；可因狀態/公式變色，但需保留文字訊息 | 尚未核免費版Conditional color權益與實際配置 |
| DS-023 | Notion官方：Database settings | https://www.notion.com/help/customize-your-database | BODY_SECTIONS | 資料庫結構設定和頁面Layout屬來源層級；Can edit以上權限可改結構 | 未逐功能測試Lock/Permission交互 |
| DS-024 | Notion官方：Columns, headings, dividers | https://www.notion.com/help/columns-headings-and-dividers | BODY_SECTIONS | Columns在手機線性堆疊；應避免只用多欄位置表示重要性 | 未通讀每種Heading/Divider組合 |
| UX-017 | Nielsen Norman Group：Progressive Disclosure | https://www.nngroup.com/articles/progressive-disclosure/ | BODY_SECTIONS | 必須先找出高頻核心任務，進階選項才按需顯示；錯把重要內容收合反而增加操作步數 | 未逐段做文章反證與情境研究 |
| UX-018 | NN/g：Recognition and Recall in UI（Raluca Budiu，2024-01-15） | https://www.nngroup.com/articles/recognition-and-recall/ | BODY_SECTIONS | 顯示選項比要求使用者記住指令容易；情境、練習和近期性影響辨識；尤其專業行政的欄位語意需能直接辨認 | 未完整通讀參考文獻和行為實驗 |
| UX-019 | NN/g：Data Tables—Four Major User Tasks（Page Laubheimer，2022-04-03） | https://www.nngroup.com/articles/data-tables/ | SUMMARY_ONLY | 搜尋取得較長的正文段落，涵蓋查找／比較／單筆編輯／操作四類任務，原文章`open`逾時；不可計全文深讀 | 需可重開文章並核對全部段落 |
| UX-020 | NN/g：Mobile Tables（2017-09-17） | https://www.nngroup.com/articles/mobile-tables/ | SUMMARY_ONLY | 搜尋取得關於小螢幕欄位取捨與比較的長段落，直開帶參數網址發生Cache miss | 需全文重新開啟、核對差異及新裝置適用性 |
| TM-017 | Notion Marketplace：Medical Office Operations Dashboard（Nation4Business） | https://www.notion.com/templates/medical-office-operations-dashboard | SUMMARY_ONLY | 索引公開描述包含診所預約/請款/工作項目；商品內部為需購買模板，**未購買、未複製、未檢查工作區DB/式樣**；網頁直開回傳部分目錄而非完整說明 | 模板內部未知、不可視為逐套學習 |
| DS-025 | Notion官方：Intro to databases | https://www.notion.com/help/intro-to-databases | SUMMARY_ONLY | 搜尋結果顯示Can edit content可編輯資料列但不能改來源Views/properties；單次直開回傳錯誤；不冒稱正文通讀 | 需成功重新展開正文後再進一步閱讀 |

以上外部來源僅記錄自網站可見的教學、摘要或研究，不宣稱取得原模板的完整內容。不存或引用任何Notion個案、財務或醫療原始紀錄。

## 三、本輪研究筆記：知識深化而非版面提案

- **負荷與任務衝突**（DS-017 × UX-017 × UX-019）：首頁多個Linked View可能拉長載入，但只用Tab/Toggle縮到一表也可能讓需要跨資料比較的人不得不反覆切換。需要用測量區分「快載入」與「快完成任務」，不能從美觀主觀認定最優。此為文獻對照的分析結果，**非Notion設計方案**。
- **視覺層級和可辨識性**（UX-018 × DS-019）：欄位/選項清晰可辨識是降低記憶負荷，不是單純減欄；凍結關鍵標識/保留明確範圍可能比使用大量圖示可靠。不能使用標籤暗示實際篩選條件沒有涵蓋的狀態。
- **跨裝置的不可直接照搬性**（DS-020 × DS-024 × UX-020）：Notion手機不保留桌面多欄。研究需區分簡報式首頁美感與手機表格原生查看限制；實機測試尚未進行。
- **變動半徑／權限**（DS-018 × DS-021 × DS-023）：原生Page Layout、Schema、Role屬跨資料表共享範圍，任何「只是美化」都可能影響本次以外的現行案件/角色；研究不授權直接修改。特別注意Business/Enterprise的資料庫頁層級權限不能假定免費版具有。
- **色彩和安全狀態**（DS-022）：Conditional color是可能的輔助訊號，但Free可用與否未核；即使可用，也不能讓「未確認」被誤讀成已確認0，文字狀態仍必要。
- **模板證據等級**（TM-017）：醫療模板行銷文案只能證明它**聲稱**採用診所業務區段，不代表模板有符合本地補助期別、心理師跨機構額度及病歷安全的實際驗證。

## 四、嚴格重讀所需的下一個證據門檻（未執行、非背景承諾）

逐篇十次的後續可稽核格式：

| source_id | deep_pass_no | reading_datetime | full_body_available | article_section_coverage | counterexample_or_tension | concept_test | cross_source_revision | pass_verdict |
|---|---|---|---|---|---|---|---|---|
| 尚無通過記錄 | - | - | - | - | - | - | - | NOT_DONE |

- 每次真正Pass必須跨全文閱讀、提取不同問題、做反例和證據校對、寫下比前一遍新增或修正之理解。**不能以同一資料重複呼叫同網址十次、單純分類十個面向，宣稱十次深度學習。**
- 迄今沒有10,000×10次學習達標證據；尚未啟動後續Notion設計或測試，沒有取得使用者對新版畫面改動的核准。

## 五、回查與安全

只要GitHub新增本研究檔與必要研究索引、驗收狀態，便完成**本輪能夠確認的研究增量**。本文件連結以GitHub commit/readback核對；沒有對Notion、Google Sheets、GAS、Cloud Run、Session、個案資料、角色權限或UI檢視設定做任何寫入。這也不意味深度學習目標已達成。
