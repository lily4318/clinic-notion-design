# CLINIC_GAS_PENDING_PATCH｜正式封包精確契約

單筆 patch.upsert 物件固定含：

    {
      "name": "檔案名稱",
      "type": "SERVER_JS、HTML 或 JSON",
      "source": "完整程式內容",
      "sourceSha256": "64位 SHA-256"
    }

- **sourceSha256** 不可寫成 sha256；刪除清單為 **deleted** 而非 delete。
- approval 必須精確等於 **APPROVED_FOR_DEPLOYMENT**。
- 每次核對 packageType、deploymentId、targetScriptId、baseProjectSha256、projectSha256、patch.upsert、patch.deleted、每筆 sourceSha256；base／expected SHA 都以最新完整正式 Snapshot 驗證。SHA 不符禁止強制部署。
- source 是**完整檔案**，不是片段；只替換必要檔案。
- pending_deployment.json 必須經真實 **connector file reference** 上傳正式 Pending Deployment 資料夾；本機路徑、sandbox URL、Drive URL、Base64、JSON 字串、檔名不可作為參照。
- 上傳成功後還須列檔、只留一份正式同名檔、比對 MIME／大小／父資料夾及完整 JSON。upload_file 的 success=true 不是通過憑證。
- **發布由使用者執行** deployPendingAndPublishProductionSafely，再驗證 deployed／verified SHA、備份與部署結果。

本文件只存格式規則，禁止放入實際敏感部署參數或可直接發布的封包。
