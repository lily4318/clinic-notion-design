# 資料庫設計研究｜如何應用於治療所 Notion

## 理論／官方依據

- Microsoft 的 [Database design basics](https://support.microsoft.com/en-us/access/database-design-basics) 以 1NF／2NF／3NF 解釋「避免重複群組、屬性應依賴正確的識別鍵、避免與其他非鍵屬性混在一起」。
- IBM 的 [Database normalization](https://www.ibm.com/think/topics/database-normalization) 闡述如何降低資料重複及更新異常。
- Notion [Relation／Rollup](https://www.notion.com/help/relations-and-rollups) 說明可連結不同資料來源的頁面，但 Notion Relation 的 UI 設置與正式 SQL PK／FK／UNIQUE **不等同**；需要額外稽核重複與斷鏈。
- Notion [Database templates](https://www.notion.com/help/database-templates) 說明模板在特定資料庫內使用，不宜讓每份模板預設連到同一個實際業務頁面。

## 不把年度做成不同欄位／資料庫

**反例（本專案不採用作通用模型）**：Cases 同時有「青壯115次數」「青壯116次數」「其他政府方案116次數」欄位；每增期別就要改 Formula、View、權限與資料搬遷。

**比較建議（已確認基本方向，仍待通用計算驗收）**：

- `Cases`：個案身份的永久主資料，不依年度重建。
- `Price Plans`：特定核定政府方案的**獨立期別／額度池實例**，記核定有效期間與適用規則；用 Notion Page ID 判別，不只用可更改的年度名稱。
- `補助參與紀錄`：一個「個案 ID ＋ Price Plan 實例 ID」候選唯一鍵；同年多政府方案與跨年記錄互不混算；Notion 本身未核實有複合唯一索引，必須定期檢查重複。
- `Sessions`：依**實際會談本身**相關 Price Plan 和已核實的狀態、日期候選計次；不得用 Care Episode 的收費方案推定全部 Sessions 都屬同一方案。
- `Care Episodes`：真實臨床歷程，補助到期不等於臨床歷程結束。
- `Staff`／心理師週回報／額度調整：按方案實例、當期規則所定義的週次或核定期別追溯；不假定所有方案都有青壯週限額。

**未確認／不適用／確認0／待人工核對**必須分辨；不要把空欄默認為0或有資格。若未核實跨期共用規則，不得混算。

## 風險：過度正規化與過度 Rollup

正規化原則是依功能依賴設計實體，**不是每個欄位都要新建一張 Notion Database**。多層 Relation → Rollup → Formula 可能造成更複雜的計算與維護。新增核心表的批准條件：發現真正跨期混算／更新異常、既有欄位確實無法表達、能列明依賴、能隔離測試、能備份復原，且使用者同意。

## 已有歷史架構快照（非即時 Schema）

2026-10-24 的前次讀取：Cases 49欄／Sessions 67欄／Staff 55欄／Price Plans 30欄／Care Episodes 50欄，合計 251 欄、70 Formula、53 Relation、38 Rollup（來源：docs/notion/decision-log.md）。**不得把這些視為現在仍精確的值**；下一次改資料庫前重新 Fetch Data Source、型別、雙向 Relation 與頁面存續。

## 問題 → 檢查 → 變更等級

| 風險 | 必須核對的事實 | 允許行動 |
|---|---|---|
| 同案同年度兩補助混算 | 個案×方案實例實際關聯、主管機關有無共用規則 | 唯讀稽核；大改先核准 |
| Session／Episode 方案不同 | 會談 Price Plan、歷程方案及收費／申報依據 | 待核對，不可自動重寫 |
| 一人兩份同方案期別參與 | Notion Page IDs、相同候選複合鍵 | 檢測重複，不能直接刪資料 |
| 計數 Formula 錯誤 | 實際 Notion Formula 真值、取消／改期／逾期狀態 | 隔離 TEST、Formula 修改須先核准 |
| 期間超出／首談未知 | 官方該期規則、首次實際服務日、時間型別 | 未確認不放行 |
