# AUTO-106｜2026-11-21 14:42（Asia/Taipei）｜Sharing & permissions 獨立針對性複讀

- 執行標記：AUTO-106-20261121-1442-SHARING-PERMISSIONS-TARGETED-REREAD；研究與GitHub紀錄限定，無Notion/正式系統寫入。
- 官方原文：https://www.notion.com/help/sharing-and-permissions
- 標題：Sharing & permissions settings；canonical：notion-help:sharing-and-permissions；官方Notion Help，原文日期未標示，2026-11-21讀取。
- 去重：docs/notion/sources.md 已有 AUTO97-S01（2026-10-29）相同canonical，**新增唯一來源0**；本次為不同日期的獨立針對性複讀，不能計為完整R2。
- 可讀範圍：官方HTML文字第107–382行（含主文與FAQ）重新逐節查核；嵌入影片、圖片、實機、角色帳號及無障礙未查，**完整深讀0次**。

## 官方事實與治療所反證

1. General access 可設定 Everyone at workspace 或 Anyone on web with link（L182–196）。反例：Session/個案工作台被設成整個workspace可見，即使僅對特定心理師分享入口，也不等於資料隔離；需查實際share規則。
2. Can edit content 可編輯資料庫內頁面及屬性值，但不可改資料庫結構、views、sorts、filters（L197–212）。反例：心理師不能改View，仍可能編輯被授權的收費或會談屬性；操作權與欄位保密是不同控制。
3. Can create 僅Business/Enterprise，且不代表可查看其他未單獨授權的資料庫列（L206–207）。反例：將Can create視為可查閱自己過去Session，會造成查詢中斷。
4. Page-level access 僅Business/Enterprise；person-property規則跨所有原庫與linked views生效（L233–260）。反例：在linked view加filter不會成為獨立存取控制；同一Session其他入口仍需權限查核。
5. 無原庫權限而僅有單筆page權限者，直接進原庫可能報錯，須通知或具授權的linked view入口（L267–293）。反例：只交付原庫網址，心理師可能無法進入自己已授權的會談。
6. Notion採最寬鬆權限；工作區Full access可蓋過person-property限制（L295–297、L314–317）。反例：原設計限定只看本人Session，卻因workspace授權而能讀到他人個案。
7. 父頁移入Private不會自動移除子頁先前個別授權（L309–323）。反例：管理者誤以為收回父工作台就撤銷所有臨床子頁權限。
8. Anyone with link頁面在其他較廣分享頁的mention、雙向relation或巢狀結構中可能被找到（L319–324）。反例：跨方案Relation可能意外擴大敏感頁面可發現性；必須實際驗證而非假定關聯本身安全。

## 計量與限制

- 新唯一URL：0；既有來源獨立針對性文字複讀：1；新增具體反例：8；本輪嚴格完整閱讀：0；本輪10/10完成：0。
- 最近已記錄的累積10/10基準為0/10,000；本次未全量驗證全部歷史檔案，不冒稱即時精確總數。
- 以上反例為研究測試假說，非本所真實權限或資料外洩已證實；沒有執行實機權限測試。
- 本次未修改Notion頁面、資料庫、View、公式、權限、GAS、Cloud Run、Session，也未開始重新設計。
