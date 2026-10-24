# 最新權威來源與查找順序

GitHub 是決策及驗收索引，**不得取代最新正式程式／部署／Notion Schema**。

- **正式 GAS**：以 Google Drive 中「治療所-GAS部署橋接器」的 Current Code／Current Snapshot、Deployment Logs、Deployed Packages 為最新基準；必要時查 Backups、Pending Deployment。每次重新定位檔案、日期、SHA、版本及相關部署實際狀態；不能沿用舊 SHA。
- **正式 GAS 名稱定位**：治療所前台系統v2。查對該次 Current Snapshot 的 Script／Deployment／權限設定，不能由歷史設計文件認定 live 值。
- **Staging**：從既有 Google Cloud 專案與「06 Auth Staging」文件重驗 Cloud Run revision／traffic、Secret version、Backend Staging GAS 原始碼、Rollback；過時 POC 記錄不等於現況。
- **Notion**：從 00.config_notion 重新取得 Database／Data Source ID，Fetch Schema、Relation 目標、Select／Status、View、頁面存在，再操作；只有 [TEST] 字首不代表與正式資料完全隔離。
- **功能／UX 需求**：最新《治療所行政前台網站需求規格書》、《治療所行政前台UX頁面清單》、《治療所前台_統一登入與系統責任分界規格》與使用者最後核可設計；Stitch 素材為版面參考。
- **GitHub**：根 README／AGENTS、docs/system、docs/gas、docs/notion 下版本化設計與驗收記錄。若與 live 來源衝突，記錄差異後再決策。

敏感 Script／Deployment ID、部署驗證原值、實際 connector file reference、Token 等不複製進此私人 GitHub；從受控正式來源重新查找，不要求使用者反覆貼出。

歷史快照標記日期與「當時」，不可聲稱即時。若缺少基準／權限／Schema／正確上傳回查，禁止正式 patch。
