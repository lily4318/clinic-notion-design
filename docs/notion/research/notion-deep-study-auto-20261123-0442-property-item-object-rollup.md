# AUTO-140｜Page property items：Rollup 計算狀態與分頁｜2026-11-23 04:42 +08

- 軌跡：AUTO-140-20261123T0442-PROPERTY-ITEM-OBJECT；研究專用，不修改 Notion 或正式系統。
- 官方來源：Notion Developers，Page property items，https://developers.notion.com/reference/property-item-object
- canonical 去重鍵：https://developers.notion.com/reference/property-item-object；與 Retrieve a page property item（https://developers.notion.com/reference/retrieve-a-page-property）為**不同官方文件**，但共享主題。已核對當期 research 目錄、初始證據清冊、來源規範及既有 AUTO-110/AUTO-126，未完成全部歷史內文與語義去重，故本次**不正式認列全域新增唯一篇數**。
- 閱讀取證：2026-11-23 取得官方正文249行；依次閱讀 L20–67（欄位/型別）、L163–202（分頁）、L203–243（Formula/Rollup）。本輪為**一次獨立針對性部分閱讀**，不是完整深讀，不把三段當三次。
- 版本限制：以2026-11-23可取得網頁為準；未實際呼叫治療所 API，也未核對治療所整合所用 Notion-Version。

## 官方契約與推論界線

1. 單筆 property_item 的 id 是**屬性 ID**，不是每個 item 的唯一 ID；Relation 的關聯頁 ID 位於 relation.id。欄位改名後 property ID 保持不變。
2. title、rich_text、people、relation 一律 list 回應，空集合為 results: []；files/multi_select 雖可含陣列，仍是單一 property_item，不可套用同一 list 分頁解析器。
3. 分頁 metadata 位於 property_item 下，next_url 不是頂層欄位；以 has_more/next_cursor 讀完。游標視為不透明字串。
4. Rollup show_original 的值在 results，不在 metadata 的空 array；sum 等計算在未到最後一頁前可能是 incomplete，最終才可能回傳 number/date。
5. 官方明示 show_unique、unique、median、count_per_group、percent_per_group 的 Rollup 端點計算可回 unsupported，並回傳底層 items；複雜依賴造成的 unsupported 亦不會因重試自動解決。**unsupported 不等於0、不等於空值，也不等於分頁尚未完成。**
6. Formula 為單一 typed result；依賴過多亦可能 unsupported。此研究只說明 API 契約，沒有驗證 Notion 畫面內公式顯示值。

## 八項反證情境（待驗假說）

1. 將 property_item.id 當作 Relation 目標頁 ID，造成多筆 Session 全被錯誤去重為同一筆。
2. 把 show_original 的 metadata.array=[] 當成無補助使用紀錄，漏掉 results 的實際值。
3. 只讀第一頁 sum=incomplete，就寫入補助剩餘額度0或未知的錯誤狀態。
4. unsupported 被當作「已確認0」，錯誤放行或拒絕方案用量。
5. unsupported 被無限重試，形成無效 API 負載；應分類為不支援並進行人工/替代驗證。
6. 將 files 的單一 property_item 誤當 paginated list，造成同意書附件漏讀。
7. 使用欄位名稱作唯一定位，改名後錯配「心理師方案額度」欄位；應先核對 schema ID。
8. 將 404/403 等取值失敗轉換為空集合，錯誤宣稱個案沒有關聯方案。

## 計量與下一步

- 本輪官方可讀來源1篇（是否全域唯一待稽核）、針對性部分閱讀1次、待驗反例8項、嚴格完整深讀0次、10/10新增0篇。
- 累積可核實10/10沿用保守基準0/10,000，**不是全歷史重新統計**。
- 後續需另輪完整逐節閱讀並與官方 page property values / pagination 交叉驗證；本輪不修改任何 Notion 頁面、DB、View、Formula、權限、GAS、Cloud Run、Session。
