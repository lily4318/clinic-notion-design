# AUTO-136｜Database settings 與鎖定不等於權限控制（2026-11-23 00:38 Asia/Taipei）

- 執行軌跡：AUTO-136-20261123-0038-database-lock-permissions
- 研究範圍：僅公開官方文件研究與 GitHub 研究紀錄；Notion / GAS / Cloud Run / Session 零寫入。
- 官方來源：Customize your Notion database settings｜Notion Help
- canonical URL：https://www.notion.com/help/customize-your-database
- 來源類型：Notion 官方 Help；查核日期 2026-11-23；發表日期未核實。
- 去重身分：canonical URL（移除語言鏡像與追蹤參數）；本輪檢查 main 研究目錄與清冊，尚未全歷史逐檔內容語義去重，故僅候選來源，**全域新增唯一來源正式認列 0**。
- 閱讀深度：取得公開頁面可讀段落並針對性部分閱讀 1 次；**不是全文完整深讀**，10/10 計數 0 次。

## 本輪讀到的官方敘述與範圍
1. Database settings 屬資料庫整體設定，不是每個 View 各自設定。
2. 修改 Database settings 需要 Can edit 或更高權限。
3. Lock database 啟用後，使用者仍能輸入資料，但不能改變 Views 或 Properties。
4. Edit properties 可建立、調整、複製或刪除屬性；設定選單亦含 Automations、Sub-items、Dependencies、Connections、Customize page layout 等功能。
5. 同主題補充交叉來源（不計新增）：https://www.notion.com/help/intro-to-databases 說明 Can edit content 可編輯資料列及欄位值，不能更改原資料庫 View、Properties、Filters、Sorts 或鎖定；但仍可建立 Linked database 並改其 View、Sort、Filter。鎖定是降低意外結構變更的防護，不是細粒度資料授權。

## 獨立反例假說（待實測，非本所已發現缺陷）
1. 鎖定原資料庫後誤以為不能新增或修改個案列，造成前台操作需求誤判。
2. 以 Lock database 取代敏感資料存取權限，未阻止已具資料編輯權限者改值。
3. 原資料庫被鎖，但有權者建立 Linked database 改其篩選，誤以為所有工作台畫面必然一致。
4. 以 View 隱藏敏感欄位當成列級／欄級安全隔離，實際仍可透過其他入口看到資料。
5. 把 Can edit content 當成 Can edit，導致維護者不能更改 Schema／View。
6. 全域 Database settings 修改被誤認只影響單一補助 View，影響其他方案的日常操作。
7. 未記錄誰能解除鎖定，將可切換的防誤觸設定當成不可變審計控制。
8. 未驗證不同角色在原始庫與 Linked View 的實際權限，僅用管理員畫面宣稱 PASS。

## 治療所設計含意（僅研究，不是改版指令）
對「補助方案用量」「心理師方案額度」「Sessions」等資料來源，未來應將原資料庫結構防誤觸、角色可編輯資料列、Linked View 呈現一致性及真正存取權限分別驗收；不得將鎖定／篩選／隱藏欄位混同權限控制。這些屬待核實設計風險，不代表現況有缺陷。

## 嚴格計量
- 候選來源 1；全域去重正式新增 0（未完成全歷史語義稽核）。
- 針對性部分閱讀 1；嚴格完整深讀 0；獨立完整複讀 0。
- 新反例假說 8；累積完成 10/10 暫採可核實保守基準 0／10,000。
- 不重複認列同 URL、不同語言鏡像、不同分析角度。
