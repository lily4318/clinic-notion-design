# GAS／部署系統設計文件

**本目錄不是正式 GAS 專案程式碼儲存庫，也不保存可重放的敏感部署封包。**

- [deployment-sop.md](deployment-sop.md)：以最新 Current Snapshot 安全部署的執行順序與硬停止條件。
- [patch-contract.md](patch-contract.md)：CLINIC_GAS_PENDING_PATCH 的固定 JSON 契約。
- [auth-staging.md](auth-staging.md)：Google 登入、Cloud Run／Firestore 與 GAS POC 的權限邊界。
- [validation-checklist.md](validation-checklist.md)：語法、權限、Notion Schema、SHA、上傳及正式驗收。
- [系統架構](../system/architecture.md)／[安全](../system/security-policy.md)／[權威資料來源](../system/source-of-truth.md)。

正式 GAS 專案名稱為「治療所前台系統v2」，部署橋接器為「治療所-GAS部署橋接器」。由 Drive 內 Current Code、Backups、Pending Deployment、Deployment Logs、Deployed Packages 定位真實最新文件。**Script ID、Deployment ID、Web App URL、權限、當前 SHA 等必須每次重新核實，不採歷史文字為 live 證據。**

正式業務程式修改一律最小變更、完整必要檔案、測試先行、備份、驗證 SHA、上傳全文回查、使用者執行安全發布、部署後再查；不能聲稱未實際完成的步驟已做。
