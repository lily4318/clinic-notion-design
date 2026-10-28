# Notion 深度學習｜AUTO-73｜2026-10-28（僅公開研究；PARTIAL）
Trace: `AUTO-73-20261028-1637-RESEARCH`；研究日 2026-10-28（Asia/Taipei）；唯一允許變更為 GitHub 研究紀錄，不修改 Notion 或正式系統。

## 基準與去重
- 本輪先從 main 重新讀取 `README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`docs/notion/decision-log.md`、`docs/notion/acceptance-status.md`、`docs/notion/research/README.md`、`docs/notion/research/audit-checklist-and-research-progress.md` 與 AUTO-72 正文，並查來源索引全文及 repo code search。
- `confirm-an-email-address`、`confirm-a-phone-number` 在已查 sources 與 GitHub code search 未見；開始寫入前再讀 sources main blob SHA，AUTO-73 檔案不存在。**尚未完成所有歷史研究文件逐檔全文與同文不同 URL 的精確去重**，所以僅列新來源候選。
- 本輪兩篇是獨立原始指南，不把彼此交叉引用、HTML/Nunjucks 示例或相同主題的舊資料收集指南算作額外篇數／閱讀輪次。

## AUTO73-S01｜Confirm an email address – GOV.UK Design System
- URL: https://design-system.service.gov.uk/patterns/confirm-an-email-address/
- Canonical: `govuk-design-system:patterns/confirm-an-email-address`；維護者 GOV.UK Design System team；類別：帳號啟用／聯絡管道確認；原文發表日及最後更新日未核實；2026-10-28 取得官方正文（156行）。
- 閱讀軌跡：`AUTO73-S01-R1-MAIN-TEXT-C1`。逐節讀官方「When to use」「How it works」「Set expiry conditions」「Let users resend」「Blocking or non-blocking」「Designing the activate your account page」及結尾研究/回饋段落。**一次主要正文文字閱讀，不等於完成嚴格 R1**。
- 官方原則：只有當電子郵件為必要功能通道、或錯誤信箱可能使他人取得敏感資訊時才適用確認迴圈；確認僅證明當時可存取信箱，**不證明本人身分**。確認連結需有效期，且用過、被新連結取代或改信箱時應失效；應提供重寄、修正信箱與明確說明。阻斷式驗證可能讓無法收信者完全不能繼續，非阻斷式又需處理未完成確認的狀態。
- 反例 C1（身份混淆）：治療所個案可存取某共用家庭信箱，並不代表該信箱持有人就是個案本人，亦不代表可收取心理治療或收據敏感內容；確認信箱 ≠ 本人核驗 ≠ 授權收件。
- 反例 C2（阻斷風險）：若把所有現場 Session/Billing 登錄都綁定個案完成 email loop，無信箱或無法即時收信者可能無法接受合法服務；反過來完全略過核對又可能誤寄敏感文件。需依實際傳送用途分層，而不是全系統一刀切。
- 反例 C3（歷史資料）：聯絡信箱更改後，歷史已寄送文件及收件稽核不應被當前欄位值覆蓋；Notion 一個 Email 欄位無法單獨證明何時、由誰核准寄送。需區分現在可用地址、寄送事件與歷史證據。
- 反證界線：此為英國政府網站設計模式，不證明 Notion 原生支援郵件驗證、token 失效、稽核或角色權限；不建議本輪實作。

## AUTO73-S02｜Confirm a phone number – GOV.UK Design System
- URL: https://design-system.service.gov.uk/patterns/confirm-a-phone-number/
- Canonical: `govuk-design-system:patterns/confirm-a-phone-number`；維護者 GOV.UK Design System team；類別：簡訊安全碼／帳號登入；發表與修訂日期未核；2026-10-28 取得官方正文（487行）。
- 閱讀軌跡：`AUTO73-S02-R1-MAIN-TEXT-C1`。逐節讀「When to use」「How it works」「When user creates an account」「When user signs in」「Domain-bound codes」「Error messages」「Technical security measures」「Research on this pattern」「Next steps」，並閱讀頁內 HTML/Nunjucks 程式碼文字及錯誤範例；**同篇不同範例不額外計篇或複讀**。
- 官方例示：以簡訊安全碼增加登入或高風險操作的驗證層，需告知號碼用途、可重寄、碼逾期處理、失去裝置的恢復途徑及防自動化攻擊。官方示例採5位碼與15分鐘有效期，且指出部分號碼遮蔽顯示仍待更多研究；**示例參數不應視為臺灣治療所可直接採用的安全規格**。
- 反例 C1（共用與失去設備）：個案或心理師的手機可能共用、遺失或換號；能收到簡訊不代表對特定個案病歷、Billing 或政府補助資料有權限。把手機號碼當唯一識別碼或權限依據可能導致跨人存取。
- 反例 C2（工作中斷）：若每次更新 Session 都強制簡訊驗證，訊號不良、海外漫遊或無障礙需求可能阻斷高頻行政作業；但完全不做風險分級又可能使高敏感動作欠缺額外核對。需依風險與使用者實測決定，不能把安全與操作效率簡化為同一個開關。
- 反例 C3（碼與錯誤回饋）：前端錯誤訊息可幫助理解逾期/格式錯誤，但不能代替伺服器端驗證、限速、監測與恢復；在 Notion 頁面放置說明文字更不能聲稱已有 OTP/MFA。
- 反證界線：GOV.UK HTML/JS、後端驗證與 Notion 原生功能不可等同；沒有實際 SMS 發送、無障礙、鍵盤、行動裝置、臺灣電信或角色測試；不建立登入或簡訊功能。

## 跨來源反證、計量及安全界線
- 本輪新增來源候選2篇、主要正文文字閱讀2篇、首次獨立反例2組6情境、既有來源完整複讀0；嚴格完整 R1=0，R2–R10=0；本輪 `FULL_DEEP_PASS_10_OF_10=0`，累積可核實仍 **0/10,000篇**。
- 核心推論：**聯絡管道控制 ≠ 身分證明 ≠ 角色授權 ≠ 業務資格核准；前端驗證體驗 ≠ 後端安全控制。** 兩篇均非直接 Notion 功能說明，不能當成已核准的產品實作。
- 未測：官方圖示與互動示例的實際呈現、鍵盤/讀屏/手機、真人可用性、Notion實帳權限、簡訊與信件傳送、登入、安全防護、歷史收費、補助規則、Formula、效能及全庫同文異址去重。
- 本輪只允許 GitHub 研究文件寫入；**不修改 Notion 正式/TEST 頁面、資料庫、View、Formula、Relation、權限、業務資料，亦不修改 GAS/Cloud Run/Session/部署**。研究門檻未達，未進入重新設計；自動與手動研究可並行。
