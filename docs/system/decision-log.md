# 跨系統決策日誌

## 2026-10-24｜專案指示合併、文件模組化

- 為滿足 ChatGPT 專案指示最多 8,000 字需求，將原十節規範保留為精簡主指示加 GitHub 明細文件。
- **沿用原私人儲存庫** lily4318/clinic-notion-design，以 docs/notion、docs/gas、docs/system 分流；目前不必建立第二個儲存庫，避免兩份知識庫漂移。
- 根 AGENTS 改為跨系統入口；原 Notion AGENTS 原文保留於 docs/notion/AGENTS.md。已核定青壯工作線仍只有 Notion TEST。
- 本次只更新設計文件，不涉及正式 GAS 程式碼、Staging revision／traffic、Notion Schema 或部署。
- 需保護 L2/L3 個資與 L4 資安資料，不把使用者原專案指示中敏感部署識別值直接搬入 GitHub。

後續每次確認設計、變更或 TEST 結果，在當回合更新受影響文件與決策／驗收，寫入後讀回 GitHub Commit；不可假稱沒有觸發也能在背景自動更新。
