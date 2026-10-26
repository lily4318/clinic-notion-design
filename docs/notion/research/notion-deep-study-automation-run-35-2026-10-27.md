# Notion 深度學習｜AUTO-35（2026-10-27 02:41 Asia/Taipei）

- 執行軌跡：`AUTO-35-20261027-0241-RESEARCH`；來源：排程獨立研究；與聊天室手動研究並行。
- 本輪範圍：公開可讀 UX 研究、GitHub 研究證據及進度紀錄；**不得且未修改 Notion 頁面／資料庫／View／公式／權限／資料、GAS、Cloud Run、Session 或部署**；未進入重新設計。
- 開始讀取 main：根 README、AGENTS、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、decision-log.md、acceptance-status.md；另讀 AUTO-34 原始研究。以 sources.md 所連 **40 份研究清冊文件**分四組逐檔核對本輪兩個 canonical slug，40/40 成功，未命中；GitHub repo code search 兩個 slug 均為零命中。這是**已查清冊**去重，不冒稱已對全儲存庫所有未索引文件完成去重。
- 原文：2026-10-27 實際開啟 NN/g 原始網頁並閱讀主要文字章節、圖片說明與結論；原圖未逐張展開，不計 FULL_DEEP_PASS。

## AUTO35-S01｜Date-Input Form Fields: UX Design Guidelines

- 原始 URL：https://www.nngroup.com/articles/date-input/
- canonical ID：`nngroup:articles/date-input`；作者 Angie Li；原文日期 2017-01-22；本次獨立閱讀輪次 `R1_MAIN_BODY_PATTERNS_GUIDELINES_CONCLUSION`；首次反例 `C1`。
- 閱讀證據：`Date-Input Patterns`、`Date-Input Design Guidelines`、`Conclusion`。逐節讀取：日期接近當下時月曆選擇器較直覺；久遠日期以鍵入較省操作；手機長清單滾動可能很慢；年/月/日拆為多個下拉選單會增加互動成本；少量合法日期可用清單；應容許合理輸入格式、對不合理日期給明確錯誤；不應強迫重複填同一日期；範圍選取的月份位置需穩定；跨地區日月順序需消除歧義。上述是 NN/g 一般 UX 建議，**不是 Notion 原生日期欄位已驗證功能**。
- **反例 A：政府方案期別不是單純日期輸入**。即使日期輸入無歧義，若用「會談預約日期」自動判定補助資格或收費方案期別，仍可能與實際執行時間、核定效期、取消改期及人工資格核對衝突；輸入便利不等於業務核准正確。
- **反例 B：不能以日期輸入元件隱含民國／西元規則**。治療所可能同時見到民國年度 115、ISO 日期 2026-xx-xx 與跨年核定期，若標籤只寫「115/10/27」而不註明年制，容易誤判；但此為需測試的風險假說，**未查實現行 Notion 的格式與操作**。
- **反例 C：日期選擇器不能代替跨期審計**。禁止非法日期可減少輸入錯誤，但不保證舊會談金額被固定保存；即使日曆正確，關聯方案的歷史價格若動態改寫仍會污染舊帳，需另處理快照/規則。
- 限制：未逐張開啟示意圖片、未測 Notion 日期控件的手機/桌面/鍵入與時區行為；僅完成一次可核實正文研讀，不計完整深讀。

## AUTO35-S02｜Front-End Style-Guides: Definition, Requirements, Component Checklist

- 原始 URL：https://www.nngroup.com/articles/front-end-style-guides/
- canonical ID：`nngroup:articles/front-end-style-guides`；作者 Page Laubheimer；原文日期 2016-03-27；本次獨立閱讀輪次 `R1_MAIN_BODY_ALL_SECTIONS`；首次反例 `C1`。
- 閱讀證據：`What Is a Front-End Style Guide?`、`The UX Benefits`、`Are not Editorial or Branding Style Guides`、`Include Responsive Design Patterns`、`Checklist of 8 Main Requirements`、`25 Common UI Components`、`Conclusion`。主要發現：元件指南與抽象模式庫不同；指南應列元件適用時機、實作規格、正反範例、響應式規則，涵蓋表格、按鈕、標籤、狀態回饋、日期選擇等常見元件；**原文特別強調只納入產品真正有的元件，不是為湊清單而加新功能**。
- **反例 A：元件一致≠業務狀態相同**。所有方案額度卡片即使外觀一致，仍需區分「未確認」「已確認0」「不適用」與「資料未載入」；如果為統一視覺而只顯示同一個 0，會破壞補助核對語意。
- **反例 B：前端 style guide ≠ Notion 可自由自訂 CSS/互動**。原文以可控制程式碼的前端元件為例；Notion 原生 View、欄位、權限與響應式呈現受產品能力限制，不能從該文推論可任意設計元件或跨裝置行為。
- **反例 C：25 種元件不是 25 個模板、25 次閱讀或新增欄位要求**。為達研究篇數而把同篇清單拆算會違反來源去重；為了「完整設計系統」把不需要的進度條/切換鈕加入治療所日常頁，也違反使用者的簡潔、同頁直見及不得擴張範圍決定。
- 限制：未逐張展開示意圖片、未實際操作 Salesforce/Material 元件範例、未做 Notion 真實版面或角色測試。只計 R1 主要文字，不計 FULL_DEEP_PASS。

## 證據分級、去重與後續門檻

- 本輪 **已查清冊的新 canonical 候選 2 篇**；主要正文閱讀 R1 = 2 篇；每篇首次獨立反例 = 1 次，共 2 次；既有來源完整複讀 = 0 次；本輪 FULL_DEEP_PASS_10_OF_10 = 0 篇；依當期 main 可驗證清冊，累積 **0 / 10,000 篇**。
- 不把文章的多個設計準則、25 個元件、搜尋命中或不同分析角度冒充額外閱讀次數；尚未完成原始圖片/互動/真人 UX/效能/權限/Notion 公式值驗證。
- 尚待全儲存庫所有歷史文件之完整 canonical URL 機器去重；沒有可稽核 10/10 完成者，不可宣稱研究門檻達成。此研究僅形成將來可能檢驗的假說，不授權修改 Notion。
- GitHub 寫入及核驗以本輪後續逐檔實際結果為準；任何未通過 SHA/內容讀回的項目不得標記 PASS。
