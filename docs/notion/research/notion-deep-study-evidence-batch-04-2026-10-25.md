# Notion 深度學習｜第四批來源、舊文再研讀與嚴格進度（2026-10-25）

> **階段：僅學習，禁止開始Notion重新設計。** 使用者要求至少10,000篇各10遍，未達成。此文沒有任何Notion業務資料、使用者資訊、程式或設計改版。所列的閱讀層級與實際取得證據逐一區分；本回合是新的對話工作回合，不是背景排程。

## 1. 與既有研究去重及學習門檻

權威研究清冊：[原始16來源](evidence-register-2026-10-24.md)、[第二批14 URL](notion-deep-study-evidence-batch-02-2026-10-25.md)、[第三批11新來源＋N09重讀](notion-deep-study-evidence-batch-03-2026-10-25.md)，另有[代表性10面向研究](notion-ux-research-and-10-lens-review-2026-10-25.md)，其中部分URL交疊。已用這四份內容比對下面5個URL；**本批5個均未在四份舊來源表出現**。但因歷史未建真正完整全域唯一清冊，仍**不可從16+14+11+5直接宣稱全域累計唯一篇數**。

本批從搜索及閱讀取得：
- **5個本批新增來源URL**（B4-01～B4-05）；**4篇正文部分或多節確實開啟**，**1篇僅搜尋引文、直開Cache miss**。
- **2篇既有來源深度重讀**：第三批RE01（原N09）Notion Database Templates與NEW02 Notion Synced Blocks。記錄新的第二輪比較及反例，**不增加唯一來源**。
- **至少另重查一篇舊URL**：Notion Views/filters/sorts（先前N02／DS-019）確認每View的開頁模式、群組與凍結欄，未增加篇數。
- **10遍深讀的驗收合格篇數仍0/10,000**；不以這一輪第二次檢視或下面同日查閱的不同章節湊成10遍，也不將一篇目錄內模板的數量當作已讀作品。
- `FULL_DEEP_PASS`必須完整讀過正文、記下新的跨資料反例與來源段落、可被第三者核對，10次還須十份獨立筆記。目前本批4篇`BODY_SECTIONS`只能算**重點章節閱讀**，不能假稱整篇深讀。

## 2. 第四批5個新增來源（按canonical URL去重）

| ID | 標題與URL | 本輪實際存取層級 | 已閱讀／核對的內容 | 尚未完成 |
|---|---|---|---|---|
| B4-01 | [Notion官方／Search for pages & content](https://www.notion.com/help/search) | BODY_SECTIONS | 搜尋快捷鍵，標題／建立者／位置／日期等搜尋選項；**工作區搜尋會查資料庫頁面內文，但資料庫內搜尋會查標題與屬性、不查頁內文字**；工作區搜尋不含Select/Multi-select屬性值等例外（部分搜尋規則隨版本可變） | 尚未逐條真人操作不同角色／語言；未驗證私人來源可見範圍 |
| B4-02 | [Notion官方／Account settings & preferences](https://www.notion.com/help/account-settings) | BODY_SECTIONS | 桌機／手機Light/Dark與**高對比模式僅桌機及Web**；高對比偏好按裝置保存。此為使用者個人設定，**不是**可替代的業務View層級條件色彩或全部手機無障礙解法 | 沒有行動裝置與真實高對比視覺驗收；本文其他帳戶管理章未完整精讀 |
| B4-03 | [Notion官方／Status property gives you clarity](https://www.notion.com/en-gb/help/guides/status-property-gives-clarity-on-tasks) | BODY_SECTIONS | 任務類`To do/In progress/Complete`及子分類；過多重疊的Status選項讓人混淆及漏篩；可Group/Hide empty groups。**狀態文字應對應清楚的業務語意** | 未通讀全篇實務配圖，也不可擅自將政府補助「未知/不適用/確認0」硬塞進三個任務Status |
| B4-04 | [Notion官方／Keyboard shortcuts](https://www.notion.com/help/keyboard-shortcuts) | BODY_SECTIONS | 搜尋Ctrl+P/K、頁內搜尋Ctrl+F、資料庫peek前後筆快捷鍵、Heading/Toggle及批次編輯；文件註明部分鍵法以英語QWERTY為主，國際化尚有差異 | 未全文精讀所有快捷鍵；無台灣Windows及各角色可用性實機測試 |
| B4-05 | [Notion官方／Sync data from other tools](https://www.notion.com/help/sync-data-from-other-tools-to-notion) | SEARCH_EXTRACT_ONLY | 搜尋來源指出外部來源同步資料到Notion時**來源系統權限未必跟隨同步**，先在Notion核對分享權限；失去上游同步不表示Notion已有資料自動移除 | 直開兩次均`Cache miss`，**未能取得全文**。不應據此認定本治療所使用該同步能力或套用任何改版 |

註：上面的官方URL是**此輪來源讀取的依據**，非使用者Notion工作空間資料。不要把技術文件的示例自動當成工作區現況。此前所看Notion Marketing/模板分類頁只計搜尋候選，不算完整分析。

## 3. 舊文第二輪獨立再研讀：分清『重新理解』與『十遍達標』

### RE01／原N09: [Database templates](https://www.notion.com/help/database-templates)｜ANALYTICAL_REVIEW 2/10（非正式FULL_DEEP_PASS）

**本輪重新取證章節**：建立並編輯模板、模板複製Property及內文、Relation預填警告、重複產生Daily/Weekly/Monthly/Yearly、定期模板巢狀與3層上限、FAQ中每來源的模板相互獨立。上一輪關注「固定Relation會指向去年Price Plan」，這一輪換角度重新推演：

- **新問題**：若使用者希望「每週週額度回報」能由Recurring Template產生，是否等於週期規則自動正確？
- **反例**：Repeat只控制*產生頁面的時間與內容複製*，**不保證**已選對期別、心理師、週的起迄、額度規則及排除假日。若模板在Page Property預填一筆當期Relation，跨期後錯誤會被週週複製。
- **修正理解**：把「產生頁面頻率」和「業務額度歸屬/期間驗證」拆開；Notion模板≠可驗證的業務排程或授權。即使看似可省操作，沒有實際資料隔離及回復驗證不得使用。這不是建立自動化的提案。
- **與另一來源矛盾檢查**：Notion Status教學說可用分類促進一致性，但模板本身仍可能複製錯誤Relation；分類規範**無法替代期別核對**。本輪取得新的反例，但沒有執行真人測試；不把第2遍當10遍完成。

### NEW02: [Synced blocks](https://www.notion.com/help/synced-blocks)｜ANALYTICAL_REVIEW 2/10（非正式FULL_DEEP_PASS）

**本輪重新取證章節**：原始區塊的存取權限、所有副本一起更新、`Editing in... other pages`顯示副本位置、解除同步單一副本、全部解除、>10份副本的刪除/Undo例外及FAQ。

- **上一輪重點**：原區塊分享權限與>10副本之誤刪風險。
- **新問題**：若只想移除某一個工作頁面的導航或內部設計文案，可否直接刪除原始同步區塊？
- **反例**：同一原始Synced Block被別的行政頁重用，直接修改/刪除原始可能影響所有副本，且原始權限不足時部分角色連副本也不可見。
- **修正理解**：在**任一**Synced Block刪除/重構前，需先界定「這是個別副本，還是ORIGINAL」，查所有引用位置與權限；若要停止共用一處內容，應分辨「解除單一副本」與「刪除原始」兩個語意。但此輪**僅研究**，不授權任何實際刪除或重組導航。
- **與資料庫Linked View交叉比對**：Synced Block同步的是**區塊內容編輯**，Linked Database View與資料源的內容/篩選分層不同；將二者視為同一個UI元件會誤判影響範圍。十次正式深讀仍未完成。

### DS-019／舊N02: [Views, filters, sorts & groups](https://www.notion.com/help/views-filters-and-sorts)｜針對性複核

本輪重查Notion官方View有各自Property visibility、Sort、Filter、Group，並有`Side peek`、`Center peek`及`Full page`三種開頁行為；Table欄可Freeze。這是重查某些章節，**未核實整篇二次深讀**。若把同一資料來源某View調得好看，不代表改了所有View，也不代表不會因改Schema影響其他模組；不能以UI效果推論角色權限。此項不增加新來源或深讀次數。

## 4. 交叉閱讀的反例／實用區分（非Notion改版提案）

1. **搜尋與權限是兩個問題**：在DB表格裡搜尋名稱/Status，和在整個工作區找病歷頁內容，是不同的檢索介面；「找不到」不必然等同資料不存在。搜尋限制不代表使用者被安全隔離，仍需要真實分享權限驗收。
2. **狀態不是顏色**：Status三大類是任務管理中的方便分類；不能將補助資格未核、確定0、已失效等特殊真值混為一個「待辦」狀態；彩色標籤也不能代替精確決策來源。
3. **高對比只是閱讀輔助**：偏好設定只在Desktop/Web且按裝置生效，不可能假設所有人都看得到相同高對比畫面；狀態仍要能從文字或數字辨識。
4. **自動複製不是自動算對**：模板產生新頁與Schema/Relation的業務一致性分離，尤其期間與計次規則每核定期不同。只測操作便利不足以驗證錯誤成本。
5. **共享內容有共享變更風險**：原始同步區塊與副本的影響面和存取權不同於Linked Views，不能以「這只是設計文字」忽略其他頁面引用。

## 5. 稽核結論、版本、限制

| 指標 | 本批可核實值 |
|---|---:|
| 本批去重新增來源 | 5（4篇正文部分、1篇搜尋摘要） |
| 舊來源第二輪有新增推論的研讀 | 2 |
| 舊來源針對性重查、不計深讀 | 1 |
| 已達『10次完整深讀』的篇數 | **0／10,000** |
| 本回合Notion／業務資料／權限／程式修改 | **0** |

本批沒有進行真人使用者、行動裝置、效能、權限或數據真值測試；只向GitHub新增**可回溯的來源分級與反例研究**，以及必要的GitHub進度索引，且必須讀回Commit/SHA。**沒有達成「完整學習後才設計」的門檻，不進入Notion設計。** 如需回復本回合文件變更，按GitHub Commit針對相應研究檔/索引精準反轉，不覆蓋他人並行內容。
