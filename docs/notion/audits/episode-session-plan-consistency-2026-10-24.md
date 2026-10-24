# 2026-10-24｜服務歷程與會談方案對照：唯讀驗證

**工作線**：Notion TEST／唯讀資料驗證。**使用者前一回合已確認現有測試資料符合實際使用情境**；青壯資格人工確認後，直接於 Care Episodes「💲收費方案」選 Price Plan 的操作決策不變。本文件只驗證最新 Notion 結構與會談資料**關聯一致性**；不含病歷、姓名、會談頁 URL 或財務明細。

## 當次來源（2026-10-24）

- Care Episodes：`collection://6b68ca66-aa4d-8274-a691-07c605c5fb54`，原管理 ALL View `view://4bc8ca66-aa4d-82ec-894b-88a840ae6242`。
- Sessions：`collection://c2a8ca66-aa4d-82d2-bd6a-8772bb463796`，原管理 ALL View `view://1f08ca66-aa4d-83d1-a201-8864c13aa5de`。
- Price Plans：`collection://8b98ca66-aa4d-83b6-a9b0-8758b5f31f63`，政府方案工作台 View `view://3f68ca66-aa4d-81d6-a376-000ce4ea92a2`。
- 原生 [Notion TEST 設計與驗收紀錄](https://app.notion.com/p/4028ca66aa4d81298984ffd18b590a1d) 已追加本回合回歸測試結果，讀回恰一節。
- 在來源 Schema 讀回確認 Care Episodes `💲收費方案`、Sessions `💲 收費方案` → Price Plans；Sessions `👣 服務歷程` → Care Episodes，Care Episodes `💬 關聯會談` → Sessions。額度與計數皆已有 Formula／Rollup 依賴。

## View 唯讀查核與逐筆關聯彙總

用 Notion **既有** saved Views 分頁查詢：Care Episodes 57筆（1頁，has_more=false）、Sessions 295筆（3頁，最後 has_more=false）、政府啟用方案 1筆。沒有新增或修改 View，沒有依「青壯」「115」對共用業務規則硬編碼，只按當時啟用 Price Plan 實例辨識。

| 項目 | 讀回結果 | 判定 |
|---|---:|---|
| Care Episodes 有主收費方案 Relation | 57／57 | **PASS：關聯欄位存在** |
| Sessions 有服務歷程 Relation 且能對應現存 Episode | 295／295 | **PASS：關聯完整** |
| Sessions 有主收費方案 Relation | 295／295 | **PASS：非空** |
| Episodes 反向「💬 關聯會談」包含相應 Session | 295／295 | **PASS：反向關聯完整** |
| Session 主方案與所屬 Episode 主方案相同 | 287／295 | **PARTIAL：有 8 筆不同** |
| Session 與 Episode 主方案不同 | 8／295 | **待人工確認：不等於8筆錯誤** |
| 啟用青壯 Price Plan Session 反向關聯與直接選該方案 Session 集合 | 41／41完全一致 | **PASS：雙向集合一致** |

### 不一致的 8 筆，僅列匿名分類

| 類別 | 筆數 |
|---|---:|
| Session 選啟用青壯方案，Episode 選另一方案 | 4 |
| Episode 選啟用青壯方案，Session 選另一方案 | 4 |
| 其他方案彼此不一致 | 0 |
| 不一致 Session 的狀態 | 已完成4、已預約2、已改期2 |

**不可自動同步或修正這8筆**：可能是個別會談刻意採用其他收費方案，也可能是未同步的資料；需有業務語義、受控測試及使用者授權，才能判定真錯誤。不能將這些差異單憑條件刪掉，亦不影響已確認的「先在服務歷程選方案」操作原則。

### 啟用青壯方案 41 筆 Session 狀態

| 執行狀態 | Session數 |
|---|---:|
| 已完成 | 23 |
| 已預約 | 13 |
| 已取消 | 2 |
| 已改期 | 2 |
| no-show | 1 |
| **總計** | **41** |

其中37筆 Session、Episode 都選青壯，4筆為 Session 青壯／Episode 其他方案；相反方向另4筆 Episode 青壯／Session 其他方案。這是**關聯與狀態分類**，**不是政府額度最終占用數**。

## Notion 原生 Formula／Rollup 真值限制

- 啟用 Price Plan 的 `核定總額度_帶入`、`已完成_帶入`、`已預約_帶入`、`待確認_帶入` 皆返回 `rollupResult://` 指標。
- `已占用_自動`、`額度狀態_自動`、`剩餘額度_自動` 皆返回 `formulaResult://` 指標，**不是數值**。
- Sessions 的 `已完成計數_自動`、`已預約計數_自動`、`青壯115占用計數_自動`、`補助占用資格_自動` 在295筆 View 結果也只提供 `formulaResult://` 指標。
- 當次 SQL／rows 共用額度已耗盡；工具回傳說明重試會失敗。改用 View 讀取完成關聯比較，但**不能驗證每一筆原生 Formula 的數值與 Price Plan 實際餘額**。尤其不能用 23+13=36 推定現行額度占用36。
- `00.config_notion` 當次搜尋未精確定位；本回合唯讀 Schema/View 直接 Fetch 可核對，而**任何共用公式或關聯的修改**仍須先取得權威設定及先行批准。

## 影響範圍、保持不變、驗收與回復

- **本回合只有 Notion TEST 驗收歷史追加文字＋GitHub 文件更新**。沒有變更原57筆 Episodes、295筆 Sessions、Price Plans、Staff、補助參與或任何 Schema／Relation／Formula／View、權限、正式 GAS／Cloud Run／Session／部署；沒有增加青壯資格核對清單。
- **效能**：只做唯讀 View 查詢，未測量 UI 開啟時間，不聲稱效能改善；資料與權限保持不變。
- **已通過**：57／295/41 項關聯集合比較，以及所有頁面分頁完整性；匿名統計經程式雙向逐筆比對。
- **部分通過／待驗**：8筆差異的合理性、原生 Session 計數、Price Plan 已占用與剩餘額度、跨方案跨期公式、使用者角色權限及真人工作流程。
- **回復**：業務資料沒有寫入，無需資料回復。若要撤回驗收日誌或 GitHub 文件，先核對最新版本及並行修改，只撤銷當次記錄，不覆蓋其他人的進度。

## 下一個安全步驟

先對 8筆差異擬定「個別會談更換方案是否合理」的人工業務對照規則，不觸碰個資與既有資料；待原生 Formula 值可取得時，以當期已確認的實際 Price Plan ID、不同 Session 狀態及核定規則查核，必要 C級核心改動另取得核准。
