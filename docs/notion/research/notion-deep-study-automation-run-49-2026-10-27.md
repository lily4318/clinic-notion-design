# Notion 深度學習｜AUTO-49｜2026-10-27（僅研究；無 Notion 寫入）

- 唯一執行軌跡：`AUTO-49-20261027-1637-RESEARCH`；台灣時間 2026-10-27 16:37 起；自動研究軌，與聊天手動續作獨立。
- 本輪已重新取得 main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md 及 research/README.md、AUTO-48 記錄。當期 sources.md 研究檔案引用可抽出 57 個不同路徑；嘗試批次全文核查，但 GitHub 工具呼叫上限阻擋，**不能聲稱57份逐檔查完**。sources.md 中以下兩個完整 slug 未出現，GitHub repository code search 對 slug/標題亦無命中；全庫所有路徑、同文不同URL精確去重尚未完成，僅列**已查索引新來源候選**。
- 取證層級：兩篇 Nielsen Norman Group 公開文章的可讀主要正文各閱讀一次、各形成獨立反例及可反證條件；原始圖片逐張、影片、外連全文、Notion 真實工作區/角色/手機/效能/公式**未驗**，故兩篇均**不算完整 R1 深讀**，也無 R2–R10 完整閱讀。
- 計量：本輪新來源候選2、主要正文R1文字2、首次反例2、完整十次深讀達標新增0；累積嚴格 `FULL_DEEP_PASS_10_OF_10` **0／10,000篇**。

## AUTO49-S01｜Accordions Are Not Always the Answer for Complex Content on Desktops

- 原文：https://www.nngroup.com/articles/accordions-complex-content/
- canonical：`nngroup:articles/accordions-complex-content`；Hoa Loranger，Nielsen Norman Group，2014-05-18；本次讀取 2026-10-27。
- 獨立閱讀標記：`AUTO49-S01-R1-MAIN-TEXT-C1`；已讀 Summary、Major Usability Issues with Accordions、Myths about Scrolling and Long Content Pages on the Desktop、Criteria for Applying Accordions、Conclusion 及文中圖說/連結文字。
- 可核對論點：Accordion 雖能縮短視覺長度並以標題呈現資訊架構，卻增加逐項開啟的互動成本、降低隱藏資訊可發現性；若使用者需閱讀大多數內容，完整顯示並合理排版往往較佳。作者區分桌面與手機：小螢幕與只需少量片段時可能更適合摺疊，並提醒同時開多節及維持展開狀態的重要性。**這是一般網頁研究，不是 Notion 原生 toggle 行為保證。**
- **獨立反例 C1**：本所補助用量、心理師本週額度、歷史 Session/方案期別需要在同頁交叉核對；若為縮短頁面而把每個資料表預設摺疊，可能增加開合操作且遮蔽異常。反過來，若將只供偶爾查閱的說明或歷史稽核長文全部展開，又會壓縮即時業務資料可視範圍，不能僵化地「永不摺疊」。
- **反證條件**：需由不同職務在桌面/手機完成「找當期用量、查歷史收費、找異常」任務，比較完成率、錯誤率、展開次數、時間及可視欄位；若少量片段查詢明顯優於全展開，才可能支持局部摺疊。不得將一般網站的捲動結論直接套用 Notion。
- 限制：原始示例圖片及互動行為未逐張/逐步驗證，沒有測 Notion toggle 在不同裝置的狀態持久性；僅主要正文文字一次，非完整深讀。

## AUTO49-S02｜Visibility of System Status (Usability Heuristic #1)

- 原文：https://www.nngroup.com/articles/visibility-system-status/
- canonical：`nngroup:articles/visibility-system-status`；Aurora Harley，Nielsen Norman Group，2018-06-03；本次讀取 2026-10-27。
- 獨立閱讀標記：`AUTO49-S02-R1-MAIN-TEXT-C1`；已讀 Knowledge Is Power、Appropriate Feedback、Compel Users to Action、Communication Creates Trust、Conclusion，包含文字案例及圖說。
- 可核對論點：操作後需讓使用者知道系統是否收到、是否正在處理、結果如何；進度指示能減少因不確定而重複點擊。不是所有後台技術細節都應顯示，但對下一步決策有影響的狀態應清楚說明，尤其狀態變更不應悄悄消失。
- **獨立反例 C1**：在本所若「已點擊資料庫按鈕」「資料已儲存」「相關自動化已完成」「補助資格已人工核准」都以相同的綠色成功訊息呈現，行政人員可能誤認後續計算與資格核定已完成。相反，若每個 Relation/Formula/同步步驟都顯示大量技術狀態，也可能淹沒重要的「待核對」「跨期衝突」資訊。需將**操作回饋**、**資料一致性**、**業務資格**區分為不同語義，不可由畫面成功標記推論財務真值。
- **反證條件**：以隔離合成情境測試按鈕執行成功但下游自動化未完成、歷史期別不匹配、資格待核對；觀察人員是否能分辨狀態與下一步。若原生 Notion 無法表達某些回饋，不得虛構已實作，應先記為能力缺口。
- 限制：原圖、內嵌影片、下載海報及原始研究未逐項核驗；Notion 自動化、角色與計算實值未測，僅主要正文文字一次，非完整深讀。

## 跨篇研究界線與本輪安全

- 兩篇相互制衡：重要業務狀態需要可見，但不表示所有低頻資訊都應展開；摺疊與回饋應依真實任務區分，**不構成 Notion 版面或公式修改授權**。
- 未修改 Notion 正式/TEST 頁面、資料庫、View、Formula、Relation、權限、個案/財務列，也未修改正式 GAS、Cloud Run、Session 或部署。只允許 GitHub 研究及進度紀錄。
- 10,000篇×10次完整獨立深讀未達成，待全部達成並取得使用者確認前不得進入 Notion 重新設計。自動排程與手動續作維持獨立並行。
