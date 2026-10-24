# 正式 GAS 與 Staging 驗收清單

- [ ] 先確認是正式 GAS、Auth／Backend Staging、Notion TEST 還是純設計；只處理當前範圍。
- [ ] 正式 Current Snapshot／Deployment Log、完整檔案類型／數量、base／expected project SHA 已重新核對。
- [ ] Staging revision／traffic／Secret version／rollback（若適用）已重新讀取。
- [ ] 00.config_notion、Notion Schema、Relation 目標及欄位型別已核對。
- [ ] GAS／JS 語法、HTML／CSS（禁 !important）、固定版本元件及函式依賴已檢查。
- [ ] 每支 API 後端 Staff／role／permission／resource-scope fail-closed。
- [ ] 最小 View Model、敏感遮罩、DOM 安全及 Browser 無 Token。
- [ ] 效能：查詢合併、欄位最小化、避免 N+1、L3 不進共享快取。
- [ ] 高風險寫入 Audit、冪等、必要 Lock／回復。
- [ ] JSON、approval、deleted、upsert 完整 source／sourceSha256、base／expected SHA 驗算。
- [ ] 真實 connector file reference 上傳後，目標資料夾單一正式 pending、檔案 metadata 與全文驗證。
- [ ] 使用者執行安全發布後，版本、deployed／verified SHA、備份、Current Snapshot、Deployment Log、URL、Access、Execute as 已核對。
- [ ] 正式測試有證據；不能測的項目明列；必要 GitHub／Google Docs 設計更新已回查。

**任何硬停止條件缺失，不得提供正式 patch。**
