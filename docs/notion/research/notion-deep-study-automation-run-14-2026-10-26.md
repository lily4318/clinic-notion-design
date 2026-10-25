# Notion 深度學習｜AUTO-14｜2026-10-26｜Relations/Rollups、Sub-items/Dependencies、Property Access

- 研究軌跡：AUTO-14-20261026-0537-Asia-Taipei；自動排程獨立批次；僅研究及 GitHub 進度記錄。
- 本輪先讀取 main 最新 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、decision-log.md、acceptance-status.md；比對當期研究清冊及已知 AUTO-01～13、MANUAL-01、首批與第二至四批清冊。寫前另外以 repo code search 檢索三個完整 slug，均無命中。因 GitHub 搜尋索引不保證完備，後續仍須以 canonical URL 清冊持續交叉去重。
- 三篇均由 Notion 官方 Help Center 公開正文實際開啟，讀取可取得的主要文字章節、限制與 FAQ，各做首次獨立反例分析；未逐張核對圖片、觀看嵌入影片或實際操作。來源更新日期未在頁面可靠顯示，僅記「2026-10-26 查閱」，不冒充來源發表/更新日。
- 計量：本輪 3 個暫經清冊去重的官方 canonical URL，文字主節閱讀 3 篇、首次反例分析 3 次；FULL_DEEP_PASS=0，10/10 達標新增=0，累積可稽核10/10達標=0/10,000。不得將一次分析的三個角度算作三輪。

## AUTO14-S01｜Relations & rollups
- URL: https://www.notion.com/help/relations-and-rollups
- title: Relations & rollups；source: Notion Help；canonical ID: notion-help:relations-and-rollups；R1: AUTO-14-20261026-0537；reading: TEXT_MAIN_SECTIONS_READ + ANALYSIS_PASS_1（非FULL_DEEP_PASS）。
- 閱讀章節：關聯與跨庫範例、建立 Relation、雙向關聯、關聯頁面增刪、1 page / No limit、顯示屬性、自我關聯、Rollup 設定、各種計算型別、跨表匯出/複製FAQ。
- 官方事實：跨資料庫 Relation 可為單向或雙向；1 page 限制單筆關聯欄位可選頁數；Rollup 的 Count all/Count values/Count unique values/Count empty 與 Sum、日期聚合的語義不同；Rollup of Rollup 不支援；CSV 匯出關聯為純文字 URL，不能靠重新匯入自動重建關聯；複製關聯資料庫可能把雙向關聯轉單向。
- 待反駁假設：「1 page 關聯限制就等於同個案×核定期別唯一；Rollup Count unique 能直接判定跨機構剩餘補助次數；CSV 備份可完整回復原關聯」。
- 反例：兩個不同 Care Episodes 各自指向同一 Price Plan，即使各欄都限 1 page，仍可能在業務層形成同個案同一期重複記錄；Count unique 是欄位值去重，無法知道已取消、改期、他處使用或跨期的法定計次；CSV 重匯後關聯結構可能丟失，不能稱可逆備份。
- 修正結論：關聯基數、業務唯一鍵、政府權威額度及備份還原是不同層級；未來任何實作必須逐條驗證，研究不直接改 Relation/Rollup。
- 尚未檢查：示例圖片、影片、互動操作、現行治療所 Relation 與原生 Rollup 值、實際匯入回復。

## AUTO14-S02｜Sub-items & dependencies
- URL: https://www.notion.com/help/tasks-and-dependencies
- title: Sub-items & dependencies；source: Notion Help；canonical ID: notion-help:tasks-and-dependencies；R1: AUTO-14-20261026-0537；reading: TEXT_MAIN_SECTIONS_READ + ANALYSIS_PASS_1（非FULL_DEEP_PASS）。
- 閱讀章節：啟用 Sub-items、各 View 的 Nested/Flattened/Card、父子篩選、搬移/複製/刪除、受限頁面、Dependencies 及三種日期自動位移模式、Avoid weekends。
- 官方事實：父項刪除會一併刪除子項；複製父項會複製所有子項；搬移至無權啟用 Sub-items 的資料庫時子項可能成為父項，沒有子項編輯權限者其子項不會被搬移；依賴可以設定自動移動日期，或完全不自動位移。
- 待反駁假設：「把多個療程/會談做成子項就能安全精簡畫面；調整一筆行政期限只會影響那筆；畫面收合代表不再計入」。
- 反例：刪除一個父項會連子項一起刪除，若子項含有必要保留的服務歷程或收費紀錄則造成連帶損失；自動日期位移可能更改下游行政期限，但政府補助核定期限不能由任務依賴演算法任意改寫；Nested/Flattened 只是顯示差異，不能保證計數或權限安全。
- 修正結論：任務依賴是工作管理機制，不是臨床業務主資料或法定期限的真相；研究階段不得為版面精簡而擅自啟用子項、搬移/刪除業務資料或修改日期。
- 尚未檢查：介面圖片、權限不同時實際搬移、跨View顯示、真實資料的依賴與日期連動。

## AUTO14-S03｜Manage database property access
- URL: https://www.notion.com/help/database-property-access
- title: Manage database property access；source: Notion Help；canonical ID: notion-help:database-property-access；R1: AUTO-14-20261026-0537；reading: TEXT_MAIN_SECTIONS_READ + ANALYSIS_PASS_1（非FULL_DEEP_PASS）。
- 閱讀章節：方案與角色先決條件、建立屬性權限、20欄限制、權限等級、Person 例外、多規則衝突、不可限制欄型、手機限制、效能、FAQ與除錯。
- 官方事實：此功能限 Business/Enterprise，需資料庫 Full access 設規則，僅可在 web/desktop 設定；最多 20 個屬性可設規則；Full access 不受欄位規則限制；有多條權限時採較寬鬆權限；欄位權限不會給未獲准開啟的頁面新增頁面存取權；Title/ID/建立編輯者與時間、部分同步欄及父子關聯欄無法受限；受限欄位被用於 View 篩選/排序/群組時可能導致 View 無法開啟；公式、按鈕、Rollup 等可能因權限而失效。
- 待反駁假設：「隱藏敏感欄位或設定欄位規則就足以保護所有個案資料；免費版也能限制；Full access 管理者測試通過代表一般員工可用」。
- 反例：Free 工作區不能使用此欄權限功能；即使付費，擁有 Full access 的人仍看得到所有屬性；若共享路徑另授予更寬權限，原先限制不成立；員工因無法讀取用於篩選的欄位，可能看不到整個 View 或使操作按鈕/公式異常。僅用管理員身分測試會漏掉這些問題。
- 修正結論：不可把 View 隱藏當作權限；未來如有權限需求，需以實際方案、角色、最小權限與操作回歸驗證，研究階段不改 Share 或方案。
- 尚未檢查：方案實際帳戶、真實角色、手機、全部圖例、權限遷移時間、實際資料庫效能。

## 研究界線、計量與後續驗證
- 本批各 1 次獨立文字主要章節研讀及反例，非完整十遍。未看所有圖片、影片、外連互動，也未對任何治療所工作區、真人操作、權限、Formula、Relation 或效能實測。
- 3 篇新來源不得按語系、不同段落或搜尋命中再增算。累積可核實 10/10 篇數仍 0/10,000；僅在逐篇各十次完整獨立閱讀及反例均具證據時才提高。
- 本批沒有寫入 Notion 正式/TEST 頁面、資料庫、View、公式、關聯、權限、資料列，也未變更 GAS、Cloud Run、Session 或部署；未開始重新設計。
