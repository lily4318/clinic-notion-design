# AUTO-104｜2026-11-21 11:42｜Notion Formula 條件、列表與自動化語義（僅研究）

Trace: AUTO-104-20261121-1142-FORMULA-EXAMPLES-TARGETED-REREAD

## 前置核對與去重
- 寫入前重新讀取 main 七份規範／索引及 SHA：README.md @ 51c750119a207e195b675f0613f43cbde9956d67; AGENTS.md @ e541f9d79fcb7a28126f70ebafe290ad0bc349b6; docs/system/source-of-truth.md @ a26ac4c914f3e5e853464d9f0515033f2e3d62c0; docs/notion/AGENTS.md @ c0fe2c5eadd92877643d8ef1c06574115729cd01; docs/notion/sources.md @ 4cb54a075ad9243054d899ec715ca2a68140dd80; docs/notion/decision-log.md @ 6c56f39c37c79421c8f5689d50d045793be86627; docs/notion/acceptance-status.md @ f1cfc159492f119d95753230c7e91e4d702ef13b。
- 官方來源：[Intro to formulas | Notion Help](https://www.notion.com/help/formulas)；canonical `notion-help:formulas`；已於 sources.md 的 AUTO-13 登錄，**新唯一來源 0**。本輪不同於 AUTO-103 的資料庫入門來源。
- 閱讀事件 `AUTO104-R-20261121-1142-FORMULAS-107-258-PARTIAL`：獨立重新開啟 Notion 官方原文，逐節閱讀主文 L107–258（公式用途、日期與狀態、list length、RICE分數、子項目自動化、編輯器預覽、Notion AI限制、語法構成）。頁面共347行含導覽與頁尾；圖片、可複製模板、外鏈公式函數全集及實際執行均未完整閱讀，故僅**針對性文字複讀1次**，不計嚴格完整R2。

## 具體官方證據與獨立反例
1. L128–132：`dateAdd`、`now`、`if(and(...))` 與 `length()` 分別操作日期、狀態條件及列表長度。反例：把 Sessions Relation 的 `length()` 當成有效補助次數，會連取消／改期等不占額狀態一併計入；此為需另驗的業務反例。
2. L143–144：RICE 範例使用除法。反例：若行政績效公式分母為0或未填，直接套用示例無法保證輸出具業務意義；必須另定未知、已確認0、不適用的語義，未測原生結果。
3. L159–163：自動化示例以 `Parent item.first()` 取得首個關聯、`every(current.Status == "Done")` 判斷子項目，並對空子項目明確返回 false。反例：在多方案或多期別關聯中使用 `first()` 選 Price Plan 可能錯配核定期；若未先處理空列表，不能把 `every()` 結果直接解讀為已完成審核。
4. L199–208：編輯器對單列提供即時預覽。反例：單筆預覽通過不證明跨年度方案、歷史價格、所有 Session 狀態或角色權限正確。
5. L216–246：Notion AI 輔助公式限 Business/Enterprise，且不支援迭代邏輯、隨機產生或記住先前提示。反例：AI 生成的公式不能視為已經逐筆測試的跨期額度計算或可稽核的規則版本。
6. L175–185：公式可在資料庫欄位、按鈕及自動化動作使用。反例：同一公式表達式可用於不同介面，不代表其執行時機、授權與寫入效果一致；不能以欄位公式的唯讀預覽替代自動化交易驗收。

## 計數與限制
- `NEW_UNIQUE_SOURCE=0`; `TARGETED_INDEPENDENT_PARTIAL_REREAD=1`; `NEW_COUNTEREXAMPLE=6`; `STRICT_FULL_READ_THIS_RUN=0`; `FULL_10_OF_10_THIS_RUN=0`。
- 依最近可核實 acceptance-status 基準，完整10/10累積仍 **0/10,000**；全歷史同文異址／語義去重未完成，未重做全量統計。
- 全部反例是研究推論，未驗本所 Notion 原生公式值、角色、跨期 Session/Billing、效能、真人 UX。**RESEARCH ONLY**：不改 Notion 頁面、DB、View、Formula、權限、GAS、Cloud Run、Session；不進入重新設計。
