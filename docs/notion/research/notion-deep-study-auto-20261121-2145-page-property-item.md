# AUTO-110｜Retrieve a page property item｜2026-11-21 21:45 Asia/Taipei

- 執行軌跡：AUTO-110-20261121T2145-PAGE-PROPERTY-ITEM；GitHub研究專用；起始/寫前 main commit de5536d701e3b17226a4c8a21988b97286ed235f。
- 官方來源：Notion Developers，[Retrieve a page property item](https://developers.notion.com/reference/retrieve-a-page-property)。
- canonical去重鍵：https://developers.notion.com/reference/retrieve-a-page-property（去除 query/fragment）。本輪核對 sources.md、research/README.md、首批 evidence-register 及當期研究目錄；未見相同精確 URL，但未逐份完成歷史研究內文語義去重，故僅候選1篇、不正式計入全域唯一篇數。
- 閱讀證據：2026-11-21 網頁正文可讀，共731行；核讀 L108–135、L210–325、L327–380、L575–643，包含端點、回應、分頁屬性、Rollup、權限與參數。此為獨立針對性文字部分閱讀1次，**不是全文完整深讀**；圖片、相關子文件與實際 API 呼叫未覆核。
- 嚴格完整閱讀：本輪 R1=0、R2–R10=0、10/10完成=0；最近可核實累積基準仍為0/10,000（尚未全歷史重算）。

## 原文事實與應用
1. GET /v1/pages/{page_id}/properties/{property_id} 可取得單一屬性；property_id 可由頁面或 data source 查得，URL 編碼 ID 須照 API 回傳使用。
2. status、select、files、multi_select 等多為單一 property_item；title、rich_text、people、relation 則可能是分頁 list，需逐頁讀至 has_more=false。
3. Rollup 會附帶計算 metadata；文件要求讀完全部分頁後才使用計算結果。
4. 403 可能是缺 read content capability；404 可能是頁面/屬性不存在或沒有頁面存取權。錯誤不可當作空值。
5. 文件列示 start_cursor、page_size 及 Notion-Version（文件顯示 2026-03-11），但未驗證治療所實際 API 版本。

## 六項反例（待驗假說，非治療所已確認缺陷）
1. 只讀頁面摘要中截斷的 Relation，就把 Session 次數當作全量：應使用屬性端點讀到 has_more=false。
2. Relation 只取得第一頁即算剩餘補助額度：應檢查跨頁重複、漏筆與方案期別。
3. Rollup 第一頁的中間計算值被當作最終核准值：應完整遍歷後驗證計算狀態。
4. 403 被轉成「本週無心理師回報」：應標記授權錯誤，不得填入已確認0。
5. 404 被轉成「個案沒有方案」：應區分 ID 失效、無權限與真實空關聯。
6. 把單一 property_item 和 paginated list 用同一解析器：應依 object/type 分支並檢驗 next_cursor。

## 範圍、限制與後續
- 本輪新候選來源1、針對性部分閱讀1、反例6、嚴格完整深讀0；未完成十次獨立全篇閱讀或全歷史語義去重。
- 僅 GitHub 研究記錄；不操作 Notion 頁面、資料庫、View、Formula、權限、GAS、Cloud Run、Session 或正式部署。
- 後續須讀取官方 linked property item object / pagination / rollup response 規範，進行不同日期、獨立全篇閱讀及證據比對，不能把本次多個角度當作多次閱讀。
