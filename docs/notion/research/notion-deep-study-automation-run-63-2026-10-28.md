# AUTO-63｜Fieldset／Textarea：欄位群組與自由文字的可用性、證據邊界（2026-10-28）

- 唯一執行標記：`AUTO-63-20261028-0641-RESEARCH`；自動研究，臺灣時間 2026-10-28 06:41 起。
- **授權界線**：僅閱讀公開研究來源與寫入 GitHub 研究/進度紀錄。不得修改 Notion 正式/TEST 頁、資料庫、View、Formula、Relation、權限、業務列、正式 GAS、Cloud Run、Session 或部署；研究門檻未達，不開始 Notion 重新設計。
- 本輪開始前重新 Fetch main：README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md、docs/notion/research/README.md、AUTO-62。
- **去重過程**：最初檢查 GOV.UK Warning text 與 Notification banner，發現已分別登記於 AUTO-52、AUTO-51，排除、不計新來源或複讀；改選 Fieldset 與 Textarea。兩個 canonical URL 在最新 sources.md 全文均未命中；GitHub repo code search 以 fieldset、textarea 搜尋未命中。仍未完成所有歷史 research 檔逐檔全文與同文異址語義去重，故僅列「新來源候選」。
- 每篇本輪僅 **1 次主要正文文字閱讀及首次獨立反例分析**；不是完整 R1，不計 R2–R10。示例頁面只作同次閱讀輔助，不能再計篇數或複讀。

## S01｜Fieldset – GOV.UK Design System

- 官方原文：https://design-system.service.gov.uk/components/fieldset/
- 官方示例：https://design-system.service.gov.uk/components/fieldset/address-group/
- Canonical identity：`govuk-design-system:components/fieldset`；GOV.UK Design System team；首發日未核，頁面所列更新日期不等於首發。
- 閱讀軌跡：`AUTO63-S01-R1-MAIN-TEXT-C1`；覆蓋 When to use、How it works、fieldset/legend、grouping、address HTML、Nunjucks 宏參數、isPageHeading、aria-describedby、其他元件內建 fieldset、簡短 help text、範例頁文字。原圖/互動/鍵盤/讀屏未實測。
- 官方可核對重點：有多個彼此相關的輸入時使用 fieldset；`legend` 描述整組關係，應為 fieldset 第一個子元素；單題頁可使 legend 同時作頁面標題以避免讀屏重複；Radios/Checkboxes/Date input 元件範例可能已包含 fieldset，不能機械巢狀重複；`aria-describedby` 可連結輔助說明。這是 GOV.UK HTML 元件規則，**不是 Notion 已支援同樣語義的證據**。
- **反例 A｜視覺分組不等於資料歸屬**：把 Session 服務日期、收費方案、期別、Billing 收款日排在同一視覺群組，仍不能保證歷史金額採服務當日有效的方案期別，亦不保證跨資料庫 Relation 正確。畫面群組不能代替方案實例 ID 與歷史金額的資料一致性檢查。
- **反例 B｜過度分組造成操作負擔**：如果把每個補助相關欄位包成多層群組，使用者已確認的「同類資料同頁、開啟即見」可能變成長頁反覆捲動；對常用單欄位也套整組標題可能使視覺與讀屏資訊重複。相反地，完全不標明「個案資格」「心理師週回報」群組又可能混淆不同責任人。
- **可推翻條件**：日後需在真正 Notion 介面與角色下驗證視覺群組是否降低誤填、是否保留同頁可見、是否造成手機/鍵盤/讀屏負擔；未實測前僅是設計假說。
- **研究推論**：輸入群組可幫助理解，但「資料在同一區塊」不等於「資料間有已驗證的約束」；分組粒度須依實際任務，而非形式一致性。

## S02｜Textarea – GOV.UK Design System

- 官方原文：https://design-system.service.gov.uk/components/textarea/
- 官方示例：https://design-system.service.gov.uk/components/textarea/default/
- 官方錯誤示例：https://design-system.service.gov.uk/components/textarea/error/
- Canonical identity：`govuk-design-system:components/textarea`；GOV.UK Design System team；首發日未核；更新紀錄包含 2018-10、2019-01、2020-07、2023-04、2025-03，但非首發日。
- 閱讀軌跡：`AUTO63-S02-R1-MAIN-TEXT-C1`；覆蓋 When to use/not、開放式問題、label 與 placeholder、rows 與輸入預期長度、複製貼上、單題/多題標題、字數限制的條件、錯誤類型與明確錯誤文案、HTML/Nunjucks、變更紀錄、預設及錯誤示例頁。未在示例輸入或實測保存。
- 官方可核對重點：長於單行的答案才適用；開放式問題可能讓使用者難以作答，必要時拆成較簡單問題；必須有可見標籤而不能僅靠會消失的 placeholder；欄高宜符合預期輸入量；不應禁止複製貼上；字數限制須有理由；錯誤需指出空白、太長、太短、禁用字元等具體情況。
- **反例 A｜自由文字不能取代結構化狀態**：若用「行政備註」自由填寫「已收款」「待核資格」「已確認他處0」，公式與跨 Session/Billing 對帳不會自動得到可靠、互斥、可稽核的狀態；備註也可能含模糊時間與未確認資訊。自由文字應承載必要脈絡，不應冒充資格/金額/期別權威來源。
- **反例 B｜拆解開放問題也可能遺失重要敘事**：把每一則行政異常都強迫拆成選單、勾選或極短摘要，可能無法記下跨日協調、例外原因與補件脈絡；但放任無結構長文也可能難搜尋且誤混入敏感臨床內容。需分清業務狀態欄與最小必要的文字補充、權限與保留政策。
- **可推翻條件**：真實使用者完成日常記錄的時間、錯誤率、查找速度與敏感資訊最小化結果，可能支持不同欄位分工；需依實際 Notion/GAS 介面與權限測試，不可從 GOV.UK 的 textarea HTML 推論 Notion 的儲存、編輯歷史或隱私控制。
- **研究推論**：短而明確的欄位標籤與合理輸入大小能減少認知負擔；結構化業務事實與自由文字背景不可互相取代。

## 交叉反證、計數與未完成項目

1. Fieldset 解決「這些輸入彼此相關嗎？」；Textarea 解決「這個問題是否需要敘述？」。兩者都不能證明跨資料庫關聯、補助資格、歷史金額或實際收款已正確。
2. 既有已確認需求是同類資料同頁直接可見、行政操作精簡、未知/未核/已確認0不可混同。上述反例僅為研究推論，不構成任何新增欄位、重排、刪除或修改授權。
3. **本輪計數**：去重排除既有來源2篇（未重新完成獨立深讀）；新來源候選2篇；主要正文文字閱讀2篇各一次；首次獨立反例2組（共4情境）；完整R1 0、R2–R10 0、`FULL_DEEP_PASS_10_OF_10`本輪新增0，累積可核實仍0／10,000篇。
4. **NOT_TESTED**：原圖逐張、實際欄位輸入/貼上/提交、鍵盤、讀屏、手機、真人UX、Notion原生表單/欄位/角色權限、公式真值、歷史金額、補助資格、效能。未完成全研究目錄逐檔與同文異址精確去重。
5. **NO NOTION/SYSTEM WRITE**：本輪僅允許 GitHub 研究與進度記錄，不開始重新設計；自動排程與聊天手動續作可獨立並行，GitHub 共用檔採最新 blob SHA 條件更新，衝突不覆蓋。
