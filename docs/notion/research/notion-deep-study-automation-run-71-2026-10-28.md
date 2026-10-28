# Notion 深度學習｜AUTO-71｜2026-10-28（純研究，PARTIAL）
Trace: `AUTO-71-20261028-1438-RESEARCH`。時間：臺灣 2026-10-28 14:38 起。任務範圍：僅外部資料閱讀及 GitHub 研究證據；不得寫 Notion 或正式系統。

## 開始前基準與去重
已於本輪重新 Fetch main：根 README、AGENTS、docs/system/source-of-truth、docs/notion/AGENTS、docs/notion/sources、decision-log、acceptance-status；閱讀 research/README、audit-checklist-and-research-progress，列舉 research 目錄 82 份文件。完整 sources.md 中未見本輪兩個 canonical URL；GitHub repo code search 亦未回傳相符結果。**未逐一全文比對全部歷史 AUTO 文件，亦未驗證同文不同網址的語義重複，因此僅計新來源候選，不計全庫嚴格去重通過。** 本輪與 AUTO-70（地址、電話）選用不同官方文件。來源頁面查核日 2026-10-28；官方個別首發／最近修訂日期未核實，不自行填入。

## AUTO71-S01｜Ask users for Email addresses
- URL: https://design-system.service.gov.uk/patterns/email-addresses/
- Canonical identity: `govuk-design-system:patterns/email-addresses`；維護者：GOV.UK Design System team；類別：表單／聯絡資料 UX。
- Evidence ID: `AUTO71-S01-R1-MAIN-TEXT-C1`。實際取得並閱讀官方正文及 HTML/Nunjucks 範例（頁面約246行；包含用途、長度、貼上、type=email、spellcheck=false、autocomplete=email、重複輸入與 email 驗證、錯誤訊息）。**僅一次主要正文與範例文字閱讀，不是完整深讀 R1。**
- 原文可核對的主張：先說明收集用途；允許貼上；建議支援長至254字元、顯示至少30字元；常見網域錯字宜提示但不應強行阻擋；重複輸入或寄送驗證信會增加負擔，應有必要性。表單範例使用 email type、關閉拼字檢查及自動完成。
- 反例 C1：個案聯絡信箱、收據寄送信箱與員工登入信箱可能不同，將一個Email欄位強制同時承擔三種目的，可能錯寄敏感內容；應依實際業務用途分辨，**不是提議現在新增欄位**。
- 反例 C2：格式通過或寄送成功不代表收件者有權看個案資訊；共用信箱、轉寄、已換帳號都可能造成資料洩漏。顯示或隱藏 Email 欄位亦不能代替角色權限。
- 反例 C3：為避免輸入錯誤而強制所有人重填Email或驗證信，可能阻礙不以Email聯繫的個案；但完全不核對又可能寄錯收據。需按寄送目的與風險選擇核對，不可把任一極端當預設。
- 反證／界線：此為 GOV.UK 通用表單設計，不是臺灣個資法、心理師保密義務或 Notion 原生功能的適法性證明；不代表 Notion 欄位原生支援 HTML type/autocomplete。未驗原圖、實際鍵盤、手機、螢幕閱讀器、中文輸入或寄送端驗證。

## AUTO71-S02｜Ask users for Bank details
- URL: https://design-system.service.gov.uk/patterns/bank-details/
- Canonical identity: `govuk-design-system:patterns/bank-details`；維護者：GOV.UK Design System team；類別：付款／敏感資料 UX。
- Evidence ID: `AUTO71-S02-R1-MAIN-TEXT-C1`。實際取得並閱讀官方正文、HTML/Nunjucks 表單、分支付款選項、國際銀行帳戶、錯誤訊息與研究限制（頁面約493行）。**僅一次主要正文與範例文字閱讀，不是完整深讀 R1。**
- 原文可核對的主張：銀行資訊應在安全服務中收集，不應要求Email傳送；UK sort code允許空白/連字號等格式；不同付款方式需考慮不願或無法提供銀行帳戶者；跨國銀行資料需依國家調整，不可照搬UK欄位。官方明言該模式尚未直接經使用者研究驗證，並列出帳號顯示/隱藏、國際帳戶與舊帳號格式的未決研究問題。
- 反例 C1：直接複製英國sort code及6–8位帳號格式至臺灣心理師匯款資料，可能拒絕合法銀行帳號或毀損前導零；臺灣欄位及驗證需以本地實際銀行作業核實。
- 反例 C2：為方便 Billing 對帳而將完整收款帳號放在同頁多個 linked views，可能使無需知悉者看到敏感財務資料；但全遮罩亦可能阻礙合法覆核，應依角色與任務做最小揭露。此為設計假說，未經權限驗證。
- 反例 C3：付款資料格式有效不等於款項已入帳、退款已執行或分潤計算正確；帳號主檔更新也不能未經核對就追溯覆蓋歷史收據與付款紀錄。
- 反證／界線：官方模式針對英國政府付款給使用者，並非臺灣診所或心理治療所銀行驗證規範；不能將它視為 PCI、資安或財務合規驗收。沒有接觸、輸出或儲存任何真實銀行帳號。

## 交叉比較與計量
- 共同結論（研究假說，非核准改版）：**輸入格式有效 ≠ 聯絡/付款對象身分已核對 ≠ 有權使用該資料 ≠ 業務狀態已完成。** 前端簡化不能取代資料權限、後端核對與歷史紀錄。
- 本輪新 canonical URL 候選：2；主要正文文字閱讀：2；獨立反例：2組、6情境；既有來源完整複讀：0；同URL重複計算：0。
- 嚴格完整 R1=0，R2–R10=0；本輪 `FULL_DEEP_PASS_10_OF_10=0`；累積可核實 `0/10,000`。範例/分析角度不另計閱讀次數。
- NOT_TESTED：原始視覺圖、互動、鍵盤、讀屏、手機、真人 Notion、臺灣銀行/個資合規、實際角色權限、歷史收費金額、Formula、效能。兩篇均列 `PARTIAL_MAIN_TEXT`，未完成完整深讀。
- NO NOTION/SYSTEM WRITE：本輪僅研究及 GitHub 進度，未更改 Notion 正式或 TEST 頁、DB、View、Formula、Relation、權限、業務列，亦未改正式 GAS/Cloud Run/Session/部署。尚未達門檻，不開始重新設計。
