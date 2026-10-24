# 治療所行政系統｜跨系統協作規範

- **否決即清除（2026-10-24使用者確認）**：使用者認為不適合的設計／功能／欄位／頁面／測試元件，須從實際使用環境**真正刪除**，不得用隱藏／停用／收合冒充完成，亦不得把過時預覽永久堆積。先確定精確範圍、最新依賴、最小安全替代、可回復備份與驗收；引用仍在、法定紀錄或無法回復時先停在 BLOCKED，不可強刪破壞其他功能。備份／稽核與暫未能刪除的依賴不算日常介面保留舊功能。


- 先讀根 README、AGENTS、docs/system/source-of-truth.md，依本輪工作類型讀 Notion／GAS／Auth 的專屬文件與最新 Google Docs；不能要求使用者重貼已有資料。
- **區分工作範圍**：Notion TEST、純設計、Backend Staging、Auth Staging、正式 GAS。只修改使用者本輪指定的範圍；目前青壯 TEST 是 Notion-only。
- 最新已驗證來源高於舊 GitHub 摘要：正式 GAS 先重讀 Current Snapshot／Deployment Log 與 SHA；Notion 先讀 00.config_notion、Schema、Relation、View；Staging 先確認 revision、traffic、Secret version、rollback。
- 最小必要修改、保留其他人變更、完整必要檔案、備份、先 TEST、再寫入、寫後回查；不能測試不得假稱已實測。
- 正式 GAS 遵守 docs/gas/deployment-sop.md、patch-contract.md 與 validation-checklist.md，硬停止條件未滿不得交付 patch。安全見 docs/system/security-policy.md。
- Notion 遵守 docs/notion/AGENTS.md。原系統只做最小修正；大幅 Schema／Relation／Formula／UX 變更須先分析風險、效益、回復，取得使用者同意。
- 政府補助支援多方案、多年度／核定期別、每期不同規則；不可在通用邏輯寫死青壯或 115。未知／未確認／不適用／已確認0不可混用。
- 禁止將姓名、病歷、財務明細、密鑰、Token、Script Properties、L4 部署驗證資料、raw Notion records 提交 GitHub，即使是 Private Repo。
- 新決策、修改、驗收在**當次對話工作回合**同步 GitHub 相關文件、決策與驗收表，必要時同步 Google Docs；更新前先讀遠端，更新後回查 Commit 與內容。不能更新就誠實說明。
- 回覆說明原因、目的、影響、保留不變、權限與效能、測試與限制、驗收及回復；不要將舊快照說成即時事實。
