# AUTO-82｜Notion 深度學習：Linked databases 指南＋Data sources 手冊對照（2026-10-29）

Trace: `AUTO-82-20261029-0143-RESEARCH`｜純外部研究與GitHub記錄｜**NO NOTION/SYSTEM WRITE**

## 開始前基準、去重及範圍
- 重新讀取 main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md，以及 research/README.md、research/audit-checklist-and-research-progress.md、research/research-to-implementation-matrix.md、AUTO-80/81紀錄。研究與日常Notion設計嚴格分離。
- 本輪 sources.md 全文查找 `using-linked-databases` 為0筆，舊 `data-sources-and-linked-databases` 已有歷史登錄；GitHub code search兩個詞均回傳0，**但對已知舊來源也回傳0，故不能把code search當可靠的全庫去重證據**。未完成所有歷史研究逐檔、跨語系同文異址與影片同源語義比對。新篇只列候選，不列已全庫唯一。
- 取用日2026-10-29；來源維護者Notion Help Center，文章首發/最近修訂日未核。兩頁均含嵌入影片/圖片，本輪只閱讀可取得的**全部主文文字段落與FAQ**，沒有播放影片、逐張檢查圖片、實際點選或真人操作；不符合完整R1，也不構成任何Notion功能PASS。

## AUTO82-S01｜Using linked databases（新來源候選）
- URL: https://www.notion.com/help/guides/using-linked-databases
- Canonical: `notion-help:guides/using-linked-databases`；內容類型：3分鐘影片指南＋簡短文字摘要；同源影片可能嵌於其他Help頁，**影片未看，不以3分鐘時長冒稱已閱讀影片**。
- 閱讀事件 `AUTO-82-20261029-0143-RESEARCH-S01-R1-MAIN-TEXT-ONLY`；可核文字位置：官方頁約L107–L130，涵蓋用途、`/linked`建立、複製既有View/新建View、Filter/Sort、資料修改回寫來源、View設定限於linked instance。原頁全文很短，主要教學內容可能在影片中，故僅計文字閱讀1篇候選。
- 反例A【把linked資料誤當複製快照】：將原方案期別的Linked View視為已保存歷史Billing金額，後續更改來源屬性時歷史摘要仍會變動。反證：linked呈現共享資料，不提供交易時點凍結證據；需以已核實的歷史收費來源判定。
- 反例B【以Filter當安全隔離】：把心理師／個案資料只靠不同Linked View篩選後公開給不同人，可能讓原始來源權限與可見資料超出預期。反證：View設定不是存取授權，必須依原來源權限核驗。
- 反例C【以精簡跳頁代替原位資料】：把多個日常來源全部改成linked入口連結而非同頁inline資料，違反已確認「同類資料同頁、開啟即見」。反證：linked技術可支援原位顯示，但是否可用須真人/效能驗收，不能擅改既有頁面。

## AUTO82-R01｜Data sources（既有來源針對性複讀）
- URL: https://www.notion.com/help/data-sources-and-linked-databases
- Canonical: `notion-help:data-sources-and-linked-databases`；此URL先前已登記為N04並有研究重讀，**不算新來源，不計完整R2**。
- 閱讀事件 `AUTO-82-20261029-0143-RESEARCH-R01-TARGETED-INDEPENDENT-REREAD`；本輪再次閱讀官方可讀主文與FAQ約L107–L206，專注區分「linked view／linked data source／move source」的權限與更動傳播；不是完整多模態重讀。
- 事實核對：來源可以被其他database連結；Linked資料源的View/Filter/Sort/Group修改不影響原庫View，但**標題、屬性、頁面**修改反映回原資料；接收頁面分享不代表接收者取得原資料庫存取權；Forms需在原始data source的database建立。
- 新反例D【把來源移動當成改View】：文件指出移動來源可讓未隨移動的Views變成linked views；若日後為整理工作台而移動來源，可能改變操作路徑與原始歸屬，不是單純視覺整理，必須先核對依賴與回復。
- 新反例E【將原庫權限和容器權限混同】：同一database多個source不能逐source另設不同access，但linked source仍遵循原庫授權；因此「把多來源放一頁」不等於能統一授權或自動隔離。需實際角色測試。
- 新反例F【官方手冊自身的角色文字不一致】：約L159稱`Can edit`可以移動data source；約L182稱只有`Full access`可以移動。此為同頁敘述衝突，不能憑文字直接決定正式環境的權限或授權操作，需未來經許可核對實際UI/方案/角色。**本輪未操作Notion**。

## 跨來源反證、研究層級與進度
- Linked View是同一來源的另一種呈現；它既不是資料快照，也不是欄位/列層級的安全邊界。複製View、移動Data Source、建立Form、分享頁面分屬不同操作，不能因名稱相近而視為等價。對治療所的候選設計仍須以「同頁直顯、保留歷史金額、原來源權限、跨方案期別」作驗收；本輪不提出已核准改版。
- `NEW_CANDIDATE=1`、`MAIN_TEXT_READ_NEW=1`、`TARGETED_REREAD_EXISTING=1`、`INDEPENDENT_COUNTEREXAMPLE_SCENARIOS=6`；`FULL_R1=0`、`FULL_R2_TO_R10=0`、`FULL_DEEP_PASS_10_OF_10_THIS_RUN=0`，累積可核實仍 `0/10000`。
- 阻礙：跨歷史全文及同文異址/影片重複去重、影片/原圖、互動、鍵盤/讀屏/手機、真人Notion UX、角色權限、Billing/Session歷史金額、原生Formula、效能尚未驗證。**沒有修改Notion正式或TEST頁、DB/View/Formula/Relation/權限/業務資料，沒有修改正式GAS/Cloud Run/Session/部署；未達研究門檻，不開始重新設計。**
