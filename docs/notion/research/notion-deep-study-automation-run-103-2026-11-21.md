# AUTO-103｜2026-11-21 10:38｜Notion 資料庫項目排序與權限界線（僅研究）

Trace: AUTO-103-20261121-1038-INTRO-DATABASE-INDEX-ACCESS-PARTIAL

## 前置與去重
- 已重新擷取 main：README.md (blob 51c750119a207e195b675f0613f43cbde9956d67)、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md (blob 4cb54a075ad9243054d899ec715ca2a68140dd80)、docs/notion/decision-log.md、docs/notion/acceptance-status.md，並核對研究目錄及 AUTO-102；本檔寫入前確認路徑不存在。
- 官方來源：[Intro to databases | Notion Help](https://www.notion.com/help/intro-to-databases)；canonical identity `notion-help:intro-to-databases`；在現有 sources.md 已出現，**既有來源，不計新篇**。同 URL 不因語言、段落或不同觀點增加唯一篇數。
- 閱讀事件：`AUTO103-R-20261121-1038-INTRO-DATABASE-MAIN-TEXT-107-310-PARTIAL`；本輪獨立重新開啟官方頁面，逐節查閱文字 L107–310：建立資料庫、inline/full-page、複製、資料庫項目、顯示/隱藏屬性、協作權限及鎖定。官方頁面共401行（含導覽與頁尾）。嵌入影片 L109–113 無法播放，圖片未逐張檢視、外鏈未完整展開，因此**僅文字部分複讀，非完整R1/R2**。官方頁面未標明首次發表日期，查核日2026-11-21。

## 官方文字事實（不等於本所已實測）
1. L122–146：資料庫每一項是頁面，資料來源可以用不同 view 呈現；同一 view 的篩選/排序/隱藏欄位是呈現設定。
2. L165–178：Duplicate with content 與 Duplicate without content 目的不同，複製不是原資料的即時同步證明。
3. L181–185：資料庫超過1,000項時，新頁可能因排序及索引顯示在中間，而非最後；不得以視覺最後一列作為完整性證據。
4. L242–258：Hide when empty / Always hide 是頁面屬性顯示規則，隱藏的屬性可在介面中再次展開；不等於清空資料或實施欄位權限。
5. L279–305：Can edit content 可以建立、修改、刪除資料庫內頁面及修改屬性值，卻不能更動來源資料庫的欄位、view、篩選排序或鎖定；仍可能在自行建立的 linked database 調整 view/filter/sort。Lock views 允許繼續編輯資料，且有編輯權者可解除鎖定。

## 六項反例／待驗假說
- CE01：超過1,000筆 Sessions 時以「最底列」認定最新會談，可能漏掉插入於中段的新頁；需依明確日期及唯一ID核對。
- CE02：Billing 某欄在頁面上被 Always hide，工作人員誤判沒有收費資料；隱藏不是空值也不是存取控制。
- CE03：將 Price Plans 複製成另一個有內容的資料庫後，兩套方案期別獨立變更，卻被誤認為同一權威來源。
- CE04：心理師有 Can edit content，無法改原始庫的 view，卻可在自己的 linked view 改篩選，不能把固定 view 當成不可變的業務核准條件。
- CE05：管理者啟用 Lock database 仍可變更 Session 屬性值；若當作禁止改價/禁止刪除的權限控制，會失效。
- CE06：把資料庫項目複製後誤認為同一 Session ID，導致重複請款或補助額度占用；需獨立核實原生複製後的 ID、關聯與計數，不能由官方複製說明推定實際發生。

## 計量、限制與安全邊界
- NEW_UNIQUE_SOURCE=0；EXISTING_SOURCE_INDEPENDENT_PARTIAL_TEXT_REREAD=1；COUNTEREXAMPLE=6；FULL_R1=0；FULL_R2_TO_R10=0；FULL_DEEP_PASS_10_OF_10_THIS_RUN=0。依最新已登錄嚴格基準，累積完成10/10仍為0／10,000篇；全歷史跨語系/同文異址語義去重尚未完成，不能聲稱已全量重新核定。
- 本輪僅公開官方文字研究與GitHub紀錄，無 Notion 實際登入、角色/權限、原生公式、交易、歷史金額、效能、手機或讀屏實測。上述反例是待驗推論，不是本所已發生問題，也不是改版核准。
- **NO NOTION/SYSTEM WRITE**：不得改 Notion 頁面、DB、View、Formula、Relation、權限、業務列、GAS、Cloud Run、Session 或部署。未達10,000×10且未獲使用者確認前，不進入重新設計；手動與自動研究維持並行。
