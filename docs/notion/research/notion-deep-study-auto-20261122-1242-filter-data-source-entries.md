# AUTO-125｜2026-11-22 12:42 Asia/Taipei｜Filter data source entries（部分閱讀）
- Run ID: AUTO-125-filter-data-source-entries-20261122T1242+0800
- Canonical URL: https://developers.notion.com/reference/filter-data-source-entries
- Title: Filter data source entries — Notion Developers
- 來源：Notion 官方 API Reference；本輪讀取 2026-11-22，網頁正文可讀。
- 去重：docs/notion/sources.md 未見此精確 URL，GitHub 研究樹未見相同主題檔名；**全歷史語義去重未完成，僅候選，不計全域唯一新增篇數**。
- 閱讀深度：**部分針對性閱讀 1 次，非完整深讀**；本輪直接核讀官方網頁 110–590 行（涵蓋篩選總覽、date、formula、relation、rollup、status 等）；未核讀後續所有章節及所有外鏈。嚴格完整深讀 0 次，10/10 達標 0 篇。
- 前輪 AUTO-124 Query a data source 的分析不重複計為本輪深讀。

## 已核對的 API 契約
1. 查詢可傳 filter；未提供 filter 時返回未封存頁面並分頁；封存頁面須明確以 is_archived=true 查詢。
2. 日期比較提供毫秒精度（含時間字串）；未提供時區預設 UTC。單一 date filter 條件僅允許一個運算子，區間需以 and 組合兩個條件。
3. Relation contains 以關聯頁面的 ID 判斷，不是名稱；Rollup 陣列可用 any/every/none，日期與數值 rollup 使用各自的型別條件。
4. 公式篩選需依公式輸出型別（checkbox/date/number/string）選擇。
5. people contains me 對 internal connections 沒有關聯使用者，會返回空結果；不可拿來當心理師身分存取控制。

## 待驗反例（研究假說，非已確認系統缺陷）
1. Session 依收費方案名稱文字查詢，遇到同名跨期 Price Plan 時混算；應測 relation page ID。
2. 以 UTC 無時區日期查詢台灣本地週界，午夜附近服務錯歸週。
3. 用單一 date 條件放兩個比較運算子，收到 validation_error 卻當成零筆。
4. 漏查 archived=true，誤稱歷史 Session 已完整備份。
5. Rollup 的 any 與 every 混用，將部分符合誤判為全部符合。
6. 公式結果為 number 卻用 rich_text filter，錯誤後直接回報空集合。
7. internal integration 使用 people contains me 作心理師本人資料篩選，結果為空或權限判斷失準。
8. 將 API 篩選視為真正的資料列授權，忽略原始資料庫分享權限。
9. 只看分頁首批資料即宣稱本週方案用量完整，未驗證後續頁面。

## 後續驗證
需獨立完整閱讀本頁剩餘章節及外部依據；以離線合成資料測試日期邊界、關聯 ID、rollup any/every、archive 與分頁。不得直接改動真實 Notion 或任何正式系統。

## 本輪統計與安全
- 新來源：候選 1；已核實全域去重新增 0（待稽核）。
- 本輪獨立部分閱讀：1；嚴格完整深讀：0；新增待驗反例：9。
- 累積完整 10/10：沿用最近可核實基準 0/10,000，尚未完成全歷史稽核。
- 本輪只研究與 GitHub 記錄；Notion、GAS、Cloud Run、Session 均無寫入。
