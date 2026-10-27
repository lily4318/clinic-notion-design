# AUTO-61｜Inset text / Panel：補充說明與交易結果不得混淆（2026-10-28）

- 執行追蹤：`AUTO-61-20261028-0437-RESEARCH`
- 時區：Asia/Taipei；本輪起始時間約 2026-10-28 04:37。
- 任務界線：公開設計來源的研究與 GitHub 研究紀錄。**沒有授權、沒有進行 Notion 重新設計或任何 Notion／正式系統寫入**。
- 去重：main `docs/notion/sources.md` 全文檢索 `components/inset-text`、`components/panel/` 均未命中；GitHub repo code search 同字串均無結果。此為「已查索引的新來源候選」，**不是全儲存庫逐檔、同文異址精確去重已完成**。
- 閱讀證據等級：兩篇各完成一次**官方頁面主要正文文字閱讀**及獨立反例推演，並讀取官方 HTML／Nunjucks 片段、更新紀錄、獨立範例；尚未完成完整 R1。官方 Confirmation pages／Interruption pages 僅為交叉查核的輔助來源，**不另計篇數**。本輪不是第二次複讀，也不是十個不同分析角度計十次。

## S01｜Inset text — GOV.UK Design System

- URL / canonical identity: https://design-system.service.gov.uk/components/inset-text/ ；`govuk-design-system:components/inset-text`；來源維護者 GOV.UK Design System team；首發日未核實。官方更新紀錄提到 2018-06 元件引入、2019-03 巢狀元件修正、2022-08 Nunjucks call 支援，**這些不是本文首發日**。
- 本輪閱讀軌跡：`AUTO61-S01-R1-MAIN-TEXT-C1`（一次文字閱讀，非完整 R1）。
- 已實際讀到的段落：When to use、When not to use、How it works、HTML/Nunjucks 範例、Recent changes；另外開啟獨立示例 https://design-system.service.gov.uk/components/inset-text/default/ 。官方用法為將引用、例子、頁面補充資訊與主文區分；在複雜頁或鄰近醒目元件時可能被忽略，不應用來承載所有人必讀的重要資訊；大量使用會失效。
- **反例 A（重要資訊隱沒）**：治療所若將「服務日期與 Price Plan 期別衝突」或「補助資格尚待人工核對」放在看似普通的側邊補充文字，行政人員可能忽略；其風險是錯誤判定，而非純粹版面不美觀。
- **反例 B（資訊過載）**：若為每一筆 Session 都增加大段 inset 補充，即使資料開頁可見，也會降低同頁跨 Session／Billing／補助用量的比較效率。短說明不等於能替代資料驗證。
- 反證條件：若真實任務研究證明補充說明在現有版面比警示更易理解，需比較可見性、誤判率、讀屏與載入表現；未測試不得決定改用 Notion Callout／Toggle。
- 本輪推論：**資訊重要性與視覺顯著程度應匹配；補充文字不能承擔需要即時處理的異常狀態。** GOV.UK inset text 不等同 Notion 原生 Callout。

## S02｜Panel — GOV.UK Design System

- URL / canonical identity: https://design-system.service.gov.uk/components/panel/ ；`govuk-design-system:components/panel`；來源維護者 GOV.UK Design System team；首發日未核實。官方更新紀錄 2026-07 新增 interruption panel variant。
- 本輪閱讀軌跡：`AUTO61-S02-R1-MAIN-TEXT-C1`（一次文字閱讀，非完整 R1）。
- 已實際讀到的段落：When to use、When not to use、Confirmation panel、How to write confirmation panel text、Interruption panel、HTML/Nunjucks 範例、Recent changes；另開啟獨立中斷示例 https://design-system.service.gov.uk/components/panel/interruption/ 。
- 官方用途界線：Panel 只用於確認交易完成的 confirmation page，或需暫停旅程的 interruption page；確認面板文字應短；中斷面板需使用者明確操作才繼續。此用途界線不能外推成「所有成功/異常狀態都要有大面板」。
- 輔助原文交叉查核（**不另計來源**）：https://design-system.service.gov.uk/patterns/confirmation-pages/ 說明交易完成頁應說明後續、必要的識別碼及可保存紀錄，並提醒在綠色確認面板放互動元素可能產生對比/無障礙問題；https://design-system.service.gov.uk/patterns/interruption-pages/ 指出僅有明確必要時才中斷，尤其是不可回復、異常或與既有資訊衝突，過多中斷會削弱效力。
- **反例 A（錯誤成功宣告）**：Notion Session 欄位已自動儲存，不等於政府補助核准、歷史金額鎖定或 Billing 已入帳。若用「申請完成／核准成功」的大型成功面板表示僅完成資料輸入，會把不同業務階段混為一談。
- **反例 B（過度中斷）**：若每次編輯日期、查看餘額、補登歷史 Session 都強制確認面板，日常高頻行政操作會被阻塞；但真正不可回復的刪除或矛盾資料，仍可能需要較強確認。是否真的不可回復、是否已經有保存／撤回機制，須先以真實系統查證。
- 反證條件：如真實操作證明某一具體動作高錯誤且難回復，應先驗證資料操作語義、權限與回復能力，再研究是否需要中斷；不得直接宣稱 Notion 支援與 GOV.UK 一樣的交易提交/中斷機制。
- 本輪推論：**「資料已儲存」「交易已完成」「資格已核准」「款項已入帳」四者不能共用一個成功狀態。**

## 跨來源獨立比較與未解問題

1. Inset text 為低顯著度的補充資訊，Panel 則為完成/中斷的重要節點；**不是以顏色或外框漂亮程度決定元件**。
2. 兩者都不能代替底層事實驗證：歷史方案期別、資格待核、Session/Billing 狀態及用量母體必須由真正的業務來源核實。
3. 依使用者已確認「同類資料同頁、開啟即見」，研究不支持擅自把資訊改為隱藏、跳轉或強制多步驟。
4. **尚未實測**：所有原始圖像/互動範例、鍵盤/讀屏、手機、真實 Notion 頁面、角色權限、效能、資料庫公式、跨期歷史金額、補助資格及實際收款；不能標 Notion UX/業務 PASS。

## 計數與驗收

- 本輪已查索引的新來源候選：2 篇；官方主要正文文字閱讀：2 篇，各1次；獨立反例分析：2篇、各2情境；輔助交叉查核：2篇（**不計來源或複讀**）。
- **完整深度閱讀 R1：0 篇；完整 R2–R10：0 次；本輪 FULL_DEEP_PASS_10_OF_10：0 篇；累積可核實 0／10,000 篇**。尚無證據可宣稱任何一篇完成10/10。
- 寫入限本研究檔與 GitHub sources／decision-log／acceptance-status 的**研究進度紀錄**。未修改 Notion 頁面、資料庫、View、Formula、Relation、權限或正式 GAS／Cloud Run／Session；未開始重新設計。
