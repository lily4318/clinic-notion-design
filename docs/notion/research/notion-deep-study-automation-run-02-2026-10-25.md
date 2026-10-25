# Notion 深度學習｜自動研究批次 AUTO-02（2026-10-25）

> **本輪僅外部來源唯讀＋GitHub證據記錄，沒有任何 Notion 操作。** 本批為每小時排程的獨立研究單元，與手動 MANUAL-01／自動 AUTO-01 並行。嚴格目標：至少10,000篇去重資料，各有10次獨立、完整且可稽核的深讀；**本批仍未達標，合格10/10篇數為0/10,000**。

## 一、基準、去重與稽核定義

- 執行日：2026-10-25（Asia/Taipei）。執行軌跡：`AUTO-02-20261025`。
- 已先Fetch `main`：`README.md`、根`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`、2026-10-24首批、2026-10-25批次02／03／04、十面向研究、AUTO-01及MANUAL-01。用文章slug及官方canonical URL去重，3個本批URL在所查清冊中均未出現；**不把語系版本算新篇**。
- `MAIN_TEXT_TARGETED`：取得官方正文，查閱全部標題結構與與本案高度相關的指定段落；**不是全文深讀**。`MAIN_TEXT_ALL`：已閱讀該篇全部可取得文字主節（不包括嵌入媒體）；仍不等於完成嚴格 `FULL_DEEP_PASS`。`ANALYTICAL_PASS_1`：有一次獨立反例與跨來源分析，不能冒稱10次。
- 本輪3篇新增來源，2篇短文章可讀文字主節、1篇長文章只讀特定段落。全部各1次反例分析；**0次嚴格完整深讀通過，0篇完成10/10**。所有來源的文章更新日期未知，不把爬取日期當發表日期。

## 二、來源登錄與正文覆蓋

| source_id | 官方canonical URL / 名稱 | 實際讀取覆蓋與層級 | 待驗證 |
|---|---|---|---|
| AUTO02-01 | [Import data into Notion](https://www.notion.com/help/import-data-into-notion) | `MAIN_TEXT_TARGETED + ANALYTICAL_PASS_1`：主題索引、How to import、CSV、PDF、FAQ及部分各格式/平台限制；官方頁約106–716行，不聲稱全部逐字精讀 | 其他匯入工具細節未逐項精讀；未進行真實匯入、對應欄位或測重複 |
| AUTO02-02 | [Back up your data](https://www.notion.com/help/back-up-your-data) | `MAIN_TEXT_ALL + ANALYTICAL_PASS_1`：Workspace export、Trash、Edit history、Accidental deletions、全部FAQ，官方正文約106–208行 | 未實測下載/還原、不同方案的歷史版次、實際備份完整性 |
| AUTO02-03 | [Duplicate public pages](https://www.notion.com/en-gb/help/duplicate-public-pages) | `MAIN_TEXT_ALL + ANALYTICAL_PASS_1`：Duplicate a page、No access blocks、Prevent duplication，官方正文約106–145行；英文英國語系不另算多篇 | 未複製模板或檢查Relation/Formula/Forms是否指向原作者、未測權限 |

## 三、各篇反例與修正理解（各一輪）

### AUTO02-01｜Import data into Notion

- **初始假設**：用CSV合併既有Notion資料庫就像SQL UPSERT，可依個案×期別鍵自動覆蓋已存在的紀錄，方便整理歷史補助額度。
- **原文查核**：CSV `Import`及`Merge with CSV`**只增加新列，不更新舊列**；新匯入不能直接產生Formula/Rollup/Relation，合併進既有資料庫時可把欄位映射到既有Relation。Free單檔5MB、付費單檔50MB；UTF-8與日期格式可能影響解讀；PDF匯入成Notion頁面且表格可能降成simple table而非Database。
- **反例**：重跑同一CSV不會修正舊補助資料，而可能再產生一組重複紀錄；若匯入欄位型別轉文字、Relation未恢復，視覺上像完整表格但公式/額度關係可能失效。
- **修正理解**：匯入是內容轉換/新增，**不是**幂等同步或可稽核資料遷移；若未來另有明確遷移需求，需獨立驗證列唯一性、欄位型別、Relation/Formula與回復。本輪不提出新匯入工作，也不碰業務資料。
- **未完成**：長文其他格式/第三方匯入全部細節尚未逐字閱讀；第2～10次未執行。

### AUTO02-02｜Back up your data

- **初始假設**：Notion官方雲端有持續備份，下載Workspace匯出檔就等於隨時可完整一鍵還原。
- **原文查核**：Workspace可匯出HTML、Markdown、CSV等；**匯出不一定包含執行匯出者無權限的私人頁**；Notion明說**不能把匯出的Workspace直接重新上傳就瞬間還原原工作區**；Trash預設保留30天，另有Edit history及意外刪除協助，Workspace匯出連結7天過期。官方同篇仍出現Business/Enterprise全Workspace PDF匯出說明，卻另註記此功能會在2026-08-31前逐步移除，故2026-10-25不應直接宣稱PDF Workspace匯出仍可用，標記`DOC_STALE_TRANSITION`。
- **反例**：若某治療師的私人頁未包含在備份，或匯出的CSV不能完整重建Relation/Formula，將ZIP檔當作可即時回復的完整快照會產生錯誤安全感。Notion內建備份和使用者實際可執行的完整復原是不同概念。
- **修正理解**：`backup existence`、`export coverage`、`restore reproducibility`、`data integrity`是四項獨立驗證；不能因官方聲稱伺服器每分鐘備份而推論能在當下無損還原。本輪不匯出個案資料，不改備份策略。
- **未完成**：實帳測試、檔案校驗、權限覆蓋、恢復測試；第2～10次未執行。

### AUTO02-03｜Duplicate public pages

- **初始假設**：從Notion Marketplace複製公開模板後，頁面與所有子頁一定會成為完全獨立且可編輯的本地版本。
- **原文查核**：複製公開頁會把頁面及子頁帶進自己的`Private`區，**但有些區塊可能顯示`No access`**，官方說這些區塊可能本就不打算開放複製；公開頁也可關閉`Duplicate as template`。
- **反例**：醫療/治療所模板複製後出現`No access`區塊時，外觀可用不等於底層資料庫、同步內容、嵌入資源或表單目的地完整可用。與AUTO-01 Forms官方警告交叉閱讀，**不應由本篇No access敘述直接推論所有複製的Forms都連到原作者**；需逐項核對資料流。
- **修正理解**：模板能複製的「頁面」與可安全使用的「完整工作流程」不是同一證據等級；本輪沒有複製模板、也沒有將任何AI設計規則寫入Notion頁面。
- **未完成**：Relation/Forms/Synced blocks/權限實機檢查；第2～10次未執行。

## 四、跨來源校對與驗收

1. **CSV匯入×備份還原**：匯出/匯入檔不等於無損Database Schema/Relation/Formula回復；即使匯入成功，仍可能新增重複列。不能把資料搬移當作「刪除青壯舊資料」的可回復保證。
2. **公開模板複製×AUTO-01 Forms**：公開頁的`No access`與表單回應可能流向原模板作者是兩種不同風險，不能合併成同一個技術結論。
3. **來源時效性**：備份文章同時保留「付費版可匯出Workspace PDF」和「該功能至2026-08-31前逐步退場」兩段，屬文件過渡文字；不可把舊功能描述當作現時實測。未查驗工作區方案及實際匯出UI。

| 指標 | 本批可稽核結果 |
|---|---:|
| 去重新增官方canonical URL | 3 |
| 官方文章全文可讀文字主節閱讀（不含媒體） | 2 |
| 官方長文針對性閱讀（不算全文深讀） | 1 |
| 新增有反例的分析輪次 | 3（各來源1輪） |
| 任一來源完成10次嚴格全文深讀 | 0 |
| 累積已完成10/10的來源數／要求 | **0/10,000** |
| Notion頁面／Data Source／View／Formula／Relation／權限／臨床資料寫入 | **0** |
| GAS／Cloud Run／Session修改 | **0** |

本檔為AUTO-02獨立研究證據，與MANUAL-01/AUTO-01不共享寫入檔案。更新共享`sources.md`、`decision-log.md`、`acceptance-status.md`前必須重新Fetch最新blob SHA、去重，條件更新；每個GitHub提交後讀回Commit/SHA及內容。無法安全合併則停該檔更新並記錄，不覆蓋其他流程。**學習目標未達標；不開始Notion設計或操作。**
