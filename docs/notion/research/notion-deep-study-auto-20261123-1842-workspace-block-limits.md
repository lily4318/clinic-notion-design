# AUTO-154｜Notion Free workspace block limit 與背景模板部分成功風險

- 執行標記：AUTO-154 / 2026-11-23 18:42 Asia/Taipei / research-only
- 原文標題：Workspace block limits — Notion Docs
- Canonical URL：https://developers.notion.com/reference/workspace-block-limits
- 去重鍵：developers.notion.com/reference/workspace-block-limits（排除 query/fragment）
- 官方正文：2026-11-23 取得並核對全篇主要章節（Scope、Creation and grace period、Background templates、Affected endpoints、Error response）；本次為一次針對性結構化**部分閱讀**，不認列嚴格全文深讀 1/10。
- 來源去重：目前 sources.md 未見此 canonical URL，研究目錄未見同名專項；**全歷史跨檔語義去重未完成**，正式唯一新增數保守記 0。

## 官方條件與限制（不是本院所現況）

1. Free 工作區若超過一位 member，累積 1,000 lifetime blocks 的限制適用；guest 不算 member；刪除 block 不回補額度。付費及單 member Free 工作區不受該上限限制。該 API 限制只適用指定類型 connection；personal access token 與可在任意工作區安裝的 OAuth connection 不適用，Notion MCP 另有政策。
2. 首次達上限的寫入可成功，並啟動三天寬限；寬限結束後，建立 blocks 的請求失敗，但讀取、刪除、不建立 block 的編輯仍可用。
3. 建立 Data Source 在既有 Database 內不一定建立 block；Create View 若需建立 linked database block 則失敗，但在既有 database 加 view tab 仍可成功。不能將所有寫入同等視為不可用。
4. 背景模板工作可能在 API 建立請求成功後失敗，留下空白或部分頁面；無公開模板工作狀態 API 或失敗 webhook。應設定等待上限，讀回 block children，不可直接再次套用造成重複。
5. 限制回應為 HTTP 403 restricted_resource，additional_data.block_limit=block_creation；與 429 rate limit、一般 403 permission denied 分開處理，重試同樣請求無效。

## 反例與研究推論（待驗，未實測）

- R1：系統看到 403 就判斷心理師被撤權，實際為 Free workspace block quota；需辨識 additional_data。
- R2：清除舊頁後預期 quota 恢復，實際 lifetime blocks 不回補。
- R3：新增 Session page 在寬限結束後失敗，但更新既有 Session 的屬性可成功；不可把工作區判為全面唯讀。
- R4：建立新 Data Source 成功卻誤認 Create Database 也會成功；兩者 block 行為不同。
- R5：建立 View tab 成功，建立 linked database block 失敗；不能用單一 View 測試代表所有頁面建置通過。
- R6：模板套用 API 回應成功，實際背景工作只建立部分區塊；應驗證子區塊完整性。
- R7：模板部分成功後自動重送，產生重複提示或重複頁面內容。
- R8：將 personal access token 或 Notion MCP 的限制直接套用到一般 internal connection，導致錯誤容量推論。

## 對治療所行政系統的未來驗證問題

在使用者完成研究門檻並另行授權設計前，僅記錄待驗項：確認實際工作區方案與 member 數、Connection 類型、建立頁面/區塊是否受 quota 限制、API 錯誤分類、背景模板完成後讀回。不可據此推定目前院所已超額或直接調整 Notion。

## 本輪計量與邊界

- 外部正文可讀候選：1；本輪獨立部分閱讀：1；嚴格完整深讀：0；反例：8。
- 本輪正式新增去重來源：0（全歷史核對尚未完成）；全體可核實完成 10/10：保守 0 / 10,000。
- 僅新增獨立 GitHub 研究記錄，不更新共享清冊、不修改 Notion / GAS / Cloud Run / Session。
