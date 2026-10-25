# Notion 深度學習｜AUTO-06 獨立研究：Calendar／Timeline／Gallery（2026-10-25）

> 執行軌跡 `AUTO-06-20261025-ASIA-TAIPEI`；僅研究公開來源與更新 GitHub，**不操作 Notion**。與聊天手動「繼續」並行；本批不共用其他 AUTO/MANUAL 研究檔。使用者要求的嚴格門檻是至少 10,000 篇唯一材料、每篇10次可稽核的完整深入閱讀；**尚未達成，禁止自行開始新版設計**。

## 1. 開始前查核與去重

- 先從 `main` 讀取根 `README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`，以及 2026-10-24 原始清冊、2026-10-25 批次02/03/04、MANUAL-01、AUTO-01～AUTO-05 原始研究證據。
- 去重標準：Notion help 文件的 canonical `/help/<slug>`（忽略語系、追蹤參數及尾斜線）；不同檢視類型的不同官方文章各計一篇，**不是**把一篇的章節或 FAQ 當多篇。與上述已登錄的 canonical URL/slug 對照，本批 `calendars`、`timelines`、`galleries` 均未見登錄；共**3篇新增來源**。未對全儲存庫全部歷史未索引文件做機器式全域去重，故此數字限「已知研究清冊」。
- 閱讀時間：2026-10-25（Asia/Taipei，本次排程）。透過 Web 直接開啟官方文章可取得的主要文字章節，逐節讀到 FAQ，非僅搜尋摘要。文章沒有可靠發表／最後更新日期，本紀錄的日期是**查閱日**，不是官方發表日。
- 本輪閱讀級別 `MAIN_TEXT_SECTIONS_READ + ANALYTICAL_PASS_1`，表示已讀該篇全部可取得的主要文字段落及FAQ，並完成一次不同假設／反例／修正推論；未逐張核對圖片、未觀看嵌入影片、未實測帳號/權限/跨裝置/效能，因此**不算嚴格 `FULL_DEEP_PASS`**。第2～10次獨立完整深讀：0。

## 2. 新來源及實際文字覆蓋

| 唯一ID | canonical URL／文章 | 逐節閱讀覆蓋與關鍵原文資訊 | 本輪級別 |
|---|---|---|---|
| AUTO06-01 | [Calendar view](https://www.notion.com/help/calendars) | Create / Add to existing DB / Weekly view / Month navigation / Move and stretch cards / Property visibility / Show calendar by date property / Start week on Monday / FAQs。官方頁正文約106–235行；需要 Date property，可切週或月，若多個 Date properties 可選擇顯示哪一個，拖動卡片到別日或拉長跨度，週起始日有偏好設定；FAQ指出行動版可看日、Timeline可呈現小時至年。 | `MAIN_TEXT_SECTIONS_READ + ANALYTICAL_PASS_1` |
| AUTO06-02 | [Timeline view](https://www.notion.com/help/timelines) | Create / Add existing DB / Adjust timeframe / Adjust project length / Today / Show-hide table / Load limit / Property visibility / Rearrange / Plot by different dates / Table calculations / FAQs。官方頁正文約106–298行；至少一個有日期範圍的欄位才有可畫資料；可從小時到年、拖曳邊界調整期間；可顯示左側表格及計算、選擇繪圖日期欄、調整Load limit。 | `MAIN_TEXT_SECTIONS_READ + ANALYTICAL_PASS_1` |
| AUTO06-03 | [Gallery view](https://www.notion.com/help/galleries) | Create / Add existing DB / Card preview / Fit image / Rearrange / Card size / Hide Name / Property visibility / FAQs。官方頁正文約106–224行；預覽可用 Page cover、Page content 的首個區塊或 Files & media；可裁切/完整顯示、拖曳卡片、調整卡片大小，甚至隱藏 Name。 | `MAIN_TEXT_SECTIONS_READ + ANALYTICAL_PASS_1` |

## 3. 三篇各一次獨立反例分析

### AUTO06-01｜Calendar view：日曆是日期視角，不是期限真值稽核

- **初始假設**：同一個資料庫有服務日、補助核定起日、付款日等日期時，切成日曆就能同時掌握所有重要期限，且在日曆上移動卡片只是調整畫面。
- **來源事實**：Calendar需Date property；`Show calendar by`一次選一個日期屬性；拖曳可將卡片移到另一天，拉伸可跨多天；週起始日與裝置/偏好相關。
- **反例**：一筆服務紀錄的「服務日期」落在本週、「核定期截止日」落在下月，若日曆正選服務日期，操作者可能完全看不到下月截止日期；**畫面沒有出現**不等於該筆業務資料不存在或沒有逾期。卡片拖曳看似整理排程，對Date property可能造成實質日期變動（此副作用須實機驗證，不能把推論當測試結果）。
- **修正理解**：單一日曆只是一個特定Date property的投影，不能替代多個期限欄位的業務檢核；顯示設定、可編輯行為與真正的核定期規則需分開。**沒有因此建立新日曆或更動日期欄**。
- **未驗證**：拖曳究竟更新哪個日期欄、含時區的日期跨日邊界、手機日視圖、實帳權限、提醒/通知送達。第2–10輪未執行。

### AUTO06-02｜Timeline view：可視化期間不等於核定期間正確

- **初始假設**：把核定期別和補助額度顯示為 Timeline，便能確保起迄日期正確、避免重複期間，且`Load limit`只限制視覺負載，不會造成誤判。
- **來源事實**：Timeline需有可用的日期範圍；時間尺度可從小時到年；可拖曳項目邊界、選擇不同Date property；左側可顯示表格並計算；`Load limit`是顯示頁數上限選項。
- **反例**：若某筆資料只有單一日期、缺少可用日期範圍，該筆可能不會被繪出；若使用者設定只載入10筆，就可能在時間軸上看不到第11筆。即使兩筆期間看似不重疊，核定期別歸屬、跨方案累計額度、資格與實際計次仍需獨立業務驗證。拖曳期間長度是可操作介面，**不應預設它是純視覺縮放**（實際寫回需測）。
- **修正理解**：`Plot eligibility`、`Load limit`、`Data truth`是不同層級；Timeline 的視覺缺席不是可稽核的零筆結論。可見表格的 Sum/Count 也只能針對當時資料與設定，不是跨方案申報驗證。
- **未驗證**：Load limit對表格計算的確切影響、公式產生日期是否可繪、權限與大表效能、拖曳更新行為、手機操作。第2–10輪未執行。

### AUTO06-03｜Gallery view：美觀卡片可能降低資料辨識度

- **初始假設**：把所有行政資料轉成漂亮卡片、隱藏名稱、用圖片預覽，即可讓工作台更直覺且不損失資訊。
- **來源事實**：Gallery有封面、首區塊內容、Files & media三種預覽來源；可設定Fit image、卡片尺寸、隱藏Name，並自訂可見屬性。
- **反例**：當兩筆不同服務/核定期使用同一張封面，隱藏Name後，操作者可能無法辨別是哪一筆；如果`Page content`的第一個區塊含不適合在列表上展示的文字或影像，對**本來就有該資料存取權**的人會增加畫面暴露（不是證明權限外洩）。縮圖裁切還可能讓「需核對」等重要文字被遮蔽。
- **修正理解**：視覺吸引力、辨識可靠性、最小必要顯示與權限保護是四個不同目標。Gallery適合以圖片為主的資料，不代表適合以跨欄比較與正確計次為主的行政判讀；不應以模板展示圖推斷實際可用性。
- **未驗證**：卡片排列拖曳是否影響其他檢視排序、可見性對不同角色的實際行為、圖片裁切與手機、真人任務完成率。第2–10輪未執行。

## 4. 跨來源反證：三種檢視不可互相替代

1. **Calendar × Timeline**：前者一次顯示選定Date欄位的月/週日期，後者以有日期範圍的資料畫期間；同一筆記錄在其中一種視圖看不到，可能是欄位選擇、日期範圍或載入限制，不可推論已刪除、無資格、零額度。
2. **Timeline × Gallery**：Timeline表格可選擇顯示欄位並計算，但Gallery的卡片視覺不等於適合進行跨筆數值比對；要判斷「額度是否正確」不能只看卡片排版或圖表。
3. **Gallery × Calendar**：預覽與日期拖曳都可能把原本「看起來只是美化」的操作變成資料識別或日期風險；研究者應分清顯示偏好、資料寫入與業務真值，不能把設計假設當實測。
4. **與既有AUTO-01 Board及AUTO-03 Feed的交叉理解**：各View對不同工作任務的支援不同；尤其拖曳動作的副作用、是否能看見全部相關記錄，必須由官方限制與未來隔離測試分別核對。**本輪不新增任何檢視**。

## 5. 嚴格進度與安全邊界

| 指標 | 本輪可核實 |
|---|---:|
| 與已知研究清冊去重的官方canonical URL | **3** |
| 讀過可取得全部主要文字章節及FAQ | **3** |
| 有獨立假設、反例與修正推論的首次分析 | **3** |
| 本輪第2～10次完整獨立深讀 | **0** |
| 累積符合每篇10次嚴格完整深讀的篇數／目標 | **0／10,000** |
| 模板實際複製、真實角色/手機/效能測試 | **0** |
| Notion Page/DB/View/Formula/Relation/權限/業務紀錄寫入 | **0** |
| GAS／Cloud Run／Session變更 | **0** |

**限制**：文章嵌入影片、圖片、互動功能、實帳驗證未完成，不能冒稱10次全文深讀；Notion文章的查閱時間不能當更新時間。這次只將可回查的研究原始證據寫入 GitHub，並用最新 main blob SHA 追加來源、決策、驗收索引；寫後重新Fetch驗證。雙軌寫入如有衝突必須重讀、去重並合併，不能覆蓋另一流程。整體目標仍未完成，**不得開始Notion設計或修改正式/TEST資料**。
