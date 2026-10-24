# Auth Staging／Backend Staging 設計與責任分界

**此為既有 POC 的歷史設計摘要，revision／traffic／Secret 版本須在當次重新核實。**

- Google 登入／Cloud Run 處理統一入口與 BFF；Firestore 中央 Session；正式業務角色、permission、資源範圍仍由正式業務 GAS 核實，不能因 Active User／Ticket POC 放行全部業務。
- 已建立的 GCP Auth Staging 專案可按名稱 clinic-auth-stg-26071501、Cloud Run service 名稱 clinic-auth-gateway-stg-v2、區域 asia-east1 查找；曾設 v0.1.4 revision 與 Phase1 POC candidate tag，現在**不可假定歷史流量仍正確**。
- 「治療所前台入口系統」為身份探測 GAS，應在 Cloud Run 正式接管後停用／封存，不承接正式業務。
- 「治療所前台 Backend Staging GAS」是獨立 Phase 1 業務 POC，不等於正式主 GAS；修改前須取得完整當前程式與 allowlist。
- Backend HMAC v1 曾暴露且已停用，v2 啟用為歷史狀態；每次重查 Secret Manager 有效版本、雙端一致性與 rollback，不可輸出 Secret 值。
- Drive 文件以「06 Auth Staging」定位。不得把歷史候選 revision、traffic、Script／Deployment ID 或 Web App URL 當成 live 驗證。

不得以此 POC 自動啟用正式業務 API；修改先確認身份驗證、授權拒絕、HMAC、最小 View Model、稽核及資料隔離。
