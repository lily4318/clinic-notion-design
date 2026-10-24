# 資料分級、業務安全與稽核

## 原則

1. 預設拒絕、明確允許，查詢或驗證失敗 fail-closed。
2. **每支業務 API** 在後端重新驗證 Staff、角色、permission、資源範圍；前端隱藏按鈕不算授權。
3. API 只回頁面必要 View Model，不輸出 raw Notion page／properties、非必要 Database ID、原始錯誤。
4. 最小化敏感資料讀取、傳輸、快取、記錄；高風險寫入需稽核、冪等、LockService 或等效鎖、追蹤與復原。
5. Token、Secret、Script Properties、Cookie、完整個資、財務明細、raw stack trace 不進前端、對話、Log、Patch 或 GitHub；瀏覽器不得直接叫正式 GAS，不存敏感資料至 localStorage／sessionStorage。
6. Notion／使用者文字進 DOM 優先 textContent、createElement、安全 template；禁止未處理的直接 innerHTML。
7. 正式文字採台灣個資法、心理師法、病歷保存等適切脈絡，不保留不適用的 HIPAA 或原型品牌。

## 資料分級

| 等級 | 示例 | GitHub |
|---|---|---|
| L0 Public | 公開文案 | 可以 |
| L1 Internal | 不含個資的設計／營運摘要 | 經審查後可以 |
| L2 Confidential | 姓名、電話、Email、預約 | 不得 |
| L3 Highly Confidential | 病歷、財務、收據、薪資、完整服務歷程 | 不得 |
| L4 Restricted | Token、Secret、Script Properties、部署驗證資料、raw stack trace | 不得；也不可回前端 |

Audit 最少包含 requestId、correlationId、actorStaffId、actorRoleSnapshot、action、targetType、targetId、result、reason、redactedBefore、redactedAfter、errorCode、timestamp。不得記完整 Token、身分證、地址或 stack trace。
