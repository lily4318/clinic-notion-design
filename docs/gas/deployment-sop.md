# 正式 GAS 安全修改與部署 SOP

來源：使用者 2026-10-24 提供的十節長期專案指示。**本文件為規範，並未在本次操作正式 GAS。**

1. 明確確認任務屬正式 GAS；Notion TEST、純設計、Auth／Backend Staging 不得直接走正式發布。
2. 從「治療所-GAS部署橋接器」重新讀**最新 Current Snapshot／Current Code、Deployment Log**；確認檔案數、名稱、類型、base project SHA-256、實際版本。不能用舊快照或回憶。
3. 重新讀 00.config_notion 並 Fetch 相關 Database／Data Source Schema、Relation、Select／Status；確認資料來源與權限。
4. 僅修改必要完整檔案，保留無關功能與並行修改；涉及大幅設計先取得使用者核准。
5. 測試 GAS／JS 語法、HTML／CSS、重複或缺少的函式、Notion 型別與最小 View Model、後端 Staff／角色／permission／資源驗證、fail-closed、Audit、冪等、必要 Lock、錯誤遮罩與敏感資訊排除。
6. 計算每個完整 upsert sourceSha256，確認預期完整專案 project SHA 與 base SHA 相容。產生最小 CLINIC_GAS_PENDING_PATCH；詳見 patch-contract.md。
7. 取得**真實 connector file reference**，把 pending_deployment.json 上傳正式 Pending Deployment；若一種方法失敗可安全更換方法，但不能假裝傳成功。
8. 列出 Pending 資料夾，移除重複正式同名檔，僅保留一份。重新核對檔名、MIME、大小、父資料夾及完整內容，並驗證 packageType、deploymentId、targetScriptId、baseProjectSha256、projectSha256、patch.upsert、patch.deleted 和每筆 sourceSha256。
9. **由使用者執行** deployPendingAndPublishProductionSafely；助手不能聲稱已代為執行。
10. 查實 deployed／verified SHA、差異、備份、Current Snapshot、Deployment Log、版本、URL、Access、Execute as 及正式環境測試，使用者確認正常後再進下一步。
11. 更新相應規格與 GitHub 的設計／驗收摘要，不將原始憑證、敏感個資或 L4 部署驗證資料提交。

## 正式 patch 硬停止條件

缺最新 Snapshot／Log 或 base／expected SHA、Notion Schema 未查、只靠前端權限、輸出 raw Notion／過量欄位、Token／raw error 泄漏、CSS !important、高風險寫入缺 Audit／冪等／必要鎖、權限拒絕不在後端、SHA 衝突仍強行部署、Pending 未正確上傳／全文回查／清除重複：**任一成立禁止交付正式 patch。**

無法在當次授權環境實際執行的測試，必須標示「未測試／受阻」，不可冒稱正式驗證通過。
