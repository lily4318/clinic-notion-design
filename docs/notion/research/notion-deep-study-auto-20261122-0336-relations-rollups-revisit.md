# AUTO-116｜Relations & rollups 針對性複讀（2026-11-22 03:36 Asia/Taipei）

- 執行軌跡：AUTO-116-20261122-0336-relations-rollups；僅研究，不修改 Notion 或正式系統。
- 標題：Relations & rollups｜Notion Help
- URL：https://www.notion.com/help/relations-and-rollups
- Canonical identity：notion-help:relations-and-rollups
- 去重：已存在 docs/notion/sources.md（N04、AUTO14-S01/R1）；本輪新增唯一來源 **0**，不能重複認列。
- 閱讀證據：2026-11-22 針對性獨立文字複讀，官方網頁可讀，共422行；重點核對第127–330行（關聯建立、雙向與自關聯、Rollup、CSV匯出與複製）。這不是全篇10/10嚴格深讀，**合格完整深讀0次**；不可將既有R1或本次部分複讀升格。
- 累積完整10/10：沿用最近可核實下限 **0／10,000篇**，未執行全歷史逐筆稽核。

## 本輪核讀事實
1. 關聯預設單向，開啟雙向後兩端可相互更新；同庫自關聯單欄可雙向表現，分離Next/Previous須兩欄。
2. Relation可限制每筆最多1個關聯頁面，但不是跨不同資料列的複合唯一性約束。
3. Rollup的Count all、Count values、Count unique、Count empty、Count not empty語義不同；Sum限數字屬性，Earliest/Latest限日期。
4. Rollup不能再Rollup；CSV匯出Relation成URL純文字，重新匯入不能自動恢復關聯；複製資料庫可能將雙向關聯變為單向。

## 新增待驗反例（推論，非本所已確認缺陷）
1. 「個案×方案期別」分別建兩列且各列Relation限制1頁，仍可出現兩筆重複用量；需另行檢查複合鍵。
2. 週額度用Count all統計有值與空值混合的關聯頁，可能與實際有效Session計次不同。
3. 用Count unique對同個案不同有效Session聚合，可能錯將多次服務縮為一次。
4. 將缺失週回報的空值與數值0混同，Count values或Sum可能掩蓋未核實狀態。
5. 複製資料庫當成回復備份，原雙向關聯可能不再同步；需驗證反向連結。
6. CSV匯出再匯入後把URL字串視為Relation已恢復，造成跨方案用量漏計。
7. 自關聯單欄用作單向流程依賴，實際可能在反方向也呈現連結。
8. 嘗試Rollup-of-Rollup作多層補助額度計算，原生功能不支援，需另行設計資料來源。

## 邊界與後續
僅核對公開官方說明與GitHub研究索引；未查Notion真實Schema、個案資料或操作權限，沒有進行任何實際業務驗收。研究需繼續採逐URL、逐次完整閱讀及獨立反例稽核；本輪不計為10/10。
