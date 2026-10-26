# 治療所行政系統｜長期設計與驗收知識庫

## 2026-10-26｜方案參與模型與已同意清理完成

目前模型以 Price Plans 保存方案與核定期規則；「補助方案用量」按個案＋方案期別保存用量；新增的「心理師方案額度」按心理師＋方案期別保存接案確認與本週摘要，沿用既有週回報。主檔僅保留通用關聯，新增方案／年度不再增加專用輸入欄位或改年度常數。服務歷程依個案與收費方案查閱。

使用者已明確同意精確清理範圍；Staff 的「額度查閱方案、補助本週摘要_自動、免週回報方案、他處接案情形、他處接案確認日、免週回報有效至」六欄及兩補助頁的四個舊人員檢視均已實際移除並回查。各頁只保留新來源的「各方案｜本週額度」「各方案｜他處回報設定」。人員、週回報與會談來源未刪除。其他有相依的歷史青壯欄位不在此次六欄清理範圍，新方案不用它們。

原生現有資料計算已回查；9 個離線合成模型情境通過，不等於多個真實方案整合、真人 UX、角色權限或載入速度通過。詳[資料歸屬修正報告](docs/notion/audits/subsidy-ownership-model-2026-10-26.md)；舊階段與舊 Staff 摘要公式僅作歷史／回復依據。本輪完成即停止，不延伸其他模組或研究工作。

## 2026-10-25 實作／2026-10-26 清除回查｜補助管理最新實作
使用者授權的[獨立補助方案用量與通用歷程查閱](docs/notion/audits/subsidy-usage-ledger-implementation-2026-10-25.md)已套用Notion：20筆既有用量移轉並原生核對；兩原補助網址同源、三日常區同頁直接看資料。新增方案期別沿用個案＋Price Plan ID模型，不增加逐年專用用量欄。14筆本次合成測試紀錄已於2026-10-26經使用者同意移到垃圾桶並逐筆回查，兩頁各20用量／2心理師／1啟用政府方案。真人UX、載入秒數、角色權限仍待驗收；舊歷史相依欄未宣稱已刪。本次只限Notion補助管理，以下先前提案／舊快照保留供追溯。

此**私人 GitHub** 原名 clinic-notion-design，現同時保存 Notion、正式 GAS、Auth／Staging 的**設計、流程與歷史驗收索引**。單一儲存庫已足以管理分模組文件，暫不必增設另一 GitHub 儲存庫。

- [ChatGPT 專案指示：8,000 字內合併版](PROJECT_INSTRUCTIONS_COPY.md)
- [根 AGENTS｜跨系統工作原則](AGENTS.md)
- [系統架構](docs/system/architecture.md) · [資料權威來源](docs/system/source-of-truth.md) · [資安規範](docs/system/security-policy.md) · [跨系統決策](docs/system/decision-log.md)
- [GAS／正式部署](docs/gas/README.md) · [部署 SOP](docs/gas/deployment-sop.md) · [封包契約](docs/gas/patch-contract.md) · [Auth Staging](docs/gas/auth-staging.md) · [驗收清單](docs/gas/validation-checklist.md)
- [Notion 索引](docs/notion/README.md) · [Notion AGENTS](docs/notion/AGENTS.md) · [決策](docs/notion/decision-log.md) · [驗收](docs/notion/acceptance-status.md)

**本 repo 不是正式 GAS 程式、部署狀態或 Notion 即時 Schema 的唯一真相。** 每次實際作業重讀 Current Snapshot／Deployment Log 或 Notion 的 00.config_notion、Schema、View 等權威來源。GitHub 不得存 Secret、L2/L3 個資與病歷、L4 部署驗證資料及 raw Notion 列。

目前「青壯方案啟用測試」限 Notion TEST，新增 GAS 文件不代表授權跨到 GAS／Cloud Run／Session／部署。每次確認設計或實際變更，同一工作回合更新相關文件並回查遠端 Commit；若失敗須回報。
