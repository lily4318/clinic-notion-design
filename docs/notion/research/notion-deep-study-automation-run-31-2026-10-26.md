# AUTO-31｜視覺層級與相似性原則：Notion 治療所行政系統研究證據
- 日期：2026-10-26（Asia/Taipei）；執行軌跡：`AUTO-31-20261026-2249-RESEARCH`
- 範圍：**只研究與更新 GitHub**。禁止寫入 Notion 正式/TEST 頁、資料庫、View、Formula、Relation、權限、業務資料，以及 GAS、Cloud Run、Session、部署；不得開始重新設計。
- 開始及寫入前讀取 main：README、根 AGENTS、system/source-of-truth、notion/AGENTS、sources、decision-log、acceptance-status；另核對 sources.md 所列 **37 份**研究清冊文件中的兩個候選 slug，37/37 可讀且未命中；GitHub code search 與 sources.md 也未命中。此為**已查清冊去重**，不冒稱全儲存庫所有未索引檔案的機器全域稽核。
- **去重教訓**：`/help/charts`、`/help/forms`、`/help/dashboards`、`/help/feeds` 雖在來源索引正文沒有完整列出，卻已在早期 research/ 清冊登錄，本輪排除，不算新增。語言版本、追蹤參數不得另算篇數。

## AUTO31-S01｜Visual Hierarchy in UX: Definition
- 原文：https://www.nngroup.com/articles/visual-hierarchy-ux-definition/
- 標題：Visual Hierarchy in UX: Definition；作者：Kelley Gordon；發布：2021-01-17；canonical：`nngroup:articles/visual-hierarchy-ux-definition`；閱讀標記：`AUTO-31-20261026-2249-RESEARCH:S01:R1`。
- 讀取範圍：頁面正文「Color and contrast」「Scale」「Grouping: Proximity and Common Regions」「The Squint Test」「Conclusion」及圖說文字；**主要文字章節 R1 一次**，未逐張開啟原圖、未實測畫面、非 FULL_DEEP。
- 來源觀察：層級由對比而非單純色相決定；過多同等醒目元素使主次不明；尺寸需有限層級；接近與共同區域可以顯示資訊歸屬；模糊/瞇眼測試可發現非預期的視覺主角。文章提醒色盲使用者不能只靠顏色。
- **本輪獨立反例分析 R1-CEX**：若把「治療所補助總額」做成最大字、把「個案資格未確認」縮小或藏在下方，畫面層級雖清楚卻強化錯誤業務判斷。若以大紅框包住所有待處理事項，真正跨期異常會被淹沒。即使同頁資訊齊全，群組間距過大也可能使使用者必須長距離捲動才能完成同一決策。
- **保留的反證/未證實假說**：視覺層級須按行政任務的重要性排序，而不是依金額大小排序；「同頁開啟即見」仍是先決條件。NN/g 的建議不是 Notion 原生能調整字級/對比/欄距的功能保證。尚未以治療所真實角色、手機、速度、可及性測試驗證。
- 原文位置：https://www.nngroup.com/articles/visual-hierarchy-ux-definition/ （正文各節及 Squint Test）；原文中所示示例圖片僅讀圖說，未完整視覺審核。

## AUTO31-S02｜Similarity Principle in Visual Design
- 原文：https://www.nngroup.com/articles/gestalt-similarity/
- 標題：Similarity Principle in Visual Design；作者：Aurora Harley；發布：2020-09-06；canonical：`nngroup:articles/gestalt-similarity`；閱讀標記：`AUTO-31-20261026-2249-RESEARCH:S02:R1`。
- 讀取範圍：頁面正文「Signify Relationships Using Shared Characteristics」「Color」「Shape」「Size」「Many Other Similar Traits」及圖說文字；**主要文字章節 R1 一次**，非逐圖/完整十次深讀。
- 來源觀察：同色、同形、同尺寸的介面元素會被視為同類；相同連結色應對應可點擊功能，不能混用於不可點的標題；同形的狀態標籤可能使差異不易察覺；若按鈕全部同色，主要操作不易辨識。相似性也可能跨距離造成錯誤群組。
- **本輪獨立反例分析 R1-CEX**：若「待核對」「已確認0」「不適用」三種狀態使用同一形狀與灰色底，心理師容易誤判為相同狀態；但把所有狀態都改成高飽和度不同顏色，可能反而使補助工作台過度花俏、破壞優先級。若「核定」和「查看」按鈕長得完全一樣，容易發生高風險操作；若用不同樣式太多，又會增加學習成本。
- **保留的反證/未證實假說**：相同語義應一致、不同風險操作應可區分，且不能僅靠顏色；不推論 Notion 支援細緻按鈕樣式或欄位標籤自訂。未執行真人辨識/誤按測試。
- 原文位置：https://www.nngroup.com/articles/gestalt-similarity/ （上述五個正文節及圖說）；原圖未逐一獨立檢視。

## 本輪去重、深度與未完成項目
| 指標 | 本輪 | 累積嚴格達標 |
|---|---:|---:|
| 新 canonical 候選（已查清冊） | 2 | 全域精確唯一總數待稽核 |
| 主要正文獨立 R1 閱讀 | 2 | 不作 10/10 加總 |
| 首次獨立反例分析 | 2 | 不作 10/10 加總 |
| 既有來源完整 R2–R10 | 0 | — |
| FULL_DEEP_PASS_10_OF_10 | 0 | **0／10,000 篇** |

- 讀取限制：可取得正文與圖片替代說明，但未逐張核對原始圖片、互動、影音，未使用真實 Notion 操作、角色/權限、效能或跨期補助公式；不把 R1 冒稱一次完整深讀。
- 下一次仍須依最新 main 清冊取不同 canonical 或獨立完整複讀；只有每篇十次**可稽核的完整**閱讀與反例均有證據，才計 FULL_DEEP_PASS。
- 研究假說**尚未經使用者核准設計**；不修改任何業務介面或正式系統。
