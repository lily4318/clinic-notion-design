# Notion 深度學習｜AUTO-44｜2026-10-27（研究，不是介面修改）

- 執行軌跡：`AUTO-44-20261027-1140-RESEARCH`；本輪為**既有來源的第二次針對性文字複讀**，不是新增URL、不是第二次完整深讀，也不是10次深讀達標。
- 範圍：僅閱讀公開Notion官方文件、核對GitHub研究清冊、記錄新的交叉反例；**沒有**寫入Notion Page、DB、View、Formula、Relation、權限、Session、GAS、Cloud Run或部署。
- 開始前讀取main：README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、decision-log.md、acceptance-status.md、research/README.md；逐份讀取研究目錄55/55份Markdown，查兩個URL與標題。確認兩篇均已在 `notion-deep-study-evidence-batch-02-2026-10-25.md` 登錄（DS-022、DS-023），其中Database properties亦見首批N11。故新增去重來源 **0**，避免將既有來源重新冒充新來源。
- 原文檢閱時間：2026-10-27（臺灣）；原始發布與最後修訂日期未從頁面可靠確認。網址語系差異視為同一canonical，不另計。
- 讀取層級：`TARGETED_REREAD_R2_TEXT_AND_CROSS_SOURCE_COUNTEREXAMPLE`；實際重新開啟原文、逐節核對文字；未逐張檢查所有圖片/嵌入影片、未操作Notion實際帳戶，故 `FULL_DEEP_PASS_10_OF_10=0`。

## AUTO44-R01｜Database settings（既有 DS-023；第二次針對性複讀）
- URL：https://www.notion.com/en-gb/help/customize-your-database
- Canonical：`notion-help:customize-your-database`；標題：Database settings；Notion Help官方。
- 本次重新閱讀：全文「Database settings」段落，確認設定對**整個資料庫**生效，而非只作用於個別View；進入設定需 `Can edit` 以上。核對 `Lock database` 允許輸入資料但禁止改View/Property、`Edit properties`、Automations、Sub-items/Dependencies、Sprints、Connections、`Customise page layout` 及 Tasks 切換等清單。
- 原文關鍵位置：正文段落「Database settings」及功能清單；公開原文沒有提供可直接推定治療所各角色實際權限的測試結果。
- 新的獨立反例（相對DS-023原登錄只說結構/權限）：若為了讓收費資料更易讀而修改 `Customise page layout`，可能改變同資料庫所有角色的頁面配置，並非只修正某個補助View；反過來，若只改一個View的欄位可見性，亦不能宣稱全庫資料或歷史帳務邏輯已修正。資料庫鎖不阻止內容編輯，故不能以鎖定當作防止歷史Session金額被改的控制。
- 跨文檔待核矛盾/邊界：此文說調整database settings需 `Can edit`；DS-022說conditional color可由 `Can edit content` 修改。兩者可能是「全庫設定」與「View層級色彩設定」不同權限路徑，**不可武斷宣稱互相矛盾或已測通過**。需待未來獲核准後在隔離環境用不同角色驗證，當下不得動Notion。

## AUTO44-R02｜Database properties（既有 N11／DS-022；本輪針對性複讀）
- URL：https://www.notion.com/help/database-properties
- Canonical：`notion-help:database-properties`；標題：Database properties；Notion Help官方。
- 本次重新閱讀：property types、建立/編輯、property visibility、日期輸入、每資料庫500個properties上限、conditional color適用View與欄位類型、權限、Property comments限制、People property permissions。
- 官方文字指出：Conditional color以**View為單位**設定，複製View會複製色彩規則；可按Formula/Relation/Rollup等條件著色。表格View可選整列或指定屬性；非表格View的色彩不等同於單一欄位著色。Property comments不支援Formula、Rollup、Button及unique ID，且一般欄位要先有值才可留言。
- 新的獨立反例（相對DS-022原登錄只說顏色與文字）：假如補助View把「待核對」標黃，另一個同資料來源View沒有相同色彩規則，跨角色或跨頁核對時可能產生「無色=已核准」的錯覺；複製View繼承色彩也可能保留不適合新期別的規則。色彩不可代替文字狀態、人工資格審查、歷史金額快照或權限。
- 第二個新反例：若設計者要求行政人員直接在「剩餘額Formula」欄位留言確認核定結果，官方明確限制Formula/Rollup不能使用property comment；不能將此設計假設當成可實作。必須另定業務審核紀錄方式（**僅研究假說，不授權新增欄位**）。
- 上限辨識：500是**單一資料庫**property上限；舊稽核「23個Data Source合計636欄」不能當作任一單庫超限證據。合併欄位或刪除欄位也需另經相依/歷史/權限審查，不得因研究自動清理。

## 交叉反例、適用性與停止條件
1. **全庫設定≠單一View呈現**：page layout/lock屬資料庫層，conditional color/欄位可見性偏View層；在補助/收費/Session跨頁查閱時不可混用驗收結論。
2. **視覺狀態≠業務核准**：顏色、已確認0、未知、待核對、不適用必須以清楚文字/原始資料區分；無色不是核准、篩選零筆不是不存在。
3. **權限文件≠實帳角色測試**：Can edit content與Can edit權限的細節、Locked DB對顏色配置的影響、免費方案可用性、行動裝置效果均未在本輪測試。
4. **功能存在≠本專案適用**：不得從原文可設定Color/Layout推導應立即改治療所Notion；本輪無任何實作核准。
5. **資料完整性**：歷史Session適用期別及金額須依原業務資料/時間判定，改顏色、鎖定或Layout均不會自動解決資料漂移。

## 嚴格計量與未完成
- 新增canonical來源：0（兩篇皆已登錄）；針對性獨立複讀：2篇，各本輪一次；本輪新增交叉反例分析：2篇。
- 完整原圖/影音/互動/真實Notion角色、手機、效能、原生Formula/歷史收費核定真值：**NOT_TESTED**。
- `FULL_DEEP_PASS_10_OF_10` 本輪新增0；截至本輪可核實累積仍 **0/10,000篇**；不把針對性R2計成完整R2，也不把多個反例計成多次閱讀。
- 研究結論狀態：`HOLD / RESEARCH ONLY`。未達10,000篇各10次且未經使用者確認，**不得進入Notion重新設計**。
