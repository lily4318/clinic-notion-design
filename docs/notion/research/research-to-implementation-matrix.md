# 研究結果 → 設計 → Notion 實際狀態｜可追溯對照

基準日期：2026-10-24。研究來源 ID 依 [16 筆歷史證據登錄](evidence-register-2026-10-24.md)。歷史紀錄中 N03、N07 僅有搜尋摘要，**不作為已全文精讀**。本表只對應既有成果與本回合實際讀回，不增加研究篇數。

| 研究／設計規則 | 來源 ID | 對應文件／決策 | 本輪之前／本輪 Notion 實作 | 尚未核實 |
|---|---|---|---|---|
| 常用任務優先、進階明細收合 | U01, U02 | `workbench-ux-principles.md` | 本輪 [行政任務 TEST v2](https://app.notion.com/p/4038ca66aa4d814297a2dbe27e8d054d) 四區任務路由＋3個收合檢視 | 真人使用者步數與操作時間 |
| 名稱應預告實際任務 | U03, U02 | `audits/b1-b3-legacy-batch-2026-10-24.md` | 帳務收據／活動收款／薪資階段明確分名；TEST 入口使用任務名稱 | 操作誤選率 |
| 避免高流量首頁大量同時開 DB | N01 | `performance-permissions-free-plan.md` | TEST v2僅保留1個獨立測試資料庫作附錄，不重複嵌入十模組76區塊 | 真實開頁延遲 |
| 一個來源可有不同 Views，但各自設定 | N02, N03 | `workbench-vnext-2026-10-24.md` | B1新增2個正確 View、舊版停用；補助參與分不同 View | 個別來源讀取資料是否符合預期、無全域同步方案篩選 |
| 保留原資料與來源關聯，不以年度複製 Cases | D01, D02, N04 | `government-subsidy-architecture.md` | TEST補助工作台沿用 Price Plans／參與紀錄／Sessions／Staff，未重建個案核心表 | 跨政府方案與核定期別真實規則 |
| 參與記錄以個案×方案實例區別 | D01, D02, N04 | `government-subsidy-architecture.md` | 已定候選唯一鍵；未見 Notion 原生複合 UNIQUE 保證 | 重複鍵、Relation 和跨期額度 |
| 避免多層 Formula／Rollup 及 Formula 篩選 | N01, N05 | `database-design-principles.md`、十模組稽核 | 23個 Data Source／636欄歷史結構盤點，未擅自刪公式 | 原生計算結果、依賴深度與延遲 |
| 設計需兼容 Notion 免費版限制 | N06, N07, N08, N10 | `performance-permissions-free-plan.md` | TEST v2只用基本連結、欄位、列視圖、折疊／兩欄，不依賴付費 Dashboard 全域篩選 | 工作區目前方案與所有角色權限 |
| 不靠隱藏 View／欄位執行角色授權 | N06, N07 | `docs/notion/AGENTS.md` | 沒有新增對敏感資料的分享權限，原頁權限不變 | 角色帳號實測 |
| Database Template 不應意外預設關聯到正式頁 | N09, N11 | `database-design-principles.md` | 本輪未建立含真實 Relation 的新模板或欄位 | 模板逐套實測 |
| 活動「報名中」及「進行中」條件要與 Status 相符 | N02, U02 | `audits/b1-b3-legacy-batch-2026-10-24.md` | 隔離五狀態測試1／2／5 PASS；原管理 View 新版條件正確、真實查詢0筆 | 真實活動案例可用性 |
| 非必要不動其他已確認功能 | U01, U02, N04 | `docs/notion/AGENTS.md` | 這輪只重整 TEST 任務預覽內容，不動十個原頁、Scheme/Session 等原資料 | 未來各頁真實需求評估 |

## 先前學習資料的完整性結論

- **已有**：資料庫正規化、Relation／Formula／Rollup、Notion Free／效能／權限、UX 理論、政府補助跨期設計、十模組結構稽核、B1～B3 回歸測試、GitHub 更新記錄及備份路徑；已建立這份可追溯連結矩陣。
- **缺少**：大量 Notion 模板逐套原型截圖／比較、個別研究文章的逐節深讀記錄、每一真實使用者任務完成率、每個角色的權限驗證、補助當期的公式與規則實值證據。
- **不可宣稱**：所有歷史網頁都已通篇精讀、1,000或10,000篇研究達標、免費版支援真正全域同步期別篩選、所有補助公式已正確、任務工作台已經受過真人可用性驗收。

## 回查規則

每次 Notion 進一步實作時，優先查此矩陣、最新 `long-term-goals.md`、`decision-log.md` 及 `acceptance-status.md`，再 Fetch Notion 真實 Schema／View、最近版本與當期官方規則；在同回合更新**實作證據**而不是只修改「已完成」字樣。

## 2026-10-24｜使用者要求學習成果實際活用：補助工作台UX v3獨立預覽（待真人確認）
- **[USER UX GATE]** 使用者明確反映Notion版面仍醜且難用，質疑學習成果是否真的被活用，要求先確認實際設計成果再繼續其他功能。這是修正設計優先順序的要求，**不是對UX v3最終版面的審美核准**；青壯免週報Formula工作線維持暫緩，角色權限依原決定DEFERRED。
- **[LIVE TEST PREVIEW]** 原[政府補助工作台](https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf)未覆蓋，在TEST行政管理下建立[UX v3獨立預覽](https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f)。首屏3種額度入口（治療所／個案／心理師），接著2張日常任務卡，歷史備查收合，底部3張精簡Linked Views；使用者可真實開啟並比較，不是靜態概念圖。
- **[LEARNING TRANSFER]** 對照Notion官方「閱讀者導向＋Callout／Columns／Toggle」、「減少首頁Inline DB與顯示屬性」、「各View獨立配置」及Business OS／Company OS／營運Dashboard範本之Quick Actions。實施成果：同一用途原頁7個Inline DB→預覽3個；治療所顯示欄11→7、心理師5→5、個案11→8；不新增假KPI、黃色警示或資格工作流，亦不宣稱完成過去要求1,000／10,000篇模板研究。
- **[STRUCTURE/DATA PASS]** 新三個View已Fetch核對欄位、順序、篩選、Relation目標；保存View查詢顯示治療所本期政府方案1筆、在職心理師2筆、青壯115單一歷程22筆，全部has_more=false，與舊View查詢筆數完全一致。Notion原始資料與既有Schema、Formula、Relation、原View、業務列皆未變。新TEST Linked Views共享來源，不等於業務資料隔離。
- **[HUMAN/PERFORMANCE PENDING]** 操作入口可見、配置與資料範圍PASS，**未**證明視覺舒適度、真人1-click體驗、手機排版或實際網頁載入變快。待使用者真實比較完成三任務：首屏找到三額度並點入、開始個案選方案、辨識免週回報公式仍未啟用。未獲認可不覆蓋原工作台、不續作公式。回復僅精準撤銷新預覽與其3個Linked Views，原頁已保留。
- **[EVIDENCE & DOCS]** 實際來源→設計→原生Notion實作及回查詳見[專項稽核](audits/subsidy-ux-v3-learning-applied-2026-10-24.md)；[Google Docs跨年額度UX規格](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)新增第二十二節並回讀，已建立[增補前備份](https://docs.google.com/document/d/1J3Z9zhvjtb53Ik06_JxTXobQ1s0oKsR1eyAc5WxYcpQ/edit)。

## 2026-10-24｜使用者實測UX v3：1B～5B全部FAIL；同頁直顯v4已建立（待驗收）
- **[USER CONFIRMED / UX v3 ALL FAIL]** 使用者逐題回覆 `1B 2B 3B 4B 5B`，5/5均不符合；第3題找不到先前指稱的「個案與服務歷程」操作。明確需求：**資料直接在目前頁面顯示，不要靠點擊跳別頁查看；大量說明文字應移除，一眼就能看懂**。v3原本資料範圍1／2／22的結構PASS不等於UX PASS，實際操作／視覺仍FAIL；先UX，後免週報Formula。
- **[CAUSE / MINIMAL FIX]** 原TEST v3預覽頁先顯示介紹、3張額度跳頁卡、2張任務跳頁卡及長文字，3張真正資料表卻放在最底下。已將**同一個預覽頁** https://app.notion.com/p/4038ca66aa4d814f959ceece0e8cb09f 更名直接顯示UX v4，完全移除頂部卡片與跳頁說明，改為四段短標題後立即放4張**inline Linked DB Views**：治療所額度、心理師週額度、青壯個案額度、進行中服務歷程之「💲收費方案」可見且可在原生View直接編輯的欄位（驗收時只看不操作業務列）。歷史／他處待確認提醒保留在唯一收合區，不新增黃色警示。
- **[SCHEMA + VIEW READBACK PASS / UX PENDING]** 維持原三資料源、三既有v3精簡View及原方案篩選；前兩張View列數1／2，第三張青壯115 Relation View 22筆，第四張新建在職? **不是Staff**，是Care Episodes既有來源篩選「狀態＝進行中」，View `view://4038ca66-aa4d-81b2-b733-000c7ed4394b`，38筆。四者has_more=false，對應欄位SHOW 6／5／6／4，第三與第四皆直接顯示「💲收費方案」。前3張數量與原一致，來源分別Price Plans／Staff／Care Episodes。Notion Fetch頁面確認四個inline資料表直接相鄰短標題且位於最上方，沒有原導覽Callout；尚無真人實際載入時間、視覺／行動裝置／可操作性PASS。
- **[SCOPE / PERF]** 沒有變更Price Plans、Care Episodes、Staff、Sessions、Billing、週回報等任何業務資料列、Formula、Schema、Relation、原營運Views或權限；角色權限仍DEFERRED，青壯免週回報公式仍NOT LIVE。v3只有3個inline資料庫，v4有4個，**可能增加載入量**，是否變快未知；用多一張直接可見服務歷程View換掉跳頁。
- **[MANUAL RETEST GATE]** 請真人逐題驗證：①開頁是否立即看到「治療所本期額度」表，不點跳頁；②下捲是否直接看到心理師與個案兩表；③「服務歷程」表是否直接顯示「💲收費方案」並知道可在原頁操作（**勿更動真資料**）；④整頁是否少文字、容易閱讀。各題A符合／B不符合／C未測。使用者尚未回覆，不得將v4寫作UX PASS或直接覆蓋原工作台。
