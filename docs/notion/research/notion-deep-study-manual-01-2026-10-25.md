# Notion 深度學習｜手動續作 MANUAL-01：識別碼、原生自動化、協作鎖定（2026-10-25）

> **範圍：研究與 GitHub 紀錄，沒有任何 Notion 寫入或新設計。** 使用者「繼續」啟動的獨立手動工作單元，與已建立的每小時排程併行。目標仍為 10,000 個真正去重的材料、每個材料 10 次可稽核的獨立深入閱讀；**此回合未達標**。時區 Asia/Taipei。沒有訪問使用者真實個案、病歷或財務記錄。

## 一、來源對照與計量方法

- 前置先讀主分支 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、decision-log.md、acceptance-status.md、sources.md、2026-10-24 首批研究清冊、2026-10-25 第二／三／四批及自動排程 AUTO-01 原始研究檔；另與早期十面向清冊比對 canonical URL。首次比對時 AUTO-01 已有 3 篇官方來源（Forms／Board／Page Verification），**本輪不重查或重算**。
- 本次 3 個 URL 與上述清冊**未見重複**（用 Notion help article slug + 文章題名比對），但**不能把先前未建立完整全球唯一清冊的所有批次件數直接相加當作最終去重總量**。研究記號 `MANUAL-01-20261025`。
- `MAIN_TEXT_READ` 表示實際打開並覆蓋該篇所有可取得的主要文字章節；`ANALYSIS_PASS_1` 表示有一輪真正的假設、反例、跨來源檢討。網頁影片、插圖的完整資訊、實機權限與業務案例**未讀/未測**，因此**不登記嚴格 `FULL_DEEP_PASS`**。
- 本輪新增 canonical URL **3**；3篇已讀主要正文文字及完成**一次分析**；沒有任何篇數達到`10/10`完整深度學習，仍 **0／10,000 篇**。本輪 3 次分析並不等於 3×10 個深入閱讀 Pass。

## 二、三篇官方來源與閱讀覆蓋

| ID | URL / 文件 | 本次查核文字段落 | 級別及限制 |
|---|---|---|---|
| MANUAL01-01 | [Unique ID](https://www.notion.com/help/unique-id) | ID 屬性自動編號、為既存及新建頁分配、Prefix 可改、帶 Prefix 的快捷 URL、被刪頁也曾占用且不改號，官方頁主要內容約 lines 124–157 | `MAIN_TEXT_READ + ANALYSIS_PASS_1`；未建立實際 ID 或測跨資料源／匯入 |
| MANUAL01-02 | [Database automations](https://www.notion.com/help/database-automations) | 權益/存取權、設定、觸發條件、三秒窗口、動作、Gmail/Slack/Webhook、Variables、錯誤/暫停、FAQ；頁正文約 lines 124–389 | `MAIN_TEXT_READ + ANALYSIS_PASS_1`；嵌入影片未看、所有外部整合未試，免費版 Slack 權益有**來源內部疑義** |
| MANUAL01-03 | [Collaborate in a workspace](https://www.notion.com/en-gb/help/collaborate-within-a-workspace) | 同時編輯、頁鎖/資料庫鎖、解鎖、FAQ，正文約 lines 124–204 | `MAIN_TEXT_READ + ANALYSIS_PASS_1`；沒有實帳多使用者操作；若未來重看其他語系，視為同一篇 |

## 三、第一輪深入分析（每篇僅一輪）

### MANUAL01-01｜Unique ID

- **初始假設**：新增 Notion ID 屬性，就能取代治療所個案與政府補助方案的複合唯一識別。
- **原文實際支持**：ID 是該資料庫專屬的流水式欄位，新增到 DB 時既有和未來列獲 ID，Prefix 可編輯；已刪除列不會令其號碼重用；帶 Prefix 可形成便利跳轉 URL。
- **反例**：同一個案參與同一個 Price Plan 實例的重複兩筆紀錄，可分配到**兩個不同 ID**，而兩筆所對應的「個案×方案實例」卻相同；原生 ID *沒有* 複合唯一鍵的存在性驗證、鎖與防重流程。跨表 ID 是否全球唯一/權限分享與網址可用性，也未在本文被充分證明。
- **修正後理解**：記錄識別子（方便引用）與業務不可重複性（需複合鍵及可靠寫入檢查）是不同責任。這是分析，不代表要求改目前 Schema 或新增 ID 欄位。
- **待驗證**：Notion 複製來源時 ID 行為、跨來源 ID／Prefix 衝突、免費版角色可否看到快捷網址、資料列刪除的恢復。**第2–10輪未執行**。

### MANUAL01-02｜Database automations

- **初始假設**：設定 Notion 的一個「當項目編輯時」Automation，即可在每次政府補助紀錄變更後自動跑完整流程，且避免人工漏報。
- **原文核對**：Automations由 triggers + actions 組成；原生自動化**不能被另一個自動化觸發**（使用者點的 Button 則可能觸發）；多個 edited triggers 的「全部符合」可能須約3秒內成立；Recurring trigger 不可和其他種類Trigger結合，而且 Recurring 不支援 Edit property 動作。View 篩選若改變會改變套用對象，觸發後頁列不再符合 view filter 也會失效。公式/webhook錯誤有時不發通知，暫停後須手動恢復。
- **權益矛盾（待核）**：**同一官方文件**「Who can use」章節寫 Free Plan 可以建立 Slack notification automations，但「actions」章節又寫 `Send Slack notification to` 只適用 Plus／Business／Enterprise。兩處說法可能指不同操作時代/功能，僅依本篇文字**無法確定Free方案實際可用性**，故保留為 `SOURCE_INTERNAL_CONFLICT`，不能單方挑對自己有利的一句。
- **反例**：A Automation 於服務歷程變更後新增週回報頁，B Automation期待其新增時自動修訂累計數字，**可能根本不會觸發**。若原先設於特定View，改顯示/篩選可能改觸發對象。另任何業務權限/保密都不能由「自動化成功建立」推出。
- **修正後理解**：自動化不等於交易完整性、重試／稽核、核定期歸屬及錯誤處理；尤其Free版權益仍應先驗證。**只做能力研究，沒有設計Notion自動化或建立新規則**。
- **待驗證**：同日Notion官方價格方案頁／當前工作區權益、不同角色、狀態邊界及Error通知、實際跨程序觸發；**第2–10輪未執行**。

### MANUAL01-03｜Collaborate in a workspace

- **初始假設**：鎖定Notion頁或資料庫就能當成安全權限邊界，阻止不適當寫入；多人同時編輯會自動互斥保護重要資料。
- **原文核對**：多人可同時編同一區塊，反映最近一次修改，並非排他鎖。頁面鎖主要防偶然修改，具編輯權的人能解除。資料庫鎖讓人員還可修改**資料值**，主要禁止改Views/Properties。也有「Unlock for me／everyone」選項。
- **跨文件證據衝突／張力**：Database automations FAQ 把「database is locked」列為不觸發原因之一，但 collaborate help 說資料庫鎖下依然可以編輯資料值。這兩點**不相互推翻**：人員編輯資料與自動化能否觸發是不同能力。不可因前者而推論後者會正常運作。
- **反例**：一位有編輯權的操作者可以解除鎖、改業務資料，另一位同步編輯的結果可能被後寫覆蓋；因此鎖不提供角色專屬的欄位級授權、Audit 或 idempotency。
- **修正後理解**：防意外改動、權限防護、並行寫入一致性為三個不同維度。研究不等於要現在加資料庫鎖或調整人員分享權限。
- **待驗證**：實帳角色、鎖頁和鎖表的跨設備差異、何種情況會令Automation不觸發、多人編輯衝突處置。**第2–10輪未執行**。

## 四、跨來源結論與研究階段硬界線

1. `Notion ID`只是每筆紀錄的標記，**不能證實** `Case ID × Price Plan Instance ID`業務唯一性，不能混用。
2. `Database locked`可降低改View和Properties的風險，但不代表業務資料寫入被禁，也不代表Automation會運作；看似相反的官方說法分別談不同層次。
3. `Free Plan automation`同一官方頁有Slack例外與Plus權益的文字不一致，應標示來源歧義，不當作已驗證方案功能；即使有付費權益也不能將連鎖Automation當成確定可用。
4. `同時編輯`可提高協作效率，但沒有可保證互斥或防雙重計次的原生交易證據；此處只是風險分析，不作不必要的新欄位/按鈕/架構建議。

**本輪未改動**：Notion TEST/正式頁面、資料表、資料列、Linked Views、Formula、Rollup、Relation、Notion權限、GAS、Cloud Run或中央Session。真人操作、效能、角色權限、實際Formula真值均**未測**。這份檔案只在GitHub保存，不貼到Notion日常頁面。源文章的官方版本未逐日追蹤，不宣稱永遠不變。

## 五、驗證門檻

| 指標 | 本回合可核實 |
|---|---:|
| 已與現有研究清冊比對的新增 canonical URL | 3 |
| 本回合完成可讀正文主節的一輪分析 | 3 |
| 付費模板實際複製／測試 | 0 |
| 任一篇完成可稽核10次完整深讀 | **0** |
| 已達標來源篇數／要求 | **0 / 10,000** |
| 本回合Notion／業務/權限/程式資料修改 | **0** |

用最新main branch和blob SHA提交本批專用研究檔；必要同步 `sources.md`、`decision-log.md`、`acceptance-status.md`，每檔寫後Fetch回查。雙軌並行時遇到其他來源新紀錄需重新去重；若衝突不安全，停止該檔寫入而不覆蓋。此工作只完成**一個研究增量**，原整體研究尚未達標，**不啟動Notion設計**。
