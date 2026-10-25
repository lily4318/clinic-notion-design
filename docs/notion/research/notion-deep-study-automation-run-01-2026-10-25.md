# Notion 深度學習｜排程獨立研究批次 AUTO-01（2026-10-25）

> 研究限定：**唯讀官方公開文章＋GitHub研究紀錄**。與聊天端「繼續」平行，採本批專屬檔名避免共用研究檔衝突。**未修改Notion或正式系統，未達10,000篇×10遍門檻，不進入版面設計。**

## 研究方法、去重與證據強度

- 開始前已從 `main` 讀取 `README.md`、根 `AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`sources.md`、`decision-log.md`、`acceptance-status.md` 及既有2026-10-24清冊、批次02/03/04、十面向研究；比對其中Notion官方URL。
- 本批**3個新canonical URL**，與上列清冊未見重複；只算各篇1個來源，不把相同語系的轉譯、FAQ分節、Marketplace模板連結當作額外篇數。其他平行執行若同時登錄，仍應在全域唯一清冊以canonical URL合併，不能雙計。
- 讀取方式：Web打開官方全文文字，逐節重查「設定／限制／權限／FAQ」，以下標 `FULL_TEXT_SECTIONS_READ + ANALYTICAL_PASS_1`，代表本次**讀過可取得的全部文字主節**並作一輪反例分析；**沒有操作影片、檢查所有截圖或實機測試**，因此**不登錄嚴格 `FULL_DEEP_PASS`**。十遍完整深讀合格篇數仍 **0／10,000**。
- 本批獨立軌跡標記 `AUTO-01-20261025`；讀取日2026-10-25（台灣時間）；文章是否更新於今日未核實，不假設發佈日期或付費功能永久不變。

## 新來源與本輪讀取

| ID | 官方唯一來源 | 文字主節覆蓋 | 可回查事實 | 未驗證 |
|---|---|---|---|---|
| AUTO01-01 | [Forms](https://www.notion.com/help/forms) | `FULL_TEXT_SECTIONS_READ + ANALYTICAL_PASS_1`：建立／從既有DB建立／編輯預覽／分享／填寫／回應檢視／自動化／阻擋外部分享 | 表單題目對應資料庫屬性；建立既有DB的Form需Full access；表單題目預設同步屬性名稱；條件邏輯僅Business/Enterprise；可用Web連結讓外部填寫；若複製他人模板中的Form，**未重新建立自己的Form可能將回答送到原模板作者**；Form View無法直接匯出，可由Table View匯出 | 未建測試表單、未核權限/受訪者登入、未驗證台灣醫療個資合規、未試手機建立 |
| AUTO01-02 | [Board view](https://www.notion.com/help/boards) | `FULL_TEXT_SECTIONS_READ + ANALYTICAL_PASS_1`：建立／分組與子群組／拖曳／卡片顯示／隱藏／欄統計／FAQ | 已有Status時通常按Status分組；若無可用分組欄位，**建立Board可能新增Status屬性**；移動卡片至其他群組是資料互動，不是純視覺；欄位統計有Count/Sum等；FAQ目前說不能直接以Relation/Formula群組（須以當時產品版本核對） | 未在本案資料庫操作，未驗證複雜公式狀態、權限、手機拖曳、效能 |
| AUTO01-03 | [Verify knowledge your teammates can trust](https://www.notion.com/nl/help/guides/verify-knowledge-your-teammates-can-trust-with-page-verification) | `FULL_TEXT_SECTIONS_READ + ANALYTICAL_PASS_1`：何者需驗證／用途／驗證節奏／集中檢視 | 驗證標章用於表示文件由負責者審核、可設定期限或無限期、到期提醒；優先標示高影響且常引用的知識，不是每頁都標；有頁面Owner/定期再審概念；文內部分截圖/展開媒體未實測 | 未核免費版可用範圍、不同語系UI、角色是否可Verify；不把驗證標章當資料庫欄位值/公式正確性的證明 |

**來源覆蓋細節：**
- Forms：建立與Existing DB Full access；Configure包含 `Sync with property name` 預設開啟及可關閉、`Required`、長答與條件邏輯；Share中工作區連結與公開連結、提交後權限、匿名、`No access` 停止收件；Responses的存取權限及匯出；Form automations；Enterprise限制公開分享。官方頁正文約106–280行（不含導航、頁尾）。
- Board：建立與從現有DB增加View、Group/Sub-group、Drag、Card preview與Property visibility、Hide group、欄統計與FAQ；官方頁正文約106–301行（不含導航、頁尾）。
- Verification：何時需要標章、搜尋顯示、owner、到期提醒、驗證節奏及集中檢視；官方頁正文約131–235行（不含導航、頁尾）。原文語系頁為`/nl/`但正文英文，未另把`/en/`語系版本當新來源。

## 分析、反例與交叉驗證（只研究，不建議立刻改版）

### A. 表單『看起來可以填』≠個資可安全收集
- 初始假設：找一份現成免費醫療接案模板的Form，複製就能快速收件。
- **反例**：官方明確警示：複製模板內既有Form而不重建，回應可能送到**原作者**，造成資料外流；而外部公開Form連結允許非工作區人士提交，這與能否看見資料庫其他列、後續回應存取是不同權限問題。
- 修正理解：模板外觀與回應實際目的地、分享設定、權限、匿名與保護敏感資料需分開核驗；在未取得資料流/安全驗證前，不能因「免費版可用Form」就認定適合收集臨床資料。本輪不建立或分享表單。

### B. 看板『視覺整理』可能改變業務資料
- 初始假設：把同一資料庫切換為Board只會改顯示。
- **反例**：沒有適用Group Property時可能新增Status欄；跨欄拖曳卡片會更動該筆分組屬性。對「待核／核定／已結案」等狀態，使用者若以為是拖動排版，可能意外改業務真值。
- 修正理解：檢視模式可以輔助流程，但新增View與操作View的資料寫入副作用不同；需要先驗證現有Status的語義與實際操作者權限，不能以更美觀替代安全驗收。本輪未新增Board。

### C. 已驗證的說明頁≠補助額度資料已驗證
- 初始假設：把高重要度工作台都標Verified，工作者就可放心使用。
- **反例**：Page Verification表示**文件知識被審核且可能有時效**，並不保證頁面中的關聯、公式、每期補助額度、付款或角色可見性全部正確；若採`indefinitely`又無再審制度，過期政策仍可能顯示驗證標章。
- 修正理解：知識文件的可信度管理和每筆業務資料/公式的正確性屬不同驗證層次；在治療所日常工作台更不應把設計者規則貼到Notion，只為取得標章。本輪不建立Wiki或Verified標章。

### D. 跨來源交叉比對
- **Forms × Synced Blocks（舊NEW02）**：兩者都可能在「複製後」保留指向原始來源的依賴，但前者是**回應寫入目的地**、後者是**區塊內容共享及權限**，不能當作同一風險；本輪未實際操作。
- **Board × Views（舊DS-019）**：View設定與來源Schema分層；Board的新增欄與拖曳卻可能改來源資料，因此不可用「只是View」概括全部行為。
- **Verification × Search（舊B4-01）**：驗證標章提高文件可信辨識度，但不能克服工作區搜尋與資料庫內搜尋覆蓋範圍的差異，亦不代表使用者擁有不該有的存取權。

## 驗收狀態及下一輪工作邊界

| 項目 | 本輪實際 |
|---|---|
| 新canonical URL（與已讀清冊比較） | **3** |
| 可取得全文文字主要章節、已做一輪反例分析 | **3** |
| 已做第2～10輪完整獨立深讀 | **0** |
| 可嚴格證明10/10完整深讀的篇數 | **0/10,000** |
| 本輪Notion頁面、資料庫、View、Formula、Relation、權限、臨床資料寫入 | **0** |
| GAS、Cloud Run、正式Session變更 | **0** |
| 真人/效能/權限/跨裝置測試 | **未做** |

後續需建立**跨批次全域唯一URL索引＋每篇10次完整閱讀稽核欄位**，防止雙軌工作重複計量；這只是研究資料管理工作，不授權進入Notion介面設計。任何新的GitHub索引寫入都需先重取`main`最新SHA、與手動軌的新增資料比對，衝突不得覆蓋。只有10,000篇每篇10次真正達標才向使用者報告等待確認，**不自行開始改版**。
