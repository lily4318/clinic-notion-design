# Notion 深度學習｜AUTO-34（2026-10-27 01:38 Asia/Taipei）

- trace：`AUTO-34-20261027-0138-RESEARCH`；工作流：每小時獨立研究，與手動研究並行。
- **權限界線**：僅閱讀公開文獻及更新 GitHub 研究證據；**未改 Notion** Page／DB／View／Formula／Relation／權限／業務資料，未改 GAS／Cloud Run／Session／部署。**尚未進入重新設計**。
- 開始先讀 main：`README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`；另讀研究目錄 README、首批 evidence-register、研究進度文件。
- 去重：讀取 main 研究目錄 **45份文件（45/45）**並查兩篇候選 canonical URL／slug；`sources.md` 的完整網址也未命中。舊「UX Strategies for Complex-Application Design」網址 `/articles/strategies-complex-application-design/` 與本輪 `/articles/complex-application-design/` **不同文章**，不合併；僅做已查清冊去重，尚未完成全儲存庫所有歷史檔案的全域機器去重。

## AUTO34-S01｜8 Design Guidelines for Complex Applications

- URL：https://www.nngroup.com/articles/complex-application-design/
- canonical ID：`nngroup:articles/complex-application-design`；作者 Kate Kaplan；發布 2020-11-08；2026-10-27 擷取全文主要正文。
- 證據：NN/g 網頁 `# What Is a Complex Application?`、`#1`–`#8`、`Conclusion`，逐段讀取。等級：`R1_MAIN_TEXT_ALL_8_SECTIONS+INDEPENDENT_COUNTEREXAMPLE`，**非完整深讀**。
- 逐節摘要：複雜應用常有非線性專業任務、多角色、巨大資料量及高風險決策；(1) 鼓勵安全的邊做邊學並即時回饋；(2) 在情境中提供效率捷徑而非只放長篇手冊；(3) 流程允許跳回及非線性前進；(4) 中斷後可找回判斷脈絡；(5) 跨工具的資料與工作交接要連貫；(6) 降低視覺雜訊但不剝奪能力；(7) 主要資料與補充脈絡可輕易切換；(8) 關鍵資訊應有可辨識層級，移除無意義圖示也能突出。
- **新反例 A（安全學習≠放任改真資料）**：若新進行政人員在正式補助期別上試按自動化或批次變更，「邊做邊學」可能直接更動真實金額或資格；安全的示範／可回復與真實授權必須分開，不能把 NN/g 原則誤讀為應允許在正式資料試錯。
- **新反例 B（漸進揭露≠藏起關鍵數值）**：把「待核對、已確認0、期別、剩餘用量」放到收合區可能使首頁漂亮，但在安排會談時造成跨頁回憶和錯誤決策；此案既有「同頁直接看見資料」決策優先。
- **新反例 C（保留脈絡≠新增必填備註）**：為記錄中斷原因新增每筆必填筆記會製造重複輸入；先辨認已有狀態、歷程和審計線索，必要性須真人驗證。
- 適用範圍：只作將來可驗證的研究假說；**沒有新增 Notion 欄位或工作流程**。
- 限制：原文圖片僅取得圖說，未逐張查原圖；Salesforce／ArcMap／TreeAge 等示例不是 Notion 原生功能證據；沒有登入操作或角色／速度測試。

## AUTO34-S02｜10 Usability Heuristics Applied to Complex Applications

- URL：https://www.nngroup.com/articles/usability-heuristics-complex-applications/
- canonical ID：`nngroup:articles/usability-heuristics-complex-applications`；作者 Kate Kaplan；發布 2021-08-15；2026-10-27 擷取全文主要正文。
- 證據：NN/g 網頁 `#1`–`#10` 與 `Conclusion`，逐節閱讀。等級：`R1_MAIN_TEXT_ALL_10_SECTIONS+INDEPENDENT_COUNTEREXAMPLE`，**非完整深讀**。
- 逐節摘要：(1) 系統進度及狀態需有回饋；(2) 以工作者真實語言表達；(3) 可取消、回復或返回；(4) 內外一致性；(5) 預防錯誤；(6) 可見線索優於記憶；(7) 專家快捷與新手路徑共存；(8) 以任務需要為限的極簡；(9) 錯誤提示能診斷及協助復原；(10) 依情境提供簡短協助。原文用 GIS、Power BI、ERP、Salesforce、Revit 等例說明，**不能直接推定 Notion 具備相同機制**。
- **新反例 A（系統狀態≠資格狀態）**：顯示「同步完成」「儲存成功」只能表示介面或資料寫入完成，不能表示補助資格、會談核定或跨期計數已由專業人員核實。
- **新反例 B（回復能力不得假定）**：原文舉的專業軟體可回溯專案版本，不代表 Notion 的批次編輯、關聯調整或權限變更可以原子性復原；不得把抽象 Undo 建議當成已驗收的功能。
- **新反例 C（快捷≠跳過核對）**：若將常見「本所使用0」做成一鍵快捷，在尚未查明其他機構使用狀態時會把未知誤記為已確認0。專家效率不能凌駕高風險資料語意。
- **新反例 D（最小化≠刪必要業務脈絡）**：為簡化表格移除期別、核對狀態、更新時間可能使相同剩餘額被誤認為同一核定範圍。需保留可見的必要判斷線索，而不是所有欄位一律越少越好。
- 適用範圍：研究證據，不形成對 Notion 改版的授權。
- 限制：原圖、示範短片及連結延伸閱讀未全部檢查；未實測 Notion／手機／不同角色／真實計算。

## 本輪反證結論及證據分級

- 兩篇均為**新候選 canonical URL**，各一次主要文字閱讀及一次獨立反例分析；即使同時談極簡與錯誤預防，**不是同篇重讀，也不把十個 heuristic 當成十次閱讀**。
- `NEW_CANONICAL_CANDIDATE=2`；`R1_MAIN_TEXT=2`；`FIRST_COUNTEREXAMPLE=2`；`TARGETED_REVISIT=0`；`FULL_DEEP_PASS_10_OF_10_NEW=0`；依最新已驗證清冊 `FULL_DEEP_PASS_10_OF_10_CUMULATIVE=0/10000`。
- 全域精確去重總數待查；圖片、互動、真人 UX、效能、角色權限、跨方案公式、原生回復均 NOT_TESTED。沒有把查到的模板目錄或圖說當完整深讀。
- GitHub 寫入需以最新 main / blob SHA 進行條件更新，寫後逐檔讀回；如果任何檔案未完成驗證，僅可回報其實際狀態。
