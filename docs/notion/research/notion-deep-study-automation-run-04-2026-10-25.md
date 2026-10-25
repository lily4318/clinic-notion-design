# Notion 深度學習｜排程獨立批次 AUTO-04：提醒、Inbox、通知設定（2026-10-25）

> **本輪僅研究及 GitHub 證據記錄，不修改 Notion、GAS、Cloud Run 或正式 Session。** 執行軌跡 `AUTO-04-20261025-1937-TPE`。查閱日：2026-10-25（Asia/Taipei）；網站未提供可核實的每篇正式更新日期，不臆測。研究目標為10,000個去重來源×每個10次可稽核完整深讀，**本輪沒有任何來源達成10/10**，尚不進入Notion設計。

## 1. 先行查核、去重與閱讀分級

- 本輪先讀取 GitHub `main` 的 `README.md`、根 `AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`decision-log.md`、`acceptance-status.md`；並逐一讀取原始16篇、批次02/03/04、十面向研究、排程AUTO-01/02/03及手動MANUAL-01清冊。三個新官方文章的 slug 在上述已知清冊未找到，**本輪暫認定3個新canonical文章**；跨所有未系統化歷史研究的全球唯一總數仍不可聲稱已完成稽核。
- `MAIN_TEXT_READ + ANALYTICAL_PASS_1`：逐節打開並閱讀網頁可取得的主要文字段落，為每篇寫出獨立初始假設、反例、修正理解及待驗證；**不代表**已逐張檢查圖片、觀看影片、用真人工作區測試、做第2–10輪完整深讀。
- 本批只新增 **3 個來源**、**3 個獨立首次分析輪次**；跨文件交叉閱讀不計新增來源或第二次深讀。文字來源已取得；嵌入媒體未逐一檢查，嚴格 `FULL_DEEP_PASS` 計 **0**。

## 2. 來源及章節覆蓋

| ID | 官方文件及唯一URL | 已讀的可取得文字主章節 | 本次等級 |
|---|---|---|---|
| AUTO04-01 | [Reminders](https://www.notion.com/en-gb/help/reminders) | `Create a reminder in a page`、`Create a reminder for someone else`、`Create a reminder in a database`、`How reminders work`、FAQs（原網頁約116–161行） | `MAIN_TEXT_READ + ANALYTICAL_PASS_1` |
| AUTO04-02 | [Inbox & notifications](https://www.notion.com/en-gb/help/updates-and-notifications) | Inbox/來源、Interact/filter、Agent、Mobile、Notifications、Page/Database update notifications、Person property notification（約113–233行） | `MAIN_TEXT_READ + ANALYTICAL_PASS_1` |
| AUTO04-03 | [Notification settings](https://www.notion.com/help/notification-settings) | How notifications work、Types/timing、Settings、Teams integration、FAQs（約115–200行） | `MAIN_TEXT_READ + ANALYTICAL_PASS_1` |

這三篇同屬「提醒／通知」領域，但有各自不同的官方頁面、URL及內容職責：建立提醒、集中處理通知、個人通知送達設定。它們不是同一文章的不同語系，不以章節切割充數。上述網頁的 header、footer、影片及圖片不納入「全文完整深讀」證據。

## 3. 各篇獨立分析與反例

### AUTO04-01｜Reminders（第一輪分析）

- **初始假設**：Notion 的Date提醒可直接充當政府補助期別的每週固定提醒及心理師行政任務派送機制。
- **可查原文**：頁面內可用`@remind`設定時間，若要提醒另一位同事需在**同一區塊**同時@提及該人；資料庫Date屬性可以設定提醒，但該文**明說在資料庫內無法用同樣方式替他人建立提醒**。提醒會在Inbox顯示，手機推播及email受使用狀態影響；FAQ仍寫「尚無原生recurring reminders」。
- **反例**：每週應核對青壯方案額度並不是單次Date提醒；即使每週有新頁面／資料庫模板產生，也**不等於**每週通知都能可靠送達、已核對、已完成申報。若使用者在資料庫直接以Date欄設定「提醒某心理師」，可能誤以為他人必然收到通知。既有批次02/03的Recurring database template與這裡的`recurring reminder`屬不同能力，不能混用。
- **修正理解**：`Date due`、`Reminder notification`、`Recurring workflow`、`Completed business check`四層必須區分；在未實測角色/設備/通知時不當作財務或申報的唯一防漏保障。
- **待驗證**：不同帳號角色、提醒發送對象、工作區方案、實際時區與推播延遲；第2–10次深讀**未執行**。

### AUTO04-02｜Inbox & notifications（第一輪分析）

- **初始假設**：Inbox只要篩出`Updates`就可以視為完整的待辦清單；手機和桌面具有相同篩選能力。
- **可查原文**：Inbox整合@mentions、Person屬性通知、提醒及邀請；類型有`Access`、`Discussions`、`Mentions`、`Automations & runs`、`Updates`、`Workspace`。篩選後只改**顯示內容**，不會停止通知送出；類型篩選僅Web/Desktop支援，手機仍可進行部分其他篩選/封存/已讀操作。針對資料庫頁面可訂閱`All updates`、`Important updates`（Status/Assignee/Due date）、`Replies and @mentions`。
- **反例**：工作者只看`Mentions`會看不到`Updates`下的提醒；某筆補助的額度數值Formula變動不必然符合`Important updates`限定的欄位類別。通知標示已讀、封存不等於補助額度完成核對，也不表示資料正確。手機可以管理Inbox不代表有桌面**同一種「通知類型篩選」**。
- **修正理解**：通知篩選是**個人注意力管理**，不是業務真值或工作狀態資料庫；必須避免把「沒有看到通知」推成「沒有待核對資料」。對治療所流程僅做風險研究，不實作Inbox工作台。
- **待驗證**：手機平台/版本、通知實際類型、Person屬性大量人員、真實欄位變動通知及漏發率；第2–10次深讀**未執行**。

### AUTO04-03｜Notification settings（第一輪分析）

- **初始假設**：使用者打開手機推播就一定會準時看到所有補助相關提醒；關閉Inbox某個通知類型就是停發。
- **可查原文**：通知通道包括Inbox徽章、Desktop、Mobile、Email、Slack、Microsoft Teams；是否發推播／郵件會受App是否開啟、當下是否正看觸發頁面、`Always send email notifications`設定影響。FAQ說App開啟時提醒可能只顯示Inbox badge；且提及Person property時**個人無法單獨取消訂閱**，可透過Inbox過濾隱藏。Teams需額外連線設定。
- **反例**：前台電腦長期開著Notion時，心理師以為手機一定同步彈出提醒，實際可能只有Inbox badge。把Inbox類型隱藏並不等於源頭取消通知。此文稱個人無法取消Person屬性通知，而AUTO04-02稱資料庫**具編輯權的人**可在Person屬性設定`Users and groups`／`Users only`／`None`：兩者的權限主體不同，**不是直接矛盾**。
- **修正理解**：`產生事件`、`送達通道`、`用戶看到`、`已執行業務`四階段不能等同；跨裝置推播不可作為核定額度及期限的唯一控制。
- **待驗證**：真實Free方案、iOS/Android與桌面差異、Email政策、不同通知類型的準時率、設定是否由管理員限制；第2–10次深讀**未執行**。

## 4. 跨來源反例／尚未解決的文本張力

1. **提醒 vs 任務資料**：`@remind`只設定通知；無法保證每週持續、也不保證補助計次或期限狀態的真實性。此項與AUTO-03的Feed/Tasks關係類似，但沒有新增第二輪重讀計數。
2. **Inbox篩選 vs 權限**：隱藏通知只是畫面過濾，和資料庫View filter一樣不構成權限隔離；不能藉隱藏資訊達到保密要求。
3. **跨平台篩選差異**：官方同頁說手機可篩選Inbox，另明說「notification type filter只支援web/desktop」；合理區分為手機可做已讀／封存等篩選，但**特定類型**篩選不可直接假定支援。標為`UX_PLATFORM_SCOPE`，非已測試結論。
4. **Person屬性通知控制**：`Notification settings`所稱個人無法自行退訂與`Inbox & notifications`所稱屬性編輯者能關閉通知並不互斥。若要驗證，需測「收件者」和「資料庫管理者」兩種角色；本輪不修改任何設定。
5. **提醒通道時間文字差異**：Reminders文章說手機5分鐘內推播、App未開時有email；Notification settings則明說App已開時通常僅Inbox badge。應以具體設備/前景狀態理解，不可由其中一段推論所有情況都能手機準時提醒。標`DELIVERY_CONDITIONAL`，不是實測故障率。

## 5. 嚴格驗收與保留不變

| 指標 | 本輪可核實 |
|---|---:|
| 與已知清冊去重的新canonical URL | **3** |
| 已讀可取得的文章主要文字章節 | **3** |
| 每篇有獨立初始假設／反例／修正推論的首次分析 | **3** |
| 第2–10次獨立完整深讀 | **0** |
| 完成10次嚴格深讀的篇數／總目標 | **0 / 10,000** |
| 任何Notion頁面／DB／Views／Formula／Relation／權限／業務資料修改 | **0** |
| GAS／Cloud Run／Session修改 | **0** |
| 實際真人、手機、權限、通知送達、效能測試 | **未執行** |

本輪研究只保存GitHub，不將AI設計規則放入Notion操作頁。研究文件寫入後需讀回blob SHA/內容及Commit；共享`sources.md`、`decision-log.md`、`acceptance-status.md`必須逐檔重新讀取最新main SHA並條件更新，遇到平行衝突不覆蓋別人的研究成果。未完成10,000篇各10次完整深讀，亦未經使用者確認，**禁止開始Notion重新設計**。
