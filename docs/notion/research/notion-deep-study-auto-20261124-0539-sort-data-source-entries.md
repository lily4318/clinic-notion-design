# AUTO-165｜Sort data source entries｜獨立部分閱讀（2026-11-24 05:39 Asia/Taipei）

- Trace: AUTO-165-20261124-0539-SORT-DS-PARTIAL
- 官方來源：https://developers.notion.com/reference/sort-data-source-entries
- 標題：Sort data source entries；canonical identity: notion-api:sort-data-source-entries；language: English
- 取得方式：2026-11-24 官網正文可讀，約164行；實際閱讀正文 L109–157，含排序優先順序、範例及 property/timestamp sort 欄位。不是全站、所有連結或相關 SDK 原始碼完整深讀。
- 去重：研究目錄未見同名 sort-data-source 檔；歷史所有研究正文及跨語系語義去重未完成。候選新來源1，不正式計入唯一來源。
- 閱讀事件：AUTO-165-R1-20261124-0539-L109-157-TARGETED-PARTIAL。僅一次獨立部分閱讀；FULL_R1=0，FULL_R2_TO_R10=0。

## 官方契約與推論界線

1. Data Source Query 接受 sorts 陣列；第一項排序優先，其後只在前項相同時進一步排序。
2. 可按欄位名稱排序，direction 僅 ascending/descending；也可依 created_time 或 last_edited_time 時間戳排序。
3. 官方範例為 Food group 降序、Name 升序。文件未承諾相同排序鍵下穩定排序，也未承諾跨多頁查詢在並行更新下有快照一致性；此為**未保證**而非已證實會出錯。

## 反例與待驗風險（8）

1. 僅以「日期」排序，日期相同的 Session 在分頁邊界可能缺乏可證明的穩定順序；需核實是否可加入可用且唯一的次排序鍵。
2. 以 last_edited_time 進行增量同步，讀取期間其他人編輯可能使資料跨頁位移；不能假定快照一致。
3. 把第一個排序鍵當成次要排序，造成跨期 Price Plan 顯示先後不符預期。
4. 以名稱作排序與唯一識別，誤把同名但不同期別的方案合併。
5. 排序後只讀第一頁，漏掉後續 Session，造成補助用量低估。
6. 把 UI View 的排序當成 API Query 的實際排序，不查 Query payload 就宣稱一致。
7. 日期空值或相同值時依顯示順序推論先後，不另核對業務日期及有效狀態。
8. 把排序成功當成 Relation、Formula、Rollup 或角色權限完整性驗收通過。

## 計量與限制

- 本輪官方可讀候選來源：1；正式新唯一來源：0（歷史跨檔去重未完成）。
- 獨立針對性部分閱讀：1；新待驗反例：8；嚴格完整深讀：0；累積可核實 10/10：0/10,000。
- 僅研究 API 文件，未查治療所實際 Schema、未做 API 實測，以上反例均未驗證為實際缺陷。
- 範圍：RESEARCH ONLY；不修改 Notion、View、Schema、公式、權限、GAS、Cloud Run 或 Session。研究門檻未達，不進入重新設計。
