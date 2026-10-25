# Notion 深度學習｜自動排程獨立批次 AUTO-05（2026-10-25）

> **僅限公開文件研究＋GitHub進度紀錄。** 本批研究記號 `AUTO-05-20261025`，查閱日期 2026-10-25（Asia/Taipei，排程回合起始約20:37）；並行的手動續作不停止。本次沒有修改 Notion TEST／正式頁面、資料庫、資料列、View、Relation、Formula、權限，亦無 GAS、Cloud Run、Session 變更。研究目標10,000篇、每篇10次可稽核完整深讀，**未達標，禁止開始Notion新版設計**。

## 1. 去重範圍與真實閱讀級別

- 研究前先讀主分支 `README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`；用 GitHub research 目錄清單取得當期16個研究檔並檢索其Notion官方URL，包含首批、批次02/03/04、十面向、MANUAL-01、AUTO-01/02/03/04。對照語系與slug後，以下三篇不在已讀URL清冊。先前已登錄的 `/help/database-buttons` 與本次 `/help/buttons` **不是同一文章**，不可混為重讀或同篇複數。
- 三篇來源均經官方頁面 `open` 查閱可取得的**全部主要文字章節**；跳過導覽、頁尾、嵌入圖片逐張內容、可能連結的影片、實機操作，因此只記 `MAIN_TEXT_SECTIONS_READ + ANALYTICAL_PASS_1`，**不登記 `FULL_DEEP_PASS`**，也不將同篇多小節計為多篇。
- `ANALYTICAL_PASS_1` 每篇有獨立假設、來源實據、反例、修正理解與尚待驗證；本輪沒有第2～10次的獨立全文閱讀。各文發布或最後編輯日期不明，不能把「本次查閱日期」冒稱文章更新日期。

| Source ID | 唯一官方來源 | 查閱範圍（Web正文行數；不含導覽） | 本輪閱讀分級 | 完整深讀10/10 |
|---|---|---|---|---|
| AUTO05-01 | [Buttons](https://www.notion.com/en-gb/help/buttons) | 約106–282：可用方案、建立、動作、Gmail、變數與公式、錯誤、編輯、FAQ | `MAIN_TEXT_SECTIONS_READ + ANALYTICAL_PASS_1` | 0 |
| AUTO05-02 | [Delete & restore content](https://www.notion.com/help/duplicate-delete-and-restore-content) | 約106–315：區塊／頁刪除、Trash、Archive、Version history、DB／欄位恢復、FAQ | `MAIN_TEXT_SECTIONS_READ + ANALYTICAL_PASS_1` | 0 |
| AUTO05-03 | [Custom data retention settings](https://www.notion.com/help/custom-data-retention-settings) | 約106–175：Enterprise限定、Trash期間、刪除後留存、搜尋／還原／永久刪除 | `MAIN_TEXT_SECTIONS_READ + ANALYTICAL_PASS_1` | 0 |

## 2. AUTO05-01｜Buttons：一鍵操作與權限／錯誤處理

- **初始假設**：按鈕可用於免費方案，所以可以安全、完整地替代治療所業務流程的權限與覆核。
- **實際查核**：Button基本功能適用所有方案，但寄Gmail、發Webhook、Slack通知等某些動作受付費方案限制；頁面上按鈕互動需要至少Can edit或Full access，若動作會新增/修改其他資料庫，點擊者仍需目標資料庫編輯權。動作含Insert blocks、Add page to、Edit pages in、Show confirmation、Open page/URL、通知、Define variables。某些動作不支援公式；按鈕可因資料庫/欄位消失或外部連線失效而報錯。模板頁面內容可能覆蓋按鈕設定的名稱。
- **反例**：操作者有權點首頁Button，但沒有目標Billing資料庫編輯權，該Button無法完成資料寫入；反過來，操作者若有目標資料庫編輯權，Show confirmation只是二次確認視窗，**不能防止具權限者不當更改或同時重複計次**。模板預設名稱覆寫也會令操作人員以為已成功依期別命名。
- **修正理解**：按鈕是可用性／減少步驟的互動，不是後端授權、事務原子性、重試去重、業務真值驗證。免費版「可建立按鈕」不等於所有動作免費；**不建議此時在Notion增設任何按鈕**。
- **尚待驗證**：免費工作區實際動作清單、角色權限、批次重複點擊、按鈕動作錯誤提示是否會造成部分完成、外部Gmail資料處理。第2–10輪未執行。

## 3. AUTO05-02｜刪除、Archive、Version history：回復不是一鍵完整回復

- **初始假設**：刪掉不合適的資料庫／欄位，只要30天內按Restore就能連同所有子頁文字、公式及檢視完整回復；Archive等同安全刪除。
- **實際查核**：一般頁面在Trash預設30天，超期後進入後續保留期；Free的Version history可追7天、Plus30天、Business90天、Enterprise不限天數（但以當時方案條款為準）。Archive在此文被標Beta且僅Business/Enterprise；封存頁仍可透過原連結存取、通常從搜尋/資料庫View隱藏。恢復資料庫歷史版本可恢復資料庫的頁與屬性，**但資料庫頁內的文字內容需要逐頁恢復**；回復資料庫也可能影響現有View與其他人的畫面。被刪除的DB屬性有Deleted Properties入口可還原，但從該入口永久刪除就無法自行復原。
- **反例**：刪除原有政府補助歷史資料表後，只Restore上層Database版本，個別Care Episode頁內記錄的文字未必跟著回復；或封存後日常表格看不見歷史列，但分享連結仍可讀，故「隱藏＝刪除／權限隔離」錯誤。Free版超過7天的頁面歷史不能假設能從UI自行還原。
- **修正理解**：Trash、Archive、Page history、Database history、Deleted Properties和獨立備份是不同復原面；不可因一種回復可用就推論整套系統可無損回滾。這與此前AUTO-02「匯出不能一鍵還原」互相印證；本輪**不執行任何刪除／封存／復原測試**。
- **尚待驗證**：不同Notion帳號的實際可用權益、Relation/Formula/Linked View的還原行為、資料庫恢復後外部引用是否完整。第2–10輪未執行。

## 4. AUTO05-03｜Enterprise資料留存：刪除後資料保留與存取權是兩個議題

- **初始假設**：Notion Trash只有30天，任何方案的管理員都能把它延長10年，因此可滿足本地研究或臨床紀錄保存需求。
- **實際查核**：官方`Custom data retention settings`明示**Enterprise workspace owners限定**。可分別調整Trash中待刪除的期間，以及永久刪除後的retention期間，範圍1天至10年；AI chat刪除後直接進retention而不進Trash。管理員可從Content search依Page status查In Trash/Retained pages；復原前可檢查原權限，選回原位置或Private。retention結束後，即使管理員也不能再存取/恢復。
- **反例**：免費或Plus工作區不能僅因官方文章寫「1天～10年」就宣稱擁有此管理設定；即使Enterprise能設10年，也不代表符合臺灣病歷、財務、研究紀錄的保存規範與個資保護要求，或確保刪除後的原分享權限不會恢復。復原到原位置與Private在權限暴露風險上不同。
- **修正理解**：`retention`是企業級資料生命週期功能，不等於法律合規、業務備份、跨資料表一致性或Free版功能；**不推導任何現有工作區方案／實際設定**。
- **尚待驗證**：實際方案、保留設定、合規責任、跨頁資料引用與備份策略、權限回復流程；第2–10輪未執行。

## 5. 跨來源反證與新理解

1. **Button × Database automations (MANUAL-01)**：兩者都有自動執行能力，但Button是人員點擊觸發，Database automation可由資料事件觸發；不能用Button的免費可用性推論Database automations全功能免費，也不能推論點擊後必然完整成功。
2. **Restore × Export backup (AUTO-02)**：Version history復原DB不保證每個DB頁面內文恢復，Workspace匯出亦不提供完整原樣匯入；兩者不是彼此的無損備援。
3. **Archive × Search/Views (舊B4-01)**：Archive會讓頁面從預設搜尋與View隱藏，但連結仍有效，不能將資料檢索不可見誤認為權限撤銷。
4. **Enterprise retention × 治療所資料保護**：留存年限是平台可設定的資料處理週期，不能直接推論法規符合性；復原到原位置前需重新審視分享權限。
5. **刪除前的回復規劃**與**實際執行刪除**是兩回事。本批僅研究，絕不因讀到Restore功能而擴張成清理舊資料、修改Notion權限或UX。

## 6. 可稽核進度與界線

| 指標 | 本次 |
|---|---:|
| 已與當期研究清冊對照的新canonical URL | **3** |
| 已查閱全部可取得文字主章節 | **3** |
| 各篇新增首次反例分析 | **3** |
| 本次新增第2–10輪獨立完整深讀 | **0** |
| 全域嚴格達成10/10完整深讀篇數 | **0 / 10,000** |
| Notion正式/TEST及業務資料/權限/程式修改 | **0** |

限制：未逐張讀取插圖、未播放嵌入媒體、未測實帳／手機／效能／權限／資料恢復，故不能計入嚴格全文10/10。查閱日期是2026-10-25，不代表官方文章當日發佈。寫入時先確認研究檔名與URL未被並行流程佔用；GitHub新增此獨立研究檔，必要同步sources/decision/acceptance索引，**各次寫入用最新blob SHA，寫後重新Fetch驗證**。若並行衝突無法安全合併，不覆蓋。
