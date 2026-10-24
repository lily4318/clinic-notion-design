# 青壯人工核對後於服務歷程選方案｜2026-10-24｜最新確認流程與 TEST 改版

## 最新業務決策（優先於過去清單設計）

青壯方案資格由治療所人員人工核對，確認適用後，直接開啟該個案的 Care Episodes／服務歷程，在既有「💲收費方案」Relation 選擇對應的 Price Plans 核定方案實例。**不另外建立、填寫或維護青壯資格核對清單，也不要求先建立補助參與記錄才能啟用方案。** 此決定只針對青壯資格操作；其他政府方案仍依各方案與核定期規則處理。人工資格核對不能替代補助使用次數、心理師週額度或政府總額度的正確計算。

## 實際 Notion 現況與改動

- Care Episodes 原有「💲收費方案」Relation，已查核目標為 Price Plans，**沒有新增 Relation 或欄位**。
- [補助工作台 TEST](https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf)：首屏流程改為「人工確認資格 → 服務歷程選擇收費方案 → 檢視額度與會談狀態」，新增原個案與服務歷程頁入口。
- 既有補助參與 linked database 已放入「歷史及其他方案設計備查」收合區；工作台專用的第二個 View 由「資格待核對與不符合」改名「既有資格狀態（歷史備查）」。**原 View 篩選／排序／顯示欄位均未改**。
- [Notion 改版前備份](https://app.notion.com/p/4038ca66aa4d81c3a70bd4730fdba9fe)：保留原頁版面，僅作回復參考。原工作台六個 linked database、共用側欄、週額度、調整／歷史區塊均保留，且無黃色警示。
- [Notion TEST 驗收歷史](https://app.notion.com/p/4028ca66aa4d81298984ffd18b590a1d)已增加此決策紀錄，讀回恰一節。
- [政府補助 UX Google Docs](https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit)已追加第十五節覆蓋第十四節過時的資格清單說明，原117段保留；[修改前備份](https://docs.google.com/document/d/1BrEuVdXKuBPturXkvUPpWovuJ--ougaTHRebTxXR_Dw/edit)已獨立回查。

## 影響及驗收

- **已完成**：TEST 工作台內容與資料庫區塊讀回、View 新名稱與其完整配置不變、Care Episodes→Price Plans Schema Relation 查核、Notion 驗收日誌及 Google Docs 文件回讀。
- **保持不變**：所有既有補助參與資料列（含歷史 TEST）、Care Episodes／Sessions／Price Plans／Staff／Cases 的業務資料與 Schema、Relation、Formula、權限，以及 GAS／Cloud Run／Session／正式部署。**不刪除原補助參與資料源**，因尚有相依及未隔離的舊測試關聯。
- **尚未實測**：真人於 Care Episodes 設定方案後的 Session 歸屬與補助占用、跨方案／跨核定期計數、原生 Formula 真值及不同角色權限；不宣稱計數或放行已通過。
- **效能**：首頁將歷史參與表收合，但未量測載入時間，不能宣稱速度改善。一般 Notion View 篩選不等於存取控制。
- **回復**：先重讀當時最新原頁、改版前備份與 View，檢查並行修改；只復原本次首頁文字／收合位置與此 View 名稱，不刪既有資料來源、不將備份複本裡新生成的 linked block ID 強行覆蓋目前來源。


## 2026-10-24｜使用者確認青壯測試資料符合實際使用情境｜後續使用者確認

使用者明確表示「測試資料符合使用狀況」，據此將**青壯 TEST 資料對日常使用情境的適切性**標記為「使用者已確認」，不再規劃僅為了補青壯資格核對清單而另造測試資料或新增流程。仍沿用人工資格確認後直接於 Care Episodes「💲收費方案」選擇 Price Plan 的決策。

**確認範圍有限**：使用者沒有報告逐筆 Notion Formula 結果或完成全部真人流程，因此 Session 與 Episode 的方案一致性、原生補助計次、週／總額度、跨期別及權限測試仍保持待驗收。這次沒有修改任何 Notion 實體、原始 TEST 列、Schema、Relation、Formula 或部署；原改版備份與回復方法維持有效。
