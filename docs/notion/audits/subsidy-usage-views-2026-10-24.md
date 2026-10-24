# 2026-10-24｜政府補助使用額度 Views：Notion TEST 實作與驗收

## 使用者要求與偏離修正
使用者明確要求建立「看使用額度的 View」，此前追查 Billing 屬於工作方向偏離。本輪只修改 Notion TEST 工作台中的 View 及一行入口，不改收款、Price Plan 業務資料、Care Episodes／Sessions、Staff、Formula、Relation、Schema、權限或 GAS。青壯資格依使用者已確認流程人工核對，再於 Care Episodes 選正確核定方案實例；不得新增額外資格清單及黃色提醒。

## 原現況與改動
1. 原工作台 https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf 的 Price Plans 來源原有 View「01｜政府方案與核定期別」，可看核定總額度、已占用及剩餘，但沒有分開呈現原有「已完成、已預約、待確認」三類使用組成。
2. 在原 Price Plans linked database 中建立新 View「02｜政府補助使用額度（完成／預約／剩餘）」：https://www.notion.so/3f68ca66aa4d8156bccfcc28f75cbb9a?v=4038ca66aa4d81278430000cd581b5e7。View ID view://4038ca66-aa4d-8127-8430-000cd581b5e7。只選收費類型=補助 AND 服務類型=政府方案（不寫死青壯115）；依方案開始日排序，顯示名稱、方案識別、期間、核定總額度、已完成、已預約、待確認、已占用、剩餘及額度狀態。原01頁籤不動。
3. 在 TEST 工作台頁尾追加原 Care Episodes 的 inline linked View「個案使用額度｜依服務歷程／方案篩選（待核對）」：https://www.notion.so/3f68ca66aa4d81cca3b4ee43b4bd8dcf?v=4038ca66aa4d81a3ab1a000ca3244dce，view://4038ca66-aa4d-81a3-ab1a-000ca3244dce；新 inline DB URL：https://app.notion.com/p/4038ca66aa4d8163b08ac5efb0d8a427。Quick Filter 預選實際青壯115 Price Plan URL，日後可換方案；呈現歷程名稱、方案、狀態、個案方案上限、歷程已完成與已預約、他處是否確認、個案補助剩餘及狀態。資料層級是「服務歷程」，不宣稱已驗證同個案跨歷程總額度。
4. 原心理師週額度 View（青壯115專用）已含本週有效占用、他處使用顯示、週上限、額度狀態，不建立重複 View、不變更其2名在職臨床心理師的原篩選。URL：https://www.notion.so/c698ca66aa4d826baa8f8773b5c2cfe6?v=3f78ca66aa4d817581c9000c3420b577。
5. TEST 工作台「② 政府方案與核定期別」下新增一行快速入口，說明到原表第02 View、個案新 View、③心理師週額度。個案新資料表因 create_view 的 parent_page_id 行為追加在頁尾、原雙欄之外；未重排既有版面或增加黃色提醒。此版面位置需要真人 UX 驗收。

## 完成的唯讀讀回／驗收限制
- Price Plans 新 View Fetch、linked DB 同時列舊01與新02兩頁籤、saved-view query 均通過，回傳目前青壯115方案 1筆、has_more=false；必要展示欄位存在。
- Care Episodes 新 View Fetch、工作台 Fetch 的 linked DB／快速入口回查通過，預選青壯115篩選回傳22筆、has_more=false。
- Google Docs「青壯方案額度管理｜跨年度資料模型與 UX 規格 v3.4」已追加本次第十六節並在 revision guard 下回讀驗證：https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit。
- 未取得 Notion Formula／Rollup 原生數字，僅能看到 formulaResult／rollupResult 參照；因此 View 欄位及資料範圍通過 ≠ 真正已完成、已預約、已占用或剩餘的數值計算 PASS。外部未知≠0；跨歷程累計、跨方案／期別通用性、10/25週換週、角色權限、真人操作步數與頁面載入效能都仍未通過。
- 新建兩個 View 無原始資料、Schema、Formula、Relation、分享權限及業務資料寫入。00.config_notion 精確權威設定檔本回合未獨立定位，實作使用當次重新Fetch的工作台原 linked database 和直接取得的 Data Source Schema／Relation／View，不把 GitHub 當即時 schema。

## 回復與查驗
回復前重新讀最新工作台／View 並核對他人改動；只從 TEST 工作台精準刪除本輪新建的 Price Plans 第02頁籤、新 Care Episodes inline linked View 及那一行入口，不刪原始 DB 或原業務列。此連接器目前未提供 View 刪除工具，回復刪除需由有權限者在 Notion UI 精準執行。Google Docs／GitHub 的本輪新增段落可在保留並行更動前提下撤回。

使用者在 TEST 工作台②切換第02頁籤應看到核定／已完成／已預約／待確認／已占用／剩餘；點個案額度入口預設應看到22筆青壯115歷程；③維持原心理師週額度。
