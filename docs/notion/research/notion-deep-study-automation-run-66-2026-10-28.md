# Notion 深度學習｜AUTO-66｜2026-10-28（研究限定）

- 唯一執行軌跡：`AUTO-66-20261028-0938-RESEARCH`；日期：2026-10-28 09:38 Asia/Taipei。
- 工作範圍：僅公開資料閱讀、反例分析及 GitHub 研究進度紀錄。**不修改 Notion 正式/TEST 頁、DB、View、公式、Relation、權限、業務資料或正式 GAS／Cloud Run／Session／部署；不開始 Notion 重新設計。**
- 前置基準：main `README.md`、根 `AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`decision-log.md`、`acceptance-status.md` 均於本輪重新 Fetch；研究目錄列舉77個 Markdown 項目（其中含既有AUTO紀錄）。曾嘗試逐檔讀取全研究目錄，但工具呼叫上限阻擋；**不得宣稱全庫去重完成**。兩來源在當時 sources 索引沒有相同 URL，GitHub code search 亦無 Breadcrumbs 命中；同文異址、其他研究文件全文仍未完成核對。

## 來源1｜Notion 官方 Keyboard shortcuts
- ID `AUTO66-S01`；canonical URL：https://www.notion.com/help/keyboard-shortcuts；去重身份 `notion-help:keyboard-shortcuts`；維護者 Notion Help Center；首次發布／最近更新日期頁面未明列，**不推定**；檢索 2026-10-28。
- 唯一閱讀事件 `AUTO66-S01-R1-MAIN-TEXT-C1`：實際閱讀可取得的官方主要文字段落（Most popular、Desktop、Markdown、Create/style、Edit/move、@、[[、+、Slash/Basic/Inline/Media/Advanced），涵蓋 Cmd/Ctrl+F 頁內搜尋、Cmd/Ctrl+P/K 工作區搜尋、[ ] 返回、peek 上/下筆、Ctrl+Shift+U 上一層、/bread 路徑、資料庫多選後 Cmd/Ctrl+/ 批次操作；不是10次閱讀，也**不是完整深讀R1**。
- 官方限制：頁面明示以英文／QWERTY 鍵盤為例，國際化尚在規劃；快捷鍵依平台及當前視窗／peek 情境不同；未操作影片與實機。
- 反例A（搜尋情境）：同頁資訊原可直接核對時，改靠全域搜尋/快捷鍵切換可能讓行政人員誤進相似名稱的另一筆服務資料，且跨個案/方案期別的資料一致性不因快捷鍵而成立。
- 反例B（操作情境）：Ctrl+K 在不同介面情境可能有不同用途；中文輸入法、OS綁鍵或瀏覽器捷徑可能干擾，不能假定官方QWERTY表能直接套用臺灣 Windows 工作流程。資料庫多選後批次編輯可能造成擴大誤改風險，必須在隔離資料/真人驗證，不能由指南推定安全。
- 反例C（層級情境）：Notion `/bread` 表示頁面所在位置，不是 Session→Billing→方案期別的業務來源鏈；頁面導覽清楚不代表歷史金額被凍結或補助額度正確。
- 研究推論：可發展「常用操作可達性」測試假說，但不得以快捷鍵取代使用者已確認的「同類資料同頁、開啟即見」或用以核准修改。

## 來源2｜GOV.UK Design System Breadcrumbs
- ID `AUTO66-S02`；canonical URL：https://design-system.service.gov.uk/components/breadcrumbs/；去重身份 `govuk-design-system:components/breadcrumbs`；維護者 GOV.UK Design System team；官方 history 顯示2018-06導入、2024-07 nav/aria-label 更新；檢索 2026-10-28。
- 唯一閱讀事件 `AUTO66-S02-R1-MAIN-TEXT-C1`：官方主文、何時用/不用、HTML/Nunjucks、mobile collapse、深色背景對比、近期變更、Nunjucks options 與 history 文字均已閱讀；仍未完成圖片/實際互動/鍵盤/讀屏，因此**不是完整深讀R1**。
- 事實：Breadcrumbs 適用多層網站結構，不適合扁平結構或線性流程進度；應在主內容之前，從首頁至當前頁的父層；行動裝置可收合中間層；深色背景版本需顧及4.5:1對比。HTML `nav`/`aria-label` 是此元件實作，不代表Notion能任意植入。
- 反例A（層級錯置）：將「首頁 > 個案 > Session > Billing」畫成麵包屑，容易把多對多/跨期關聯誤當成唯一父子路徑；歷史 Session 可能涉及多個 Billing/方案期別，Breadcrumbs 不提供資料來源正確性。
- 反例B（誤作進度）：把「預約→完成服務→確認收款」當成麵包屑會混淆導覽與業務進度，且資格待核/未確認0不會因導覽變成已核准。
- 反例C（手機收合）：行動版只露出首末節點可能隱去中間重要工作情境；也不代表 Notion 原生手機介面支援相同收合/讀屏行為。
- 研究推論：導覽路徑、任務進度、資料來源鏈必須分開驗證；不得因此改動目前Notion的頁面結構。

## 計量與未完成
- 本輪新來源**候選2**（同URL索引未見，**全儲存庫/同文異址去重未完成**），官方主要文字實讀2篇，首次獨立反例2組共6情境；**完整R1=0、R2–R10=0、FULL_DEEP_PASS_10_OF_10本輪0，累積可核實0/10,000**。
- 缺口：官方原始圖片/嵌入影片、實際鍵盤與讀屏、Windows中文輸入法、手機、真人 UX、Notion 真實帳號/權限、資料公式、歷史金額、效能；均NOT_TESTED。
- 文獻連結：[Notion Keyboard shortcuts](https://www.notion.com/help/keyboard-shortcuts)；[GOV.UK Breadcrumbs](https://design-system.service.gov.uk/components/breadcrumbs/)；[Breadcrumbs Nunjucks](https://design-system.service.gov.uk/components/breadcrumbs/nunjucks/)；[Breadcrumbs history](https://design-system.service.gov.uk/components/breadcrumbs/history/)。
- 本輪所有反例是研究假說，**不是已核准設計、實際測試或正式驗收**。使用者未完成10,000篇各10次前，不得進入Notion重新設計。
