# 效能、權限與 Notion 免費版能力邊界

## 效能：先評量而不是先新增資料庫

Notion 官方 [效能建議](https://www.notion.com/zh-tw/help/optimize-database-load-times-and-performance) 指出高流量首頁同時顯示很多 inline database、過多可見屬性、Formula／Rollup 鏈與對複雜欄位排序／篩選可能拖慢使用感受。官方亦建議優先用簡單欄位篩選與減少不必要的可見屬性。

與治療所的對應測試：

1. TEST 首頁 **目前 6 個 linked database**，其中 3 個主表展開、另外3個收合（2026-10-24 vNext 實作紀錄；需重新 Fetch 驗證現況）。
2. 對每個 View 記錄可見欄位、篩選型別、排序欄位與是否使用深層 Formula／Rollup；**收合是否確實改善載入時間必須量測**，不可從版面推定。
3. 目前五個核心 Schema 歷史快照 251 欄，其中 70 Formula、53 Relation、38 Rollup；先畫關聯與計算依賴，不直接刪除。
4. 對可能造成 N+1 的 Notion 查詢設批次化方案，但此輪只研究 Notion；不改正式 GAS。

[Notion Formula 錯誤](https://www.notion.com/help/common-formula-errors) 說明 Formula／Rollup 參照有 15 層限制。這是**平台設計限制**，不能靠新增另一層 Rollup 解決。

## 權限：View 是資訊組織工具，不是存取控制

Notion 官方 [Sharing & Permissions](https://www.notion.com/zh-tw/help/sharing-and-permissions) 說明「資料庫頁面層級」存取權限定於 Business／Enterprise；[Property Access](https://www.notion.com/help/database-property-access) 的欄位級別權限也只在 Business／Enterprise（本批正文取回失敗，僅由搜尋摘要確認，正式採用前重新打開官方正文）。

**本專案以 Notion Free 為必要條件**，不能在同一個所有人都能進入的資料庫中僅靠不同 View 篩選、隱藏屬性就宣稱心理師 A 看不到心理師 B 的高敏感資料。須用既有真正能限制共享範圍的 Notion 頁面權限、資料最小揭露設計，或在未來正式後端進行 Staff/role/resource scope 審核（本輪沒有實作）。隱藏資料與授權是兩回事。

## Free 的圖表與模板限制

- [Notion Charts](https://www.notion.com/help/charts) 官方說 Free 可建立**一張圖表**；付費有較寬額度。不能把工作台方案建立在大量免費 Chart 上。
- 該文提到 Dashboard View 可具有 global filters；此一敘述**不能自動推論一般 Linked View 可以跨表全域同步篩選**，亦不能未核實相應方案資格就規劃為免費版必用功能。
- [Notion Pricing](https://www.notion.com/pricing) 需定期回查產品功能；頁面歷史與多人協作額度可能與方案類型有關。
- [Database Templates](https://www.notion.com/help/database-templates) 提醒：在模板預先填固定 Relation 可能使新建業務資料全部誤連到同一真實頁面。本專案新增模板應先隔離驗證。

## 先量測再聲稱達標

| 驗收 | 建議證據 | 目前狀態 |
|---|---|---|
| 首頁載入與檢視切換 | 同一帳號/設備前後計時與步驟記錄 | 未測 |
| Formula 深度與依賴 | 逐欄 Schema＋原生 Notion 公式實際求值 | 未完成 |
| 多期別清單正確 | 同案跨兩方案與跨年度真正隔離資料 | 未完成 |
| 權限隔離 | 角色帳號實際測試可見資料清單 | 未測 |
| 一張圖表是否可用 | 現行 Free workspace 權益確認與建立測試 | 未測 |

**本次僅更新 GitHub 的研究文件，不更改 Notion 內容、設定、權限或人員資料。**
