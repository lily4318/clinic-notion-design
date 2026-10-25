# Notion 深度學習｜AUTO-13｜2026-10-26｜Formula syntax／Intro to formulas／Properties guide

- 執行軌跡：AUTO-13-20261026-0436-Asia-Taipei；獨立排程批次；僅公開文獻研究與GitHub紀錄。
- 研究基準：本次重新讀取 main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md，並比對首批16筆、第二～四批、十面向研究、MANUAL-01、AUTO-01～12；官方同篇語系變體合併，搜尋結果/索引不算已讀。讀取日 2026-10-26 Asia/Taipei。
- 本批候選3篇，三篇canonical URL均未見於上述已登錄研究來源；本文為本批來源唯一性與閱讀軌跡的補充證據。來源頁無可核實的最近修訂日，記為「未核實」，不得以查閱日當作更新日。
- 閱讀級別：三篇官方頁已實際開啟並核對可取得的文字主節、函數清單或案例，分別完成首次反例分析；尚未逐張檢查所有圖片、外連示範/模板或實際操作，故均標記 `TEXT_MAIN_SECTIONS_READ + ANALYSIS_PASS_1`，**不列 FULL_DEEP_PASS，亦不列 10/10**。

## AUTO13-S01｜Formula syntax & functions
- canonical URL：https://www.notion.com/help/formula-syntax
- 標題：Formula syntax & functions；來源/作者：Notion Help／Notion；去重ID：notion-help:formula-syntax；R1：AUTO-13-20261026-0436。
- 實際查閱：Properties（Title/Text/Select/Multi-select/Checkbox/Date/Number/Relation/Rollup對應類型）；Built-ins（布林、比較、條件）；Functions（if/ifs/empty、數字/日期、列表filter/map/some/every/unique、let/lets、id、format等）。原文是函數參考表，並非治療所額度規則。
- 官方明示的關鍵語義：`empty(0)`為`true`；`empty([])`也為`true`；Relation是page list、Rollup結果型別依配置而變；`unique()`僅對列表值去重，`find()`找不到回Empty、`findIndex()`找不到回-1；`dateBetween()`取日期差，`parseDate()`依ISO 8601解析。
- 待反駁假設：「用`empty(已使用次數)`判斷未知資料，不會誤判已確認0；Relation的`unique()`即可保證每個案每核定期只計一次」。
- 具體反例：核定使用次數已確認為0時，`empty(0)`仍成立；若以此視為未填，便把已確認0誤判未知。反之，重複關聯頁的`unique()`不會自動判斷不同Sessions是否同次會談、取消或跨期計次，也不會實施複合業務唯一約束。
- 修正結論：日後公式檢驗必須分開「未確認、已確認0、不適用」；列表去重、關聯計數、核定規則三者不同。這是文獻推論，尚未驗證實際治療所原生Formula，不提出任何公式改寫。
- 待核：函數示例的UI/型別與現行工作區實際執行一致性、時區邊界、Null/空列表/0真值、依賴深度及資料量；未實測。

## AUTO13-S02｜Intro to formulas
- canonical URL：https://www.notion.com/help/formulas
- 標題：Intro to formulas；來源：Notion Help；去重ID：notion-help:formulas；R1：AUTO-13-20261026-0436。
- 實際查閱：三組案例（到期提醒、RICE優先度/投票、父子任務狀態自動化）；公式適用位置（資料庫屬性、一般按鈕、資料庫按鈕、自動化）；新增/編輯/即時預覽；Notion AI產生公式與限制。
- 官方明示：編輯器可在單筆資料預覽計算結果；Notion AI編輯公式目前在Business/Enterprise方案；AI不支援迭代式for loop、random()或記住前次提示。官方父子任務例子使用`Parent item.first()`與`.every()`判斷。
- 待反駁假設：「在某筆測試資料上公式預覽正確，足以證明所有方案/期別的額度計算正確；AI能產生公式等於可自動批准補助」。
- 具體反例：單筆預覽只有一個當下Relation/Status配置，無法涵蓋空值、已確認0、跨年度核定期、取消/改期與同一個案多歷程。父任務自動標完成的例子是任務狀態邏輯，不能轉用為政府補助核定；AI產生的式子仍可能漏掉特殊規則。
- 修正結論：公式編輯器預覽是開發輔助，非跨期業務真值驗收；未來需要多分支測試、權威規則對照與真人核准。研究階段不執行Notion AI、不改任何公式。
- 待核：現行方案AI權益、資料庫自動化觸發時序、真實原生Formula值、UI示例圖與嵌入模板。

## AUTO13-S03｜Database properties help organize your team’s information
- canonical URL：https://www.notion.com/help/guides/database-properties-help-organize-your-teams-information
- 標題：Database properties help organize your team’s information；來源：Notion官方指南；去重ID：notion-guide:database-properties-help-organize-your-teams-information；R1：AUTO-13-20261026-0436。
- 實際查閱：基本欄位Name/Select/Multi-select/Person/Date；File/Text/Checkbox/URL/Email/Phone；Relation/Rollup/Created time/by/Last edited time/by/Formula；依View顯示或隱藏欄位。原文特別提醒：2022年3月資料庫重新設計，文中操作步驟或圖片可能過時。
- 待反駁假設：「將核對欄位設為Checkbox並在View隱藏已勾選資料，就代表核定完成、其他人無法看見且資料已清除；Last edited可代表誰核准」。
- 具體反例：Checkbox只有布林勾選，無法表達未知/不適用/已確認0/核准者/依據；View隱藏是可見性調整，非刪除與權限；Last edited可能因無關文字更改而更新，不能替代正式核定者與核定時間的證據。
- 修正結論：欄位語義與可見性必須分開；簡化畫面不應混淆資料狀態、權限與核定證據。2022以前UI示例僅作概念參考，操作前須重查現行官方規格。此處不提出實際新增欄位或改版。
- 待核：圖片/可展開互動示例未逐一操作；當前免費版權限與實際治療所欄位現況未測。

## 去重、計量與不可跨越界線
- 新來源：3篇（AUTO13-S01～S03）；舊來源/重複語系不另計。三篇各有1次文字主要章節閱讀及獨立反例，**不等於1次嚴格完整深讀PASS**；本批嚴格FULL_DEEP_PASS=0，累積可稽核每篇10/10完整深讀達標仍0／10,000。
- 未取得或未完整檢查圖片、互動示例、外部模板；無真實Free/Business權限、臨床資料、公式結果、效能、手機或使用者操作測試。只研究公開來源與GitHub紀錄。
- 未修改Notion正式或TEST Page/Database/Data Source/View/Formula/Relation/Permission/任何資料列；未修改GAS、Cloud Run、Session或部署；未進入重新設計。
