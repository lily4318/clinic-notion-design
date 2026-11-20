# AUTO-98｜2026-11-21｜Notion 欄位權限原文研究

Trace: AUTO-98-20261121-0544-PROPERTY-ACCESS

- 既有來源 N07，canonical URL https://www.notion.com/help/database-property-access ，標題 Manage database property access，Notion Help，2026-11-21 取得；無明示更新日期。與既有清冊同URL，**新增唯一來源0**。
- 當次讀取網站全文321行，實際研究主文 L107–244，包含設定前提、設定程序、權限級別、Person欄位例外、規則交互、限制及疑難排解。外部連結與嵌入媒體未全部深入查核，僅認列既有來源主文核讀一次，**不計嚴格完整深讀 R1–R10**。

## 原文核對

1. L114–146：僅 Business/Enterprise，需 Full access；網頁/桌面設定，最多20個受控欄位，必須從原資料庫而非 linked view 設定。
2. L147–169：區分只看欄名、看值、編輯及無權限；Person欄位動態例外可能顯示欄名而不顯示值。
3. L170–181：Full access 不受欄位限制；不能靠欄位規則開啟原本無權限的頁面；多例外取最寬鬆；受限欄位篩選的 View 可能無法開啟；版本還原不回復過去欄位權限。
4. L182–224：Title、ID、建立編輯者與時間、部分同步欄、父子項關聯不可限制；大量欄位規則可能影響速度；按鈕、automation、formula、rollup 可能因權限失效。

## 六個未實測反例

- CE1：僅隱藏收費欄卻讓心理師擁有 Full access，仍可見財務值。
- CE2：同時屬於寬鬆和嚴格群組，最寬鬆例外造成不預期揭露。
- CE3：Session View 依受限欄位篩選，對特定角色無法開啟，誤以為無會談。
- CE4：回復舊頁版本後誤以為欄位權限也回復，實際沿用當前規則。
- CE5：把敏感資料放在 Title 或父子項關聯，期待欄位限制而失敗。
- CE6：受限角色的 Rollup/Formula/按鈕失效，被誤判為資料遺失而修改業務列。

## 研究口徑與邊界

NEW_UNIQUE_URL=0；EXISTING_SOURCE_MAIN_TEXT_REVIEW=1；COUNTEREXAMPLE=6；FULL_R1=0；FULL_R2_TO_R10=0；NEW_10_OF_10=0。依最新 AUTO-97 登錄，累積嚴格達標仍0/10000，尚未完成所有歷史語義去重。Notion 本所方案、角色、資料、View、原生公式、手機與真人UX、效能及回復均 NOT_TESTED。沒有任何 Notion 或 GAS/Cloud Run/Session 寫入；研究不足，不進入重新設計。
