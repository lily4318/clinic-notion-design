# 2026-10-24｜政府補助工作台 vNext 一次性改版｜完整設計與回復

狀態：Notion TEST 頁面及專用 Linked Views **已改版並讀回**；共用資料庫 Schema、公式、真實會談資料及正式系統均未更動。

## 問題與設計目標

原工作台把青壯115視為總頁面，年度參與資料只能從文字連結另開，Cases 舊專年計算表仍是主要個案區；Staff 篩選週回報 Relation 非空，可能漏掉未建立任何週報的心理師。新需求需容納多政府方案、多年度／核定期別，避免硬編碼115；使用者不希望逐次加零散提醒，且明確拒絕黃色 Callout。

## 一次完成的主頁架構

TEST 主頁：https://app.notion.com/p/3f68ca66aa4d81cca3b4ee43b4bd8dcf

1. **政府方案與核定期別**：Price Plans 專用檢視，方案個別核定期間及總額度。
2. **個案參與與期限**：一張新增的 linked database，依「個案 ID × Price Plan 方案實例 ID」追蹤資格、會談 Relation 與期限，包含三個頁籤。方案關聯可快篩。
3. **心理師週額度**：原 Staff linked View 留在首頁但標示為「現行青壯115專用」，沒有宣稱對新年度或其他方案適用。
4. **額度調整與歷史**：原本心理師週回報、額度調整、115年度 Cases 專用對照與驗收紀錄全都以收合方式保留。

首頁目前3張展開資料表，3張收合；6個 linked database（原5+新1）、原左側同步選單及驗收子頁均保留，不新增黃色提醒。

## 工作台專屬 View 設定與差異

| 原始 Data Source | View ID | 變更 |
|---|---|---|
| Price Plans `collection://8b98ca66-aa4d-83b6-a9b0-8758b5f31f63` | `view://3f68ca66-aa4d-81d6-a376-000ce4ea92a2` | 「政府方案與核定期別」，改用 收費類型=補助 AND 服務類型=政府方案；可快篩補助方案識別、啟用；按開始日降序。舊 View 只篩補助方案識別=青壯 |
| 補助參與 `collection://8546d9e1-2e10-471a-8b83-3eb235544471` | `view://4038ca66-aa4d-8169-b723-000c8a3dcfc8` | 01總覽，排除隔離驗證，方案 Relation quick filter |
| 同上 | `view://4038ca66-aa4d-81f4-aae8-000c080383a6` | 02資格待核對、不符合 |
| 同上 | `view://4038ca66-aa4d-8123-bb2c-000cef6c590c` | 03會談 Relation 空或期限屆滿日空 |
| Staff `collection://c698ca66-aa4d-826b-aa8f-8773b5c2cfe6` | `view://3f78ca66-aa4d-8175-81c9-000c3420b577` | 青壯115專用週額度；在職狀態=在職 AND 職稱=臨床心理師 AND 排除隔離心理師；舊 View 必須曾有「🎫 補助週額度紀錄」Relation |
| Cases 舊版 | `view://4028ca66-aa4d-819b-b90a-000cf16d1e36` | 保留原設定，收合當作115歷史備查 |

**重要**：Notion 的「年度補助方案」quick filter 只控制補助參與表，不與 Price Plans 或 Staff 自動同步。未來各方案需獨立計數、符合該核定期別的官方規則。青壯115專用 Staff Formula 不可被當成通用邏輯。

## 已完成唯讀驗收

| 檢視 | 筆數 |
|---|---:|
| 政府方案核定期別 | 1 |
| 個案參與總覽 | 22（待核對21、不符合1） |
| 資格待核／不符合 | 22 |
| 會談或期限資料待補 | 22 |
| 在職臨床心理師週額度 | 2 |
| 115舊版個案對照 | 22 |

上述查詢 has_more 均為 false。Notion 主頁 Fetch 有6個原始資料來源 linked database 區塊、側欄 synced reference 1個、原驗收子頁仍在、黃色警示不存在。

**沒有完成**：Notion 原生 Formula 精確數值；跨多政府方案與跨核定期別的週額度／期限規則；真實 Staff 零週報隔離測試；真人 UX 測試；效能測量；核定下一期規則；舊22筆會談 Relation／期限回填；10,000篇逐篇閱讀研究。不能認為自動核准已通過。

## 效能、安全與回復

主頁比原來多一張年度參與 linked database，但展開資料庫仍維持3張，其餘放在收合區；是否更快**未實測**。新 linked database 不會修改原來源或授與權限，Notion View 篩選不等於授權。原 Core Database／Formula／Relation、真實會談／收費／額度數字及其他10個行政舊模組均未更動。

修改前的 Notion 原生備份：https://app.notion.com/p/4038ca66aa4d816480bad8a54db6aeab
Google Docs 已同步第十四節與備份：https://docs.google.com/document/d/1TT0vtUrg3yJmcxBLyskftRzlHbBnfjnfXdJka0J269Q/edit

回復時先 Fetch 當時最新 Schema／View、檢查他人修改；比對備份布局，還原原5個 linked database 的位置與標題；Price Plans 恢復「補助方案識別=青壯」專用篩選，Staff 恢復「週回報 Relation 非空且排除隔離心理師」的舊 View；新年度參與 linked block 可從首頁移除，但**不得刪除原始補助參與資料來源或實際個案資料**。

其他十個既有行政模組沒有整體重構；若將來提出大改，仍須先給使用者效益／風險／回復比較並取得同意。

## 本輪已查閱的官方來源（不冒充10,000篇）

- https://www.notion.com/help/views-filters-and-sorts
- https://www.notion.com/help/notion-academy/lesson/linked-views
- https://www.notion.com/zh-tw/help/optimize-database-load-times-and-performance
- https://www.notion.com/zh-tw/help/relations-and-rollups
- https://www.notion.com/help/common-formula-errors

10,000篇研究目標尚未完成、沒有逐篇已讀的證據與去重清冊。


## 青壯人工核對後於服務歷程選方案｜2026-10-24｜覆蓋舊版青壯資格流程說明
本文件上方的「② 個案參與與期限／資格待核對」是**當次歷史版面快照**。使用者最新確認青壯直接「人工核對 → Care Episodes 💲收費方案選 Price Plan」，不需要額外資格核對清單。TEST 主頁已將原補助參與資料區塊收合為歷史與其他政府方案設計備查，且更名舊資格 View；原6個區塊、來源、歷史及週額度保留。以 [最新決策](audits/youth-manual-eligibility-episode-plan-2026-10-24.md) 及即時 Notion Fetch 為準。
