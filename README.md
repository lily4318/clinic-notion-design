# 治療所行政系統｜長期設計與驗收知識庫

此**私人 GitHub** 原名 clinic-notion-design，現同時保存 Notion、正式 GAS、Auth／Staging 的**設計、流程與歷史驗收索引**。單一儲存庫已足以管理分模組文件，暫不必增設另一 GitHub 儲存庫。

- [ChatGPT 專案指示：8,000 字內合併版](PROJECT_INSTRUCTIONS_COPY.md)
- [根 AGENTS｜跨系統工作原則](AGENTS.md)
- [系統架構](docs/system/architecture.md) · [資料權威來源](docs/system/source-of-truth.md) · [資安規範](docs/system/security-policy.md) · [跨系統決策](docs/system/decision-log.md)
- [GAS／正式部署](docs/gas/README.md) · [部署 SOP](docs/gas/deployment-sop.md) · [封包契約](docs/gas/patch-contract.md) · [Auth Staging](docs/gas/auth-staging.md) · [驗收清單](docs/gas/validation-checklist.md)
- [Notion 索引](docs/notion/README.md) · [Notion AGENTS](docs/notion/AGENTS.md) · [決策](docs/notion/decision-log.md) · [驗收](docs/notion/acceptance-status.md)

**本 repo 不是正式 GAS 程式、部署狀態或 Notion 即時 Schema 的唯一真相。** 每次實際作業重讀 Current Snapshot／Deployment Log 或 Notion 的 00.config_notion、Schema、View 等權威來源。GitHub 不得存 Secret、L2/L3 個資與病歷、L4 部署驗證資料及 raw Notion 列。

目前「青壯方案啟用測試」限 Notion TEST，新增 GAS 文件不代表授權跨到 GAS／Cloud Run／Session／部署。每次確認設計或實際變更，同一工作回合更新相關文件並回查遠端 Commit；若失敗須回報。
