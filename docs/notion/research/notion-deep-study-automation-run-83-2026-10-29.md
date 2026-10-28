# AUTO-83｜Notion 深度學習：Interruption／Page not found（2026-10-29）

Trace: `AUTO-83-20261029-0240-RESEARCH`｜範圍：外部設計文獻閱讀及 GitHub 研究紀錄；**NO NOTION/SYSTEM WRITE**

## 研究前置與去重

- 已重讀 main：`README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`，以及 `docs/notion/research/README.md`、`audit-checklist-and-research-progress.md`、`research-to-implementation-matrix.md`、AUTO-82 研究紀錄。當時 research 目錄列出 94 個項目，尚無 AUTO-83。
- 在當時最新 `sources.md` 全文查找兩篇 canonical path：`patterns/interruption-pages` 與 `patterns/page-not-found-pages` 各 0 筆；本輪新來源**候選** 2 篇。未完成全部歷史研究檔逐檔全文、跨語系及同文異址語義去重，不能稱已完全唯一。
- 2026-10-29 查閱 GOV.UK Design System 官方正文與頁內 HTML／Nunjucks 文字範例。頁面實際原始視覺呈現、獨立示例連結互動、鍵盤、螢幕閱讀器、手機與真人操作未驗證；以下只算**文字與範例閱讀**，不算完整深讀 R1。

## S01｜Interruption pages（新來源候選）

- 官方 URL：https://design-system.service.gov.uk/patterns/interruption-pages/
- Canonical：`govuk-design-system:patterns/interruption-pages`；標題 `Interruption pages`；維護者 GOV.UK Design System team；檢索 2026-10-29；首發與最近修訂日未核。
- 閱讀事件 `AUTO-83-20261029-0240-RESEARCH-S01-R1-MAIN-TEXT-AND-EXAMPLES-PARTIAL`；原文位置約 L51–L170：用途、適用與不適用、稀疏使用原則、返回／取消連結、簡短面板、HTML／Nunjucks 範例及研究來源。
- 原文可核：適用於可能是錯誤的異常操作、不可復原操作、與既有資料衝突的回答；但**只有確有必要中斷且不如此會漏看重要資訊時**才應使用。過多中斷頁會降低效力；短內容且不應在面板放其他表單元件。官方例子以 109 歲異常值詢問是否正確。
- 反例 1【每筆 Session 修改都彈出阻斷頁】：日常高頻編修若每次都中斷，造成操作負擔及警告疲乏；必須先有實際錯誤風險證據，不能把重要性當作普遍阻斷理由。
- 反例 2【按下「確認」即視為補助核准】：中斷面板是介面確認，不會自動取得政府補助資格、角色授權或當期方案規則證據；人工核定與交易狀態不可被 UI 點擊取代。
- 反例 3【警告出現就等於防止不可逆錯誤】：刪除、退款、修改歷史收費若無權限、版本、稽核、回復與真正交易驗證，僅有「確定嗎」仍可能產生錯誤。此為風險推論，未測 Notion 原生功能。

## S02｜Page not found pages（新來源候選）

- 官方 URL：https://design-system.service.gov.uk/patterns/page-not-found-pages/
- Canonical：`govuk-design-system:patterns/page-not-found-pages`；標題 `Page not found pages`；維護者 GOV.UK Design System team；檢索 2026-10-29；首發與最近修訂日未核。
- 閱讀事件 `AUTO-83-20261029-0240-RESEARCH-S02-R1-MAIN-TEXT-AND-EXAMPLES-PARTIAL`；原文位置約 L51–L185：不存在頁面與錯誤 URL、測試連結、簡短不責備的錯誤訊息、聯絡管道、避免技術術語及兩組 HTML／Nunjucks 範例。
- 原文可核：404 對應**不存在**頁面或錯誤網址；應檢查系統內外連結、清楚提示核對網址及必要聯絡資訊；頁面不建議用 404 等技術術語、責備語氣或裝飾性錯誤警告；官方也承認需要更多使用者研究。
- 反例 4【看不到 Notion 個案頁就判定已刪除】：權限不足、未分享來源、已搬移、連結失效與真正不存在是不同原因；不能把「找不到」當成業務紀錄已刪或不存在的證據。
- 反例 5【404 直接顯示敏感個案標題或內部路徑】：為了方便復原而透露被限制存取之個案或 Billing 詳情，可能造成資訊洩漏；錯誤回覆需依授權與資料分類控制內容。
- 反例 6【錯誤頁只叫使用者重建一筆 Session／Billing】：原連結可能暫時失效或記錄仍存在；直接重建會增加重複收費、會談或歷程風險。應先查明狀態與原資料來源，不可把前端錯誤當成交易失敗。

## 交叉分析與證據界線

- 中斷頁處理**高風險決策前的必要停頓**；找不到頁處理**資源／導覽錯誤**。二者不應與資格未核、資料存取權限不足、資料同步失敗、交易結果未知混為一談。
- GOV.UK 是外部網頁設計參考，**不代表 Notion 原生支援相同元件或行為**。治療所已確認「同類資料同頁、開啟即見」，不應為追求 GOV.UK 流程外觀擅自加入多層跳頁；對敏感資料與歷史交易必須另作原生權限／公式／狀態驗證。
- 採用狀態：`RESEARCH_ONLY / NOT_APPROVED / NOT_TESTED`。沒有提出或執行任何 Notion 重新設計。

## 本輪嚴格計數與限制

- `NEW_SOURCE_CANDIDATE=2`；`MAIN_TEXT_AND_SELECTED_EXAMPLES_READ=2`；`INDEPENDENT_COUNTEREXAMPLE_GROUPS=2`、共 6 情境；`FULL_INDEPENDENT_REREAD_EXISTING=0`。
- `FULL_R1=0`；`FULL_R2_TO_R10=0`；`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`；沿用最新可核實累積 `0/10000`，非推算新增。
- 未完成：全部歷史與跨語系同文去重、原始視覺／獨立互動、鍵盤／讀屏／手機、Notion 即時 Schema、角色權限、真人 UX、歷史 Billing／Session／方案期別 Formula 與效能。**本輪只寫 GitHub 研究文件，沒有修改 Notion 正式／TEST 頁面、DB、View、Formula、Relation、權限、業務資料，也沒有修改正式 GAS／Cloud Run／Session／部署。**
