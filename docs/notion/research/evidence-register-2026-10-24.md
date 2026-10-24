# Notion／UX／資料庫研究證據登錄表｜首批

> 登錄日期：2026-10-24。**16 筆唯一 URL**，其中 14 筆已成功取得網頁正文並核對與設計相關的段落，2 筆僅有搜尋摘錄（全文重新取得待辦）。**16 筆不等於 16 篇完整精讀**，更不等於已讀 10,000 篇。來源可更動，必須在採用前重新核對。

## 登錄定義

- **候選**：發現來源，但未去重。
- **去重唯一**：以 canonical URL（去查詢參數／標準化網域）建立唯一 ID；同文件不同語系版本只保留一種主要語系。
- **正文可取**：可取得網頁正文且查閱了與本專案相關的段落；**不表示逐頁、全文精讀**。
- **搜尋摘錄**：僅搜尋回傳摘錄、未成功取得正文；不能當作全文精讀或完全證實細節。
- **深入精讀**：需另外留下逐節摘要、反例、版本與測試適用性證據；本批**尚無符合深讀標準項目**。
- **採用**：本次已轉成可追溯的設計限制／研究建議，不表示 TEST 已實作。

## 來源（每個 ID 對應唯一 URL）

| ID | 來源 | 類別 | 文件／URL | 取證程度 | 對專案用途 |
|---|---|---|---|---|---|
| N01 | Notion | 效能 | [最佳化資料庫載入時間與效能](https://www.notion.com/zh-tw/help/optimize-database-load-times-and-performance) | 正文可取 | 計算鏈／表格數／屬性顯示 |
| N02 | Notion | View | [Views, filters, sorts & groups](https://www.notion.com/help/views-filters-and-sorts) | 正文可取 | View 自身篩選、排序與分組 |
| N03 | Notion | Linked View | [Linked views](https://www.notion.com/help/notion-academy/lesson/linked-views) | 搜尋摘錄 | 共用來源、獨立 View 設定；待完整回讀 |
| N04 | Notion | Relation | [Relations & rollups](https://www.notion.com/help/relations-and-rollups) | 正文可取 | 關聯雙向性、限一頁選項與匯總 |
| N05 | Notion | Formula | [Fix common formula errors](https://www.notion.com/help/common-formula-errors) | 正文可取 | 依賴深度 15 層、型別錯誤 |
| N06 | Notion | 權限 | [共享與權限設定](https://www.notion.com/zh-tw/help/sharing-and-permissions) | 正文可取 | 頁面層級存取僅 Business/Enterprise |
| N07 | Notion | 欄位權限 | [Manage database property access](https://www.notion.com/help/database-property-access) | 搜尋摘錄 | 欄位存取限制僅 Business/Enterprise；待正文回讀 |
| N08 | Notion | 圖表 | [Chart view databases](https://www.notion.com/help/charts) | 正文可取 | Free Plan 一張圖表、Dashboard 差異 |
| N09 | Notion | 模板 | [Database templates](https://www.notion.com/help/database-templates) | 正文可取 | 模板僅限來源資料庫、模板 Relation 不宜設共同預設 |
| N10 | Notion | 方案限制 | [Pricing plans](https://www.notion.com/pricing) | 正文可取 | Free Plan 與不同功能可用性 |
| N11 | Notion | 欄位模型 | [Database properties](https://www.notion.com/help/database-properties) | 正文可取 | Select／Status／Date／Formula 的用途 |
| U01 | Nielsen Norman Group | UX | [Progressive Disclosure](https://www.nngroup.com/articles/progressive-disclosure/) | 正文可取 | 首頁顯示常用，進階資訊可被找到 |
| U02 | Nielsen Norman Group | UX | [10 Usability Heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/) | 正文可取 | 狀態可見、辨識非記憶、避免錯誤 |
| U03 | Nielsen Norman Group | UX | [Information Scent](https://www.nngroup.com/articles/information-scent/) | 正文可取 | 導航名稱應預告目的地 |
| D01 | Microsoft Support | 正規化 | [Database design basics](https://support.microsoft.com/en-us/access/database-design-basics) | 正文可取 | 1NF/2NF/3NF、主鍵與屬性依賴 |
| D02 | IBM | 正規化 | [What is database normalization?](https://www.ibm.com/think/topics/database-normalization) | 正文可取 | 減少重複、更新異常與維護代價 |

## 本批計數（不與歷史未系統化搜尋相加）

| 指標 | 首批確認值 |
|---|---:|
| 已登錄候選 | 16 |
| 去重後唯一 | 16 |
| 正文可取且相關段落查核 | 14 |
| 僅搜尋摘錄 | 2 |
| 符合「逐篇深入精讀」可核實標準 | 0 |
| 模板實際複製／逐項評測 | 0 |
| 經用戶核可之重大 Schema／UX 修改 | 0 |

> 研究目標 10,000 篇是使用者訂立的長期目標，**尚未達成**；不能透過大量搜尋命中、頁面總數、範本庫列表充數。每次後續新增來源應附 ID、canonical URL、日期、來源版本、閱讀層級、逐節摘要與反例，嚴格去重。

## 待補證據

- N03 Linked Views、N07 Property Access 原文待再開啟核對。
- Notion 最新 Free 方案與 Dashboard 全域篩選限制須逐功能驗證；不能把 Dashboard View 功能外推一般 Linked Views。
- 尚無可核實的外部模板逐套分析與治療所真實使用者可用性研究。
