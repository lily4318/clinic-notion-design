# AUTO-43｜2026-10-27 Notion 深度學習：固定導覽與左側垂直導航（僅研究）
Trace: `AUTO-43-20261027-1041-RESEARCH`。執行範圍：外部可讀研究＋GitHub研究清冊；**未授權且未執行任何Notion/正式系統寫入**。

## 前置規範、研究清冊與去重
- 重新 Fetch `main` 的 `README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md` 及 `docs/notion/research/README.md`。
- `docs/notion/research/` 當時有54份 Markdown，逐份取得文字並檢查 `sticky-headers`、`vertical-nav` 及標題關鍵字，54/54可讀、未命中；`sources.md` 未見兩個 canonical slug；GitHub code search 未作全庫唯一性的充分證據。
- 去重候選：`nngroup:articles/sticky-headers` 與 `nngroup:articles/vertical-nav`。URL去除追蹤參數；不同頁面各一篇，沒有把各項建議當成不同來源。**全儲存庫其他路徑、同文異址、未索引歷史材料的全域去重仍未完成**，故僅稱「已查清冊的新來源候選」。
- 曾檢視 `/articles/data-tables/` 與 `/articles/empty-state-interface-design/`，發現分別已有 AUTO-26/早期批次及 AUTO-27 登錄，**沒有重複計入新來源或完整複讀**。

## AUTO43-S01｜Sticky Headers: 5 Ways to Make Them Better
- URL: https://www.nngroup.com/articles/sticky-headers/
- Canonical ID: `nngroup:articles/sticky-headers`；作者 Page Laubheimer；發表 2021-04-04。
- 閱讀軌跡：`AUTO43-S01-R1-TEXT-C1`。取得文章可讀正文，閱讀定義、五項指引、結論與圖片說明文字；**僅主要正文一次閱讀＋首次獨立反例**，非完整深讀R1，原圖未逐張查驗。
- 原文逐節要點：①固定標頭占用內容高度，尤其手機需比較content-to-chrome與可點擊尺寸；②背景與主內容須足夠區隔，半透明容易造成辨識困難；③避免多餘移動與突然跳動；④部分固定標頭在向上捲動時可能錯判使用者意圖；⑤先判斷導覽、搜尋、工具是否需要隨時可見，再決定是否值得常駐。原文案例是一般網站/應用，**不是Notion原生元件功能證明**。
- 治療所情境：行政人員在同頁核對方案用量、心理師週額度與會談日期時，若為了「快速跳轉」增加常駐導覽，可能擠掉真正需要直接可見的表格欄位，特別是小螢幕。
- **反例 C1**：若同一頁的長表確實需要頻繁跨區返回，沒有任何可見定位入口也會造成大量捲動。不能因「固定標頭會占空間」便一律禁止導覽；應以實際工作步數、表格可見面積與誤操作率比較有無導覽。Notion原生是否能控制sticky行為/動畫尚未驗證，不得把CSS建議當成已可實作。
- 待反證：使用者完成「同頁查個案餘額→核對服務日→看心理師週額度」時，常駐入口是否降低總時間且不使關鍵欄位不可見？尚無真人、手機或效能資料。

## AUTO43-S02｜Left-Side Vertical Navigation on Desktop: Scalable, Responsive, and Easy to Scan
- URL: https://www.nngroup.com/articles/vertical-nav/
- Canonical ID: `nngroup:articles/vertical-nav`；作者 Page Laubheimer；發表 2021-05-16。
- 閱讀軌跡：`AUTO43-S02-R1-TEXT-C1`。取得可讀主要正文，閱讀 Benefits、Space tradeoff、四項 Guidelines、Summary及圖片說明文字；**僅主要正文一次閱讀＋首次獨立反例**，非完整深讀R1，原圖未逐張查驗。
- 原文逐節要點：垂直導覽可容納較具體的類別、便於成長及垂直掃視，也熟悉於桌面應用；代價是橫向內容空間、較小視窗及過長選單在首屏以下的發現性。四項建議：放左側且明顯、不要同時複製兩套導覽、不要僅用圖示藏標籤、長清單將低頻項目置後。文章中的網站注視比例不能直接套用本所Notion使用者。
- 治療所情境：行政頁可能有補助、收款、服務歷程、人員與活動等多類入口；若強行壓縮為「管理」等模糊大分類，找資料成本可能增加。原使用者要求「同類資料同頁、開啟即見」，不應把左側選單當作替代同頁直接顯示的理由。
- **反例 C1**：對於需並排查看多欄資料的治療所桌面頁，常駐寬側欄可能壓縮表格、增加橫向捲動；但完全隱藏導覽又可能讓新進人員找不到入口。對於不同職務/視窗尺寸，最佳入口組合可能不同；不能單憑左側導航的一般優勢決定Notion版面。
- 待反證：實測「找出當期方案／歷史Session／週額度」的尋找時間、誤入次數、表格可見欄數及新手/熟手差異；確認Notion現有sidebar/頁內導覽原生能力後再提設計，**本輪不改頁**。

## 跨來源反證與邊界
- 兩篇同時強調「可發現性」與「畫面空間」的取捨，**沒有**支持一律增加側欄或一律固定標頭。若導覽占用的可視面積使補助期別、日期與金額不能同時核對，增加入口反而可能惡化正確性。
- 一般UX文章提供設計假說，不是治療所真人測試、Notion官方支援能力、政府補助核定或歷史帳務正確性證據。
- 舊文已提及資料表與空狀態的來源，本輪只用於去重核查，不作新增來源或獨立完整複讀。
- 目前無圖片原圖逐張核對、無影片/互動實測、無Notion帳戶/手機/角色權限/公式真值/載入秒數驗收；任何建議均為HOLD，不等於核准重新設計。

## 計數（嚴格）
| 指標 | 本輪 |
|---|---:|
| 已查清冊新canonical候選 | 2 |
| 新候選主要正文R1文字閱讀 | 2 |
| 新候選首次獨立反例 | 2 |
| 舊來源完整複讀R2-R10 | 0 |
| FULL_DEEP_PASS_10_OF_10新增 | 0 |
| **累積可核實FULL_DEEP_PASS_10_OF_10** | **0／10,000篇** |

僅GitHub研究與進度紀錄；不修改Notion Page/DB/Data Source/View/Formula/Relation/權限/業務資料，亦不修改正式GAS/Cloud Run/Session/部署。未達門檻前不進入重新設計。手動與每小時研究雙軌仍可並行，任何GitHub共用檔寫入均需最新SHA條件更新及回讀核驗。
