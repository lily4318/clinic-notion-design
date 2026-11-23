# AUTO-152｜Retrieve a view：檢視設定讀回與權限邊界（僅研究）

- Trace: AUTO-152-20261123-1640-RETRIEVE-VIEW
- 官方標題：Retrieve a view — Notion Docs
- 原始／canonical URL：https://developers.notion.com/reference/retrieve-a-view
- 來源：Notion Developers；取證日期：2026-11-23；文件顯示最新 Notion-Version 2026-03-11
- 閱讀範圍：取得官方頁面正文約683行；針對端點、回應、錯誤、能力要求、View物件種類進行**一次獨立針對性部分閱讀**，非完整深讀，不認列10次之一
- 去重：已對照 sources.md 與 AUTO-151（Create a view，非同URL）；未完成全歷史研究清冊與異址同文去重，因此僅列候選，不認列新增唯一來源
- 正式累積10/10：沿用保守0／10,000；本輪完整深讀0、候選1、部分閱讀1

## 可核實技術事實

1. GET /v1/views/{view_id} 以View ID取得View物件，與建立View的POST操作不同；取得View設定不等於查詢所有Session資料列。
2. 官方明示需read content capability；404可能是View不存在，也可能是connection無權存取，不能當成View已刪除的充分證據。
3. View物件有parent、type等欄位；列舉類型包含table、board、list、calendar、timeline、gallery、form、chart、map、dashboard。只核對type不能證實篩選、資料列完整性、使用者畫面或權限隔離。
4. 文件列出429與多種5xx回應；錯誤不得轉換成空資料或已確認用量0。

## 待驗反例（研究假說，非已確認系統缺陷）

1. 取得View物件成功，卻將其當成Session列已全部查完。
2. 404直接判定View已刪除，忽略Integration分享權限。
3. View ID與Database/Data Source ID混用，造成錯誤查詢。
4. 僅核對View type=table就誤判補助篩選與欄位配置正確。
5. 複製Linked View後未核對parent，誤用跨方案資料來源。
6. 429/503當作無資料，讓本週補助用量錯誤顯示0。
7. API讀回設定正確，卻宣稱真人UX與載入效能已驗收。
8. 把View可見範圍誤當成個案資料的角色存取控制。

## 證據與限制

官方來源：https://developers.notion.com/reference/retrieve-a-view
先核對README、根與Notion AGENTS、source-of-truth、sources、decision-log、acceptance-status及最近AUTO-151。尚未逐一掃描全歷史研究清冊，因此無法證明唯一性或完成輪次；不將本次部分閱讀計入完整深讀。未使用Notion真實個案、未讀寫任何Notion頁面、Schema、View、公式或正式GAS/Cloud Run/Session。本文件只記研究增量，不構成重新設計授權。
