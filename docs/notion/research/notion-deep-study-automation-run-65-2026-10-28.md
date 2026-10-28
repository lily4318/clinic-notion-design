# AUTO-65｜操作按鈕與返回路徑：重複提交、歷史狀態及可復原性（2026-10-28）

- 唯一執行軌跡：`AUTO-65-20261028-0844-RESEARCH`；自動研究；臺灣時間 2026-10-28 08:44。
- **授權範圍**：僅公開設計指南研究與 GitHub 研究紀錄；不得修改 Notion 正式/TEST 頁面、DB、Data Source、View、Formula、Relation、權限、業務資料或正式 GAS、Cloud Run、Session、部署；不得提前重新設計。
- **基準核對**：開始前讀取 main README、根 AGENTS、docs/system/source-of-truth、docs/notion/AGENTS、sources、decision-log、acceptance-status、research README、AUTO-64；列舉研究目錄76份 Markdown。sources 全文沒有兩個 canonical URL，GitHub code search 各零命中。嘗試全研究目錄逐檔全文核對時觸及工具呼叫上限，因此**未完成76份逐檔全文、同文不同網址與語義去重**；只列「新來源候選」。
- **閱讀等級**：兩篇官方完整主要正文（含HTML/Nunjucks文字示例、限制與近期變更），另讀各自獨立 change history；每篇一次針對治療所情境的反例分析。沒有原始圖片逐張核驗、真實互動、鍵盤/讀屏/手機/真人Notion測試，故**不是完整 R1**，更不是 R2–R10；change history 是同篇附屬頁，不計額外文章或閱讀遍數。

## AUTO65-S01｜Button — GOV.UK Design System

- 原文：https://design-system.service.gov.uk/components/button/；變更史：https://design-system.service.gov.uk/components/button/history/
- canonical identity：`govuk-design-system:components/button`；GOV.UK Design System team；原件於2018-06導入（據變更史）；本輪查得2026-07更新。閱讀標記：`AUTO65-S01-R1-MAIN-TEXT-C1`，**PARTIAL，不是完整深讀R1**。
- **實際閱讀**：目的、動詞式按鈕標籤、主/次要/開始/警告/禁用/反色按鈕、群組、HTML與Nunjucks、阻止重複點擊、JS與伺服端防護、變更史。官方強調單頁避免多個同級主操作；刪除等嚴重不可逆動作可採最後確認；禁用按鈕可能有對比與理解問題。其 `data-prevent-double-click` 只在啟用JS時有效，伺服端仍須防重複；慢速網路應先考慮處理中回饋。
- **反例A｜同一筆Billing被雙擊產生兩筆**：若將「確認收款」做成顯眼按鈕，使用者因載入慢或手抖重按，UI阻擋第二擊仍不等於Notion/GAS後端具冪等性。可能造成雙筆Billing或重複扣額；不能以按鈕樣式或前端停用宣稱防重複已通過。
- **反例B｜把未知狀態當成禁用按鈕**：若補助資格尚未核對，僅把「提交」灰化而不說明原因/待補證據，行政人員無法判斷下一步；但若直接啟用提交，也可能把未核准當已核准。需要區分輸入完成、資格核實、申報/收款狀態，不能用單一按鈕狀態替代業務規則。
- **反例C｜過度確認**：若每次修正普通Session備註都跳出破壞性確認，操作成本上升；若真正不可逆刪除卻無清楚後果和回復路徑則風險上升。需按不可逆性而非所有按鈕一律套用警告樣式。
- **可反證的未來驗證**：以隔離資料測雙擊、延遲回應、斷線重試、跨裝置同時提交及鍵盤觸發；檢查後端唯一鍵/冪等結果與錯誤回饋。**本輪未實測**，也不假設Notion原生按鈕可插入GOV.UK HTML/JS。

## AUTO65-S02｜Back link — GOV.UK Design System

- 原文：https://design-system.service.gov.uk/components/back-link/；變更史：https://design-system.service.gov.uk/components/back-link/history/
- canonical identity：`govuk-design-system:components/back-link`；GOV.UK Design System team；元件於2018-06導入（據變更史）；2025-12新增自動化可及性稽核警告說明。閱讀標記：`AUTO65-S02-R1-MAIN-TEXT-C1`，**PARTIAL，不是完整深讀R1**。
- **實際閱讀**：多頁交易中的返回、何時不使用、與breadcrumbs互斥、放在main前、保留前頁狀態、無JS退化、複雜行政流程應明確指出返回目標、HTML/Nunjucks、已知landmark稽核警告與變更史。官方說明自動檢查器警告不必然等於真實使用者障礙，仍需要實際研究。
- **反例A｜返回卻遺失期別篩選**：行政人員從「某個案＋某期Price Plan」進入Session後按返回，若回到未篩選的全量清單或預設最新期，可能錯將別期金額/用量當原核對目標。返回上一頁URL不保證保留篩選、排序、展開狀態與草稿。
- **反例B｜上一頁不一定是正確工作目標**：使用者從搜尋、通知、歷程或跨模組捷徑進入Billing，同一個「返回」可能回到不相干的上一頁；若返回鈕文字沒有目標，容易誤解。另一方面，將所有資料拆成逐頁交易又違反已確認的「同類資料同頁、開啟即見」需求。
- **可反證的未來驗證**：不同入口（個案/方案/通知/搜尋）、篩選/排序/頁籤/草稿、無JS/網路中斷、鍵盤與讀屏下返回的路徑及狀態恢復；**未在Notion或前台實測**，不能宣稱可直接套用GOV.UK元件。

## 交叉反例、嚴格計數與安全

1. 「按下操作」不等於「只提交一次」；「返回上一頁」不等於「回到原來的業務上下文」。視覺回饋不能代替後端冪等、方案期別一致性、歷史金額保全與權限驗證。
2. **本輪**：新來源候選2、主要正文文字閱讀2（各一次）、獨立反例分析2組（Button三情境、Back link兩情境）、完整R1 0、R2–R10 0、`FULL_DEEP_PASS_10_OF_10`新增0。**累積可核實完整10/10：0／10,000篇**。
3. **限制**：未全庫精確去重、未核對原始圖片及互動/鍵盤/讀屏/手機/真人UX/Notion角色權限/效能/Formula/收款真值；本輪無設計核准、無Notion或正式系統寫入。手動/自動兩路共享最新main，避免重複計數。
