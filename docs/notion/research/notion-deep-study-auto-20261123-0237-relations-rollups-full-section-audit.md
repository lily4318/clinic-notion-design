# AUTO-138｜Relations & rollups 官方全文逐節研究（2026-11-23 02:37 Asia/Taipei）

- 研究軌跡：AUTO-138 / relations-rollups / 20261123-0237；只新增獨立文件，不修改共享清冊。
- 來源標題：Relations & rollups｜Notion Help
- canonical URL：https://www.notion.com/help/relations-and-rollups
- 去重身份：N04（2026-10-24 evidence-register 已有）；本輪新增唯一 URL = 0。
- 取證：2026-11-23，官方網頁完整可讀正文，已逐節閱讀說明、建立、雙向、自關聯、顯示、Rollup、FAQ；這是**本輪一次全文結構化閱讀**，不是10次獨立閱讀。歷史各次深讀身份未完成完整稽核，**暫不認列10/10**。
- 官方章節：relation creation（預設單向）、two-way、1 page / no limit、property visibility、related-page properties、self relation、rollup calculation、FAQ。影片未播放，不將影片計入正文閱讀。

## 逐節證據與限制
1. Relation 建立後可在欄位中選擇其他資料庫頁面；跨資料庫 relation 預設單向，雙向需要啟用對側欄位。自關聯單欄位並非完全單向。
2. 「1 page」限制的是該 Relation 可選頁面數量；**不能推論**資料庫有「個案ID＋方案期別ID」複合唯一鍵，也不能阻止另一筆資料重複建立。
3. Relation 顯示選項 Always show／Hide when empty／Always hide 與關聯頁屬性顯示，屬 UI 呈現，不是安全存取控制。
4. Rollup 的 Count all、Count values、Count unique values、Count empty、Count not empty 語意不同；未核對空值和重複關聯時，不可將其等同有效會談次數。
5. Rollup 數值運算 Sum、Average 等要求 Number；日期有 Earliest/Latest/Date range；Rollup 僅在輸出數值時可排序。官方 FAQ 明示不能 rollup a rollup。
6. CSV 匯出 Relation 成文字 URL，重新匯入不能恢復原有關聯；複製資料庫會將原雙向關聯變為單向。備份與回復不能只靠 CSV 或複製資料庫假定等價。

## 獨立反例推演（未在真實治療所驗證）
- R1：同一個案＋同一方案期別建立兩筆用量列；1-page Relation 仍允許兩筆不同列，破壞唯一性假設。
- R2：Sessions 的 Price Plan 與 Care Episode 的 Price Plan 不一致，從歷程 Rollup 取值會錯算期別。
- R3：取消或改期的 Session 仍有 Relation；Count all 大於實際有效服務次數。
- R4：重複關聯／空白欄位時 Count values、Count unique values 與 Count all 產生不同數字，不能互換。
- R5：跨年複製資料庫後雙向同步失效，管理員仍從舊側查看而漏掉新資料。
- R6：CSV 匯出再匯入後 Relation 只剩 URL 字串，公式和 Rollup 依賴中斷。
- R7：將欄位設為 Always hide 後誤當成限制心理師讀取敏感資料。
- R8：用 Rollup 再 Rollup 設計跨層額度，因官方不支援而失敗；需要重新評估依賴圖，**非本輪改動授權**。

## 可否證檢查（僅研究規格，未執行）
用完全合成資料建 2 個同案同方案用量列、取消/完成/空白 Session、錯期 Relation；逐項比較 Count all／Count values／Count unique、檢查複製和 CSV 還原後的 Relation 是否存在。必須在未來另行獲得設計/測試授權及真正隔離後才能執行。

## 計量與界線
本輪：既有來源全文結構化閱讀 1 次；新增唯一 URL 0；新增獨立反例 8；累積完成 10/10 仍採保守基準 0/10,000（全歷史未稽核）。本輪僅研究 GitHub 記錄，Notion/GAS/Cloud Run/Session 零寫入。
