# AUTO-153｜Notion Forms：表單欄位同步與公開收件的資料治理邊界（僅研究）

- Trace: AUTO-153-20261123-1742-FORMS-SCHEMA-SHARING
- 標題：Forms — Notion Help
- canonical URL: https://www.notion.com/help/forms
- 來源：Notion 官方 Help；查閱日期：2026-11-23；官方頁面本輪取得約368行，正文L107–L281。
- 去重：docs/notion/sources.md 已有 AUTO-90，明示 AUTO-01 已登錄 canonical notion-help:forms；**不是新來源**。本輪只計同一來源一次新的針對性部分複讀，不計完整深讀R1–R10；全歷史逐輪稽核尚未完成。
- 研究方法：獨立核對表單建立、欄位名稱同步、分享及匿名、回應權限、資料匯出與自動化段落。未進行逐節十遍完整閱讀、未播放影片、未實測Notion。

## 本次核對的官方規則

1. 表單題目對應資料庫 property，題目名稱預設與 property 名稱同步；修改問題文字可能同時更改資料庫欄位名稱，可關閉 Sync with property name（官方正文L168–L189）。
2. 從既有資料庫建立表單需 Full access；編輯表單需 Can edit 或 Full access；更改表單分享設定需 Full access（L141–L163、L196–L205）。
3. 「Anyone on the web with link」允許外部人提交，且這種表單回覆者預設匿名；匿名不能等同身份已驗證（L208–L235）。
4. 對內部回覆者可設定提交後 No access / Can view / Can comment / Can edit / Full access；這是回覆頁的後續權限，不能當成全部資料庫的角色隔離證據（L218–L227）。
5. 複製別人的模板後，官方提醒重新建立表單以避免回覆流向原模板作者；Form view 不能直接匯出，需從 Table view 匯出（L237–L259）。
6. 大量回覆可能影響載入速度；表單可掛自動化，但自動化的實際權限、可用方案與失敗通知須另外驗證（L245–L273）。

## 本輪新增待驗反例（研究假說，不代表系統已發生）

1. 行政改表單題目文案，意外同步改名既有補助欄位，讓其他 View/整合依欄名查找失敗。
2. 公開表單可提交，但沒有可核實身份，錯將匿名申請當成資格已確認。
3. 以為表單「No access」保證個案資料安全，卻未稽核其他分享連結、來源資料庫與回覆頁權限。
4. 複製外部模板後未重設表單，真實回覆誤送原作者的資料庫。
5. 只試 Form view 匯出失敗，誤判歷史資料不存在或不能備查。
6. 表單收件成功即認定補助 Session/Price Plan 關聯及期別皆正確，未查實際資料庫寫入與人工資格。
7. 高量表單回覆使工作台載入變慢，卻只用少量合成紀錄宣稱效能 PASS。
8. 表單自動化失效後沒有告警，行政仍把「已送出」等同後續通知／分流完成。

## 嚴格計數與範圍

- 本輪新唯一來源：0（已存在 canonical）。
- 本輪新的針對性部分複讀：1（AUTO-153，與 AUTO-90 非同一次）；完整深讀：0；待驗反例：8。
- 全歷史唯一來源及閱讀輪次尚未完成全量稽核，**不增加任何可核實10/10篇數**；保守累積0／10,000。
- 本文件只記研究。未修改Notion頁面、資料庫、View、公式、權限、正式GAS、Cloud Run、Session；未開始重新設計。
- 參照：docs/notion/sources.md、README.md、AGENTS.md、docs/system/source-of-truth.md、docs/notion/AGENTS.md、docs/notion/decision-log.md、docs/notion/acceptance-status.md、docs/notion/research/README.md及最近AUTO-152。
