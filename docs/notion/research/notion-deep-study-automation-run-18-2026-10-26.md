# Notion 深度學習｜AUTO-18｜2026-10-26（僅研究）

- 執行軌跡：`AUTO-18-20261026-0938`；來源身分 `AUTO18-S01`、`AUTO18-S02`。
- 本輪為每小時排程的獨立研究單元；聊天室手動續作不受影響。只允許官方公開文件閱讀與 GitHub 研究記錄，**不修改任何 Notion 頁面、資料庫、View、Formula、Relation、權限、GAS、Cloud Run 或 Session**。
- 讀取基準：2026-10-26 的 `main`：根 README、AGENTS、docs/system/source-of-truth、docs/notion/AGENTS、sources、decision-log、acceptance-status，以及 research/README、首批 evidence-register、第二～四批、十面向、MANUAL-01、AUTO-01～17 研究清冊。比對 `sources.md` 未發現本輪兩個 canonical slug；GitHub 程式碼搜尋亦未命中。全域完整去重仍待另行機器稽核，故新來源為**目前已查清冊暫列2篇**。
- 網頁查閱日：2026-10-26（臺灣）；**不是**原文發表或更新日。語系 canonical 統一為英文 `https://www.notion.com/help/{slug}`；同語系變體不得重複計數。
- 深度定義：本輪各自閱讀可取得的主要正文、章節與 FAQ，留下反證；未逐一驗證全部插圖、示範影片、付費功能或真人權限，故只能標 `BODY_MAIN_AND_FAQ_R1`，**不可計入10次完整深讀**。R2～R10未執行；FULL_DEEP_PASS=0。

## AUTO18-S01｜What are Custom Agents?

- 標題：What are Custom Agents?；URL：<https://www.notion.com/help/custom-agents>；canonical identity：`notion-help:custom-agents`；閱讀輪次：`R1/BODY_MAIN_AND_FAQ`。
- 實際核對章節：產品用途與方案資格、建立方式、Triggers & schedules、Notion/Slack 事件、Tools and access、Web access、agent hand-off、模型與管理控制、分享、Embed、Activity/Version history、Duplicate、Insights CSV、FAQ。官方全文頁面約822行（包含大量導覽及頁尾），正文從標題至 FAQ。
- 官方可核對事實：Custom Agents 為 Business/Enterprise 功能；可定時或依事件觸發、讀取被授權頁面與外部連接來源；嵌入頁面**不會**自動授予讀取該頁權限，也不會讓所有頁面讀者直接使用 Agent；複製 Agent 不繼承無權資源、外部工具連線與既有執行歷史。來源章節位置（2026-10-26網頁可見行）：181–185、225–275、327–347、458–496、550–608、611–722。
- **原假設**：只要將行政助手嵌入首頁，所有看到首頁的人便可安全使用助手，助手也會自動讀到首頁內容。
- **反例**：頁面閱讀權、Agent互動權、Agent可讀的資料來源是三套不同設定。嵌入可顯示但無法聊天；Agent能聊天卻未被授予首頁資料存取時，也不會自動理解頁面；擁有Agent權限者還可能看到來源頁的輸出，即使無直接來源頁權限。
- **修正結論**：介面可見性不能取代Agent資源授權、輸出對象權限及跨角色敏感資料測試；這是未來安全驗收議題，**不是**建議立即部署付費 Agent。對免費版優先的現況不可假設可用。Activity/Version history可輔助追溯，但不等於對個案資料存取已符合規範。
- 未驗：影片、圖片、官方示範模板、Business/Enterprise帳戶實際費用與權限、行動裝置、跨角色資料外洩測試、真實輸出或刪除後復原。

## AUTO18-S02｜Custom Agents sharing & permissions

- 標題：Custom Agents sharing & permissions；URL：<https://www.notion.com/help/custom-agents-sharing-and-permissions>；canonical identity：`notion-help:custom-agents-sharing-and-permissions`；閱讀輪次：`R1/BODY_MAIN_AND_FAQ`。
- 實際核對章節：Agent自己的資源權限與人員的Agent使用權分離、Tools and Access、權限層級、Duplicate、協作、Guest/Restricted Member、Admin Directory、Enterprise Audit/Analytics、所有權轉移、FAQ。官方頁面約462行（含導覽頁尾），正文從標題至 FAQ。
- 官方可核對事實：Custom Agent以自己的授權讀取資料，**不以觸發者權限過濾結果**；分享Agent可能讓使用者得到原本無法直接開啟頁面/資料列的內容。移除使用者對來源頁的直接存取，若Agent仍可讀且使用者仍能互動，仍可能間接讀到資料。可從Agent的Tools and Access或原頁Share移除Agent存取；Enterprise具額外Audit/管理功能。來源可見行：115–156、166–230、240–319、322–368。
- **原假設**：已將個案資料庫設成私有，且個別工作者不能直接讀取，因此透過共享AI Agent查詢也必然無法看到那些資料。
- **反例**：Agent的資料權限與人員直接頁面權限獨立。若共享Agent本身可讀受限個案列，使用者可能從Agent回答取得不應讀取的個案資訊。僅把頁面隱藏、移至Private或撤銷某人的直接頁面權限，不能保證透過Agent的間接資料路徑也被封鎖。
- **修正結論**：未來若評估此付費功能，必須做「人員×Agent×資料列×輸出管道」權限矩陣及反向撤權測試；不可把Agent當作自動遵守使用者本人權限的安全邊界。這項研究不證明目前治療所存在Agent或外洩，亦不授權變更現有分享設定。
- 未驗：實帳權限、Guest限制邊界、所有權移轉後停止執行的實際行為、Enterprise audit紀錄、圖片與任何臨床資料實測。

## 交叉反證與研究限制

1. S01描述「預設只存取明確授權的資源」，S02補足**授權主體是Agent而非每個使用者**。這不是矛盾，而是權限模型兩個層次；不能只摘第一句「安全」便推論最小權限已達成。
2. 兩篇均與先前AUTO-10的Member/Guest、AUTO-11的Teamspace、AUTO-17的Webhook/Workspace研究有交集，但**不同原文canonical URL，且不是同一次閱讀**。未把交叉比較另算新來源或第二次閱讀。
3. 官方網頁可能更新；未核實確切文章修訂日。任何方案權益、AI模型、Agent credit與權限功能在未來採用前必須重新查驗。
4. 無真人、手機、效能、資料庫操作、權限或資安實測；不能宣稱功能已驗收、符合醫療個資規範或適合免費版。
5. 目前累積可核實完成「每篇10次獨立完整深讀」**0/10,000篇**。本輪新增暫列2個 canonical，2篇主要正文+FAQ文字閱讀，各1次反例；10/10嚴格完成新增0。全域唯一來源精確累計仍待跨檔去重稽核。

## 參照

- <https://www.notion.com/help/custom-agents>
- <https://www.notion.com/help/custom-agents-sharing-and-permissions>
- 專案內部：`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`、`docs/notion/research/` 既有清冊。
