# AUTO-151｜Create a view：資料來源範圍、權限與呈現設定（研究，非實作）

- Trace: AUTO-151-20261123-1542-CREATE-VIEW-API
- 官方標題：Create a view — Notion Docs
- URL / canonical identity: https://developers.notion.com/reference/create-view
- 來源：Notion Developers；查核：2026-11-23；文件頁標示最新 Notion-Version 2026-03-11。
- 本輪讀取：搜尋工具回傳官方文件正文的端點、參數、錯誤與回應節錄；一次獨立針對性**部分閱讀**，非全文深讀。未讀完所有 configuration 子型別、例圖或互動實測。
- 去重：本輪查閱 docs/notion/sources.md 與最近 AUTO-150，未完成全庫所有研究檔全文/同文異址去重；因此僅候選來源，不正式認列新唯一來源，也不計完整 R1。

## 直接證據（官方文件）

1. POST /v1/views 建立 View；成功回傳 view object；需 connection 的 insert content 與 update content 能力。
2. 必填 data_source_id、name、type；type 列出 table、board、list、calendar、timeline、gallery、form、chart、map、dashboard。
3. database_id、view_id、create_database 三者必須**恰選一個**：前者建立於資料庫，第二者於 dashboard 加 widget，第三者建立 linked database block 並加 view。缺少或多選會 400。
4. filter 使用 data source query filter 形狀；sorts 最多 100；quick_filters 為使用者可操作的快捷篩選，與進階 filter 不同。
5. 404 可表示 database/view 不存在**或** connection 無存取權；400/429 亦可能為 request limits。
6. 文件支援 position 與 placement，但本輪未完整閱讀其所有子型別，不推定跨 View 的視覺順序。

## 反例分析（8 項待驗假說，非已確認缺陷）

1. 在錯誤 data_source_id 建立 View，混合不同方案期別資料。
2. 以 View filter 隱藏其他心理師 Session，誤當成真正資料權限隔離。
3. 同時提交 database_id 與 create_database，400 被誤當系統暫時失敗而盲目重送。
4. create_database 建立另一 linked block，與原同頁直顯工作流程重複，增加載入負擔。
5. quick_filters 由使用者切換後，截圖/匯出結果與固定 advanced filter 的查核口徑不同。
6. connection 無權存取回 404，誤以為原資料庫已刪。
7. 並行新增同名 View，造成多個外觀相同的日常入口。
8. 只看 view 建立 200 回應便宣稱權限、真實資料篩選、真人 UX 與載入速度均通過。

## 研究限制與計量

- 本輪官方可讀候選 URL 1；針對性部分閱讀 1；反例 8；嚴格全文深讀 0；正式認列新增唯一來源 0。
- 全歷史同 URL/語義去重及逐篇十次完整閱讀尚未完成；累積可核實完成 10/10 暫維持保守 0/10,000。
- 未對 Notion API 執行任何請求；無實際 View/權限/UX/效能驗收。
- 只允許 GitHub 研究文件，不修改 Notion 頁面、資料庫、View、公式、權限或 GAS/Cloud Run/Session，不進入重新設計。
