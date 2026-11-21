# AUTO-101｜2026-11-21｜資料庫模板與重複建立之關聯污染風險（僅研究）

Trace: AUTO-101-20261121-0843-DATABASE-TEMPLATES-RESEARCH

## 官方來源、去重與閱讀事件
- [Database templates | Notion Help](https://www.notion.com/help/database-templates)；canonical identity: `notion-help:database-templates`；發布者 Notion Labs；查閱日期 2026-11-21；原始發布日期未核實。
- 2026-11-21 08:43（Asia/Taipei）公開 HTML 共 280 行，主文 L107–194 逐節閱讀一次：建立模板、預設屬性、Relation、使用模板、重複模板、巢狀限制、編輯/刪除與 FAQ。圖片、影片、外部連結、實機操作及完整多輪交叉查證未完成；記為 `PARTIAL_MAIN_TEXT_READ=1`，不是嚴格完整深讀 R1。
- 寫入前已重新擷取 main 七份核心文件；`docs/notion/sources.md` 精確 URL 不存在。僅記 `NEW_SOURCE_CANDIDATE=1`，**不宣稱完成全歷史語義/跨語系去重**，不計嚴格合格篇數。
- 本次獨立事件 `AUTO101-S01-20261121-0843-HTML-L107-194-PARTIAL`，與 AUTO-100 Database buttons 不同來源。

## 官方規則與反例（本所未實測）
1. L124–140：模板可預填屬性及頁面內容；Relation 預填會讓每個新頁關聯到相同舊頁。反例 CE1：把一位個案或某個 Price Plan 實例預填到 Session 模板，可能使不同新會談繼承錯誤對象/期別；模板方便不等於關聯正確。
2. L150–164：重複模板可每日、每週、每月、每年產生新頁。CE2：若重複產生「本週額度」或帳務頁但未與唯一業務鍵核對，可能形成重複待辦/雙重統計；頁面建立不等於真實會談或交易。
3. L165–171：每日重複模板不能巢狀模板；每個模板最多三層巢狀。CE3：把多層行政子資料庫放入每日模板可能超出產品限制，不能假設遞迴建立成功。
4. L181–189：模板只在建立它的資料庫中可用。CE4：新方案期別採另一資料庫後，不能假設舊模板自動跨庫共享或同步更新。
5. L135–140：模板可預設屬性值。CE5：預設「已核准」或特定收費期別可能被誤當本期人工資格確認；預設值不能代替核定與對帳。
6. L143–149：使用模板後仍可編輯內容。CE6：同名模板建立的頁面可被後續個別修改，不能只憑模板名稱推定所有既有 Session 欄位一致。

## 計量、界線與後續
- `NEW_SOURCE_CANDIDATE=1`; `PARTIAL_MAIN_TEXT_READ=1`; `COUNTEREXAMPLE=6`; `FULL_R1=0`; `FULL_R2_TO_R10=0`; `NEW_10_OF_10=0`。
- 依先前可核實驗收基準，完整10/10仍為 **0/10,000**；全歷史來源清冊、跨語言同文與十次獨立完整深讀仍待驗。
- 反例屬官方規則延伸的風險假設，不代表本所實際存在模板設定、資料錯誤或已通過原生驗收。
- **RESEARCH ONLY**：本次不修改任何 Notion 頁面、資料庫、View、Formula、Relation、權限或正式 GAS/Cloud Run/Session/部署；不進入重新設計。自動與手動研究雙軌維持獨立並行。
