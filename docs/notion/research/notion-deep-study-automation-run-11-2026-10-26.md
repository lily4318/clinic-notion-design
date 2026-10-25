# Notion 深度學習｜排程獨立研究批次 AUTO-11（2026-10-26）

> 研究軌跡：`AUTO-11-20261026-0244-ASIA-TAIPEI`。範圍只含公開Notion官方文件唯讀與GitHub研究紀錄；未修改Notion頁面、DB、View、Formula、Relation、權限、業務資料或正式GAS/Cloud Run/Session。研究目標10,000個去重來源各10次獨立完整深讀仍未完成；本批**不是**完整十次深讀或重新設計授權。

## 1. 本輪前置查核與來源身份

- 於2026-10-26（台灣時間）先讀取GitHub `main` 的 `README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`，並對照研究來源批次02～04、AUTO-01～10、MANUAL-01及來源索引。三個slug在已核對清冊中均未登錄；不同語系相同slug不另計。歷史清冊未有全面機器化全域唯一索引，故此結論限於本次可取得的清冊；遇平行新增須以最新main再去重。
- 實際開啟三篇Notion官方文章並讀取可取得的文字主章節：Manage teamspaces約L106–210；Create, join, & leave teamspaces約L106–157；Intro to teamspaces約L106–298。本文頁碼是本次web文字擷取的行號，非Notion固定段落ID。原文未提供可確認的修訂日，不推測。
- 三篇均屬`MAIN_TEXT_SECTIONS_READ + ANALYTICAL_PASS_1`；未逐張核對圖片、播放Intro嵌入影片、在免費/付費實帳做權限測試，`FULL_DEEP_PASS=0`，各篇**嚴格完整深讀次數0/10**。

| ID | 標題／官方唯一URL | 已核對主章節 | 狀態 |
|---|---|---|---|
| AUTO11-01 | [Manage teamspaces](https://www.notion.com/help/manage-teamspaces) | Workspace設定、Default、建立權限、所有Teamspace、接管、封存/還原、無Owner案例 | 主文字閱讀＋第1次反例；FULL 0/10 |
| AUTO11-02 | [Create, join, & leave teamspaces](https://www.notion.com/help/browse-join-and-create-teamspaces) | Browse、加入方案差異、建立/複製、Owner、Open/Closed/Private、離開 | 主文字閱讀＋第1次反例；FULL 0/10 |
| AUTO11-03 | [Intro to teamspaces](https://www.notion.com/en-gb/help/intro-to-teamspaces) | 建立/頁面轉Teamspace、成員/邀請、搬頁、General/Members/Permissions/Security、封存 | 主文字閱讀＋第1次反例；FULL 0/10 |

## 2. 三篇首次獨立假設—反例—修正

### AUTO11-01｜管理Teamspaces：Default與Archive的非直覺副作用
- **初始假設**：將治療所常用工作台指定為Default teamspace，等同於只改善側邊欄可見性，不改人員存取範圍；被否決的舊Teamspace可以直接刪除。
- **官方主文**：指定Default會讓現有及新加入的Workspace Members自動加入（Restricted Members例外）；從Default改回普通Teamspace時，原本所有Workspace Members會被移出；Teamspace只能Archive不能Delete；還原Archive會回到原可存取成員側欄。Enterprise Workspace Owner才有跨Teamspace接管權。
- **反例**：原本僅櫃檯人員在使用的行政Teamspace被設成Default後，其他一般Members也被加入，這是成員範圍變動，不只是UI美化；若再取消Default，可能讓需要使用的人員失去Teamspace成員資格。Archive不滿足使用者「否決設計必須真正清理」的資料刪除要求，但Notion此層級官方功能本身不提供Delete，不能謊稱已刪。
- **修正理解**：Default是群組成員配置動作，Archive是導覽/存取狀態變更而非實體刪除；任何日後改版需先辨識工作區/Teamspace/Page三層權限及依賴，不能從UI預覽推斷安全。**本批不提出也不執行實際設定變更。**
- **來源內部疑點**：同文「Manage teamspaces without an owner」說可指定新Owner，但步驟最後卻寫「Restore teamspace」，文案可能誤植；標記`DOC_INTERNAL_INCONSISTENCY`，未實帳核對，不採作操作SOP。

### AUTO11-02｜加入與離開：Closed可見不等於可進入
- **初始假設**：只要同在Workspace，所有人都能透過Teamspace清單進入治療所行政內容；若某人看不到清單項，代表內容已刪除。
- **官方主文**：Open可直接Join；Closed顯示存在但需Request；Private只在Business/Enterprise提供，未加入者不會看見。新建Teamspace的Creator成為Owner；能否建立新Teamspace受Workspace Owner設定控制；Leave只讓目前成員離開。
- **反例**：心理師在同Workspace可看到Closed行政Teamspace名稱，卻沒有權限直接加入；在Free/Plus不能假設有Private Teamspace隔離病歷；某成員Leave後看不到日常入口，原始Teamspace及內容仍存在。
- **修正理解**：Teamspace發現、成員加入、頁面可讀/可改、原始資料存在性各不相同。不能把「看不到」當刪除或把Closed當個案層級權限；需依實際方案與角色獨立驗證。**未做任何權限變更。**

### AUTO11-03｜Teamspace設定：Workspace安全繼承與方案限制
- **初始假設**：在Teamspace Security關閉訪客/匯出/公開連結等選項即可讓任何免費Workspace具備完整的敏感資料隔離，移動頁面只改導覽。
- **官方主文**：Teamspace有Members、Permissions、Security等設定；Open/Closed/Private範圍不同，Private限Business/Enterprise；Disable guests、Disable export、Disable publishing sites/forms/public links列為Enterprise-only；Teamspace安全設定繼承Workspace，部分放寬權限只有兼任Workspace Owner的Teamspace Owner可調；Teamspace只能Archive，不能Delete。
- **反例**：若使用免費方案，設計稿要求「關閉所有訪客及匯出」的Teamspace級開關會無法實作；將原有臨床資料頁Move to另一Teamspace，可能改變繼承的可見/管理範圍，不能當成純視覺整理；Archive只讓Teamspace從側欄消失，不是抹除資料。
- **修正理解**：需要將**功能可用性（方案）**、**工作區/Teamspace/頁面權限**、**資料層保護**分開查證，尤其敏感資料不得依賴導覽隱藏。此為限制識別，不代表已確認本治療所目前的實際Notion方案或角色設定。

## 3. 跨來源反證與稽核界線

1. AUTO-10已指出Member/Guest及席次成本差異；本輪補充Default teamspace可能一次擴大Members的Teamspace成員集合。不能因「自動加入」推論額外費用一定產生：需另外核對Member席次是否已存在。
2. AUTO-07/08指出Sidebar Hide不等於Delete；本輪官方進一步確認Teamspace只能Archive不能Delete。使用者要求實際清理時，不能以Archive冒稱真正刪除，也不能擅自以刪除業務頁取代。
3. AUTO-03指出Can edit content仍可能刪資料列；Teamspace級安全與資料庫權限不是同一層。不得從Teamspace是Closed推論每位成員都只能讀到自己個案。
4. 本輪未操作Notion或實帳，不能驗證本治療所使用哪個方案、任何人員的實際存取、角色或計費。來源中的功能描述可能隨版本變動。

## 4. 嚴格進度

| 指標 | 本輪可核實值 |
|---|---:|
| 新增、經已知清冊去重的官方canonical文章 | 3 |
| 文字主章節實讀＋首次獨立反例分析 | 3 |
| 既有來源本輪第二次完整深讀 | 0 |
| 圖片逐張/嵌入影片/實帳操作 | 0 |
| 本輪嚴格FULL_DEEP_PASS | 0 |
| 累積已完成各10次完整深讀的文章／10,000 | **0 / 10,000** |
| Notion/正式系統更動 | **0** |

研究僅記錄證據與反例，不產生新Notion設計或修改。若研究檔與平行流程發生重複，應以最新main重新合併去重；無法確認不得寫入共用索引。GitHub寫後須逐檔讀回Commit與blob SHA，不能把未驗證寫入稱為保存。
