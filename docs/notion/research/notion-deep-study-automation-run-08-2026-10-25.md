# Notion 深度學習｜排程獨立研究批次 AUTO-08（2026-10-25）

> 本次只閱讀外部公開文件、更新 GitHub 研究記錄；**沒有任何 Notion 或正式系統寫入**。研究目標為至少10,000篇去重來源各10次獨立且可稽核的完整深讀；本輪未達標，也沒有授權重新設計。研究批次識別：`AUTO-08-20261025`，查閱日期：2026-10-25（Asia/Taipei，約23:38–23:59）。官方文章實際發佈/最後修訂日未知，不猜測。

## 1. 本輪研究前置與去重

已從 GitHub `main` 重讀 `README.md`、根 `AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`decision-log.md`、`acceptance-status.md`、2026-10-24研究清冊、十面向研究、2026-10-25第二～四批、AUTO-01～07、MANUAL-01，寫入前再次逐文件搜尋本輪兩個 canonical slug。這兩個 URL 在上述來源清冊未見已登錄；**本輪新來源2篇，不是4篇**。不同語系不重複計數。既有的 Layouts (DS-018) 與 Dashboards (N06) 僅為原來源重新查核，絕不算新文章。

額外的去重/時效測試：嘗試直接開啟 `https://www.notion.com/help/home-and-my-tasks`，**現行網址實際重新導向** `https://www.notion.com/help/navigate-with-the-sidebar`（已登錄AUTO-07）；搜尋引擎保留的其他語系 Home 舊內容不能冒充新 canonical 官方文章，故本輪不把 Home 當新來源。這個轉址是本輪實際取得的行為，未驗證每個語系或帳號都相同。

## 2. 來源、文字章節與反例分析

### AUTO08-01｜Manage sidebar presets for your workspace（新增）
- 官方來源：<https://www.notion.com/help/manage-sidebar-presets-for-your-workspace>
- 取得程度：`MAIN_TEXT_SECTIONS_READ + ANALYTICAL_PASS_1`；網頁可讀正文約lines 106–189，閱讀Default/Optional、Create、Rename/Reorder、Delete、Member actions、FAQs。圖片/所有嵌入媒體未逐一核查，無實帳操作，不算嚴格 `FULL_DEEP_PASS`。
- **原文重點**：Preset是工作區Admin設定的**起始側邊欄**，分Default（自動提供）和Optional（成員自選）；每工作區至少一個Default。成員仍可自行改/移除/Reset自己的Tab；刪Preset先進Deleted清單，儲存後才真正套用刪除；文件操作步驟針對桌面版。
- **初始假設**：工作區管理員建立Preset，就能強制所有合作心理師持續看見相同導航、避免找不到入口。
- **反例**：成員可以移除預設Tab，並且新加入者收到的Preset不等於已登入成員的Sidebar配置被強制鎖定；操作文件也未證實手機有相同設定介面。
- **修正理解**：工作區預設配置 ≠ 個人固定導航 ≠ 資料存取權限；不得把「我設定了Preset」視為角色必定看見首頁或資料已獲權限保護。這是研究，不提議或執行任何新增Preset。
- **第2–10次嚴格完整深讀**：未執行；實帳權限/版本與跨裝置仍待驗證。

### AUTO08-02｜Customize your sidebar（新增）
- 官方來源：<https://www.notion.com/help/customize-your-sidebar>
- 取得程度：`MAIN_TEXT_SECTIONS_READ + ANALYTICAL_PASS_1`；網頁可讀正文約lines 106–200，閱讀自訂項目、Tab來源、顯示/隱藏/重排、Tab增刪、Reset、釘選DB View、頁面捷徑與FAQ。圖片/媒體未逐一核查，無實帳操作，不算嚴格 `FULL_DEEP_PASS`。
- **原文重點**：每Tab最多25個Shortcuts與25個Sections，Sidebar最多6個Tabs；個人Hide不刪除資料或改他人Sidebar；刪Tab也不刪頁；釘選同一DB View至Sidebar每Tab最多3個，會保留其篩選排序，但若他人修改該View，釘選內容亦會變。
- **初始假設**：將不常用或被否決的舊設計藏到Sidebar之外，就算已按使用者要求清理。
- **反例**：官方明言Hide/Delete Tab不會刪除任何原頁、View或資料；釘選的View還可能受他人後續改動影響。使用者明確「否決的舊設計應真正刪除」，不能把個人導航收合冒充舊元件已刪除。
- **修正理解**：個人Sidebar清爽、原資料/頁面生命週期、View共享狀態、角色權限是不同責任；這也解釋為何單看某位使用者的Sidebar不能當全體UX/資料清理驗收。僅作研究，不變更現有導航或刪任何內容。
- **第2–10次嚴格完整深讀**：未執行；跨角色共享View/多裝置體驗未實測。

### 既有DS-018｜Layouts（已登錄；本輪獨立重讀，不新增來源）
- 官方來源：<https://www.notion.com/help/layouts>
- 本次讀取：原先第二批只標 `BODY_SECTIONS`，本輪重讀可取得文字主節約lines 106–249，包含Heading/Pinned（最多15）、Property group、Details panel、Tabbed Structure、Apply to all pages、Reset、Module限制。級別：`TARGETED_REVIEW_WITH_NEW_COUNTEREXAMPLE`；不是10次正式深讀中的第2次 `FULL_DEEP_PASS`。
- **新反例**：為讓一個特定補助年度頁面看起來簡潔而改該資料庫Layout，官方明言**同一資料庫所有既有與未來頁面都套用**，不能只改某個View或個別頁；移除Module不等於刪Property，而在Layout builder編輯Property卻可能改真Schema。Tabbed layout含其他DB View不代表其業務Relation正確，且Relation不能隨意移入Details panel。
- **修正理解**：視覺布局的作用域、來源Schema的作用域與業務真值要分開；原生Layout不是每期不同UX的局部隔離器。無本案TEST/正式實測或修改。

### 既有N06｜Dashboards（已登錄；本輪獨立重讀，不新增來源）
- 官方來源：<https://www.notion.com/en-gb/help/dashboards>（與原清冊 `/zh-tw/help/dashboards`同一官方文章的不同語系，不新增來源）
- 本次讀取：可取得文字主節約lines 106–402，涵蓋Business/Enterprise權益、最多12 Widgets/每行4個、Widget和underlying View不同修改層次、Global filter只作用於具有對應Property的Widgets、View mode編輯資料權限、效能與Inline Views對比、FAQ。級別：`TARGETED_REVIEW_WITH_NEW_COUNTEREXAMPLE`，不當作正式10/10完整Pass。
- **新反例A**：跨多個資料庫使用Global Filter（如期別）時，只有包含對應Property的Widget會被過濾；缺該欄的Widget可能仍顯示其他年度資料，導致同畫面多種時間範圍，不能以「一個總篩選器」保證所有補助額度一致。
- **新反例B**：View mode可依權限修改業務資料，非只讀；編輯Widget引用的底層View可能影響其他頁使用同一View。Dashboard效能指南還提醒大型未過濾表格及過多Widget會變慢。官方Dashboard view目前限Business/Enterprise，不能假定Free可用，也不能把它的Global Filter能力外推一般Inline Linked Views。
- **修正理解**：UI統一 ≠ 資料真值統一；Dashboard的功能、方案權益、角色授權與性能是四個不同的驗證門檻。僅研究，未對本案建立Dashboard或測量載入秒數。

## 3. 跨來源矛盾/反證與本案限制

1. **Presets × Personal Sidebar**：管理員給的是起點，個人可重排/刪Tab；沒有證據證明Preset能強制角色長期一致，故不把它視為存取權限。
2. **Sidebar × 使用者否決即刪除**：Hide/Remove Tab不刪原頁。日常畫面隱藏不是對已否決舊設計的真刪除；但實際刪除需另外驗證引用與業務保存，研究不能授權清理。
3. **Layouts × Dashboards**：Layout對整個Data Source的頁面生效，Dashboard Widget可引用既有View並可能影響別頁；兩種UI配置的變更作用域不同，不能混同「只改畫面」。
4. **Global Filter × 多核定期**：不同Widget可能沒有相同可篩選屬性；篩選表面一致不保證同年度/期別，更不代表額度公式正確。
5. **Legacy Home URL redirect**：搜尋結果可能保留舊Help文章，但現行Canonical已跳到已登錄Sidebar文章；不能用語系、舊標題或redirect冒充新增學習篇數。

## 4. 本輪可稽核狀態

| 指標 | 真實值 |
|---|---:|
| 新增去重官方canonical URL | **2** |
| 新來源可取得文字主節並完成第一次反例分析 | **2** |
| 舊來源有新反例的針對性重讀 | **2** |
| 發現已重導向的舊Help URL（不計來源） | **1** |
| 嚴格完成10次獨立完整深讀的文章 | **0** |
| 累積10/10合格篇數／目標 | **0／10,000** |
| Notion、業務資料、角色權限、GAS、Cloud Run、Session變更 | **0** |

以上沒有檢查每張示意圖、嵌入影片、實機功能、免費方案角色權益、真人UX、效能或任何業務真值；**不把MAIN_TEXT_SECTIONS_READ或TARGETED_REVIEW冒稱FULL_DEEP_PASS**。GitHub研究檔與索引寫入後需重新Fetch比對Commit、blob SHA和完整內容；若並行衝突無法安全合併就停止該筆寫入。整體研究未完成，**不得開始Notion新版設計**。
