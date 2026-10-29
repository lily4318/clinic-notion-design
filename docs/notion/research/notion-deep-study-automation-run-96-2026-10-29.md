# AUTO-96｜Notion 原生跨工具資料庫同步、分享邊界與同步建立權限（2026-10-29）
- Trace: `AUTO-96-20261029-1539-MANAGED-SYNC-GOVERNANCE`; lane: hourly automation; batch: NOTION-MANAGED-SYNC-GOVERNANCE; repository: `lily4318/clinic-notion-design`; **RESEARCH ONLY / NOT DESIGN**.
- 開始前 Fetch main：`README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`、`docs/notion/research/README.md`、`docs/notion/research/audit-checklist-and-research-progress.md`、`docs/notion/research/evidence-register-2026-10-24.md`、`docs/notion/research/notion-deep-study-manual-01-2026-10-25.md`、`docs/notion/long-term-goals.md`、`docs/notion/research/research-to-implementation-matrix.md`；列出當期 research 目錄並確認 AUTO-95 為最新既有自動研究紀錄。
- 2026-10-29 臺灣查核；兩 canonical URL 在當期 `sources.md` 精確全文比對均為0命中，首批證據與 MANUAL-01 亦未見，GitHub 私人庫 code search 不足以完成全歷史語義去重；**兩篇僅登記新來源候選**，同文不同網址、翻譯版、其他歷史批次逐檔比對 PENDING。
- 計量：`NEW_SOURCE_CANDIDATE=2`、`OFFICIAL_MAIN_TEXT_SECTION_READ=2`、`COUNTEREXAMPLE=6`、`FULL_R1=0`、`FULL_R2_TO_R10=0`、`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`；累積可核實 **0／10,000篇**。此為兩篇官方主文各一次文字段落閱讀與反證，不計為10遍獨立完整深讀。

## S01｜Sync data from other tools to Notion
- URL: https://www.notion.com/help/sync-data-from-other-tools-to-notion
- canonical identity: `notion-help:sync-data-from-other-tools-to-notion`; publisher: Notion Help；作者與首次發表日未核；查核 2026-10-29。
- 獨立閱讀事件 `AUTO-96-20261029-1539-MANAGED-SYNC-GOVERNANCE-S01-R1-MAIN-TEXT-SEC107-243-PARTIAL`。官方頁可讀主要正文約 L107–243，逐節查核 What you can sync、Before you start、Set up、first import、ongoing updates、history windows、use/share、sync status、managed vs Worker、troubleshooting；原圖、原始實際操作、外鏈各篇未完整查閱，故 `PARTIAL_MAIN_TEXT` 而非完整R1。
- 來源證據：(1) 2026-10-30 舊版 GitHub/Jira/Asana/GitLab sync 停止更新，既有同步庫留存但不再刷新；新同步另建新庫、不會原地搬移。(2) 新 managed sync GitHub/Jira需Business（或文件所述Mobile Business add-on）、Salesforce需Enterprise；一方向來源→Notion，來源同步欄位在Notion唯讀。(3) 初始匯入可只出現部分資料；更新延遲依來源/配額；Healthy或近期執行不保證每筆資料已同步。(4) 30/90/365天滾動歷史視窗按來源最後更新日；資料超出範圍時，Notion同步頁**連同自建欄位值**可被移除，並非單純View篩選。(5) 來源系統個別使用者權限不會複製到Notion每個檢視者；Notion資料庫分享可能讓人看見其在來源系統無權存取的資料；來源權限變更也未必移除既有Notion資料。(6) Relation需要兩端頁面均已同步；狀態/缺資料須查history、匯入、權限與View。
- S01-CE1：若把同步的GitHub/Jira或外部補助清冊當 Billing／Session 的長期歷史主檔，選30日歷史視窗可能使未更新的資料頁及自建欄位消失；**不能以同步庫代替法定歷史與跨期金額快照**。
- S01-CE2：同步狀態顯示Healthy或近期同步時間，卻仍有待匯入／延遲／權限導致的缺項；**不能把Healthy推定為全部會談、收款、核定期別完整一致**。
- S01-CE3：以有權存取外部資料的管理者帳號建立同步後，把Notion資料庫分享給其他心理師；來源權限不會逐位繼承，可能使無來源權限者看到敏感資訊。**Notion資料庫分享需要獨立授權檢查**，不得將此功能直接用於病歷/財務明細。
- 期限反證：10/30停止更新是**特定legacy sync**官方公告，並無證據本所實際使用legacy sync，故僅標為條件性風險，不宣稱本所同步即將中斷或已受影響。

## S02｜Manage who can create database syncs
- URL: https://www.notion.com/help/manage-who-can-create-database-syncs
- canonical identity: `notion-help:manage-who-can-create-database-syncs`; publisher: Notion Help；作者與首次發表日未核；查核 2026-10-29。
- 獨立閱讀事件 `AUTO-96-20261029-1539-MANAGED-SYNC-GOVERNANCE-S02-R1-MAIN-TEXT-SEC107-239-PARTIAL`。官方頁主要正文 L107–239，逐節查核 Who can manage、connections settings、who can create、providers、existing connections、connect、create、sync health、FAQ；圖像、實際帳號與角色權限未測，`PARTIAL_MAIN_TEXT`。
- 來源證據：(1) 僅workspace owner可管理 Settings→Connections→Manage 的建立權限；可設定all members／owners only／owners and selected groups，guests不可建立。(2) 「限制誰可建立同步」與「限制誰可安裝connections」為不同設定。(3) Connected頁列出的是連線，不等於每筆資料庫同步；逐筆須進供應者的 Your syncs。(4) 更改建立權限**不會影響已存在的同步**；workspace owner可管理其他成員建立的同步。(5) provider的synced-through time與健康狀態可檢視；Notion官方頁列出Business/Enterprise適用限制。
- S02-CE1：管理者把「可建立同步」從所有人改成僅owner，就認為既有外部同步已被關閉；官方明言既有同步不受此設定變更影響。**治理設定不是撤銷已建立的資料管道**。
- S02-CE2：只檢查Connected清單沒有看到某個單獨同步，就推定資料庫沒有從外部匯入；連線列表與逐筆sync清單不同，可能漏查資料流。
- S02-CE3：即使限制建立者，也不等於已限制同步資料庫的讀取/分享；對心理師/行政/負責人仍需獨立檢查Notion頁面權限、來源權限、實際資料類型。不能以「owner only」代替個案資料保密驗收。

## 交叉結論、未核實事項與界線
- 同步功能的**來源授權、建立權限、資料庫分享權限、歷史保留、同步新鮮度**是五個不同控制面；不能以任一面通過代替其他面。研究只提供未來風險比較，不核准新增同步、改設定、建資料庫或重設流程。
- `NOT_TESTED`：本所是否存在legacy sync、目前Notion方案與workspace owner身分、實際Connections/Your syncs、頁面分享、真人角色、原始資料完整性、歷史Billing/Session/Price Plans與補助跨期、手機/鍵盤/讀屏、效能/外部系統連線。未查任何真實病歷、個資或財務列。
- 本輪僅允許 GitHub 研究/來源/決策/驗收紀錄；**沒有修改任何Notion正式/TEST頁面、資料庫、View、Formula、Relation、權限或業務資料，也沒有修改GAS/Cloud Run/Session/部署**。研究門檻尚未達成，禁止進入Notion重新設計；自動與手動研究可並行且不得重複計數。
