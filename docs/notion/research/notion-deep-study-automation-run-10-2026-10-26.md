# Notion 深度學習｜AUTO-10（2026-10-26）頁面分析、成員角色、邀請權限

> 範圍：官方公開文件唯讀＋GitHub研究紀錄；與手動「繼續」獨立並行。沒有修改 Notion 頁面、資料庫、檢視、公式、權限、業務紀錄或正式GAS/Cloud Run/Session。**本批未達十次完整深讀；整體0／10,000篇合格**。本批標記 `AUTO-10-20261026`，台灣時間2026-10-26查閱，非文章發布日期。

## 去重與來源分級

本輪開始先讀 main 最新 README、根AGENTS、source-of-truth、Notion AGENTS、sources、decision-log、acceptance-status、2026-10-24首批、2026-10-25研究批次02–04、十面向研究、MANUAL-01、AUTO-01–09；依 canonical slug 去重，不把語系翻譯或同頁不同段落重算新篇。本批新增 **3篇未在既有索引出現的官方URL**。以下皆取得官方可讀的文字主要章節並進行各一次新的反例分析（`MAIN_TEXT_READ + ANALYTICAL_PASS_1`），**沒有觀看嵌入影片、逐張解讀全部圖片、實帳操作、權限或效能測試**；不符合嚴格`FULL_DEEP_PASS`。

| Source ID | 唯一來源URL與標題 | 文字覆蓋／證據等級 | 尚未驗證 |
|---|---|---|---|
| AUTO10-01 | [Page analytics](https://www.notion.com/help/page-analytics) | 官方正文約106–142行：View page analytics、Opt out of page analytics；`MAIN_TEXT_READ + ANALYTICAL_PASS_1` | 付費層級實帳、圖表實際數值、匿名/跨裝置瀏覽、圖片 |
| AUTO10-02 | [Who's who in a workspace](https://www.notion.com/help/whos-who-in-a-workspace) | 官方正文約106–280行：Members、Restricted members、Guests、Temporary members、Owners/Admins、移除與FAQ；`MAIN_TEXT_READ + ANALYTICAL_PASS_1` | Free實際block計數、restricted權益、邀請及移除實帳測試 |
| AUTO10-03 | [Manage members & guests](https://www.notion.com/help/add-members-admins-guests-and-groups) | 官方正文約106–352行：成員邀請／域名／臨時成員／訪客／申請核准／移除／FAQ；`MAIN_TEXT_READ + ANALYTICAL_PASS_1` | 嵌入影片無法播放、Enterprise流程、Guest邀請與繼承權限實帳 |

## AUTO10-01｜頁面瀏覽分析不是業務驗收

- **假設**：Notion頁面顯示很多人瀏覽，代表治療所使用者已讀懂最新青壯補助額度規則。
- **核對**：需有該頁Owner或Editor權限才能看Page analytics；可見總瀏覽量與不重複瀏覽量、建立／編輯／瀏覽資訊。官方明示使用者可在全域或單頁選擇`Don't record`，因此紀錄可能不完整。
- **反例**：工作台頁面有10次瀏覽，但可能都是同一位管理者重開；即使10位不同使用者開過，也不能證明理解正確或額度Formula計算正確。有人停用view history，無法把缺席解讀成沒看過。
- **修正**：流量分析、真人UX測試、業務資料驗算是三種不同證據；不得用Page analytics當補助核定/使用者驗收PASS。
- **尚未做**：實帳開啟圖表、匿名分享/權益驗證、第2～10次獨立完整重讀。

## AUTO10-02｜Guest／Member／Restricted member不是同一種權限或成本

- **假設**：為每位兼職心理師建立Workspace Member與Guest在權限、費用、功能上差不多。
- **核對**：Guest需逐頁受邀，不能取得workspace-wide access或加入成員群組；Restricted member需被加進特定Teamspace/頁面且有部分功能限制，但仍像Member計費；Free方案超過一名Member，官方現行文件表示Workspace有1000 blocks限制，付費方案Member按席計費。Temporary member是特定Notion Marketplace顧問類型，不是一般臨時工免付費的通用角色。
- **反例**：把Guest轉為Member以解決某一頁存取問題，可能增加計費席次或暴露更廣的workspace內容；反過來只給Guest單一頁面，也不能推論其可查看其他必要來源表。以Restricted member名稱推論最低權限亦不成立，Teamspace角色及個別分享規則仍需檢驗。
- **修正**：必須分辨Workspace role、Teamspace membership、Page permission、Guest inherited subpages、Billing entitlement；單一名稱不足以證明資料隔離或成本。
- **尚未做**：Free方案實際席次/Block計數、心理師真實權限、繼承權限與費用核對、第2～10次獨立完整重讀。

## AUTO10-03｜邀請頁面可能連帶授權子頁，邀請連結不等於安全白名單

- **假設**：只要邀請對象加入特定頁，便只會看見該頁的內容；且訪客邀請一律不會有費用或權限意外。
- **核對**：官方寫明Guest可在單頁受邀、預設可能連帶看到子頁，除非另設子頁限制。Invite link可讓取得連結的人自動加入為Member（在付費方案可能產生席次費用）；Allowed email domains可能讓相符網域的人加入Member。非Enterprise的外部訪客請求預設開啟，Free不能關閉此請求入口；這不是自動核准。Enterprise另有Guest邀請申請核准流程。
- **反例**：若補助管理父頁下含跨個案/財務子頁，分享父頁給兼職心理師可能連帶暴露不必要資料；以「連結很隱密」假設不會加入付費Member亦不成立。訪客的**請求**與**取得存取權**是兩個事件，不能混為一談。
- **修正**：受邀對象身分、頁面與子頁繼承、workspace網域/邀請連結、實際授權及帳單須分開核對；本輪不更動任何Share/Permission。
- **尚未做**：多角色實帳測試、Enterprise與Free細節及UI截圖逐張核對、第2～10次獨立完整重讀。

## 跨來源校驗、進度及界線

- **Page analytics × Who's who**：可被追蹤的瀏覽量並不等於某種角色確實理解或有足夠權限；Owner/Editor才可查看分析，並不表示所有閱覽者被完整計入。
- **Who's who × Manage members**：Guest在頁層級授權與其子頁繼承範圍須一起看；Member/Restricted member與付費席次/工作區預設權限又是另一層。此為官方文字交叉分析，不是已驗證治療所權限。
- **來源內限制**：2026-10-26讀取的官方版本可能更動；同一文章可讀主節不代表已檢查所有圖片/影片/實機；只保留可公開的非敏感研究結論。
- **可核實計量**：本批新去重來源3；主要文字章節+獨立反例分析各1輪（共3篇）；十次嚴格完整深讀合格新增0；**全域合格仍0／10,000**。無付費模板實際複製、真人UX/效能/角色權限/資料真值驗收。
- **禁止擴權**：本批只寫入GitHub研究檔及必要索引，不設計新Notion版面、不改任何業務內容/公式/資料來源/權限/正式系統。與手動流程並行：不同批次檔名，索引寫入前取最新main與SHA、寫後讀回；衝突只合併非重複增量，無法安全合併則停止該檔寫入。
