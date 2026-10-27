# AUTO-55｜2026-10-27｜跨模組導覽 vs 有順序的長流程：原文閱讀與反例（純研究）

- Trace：`AUTO-55-20261027-2238-RESEARCH`；台灣時間 2026-10-27 22:38 起；來源：GOV.UK Design System 官方公開網頁。
- 本輪開始重新閱讀 main 根 README、AGENTS、docs/system/source-of-truth、docs/notion/AGENTS、sources、decision-log、acceptance-status、research README 及 AUTO-54；研究目錄列出 66 份 Markdown；候選 URL 在最新 sources.md 與 GitHub repository code search 均無命中。嘗試研究目錄全量逐檔比對遭工具呼叫上限中斷，**未完成全庫同文異址與全部歷史檔案精確去重**；本輪僅列「已查索引新候選」。
- 兩篇均實際開啟、逐節閱讀可取得的主要正文（用途、何時使用/不使用、運作、研究/限制）；另開啟 Service navigation 元件與 GDS 延伸文章供交叉核對，**延伸文章不另計新增來源或複讀次數**。尚未逐張核對原圖、真實操作/鍵盤/讀屏、手機及 Notion 實帳，因此兩篇均為 `R1_MAIN_TEXT_PARTIAL`，不計完整 R1，也不計 R2–R10。

## AUTO55-S01｜Help users to Navigate a service

- URL：https://design-system.service.gov.uk/patterns/navigate-a-service/
- 標題：Help users to Navigate a service – GOV.UK Design System；維護者：GOV.UK Design System team；原文說明此 pattern 與 Service navigation component 於 **2024-08** 引入（不等於此頁首發日期已核實）。
- Canonical：`govuk-design-system:patterns/navigate-a-service`；唯一閱讀記號：`AUTO55-S01-R1-MAIN-TEXT-C1`。
- 閱讀覆蓋：反覆使用、多種任務且無單一線性順序的服務適合導覽；若本來是明確單一路徑則避免導覽，考慮任務清單。服務名稱連結至首頁；導覽連結只放重要頂層區域，不必充當全站地圖；區分服務全域工具與當頁工具；站內搜尋要明確標示搜尋範圍。已閱讀 GOV.UK Header / Service navigation 分工、外部連結處理、組織切換、slots 及無障礙層級；另閱讀 Service navigation HTML/Nunjucks 與 active link `aria-current` 範例及 2026 更新。元件 URL：https://design-system.service.gov.uk/components/service-navigation/ （**輔助閱讀，不另計篇數**）。
- **反例1（頂層導覽不等於把業務資料移走）**：治療所跨 Session、收費、補助等多模組反覆操作，可能需要明確的頂層導覽；但使用者已否決把原本同頁可直接看到的資料換成只有連結入口。應將「跨模組切換」與「同頁直接核對資料」視為兩種不同需求；不能引用此模式授權拆頁。
- **反例2（導覽名稱/搜尋範圍）**：若「補助」入口只顯示設定而非用量，或搜尋只搜尋目前 View 卻標成全系統搜尋，行政人員可能錯認資料不存在；未驗 Notion 原生搜尋/Linked View 能否精確提供相同的範圍說明。
- **限制**：GOV.UK 的 HTML/CSS/JS header 和 slots 不代表 Notion 能原生複製；沒有真人任務測試或權限/手機驗證，不提出實作變更。

## AUTO55-S02｜Step by step navigation

- URL：https://design-system.service.gov.uk/patterns/step-by-step-navigation/
- 標題：Step by step navigation – GOV.UK Design System；維護者：GOV.UK Design System team；頁面首發日期未核實。
- Canonical：`govuk-design-system:patterns/step-by-step-navigation`；唯一閱讀記號：`AUTO55-S02-R1-MAIN-TEXT-C1`。
- 閱讀覆蓋：有起點/終點、跨多項指引或交易且順序重要的旅程；不適用無自然順序的選項清單、只讀內容或交易系統內部；可跨線上/線下及多機關；介紹、編號步驟、任務連結、and/or 分支、費用提示、螢幕閱讀器可辨識的步驟編號。官方指出**此 pattern 在 GOV.UK Design System 僅供 prototype，無法自行發布到 live GOV.UK，亦不提供 govuk-frontend 元件碼**；不可把它誤認為可直接安裝的 Notion 功能。官方報告開發時進行8輪使用者研究，並記錄使用者較少點擊 step-by-step header、跨步驟往返造成挫折、確認頁不能放該元件等缺口。
- **反例1（補助資格不是一律線性）**：治療所補助初次資格核對或跨單位文件蒐集，可能涉及多個有順序的步驟；但某些證據需要等待外部回覆，其他步驟可並行。若強制所有 Session 的高頻收費都依同一序列操作，會阻擋例外且增加成本。
- **反例2（完成任務≠資格核准）**：即使清單中的步驟全完成，也不能自動推論政府核定、Session 歷史金額凍結、補助額度正確或已收款；需另有業務證據與驗證。亦不能將 `and/or` 分支誤作 Notion 公式邏輯已測試。
- **延伸證據**：https://gds.blog.gov.uk/2018/10/17/building-a-better-gov-uk-step-by-step/ 及 https://insidegovuk.blog.gov.uk/2018/02/07/how-we-approached-service-mapping/ 已開啟供交叉參照，但未完成全文深讀，不計獨立來源篇數。

## 跨來源反證、可稽核進度與範圍

- S01 的前提是「**多任務反覆使用、無固定順序**」；S02 的前提是「**有起終點且順序有幫助**」。同一治療所可同時存在兩種任務，但不能將同一個 Session 高頻工作硬塞成線性流程，或將需順序核對的補助資格流程簡化成無差別入口；需要真人任務、例外、角色、跨期及效能證據才可決定。
- 本輪新候選 **2**（僅已查索引去重）；主要正文文字閱讀 **2**；首次獨立反例分析 **2篇**；既有來源完整複讀 **0**；完整 R1 **0**；完整 R2–R10 **0**；本輪 `FULL_DEEP_PASS_10_OF_10` 新增 **0**，累積可核實仍 **0／10,000篇**。
- **NOT_TESTED**：全部原始圖片、原型互動/鍵盤/讀屏/手機、Notion真實資料/角色/權限/效能/公式、跨期 Session 金額及補助資格；全庫同文異址精確去重未完成。
- **NO NOTION/SYSTEM WRITE**：僅限 GitHub 研究及進度紀錄；未修改 Notion 正式/TEST 頁、資料庫、Data Source、View、Formula、Relation、權限、個案/財務資料或正式 GAS、Cloud Run、Session、部署。10,000篇×10次門檻未達，未進入重新設計；自動與手動研究可並行。
