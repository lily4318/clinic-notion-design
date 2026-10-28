# Notion 深度學習｜AUTO-75｜2026-10-28｜純研究
- Trace：`AUTO-75-20261028-1842-RESEARCH`；臺灣時間 2026-10-28 18:42；本次僅公開官方文件研究及 GitHub 研究紀錄，**不修改 Notion／GAS／Cloud Run／Session／部署**。
- 開始前重讀 main：`README.md`、根 `AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`decision-log.md`、`acceptance-status.md`；另讀 `research/README.md`、`research/audit-checklist-and-research-progress.md`、AUTO-74 原始研究。寫入前再查 main blob SHA 與既有 trace。
- 候選去重：在 main `sources.md` 全文未見 `/help/boards`、`/help/lists` 或對應 canonical；GitHub repository code search 四個精確 URL/canonical 詞均 0 命中。**未逐檔取得所有歷史研究全文、未做跨語系與同文異址內容指紋比對，兩篇僅列「新來源候選」，不宣稱全庫去重 PASS。**
- 來源為 Notion 官方 Help Center 的獨立編輯頁，非付費模板目錄或搜尋摘要；兩篇各閱讀一次可取得的完整主要文字及 FAQ。未完整檢查圖片、影片、實際拖曳、鍵盤、讀屏、手機與真人治療所操作，因此**非嚴格完整 R1**，不把反例數算成閱讀次數。

## S01｜Board view（新來源候選）
- URL：https://www.notion.com/help/boards
- canonical：`notion-help:boards`；標題 `Board view`；維護者 Notion Help Center；發布／最後更新日頁面未明列，取證 2026-10-28；閱讀軌跡 `AUTO-75-20261028-1842-RESEARCH-S01-R1-MAIN-TEXT`。
- 讀取範圍：官方頁面主要正文約 L107–L302：Create a board、Add board view、Edit groups、Group by property、Add group、Sub-groups、Reorder columns/cards、Card size/preview、Property visibility、Hide columns、Calculations、FAQ。原文也含影片/圖片，但本輪未逐一實際觀看或操作。
- 官方產品描述：Board 可按 Status、Assignee、Priority 等屬性分組，支援子群組、拖曳卡片、顯示/隱藏卡片屬性、欄位計數與 Sum。當資料庫沒有可分組屬性時，新增 Board 可能**自動建立 Status 屬性**（官方 L141）；這是潛在 Schema 影響，不能在正式庫未核對就試。
- **官方內部矛盾**：主文 L141 說無 Status 時可用 Select、Person、Multi-select **或 Relation** 分組；同頁 FAQ L295–296 卻說目前不能按 **Relation 或 Formula** 分組。兩處同頁相互牴觸，不能從這份文件推定現行版本實際支援 Relation grouping；需要未來獲授權在隔離環境實測。此差異是來源品質發現，非治療所系統故障。
- 反例 A：將 Session 或 Billing 以「已完成／待核對」卡片分欄，可能讓行政人員把 UI 分組視為正式收款或補助核准；Board 的欄位 Sum/Count 是目前顯示集合的統計，不是跨方案期別、取消狀態、資格與歷史收費的核准計算。
- 反例 B：卡片拖曳改動 Status/Select 可能改變真實業務狀態；即使只是為了排版，對已完成會談、待收款、資格待核資料也可能造成不當狀態轉移。應先區分「純顯示分類」與「可修改業務狀態」，不能假定拖曳只改外觀。
- 反例 C：Board 隱藏欄、卡片 Property visibility 不代表權限隔離。個案敏感資料不能因看不到卡片上的欄位就視為安全；且大量卡片與欄位可能違反使用者「同類資料同頁、開啟即見」的高頻核對需求。
- 推論：Board 適合狀態流程的視覺化，但**不能直接替代**既有同頁表格核對與正式狀態／金額計算；是否適用必須以任務、角色、效能、權限與歷史資料驗證。未批准新增 Board。

## S02｜List view（新來源候選）
- URL：https://www.notion.com/help/lists
- canonical：`notion-help:lists`；標題 `List view`；維護者 Notion Help Center；發布／最後更新日頁面未明列，取證 2026-10-28；閱讀軌跡 `AUTO-75-20261028-1842-RESEARCH-S02-R1-MAIN-TEXT`。
- 讀取範圍：官方頁面主要正文約 L107–L185：用途、Create a list、Add list view、Property visibility/排序、inline/full-page 轉換、Open pages in full page、FAQ；影片/圖片未完整實際觀看。
- 官方產品描述：List 是簡潔的資料庫檢視，適合不需顯示大量屬性的筆記、文章與文件；每個項目仍是可開啟的資料庫頁面，屬性出現在項目右側，可調整顯示與順序。這不表示原始屬性或資料庫關聯被刪除。
- 反例 D：若把高頻 Billing／Session／補助額度工作台改為僅顯示名稱的 List，行政人員須逐筆點開才能核對期別、金額、狀態與異常，反而違反「同頁直接看見」及降低操作成本的要求。
- 反例 E：List 的隱藏屬性只處理畫面密度，不是敏感資料的欄位層級授權；不能用 List 取代真正的角色與資料權限。
- 反例 F：將原本一覽式表格換成 List 可能使同案多 Session／跨期 Price Plan 的比較上下文消失；若只保留短標題，也可能讓同名個案或相似收款項目被誤選。精簡不等於可辨識性與資料正確性。
- 推論：List 可能適合低頻文件／備查導覽，不應無證據地取代需要多欄比較的日常財務與會談核對；**不授權變更現有 View**。

## 交叉反證、嚴格計數與安全
- 跨文件結論：Board 的狀態視覺化與 List 的精簡都可能改善特定任務，但**同頁可見性、業務狀態真值、權限、歷史方案期別、公式與效能**是獨立驗證責任。官方 Board 同頁的 Relation grouping 互斥敘述需獨立核對，不能直接採用任一版本。
- 本輪 `NEW_SOURCE_CANDIDATE=2`、`MAIN_TEXT_READ=2`、`FIRST_COUNTEREXAMPLE_GROUPS=2`、`COUNTEREXAMPLE_SCENARIOS=6`、`FULL_R1=0`、`FULL_R2_TO_R10=0`、`FULL_DEEP_PASS_10_OF_10=0`、`CUMULATIVE_VERIFIED_10_OF_10=0/10000`。同 URL、語系鏡像、FAQ 與同一次分析不重複計篇或閱讀次數。
- **NOT TESTED**：原始圖片／影片／實際拖曳與 UI、鍵盤/讀屏/手機、Notion 真實 Board/List View、角色權限、Formula、Billing/Session/補助真值、跨期與效能。未取得研究門檻或使用者確認，**不得開始重新設計**。
- **NO NOTION/SYSTEM WRITE**：只更新 GitHub 研究與進度紀錄；不改 Notion 正式/TEST 頁面、Database、Data Source、View、Formula、Relation、權限或業務列；不動正式 GAS、Cloud Run、Session、部署。手動與排程研究仍可並行。
