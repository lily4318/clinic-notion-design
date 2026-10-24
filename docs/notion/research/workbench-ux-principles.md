# 工作台與 UX 研究｜治療所資料庫導覽

## 理論來源

- [Nielsen Norman Group：Progressive Disclosure](https://www.nngroup.com/articles/progressive-disclosure/)：常用功能優先在初始畫面，低頻詳細設定放在可找到的第二層；第二層的標題應能預期內容。
- [NN/g：10 Usability Heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/)：看得見系統狀態、減少記憶負擔、預防錯誤、保留使用者可控性。
- [NN/g：Information Scent](https://www.nngroup.com/articles/information-scent/)：導航名稱應明確預告目的地內容，不以華麗的分類詞取代工作任務。
- [Notion：Views／Filters](https://www.notion.com/help/views-filters-and-sorts) 與 [Linked views](https://www.notion.com/help/notion-academy/lesson/linked-views)：相同資料可依任務使用不同表格、看板、清單等檢視；變更檢視設定和變更資料來源內容是兩件不同的事。

## 對治療所的具體運用

**導航規劃不以資料庫技術名稱要求人員做記憶轉換**：

1. 「補助方案與核定期別」：先辨識正在處理哪個政府方案實例。
2. 「個案參與及使用期限」：查看個案在這一期的資格、使用、已確認與待核對事項。
3. 「心理師週額度」：確認適用該方案的週限額及回報狀態（目前 Staff 公式**僅**青壯115專用，不應暗示已通用）。
4. 「核定額度調整與歷史」：提供可追溯記錄，但收合避免壓迫首頁。

這是任務流的結構，不表示真的有所有 Linked Views 共用的「全球同步方案選擇器」。依 Notion 官方 View 的獨立設定特性，**不得宣稱切換一張表會同步過濾其它表**；Notion Dashboard 的 global filters 另屬不同功能且要核對免費版限制。

## 對既有十個行政頁面的評估策略

前次僅做初查的十個功能頁含 76 個嵌入／引用資料庫區塊（並非76個不同資料來源）：Intake 3、Cases & Episodes 9、Sessions 5、Billing 14、Events & Groups 15、Staff 14、Rooms 5、Tasks 3、Projects & Meetings 3、Documents 5。

**候選先查** Billing、Events/Groups、Staff 的區塊顯示與用途是否重複；即使引用區塊數很多，也不能未確認依賴就刪除。除政府補助 TEST 工作台已確認改版外，其餘舊頁只允許 A 保留／B 小幅修正，大規模重構 C 需使用者明確核准。

## 如何驗收「比較直覺」

以每種使用者角色設情境（負責人／行政／心理師）；只有在有權檢視的測試帳號下檢查：

- 「找到某一核定期別個案是否可用額度」需幾個導覽點擊、是否需要切換兩處未同步的快篩。
- 「某心理師本週未回報」是否可由正確方案與本週情境找到，而不是因沒有歷史週報被排除。
- 「額度不足或期限未知」是否保留**非自動放行**狀態，而非一張醒目黃色大 Callout；使用者已明確要求不要黃色提醒。
- 其他舊頁的高頻任務是否能直接進入；維護需求是否藏在清楚標籤的收合區而不是失去入口。
- 多個方案與不同期別可在相同 UI 模式操作，仍以 Price Plan Page ID 防混算。

尚未取得真人任務完成率、操作時間、主觀負擔等資料；**此文只代表可測試的 UX 假說和既有使用者決策**。
