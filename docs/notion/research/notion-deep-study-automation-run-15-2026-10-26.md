# Notion 深度學習｜AUTO-15｜2026-10-26｜文件維護、區塊編輯、公開發佈風險

- 獨立執行軌跡：AUTO-15-20261026-0643-Asia-Taipei；僅公開文獻研究及GitHub記錄；不操作Notion。
- 開始時已重讀main的README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/sources.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md、research/README.md、首批16來源、2026-10-25第二～四批、十面向來源、MANUAL-01及AUTO-01～14研究檔。新增來源經以上清冊 canonical slug 去重；不是只靠GitHub搜尋命中。實際查閱日期2026-10-26；官方頁未顯示可核實的發表/更新日期，不自行推測。
- 本輪新增3個原清冊未列的Notion官方Help/Guide文章；各開啟可讀正文，逐段檢查主要文字章節/FAQ，做1次假設→反例→修正。文字閱讀不等於完整媒體/實機深讀，FULL_DEEP_PASS=0；10/10達標新增0，累積可核實完成仍0/10,000。沒有把相同文章不同語系或不同角度當成額外篇/輪。
- 特別稽核：先前AUTO-14把首批N04 `relations-and-rollups`、N07 `database-property-access`重列「新來源」；AUTO-13 `formulas` 已在第三批NEW05出現。這些舊來源的後續閱讀可保留為研讀記錄，但**不能再算新增去重URL**。本輪只修正計數口徑的索引說明，不改寫歷史原始研究證據；全域唯一URL累計值需另做跨檔完整去重盤點，暫不宣稱確定總數。

## AUTO15-S01｜Tips to keep your team’s Notion pages up to date
- URL：https://www.notion.com/help/guides/tips-to-keep-your-teams-notion-pages-up-to-date
- canonical ID：notion-help:guides/tips-to-keep-your-teams-notion-pages-up-to-date；source：Notion Help Guide；author：Notion（未見具名作者）；publication/update：未核實。
- 2026-10-26 R1，trace AUTO-15-20261026-0643；TEXT_MAIN_SECTIONS_READ + ANALYSIS_PASS_1；不是FULL_DEEP_PASS。
- 閱讀範圍：How to stay on top of frequently updated pages／Updates & analytics／Version history／Created time/Created by/Last edited time/Last edited by／archive subpages／maintain foundational pages／Lock page／page owner／reminders；模板與站外連結僅列參考，未逐套操作。
- 官方內容：更新/分析、版本歷史、系統時間欄位可協助發現待檢查的舊頁；官方提出用子頁封存保留參考、鎖定避免誤編輯、以Callout指定負責人與提醒定期複核。
- 待反駁假設：「Last edited time較新就表示政策仍有效；移至Archive就等於使用者要求的實際刪除；Lock page就能防止所有有編輯權者更動資料」。
- 反例：2025年編寫的青壯方案說明在2026年僅改標點，Last edited變新卻仍可能沿用過期條款；移到Archive仍有舊副本及連結，無法證明被否決的業務入口已刪除；頁面鎖是可解除的操作保護，不是完整權限、稽核或法規保存機制。
- 修正結論：把「文件更新活動」「內容有效期/核定期」「被否決項目真正刪除」「存取控制」視為四個不同維度；研究不授權建立Archive或更改現有頁。
- 未驗：示例圖片、可展開互動內容的完整操作、歷史復原真值、不同角色解鎖、Notion工作區實際流程。

## AUTO15-S02｜Intro to writing & editing
- URL：https://www.notion.com/help/writing-and-editing-basics
- canonical ID：notion-help:writing-and-editing-basics；source：Notion Help；publication/update：未核實。
- 2026-10-26 R1，trace AUTO-15-20261026-0643；TEXT_MAIN_SECTIONS_READ + ANALYSIS_PASS_1；不是FULL_DEEP_PASS。
- 閱讀範圍：Editing tools（+、⋮⋮、/）／basic blocks、database、media、embeds、advanced/inline／spell check／style／select/drag-drop／Markdown／collaborative content／mobile差異／FAQ。
- 官方內容：Block可直接Turn into、Duplicate、Move to、Delete；Toggle目前需逐個手動開合、不能全部一鍵開合或設預設開合；inline database可嵌入頁面；手機沒有桌機的/命令及hover操作，而使用鍵盤上方工具列。
- 待反駁假設：「把全部管理資訊收進Toggle就能讓日常人員一鍵展開所有關鍵欄位；桌機設計在手機有相同操作入口；複製區塊只產生無害的顯示捷徑」。
- 反例：工作台多層Toggle會讓人員逐個展開才能看到剩餘額度，違反『同頁直接看見』；手機沒有相同hover/Slash操作，造成訓練/操作負擔；Duplicate可能生成內容副本而非引用，讓兩份政策說明不同步。
- 修正結論：應區分「日常直接顯示」與「低頻折疊文件」，將跨裝置可用性與副本來源一致性列未來驗收，不能從桌機靜態圖判定手機可用。**不改任何頁面/Toggle**。
- 未驗：影片、示例圖片、手機實機、所有embed的權限與安全、實際資料庫操作。

## AUTO15-S03｜Publish a Notion Site
- URL：https://www.notion.com/help/public-pages-and-web-publishing
- canonical ID：notion-help:public-pages-and-web-publishing；source：Notion Help；publication/update：未核實。
- 2026-10-26 R1，trace AUTO-15-20261026-0643；TEXT_MAIN_SECTIONS_READ + ANALYSIS_PASS_1；不是FULL_DEEP_PASS。
- 閱讀範圍：What you can do／Publish a Site／embeds／Site settings（search indexing、duplicate as template）／visitors／Unpublish／Enterprise禁發佈／FAQ。
- 官方內容：公開父頁時子頁預設也公開，需另限制子頁權限；公開頁內的資料庫可由訪客切換Views及開啟其中頁面；頁面公開或Anyone on web with link可能在網頁metadata包含貢獻者姓名、頭像、email；Notion Site Unpublish不會自動移除一般分享設定的Anyone on the web with link；Enterprise有禁公開功能，不能外推Free；Notion Site公開後內容更新同步反映。
- 待反駁假設：「只把首頁公開、子頁/資料庫仍天然私有；取消Publish就完全撤銷外部讀取；畫面沒有顯示email就不會外洩metadata」。
- 反例：治療所行政首頁若含有個案/員工子頁與Linked資料庫，父頁發佈可能連帶公開子頁及可切換的View；管理員只Unpublish卻未取消Anyone on web with link，仍可能讓持連結者存取；貢獻者email可能存在metadata，非肉眼可見正文即可判定安全。
- 修正結論：正式業務資料不可由研究直接發佈；未來若有公開網站需求，應先獨立建立不含個資的內容、逐層核權限與公開View、同時檢查Publish和General access撤銷。此為風險研究，**不聲稱現有頁面已公開或存在洩漏**。
- 未驗：影片、示例圖、公開網站實際網頁metadata、角色權限、任何真實治療所分享設定。

## 本批稽核與嚴格計數
| 指標 | AUTO-15實際值 |
|---|---:|
| 新增且本次清冊去重的canonical URL | 3 |
| 已取得主要文字章節並研讀 | 3 |
| 各篇首次獨立反例分析 | 3 |
| 本輪完整深讀10/10達標 | 0 |
| 累積可稽核完成10/10篇數 | 0/10,000 |

**限制**：沒有逐張檢查所有圖、觀看全部嵌入影片、打開所有外連/互動示範、登入Notion測試、跨角色/手機/效能/安全實測。讀取官方文字只能證明官方說明的內容，不證明治療所現況。來源版本未有可靠更新日期。只寫GitHub研究及索引，Notion Page/DB/Data Source/View/Formula/Relation/Share/業務列及GAS/Cloud Run/Session/部署完全不動；未開始重新設計。
