# AUTO-105｜2026-11-21 12:44｜Relations & rollups：跨方案關聯與聚合失效反例（僅研究）

Trace: AUTO-105-20261121-1244-RELATION-ROLLUP-TARGETED-REREAD

## 前置與來源去重
- 研究前讀取 main 的 README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md；查閱當期研究檔案樹與 AUTO-104。研究前 main tree SHA/commit: ce217e6a5b68ce6d621c7e5aff887f457a31fc8b。
- 來源：Notion Help, **Relations & rollups**；canonical URL: https://www.notion.com/help/relations-and-rollups
- 去重 ID：notion-help:relations-and-rollups；sources.md 已包含同一 canonical URL，故本輪新增唯一來源 **0**。
- 取得方式：2026-11-21 當次公開官方頁面正文；已獨立核讀文字 L107–330（關聯建立、雙向/自關聯、限制一頁、顯示、rollup 聚合、CSV/複製 FAQ）。頁面影片 L109–113 未播放、圖示未逐張解析；因此僅記「獨立針對性文字複讀 1」，**完整深讀 0**，不冒稱10次。
- 內容證據：L170–193 雙向關聯及1頁上限；L223–241 自關聯方向；L242–305 rollup 與 Count all/values/unique/empty、數字/日期聚合；L319–330 CSV 關聯無法直接重匯入、複製DB雙向變單向、不可rollup另一rollup。

## 本輪獨立反例分析（待測假設，非本所已確認缺陷）
1. **Session → Price Plan 選錯期別**：Relation 可選其他資料庫頁面，但不是業務上的期別唯一鍵。若只以方案名稱辨識，可能將跨年 Session 連到舊期；需要以方案實例 ID 和有效期人工/規則核對。
2. **關聯一頁限制不足以證明正確**：設定 `1 page` 只能限制選取數量，無法驗證所選的 Price Plan 是否為正確核定期；也不能保證同案同方案只有一筆用量。
3. **Count all 與 Count values 混用**：若補助會談的可計次狀態欄空白，Count all 可能包含尚未核實的關聯列，Count values 則可能排除；均不能直接替代「已完成且符合補助條件」的計數。
4. **Count unique values 不能替代 Session 唯一性**：多個 Session 共用同一個狀態或日期值時，按屬性 unique 計數會低估實際會談；須以穩定 Session ID 去重，且先套業務狀態條件。
5. **複製資料庫使雙向關聯失效**：官方說明複製資料庫後原雙向同步轉單向；若複製「補助方案用量」作年度備份卻誤當正式來源，反向歷程顯示可能與預期不同。
6. **CSV 匯出/匯入無法還原關聯**：官方說明 CSV relation 以文字 URL 匯出且不能直接重匯入恢復關聯；因此 CSV 備份不可被宣稱為可完整回復 Price Plan／Sessions／Care Episode 的關聯拓樸。
7. **Rollup of rollup 不支援**：若試圖以「Session → 用量 rollup → 心理師額度 rollup」直接串兩層，會遇到功能限制；應先驗證可行的原生公式/來源路徑，不能宣稱現有配置已測過。
8. **自關聯單欄具有對稱性**：若用單一 self-relation 表示「下一期」，A 指向 B 時 B 也可能顯示 A；官方建議方向需獨立時用雙欄，否則可能誤判新舊期方向。

## 計量與邊界
- 本輪新增唯一來源 0；既有來源文字針對性獨立複讀 1；新反例 8；完整可稽核深讀 0；新增完成10/10篇數 0。
- 最近可核實累積完成10/10基準仍為 0/10,000；未進行全歷史語義去重及全量清冊重新驗算，故此數字不是新全量審計。
- 未觀看頁面影片，未檢查全部圖像及延伸連結，未執行 Notion 原生測試；不得把研究推論當成實際缺陷或權限/公式驗收 PASS。
- 本輪只建立獨立 GitHub 研究證據，不修改 Notion、GAS、Cloud Run、Session、部署及其他流程檔案。
