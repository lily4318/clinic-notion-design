# Notion 深度學習｜AUTO-22｜Library、People profiles、Notion Agent（2026-10-26）

> 執行軌跡：`AUTO-22-20261026-1335`。本輪只讀取公開研究資料並更新 GitHub 研究／索引；未讀取或修改 Notion 真實業務資料，未變更任何 Notion 頁面、資料庫、View、公式、權限或正式 GAS／Cloud Run／Session。仍在研究階段，**未開始重新設計**。

## 0. 起始基準與防重稽核

- 開始前已從私人儲存庫 `lily4318/clinic-notion-design` 的 `main` 重新取得根 `README.md`、`AGENTS.md`、`docs/system/source-of-truth.md`、`docs/notion/AGENTS.md`、`docs/notion/sources.md`、`decision-log.md`、`acceptance-status.md`；亦取得 `docs/notion/research/` 當期目錄、首批 evidence register、十面向研究、批次02–04、MANUAL-01、AUTO-01～21研究紀錄，核對候選文章的 help slug。
- 已排除既有 `/help/search`、`/help/navigate-with-the-sidebar`、`/help/customize-your-sidebar`、`manage-sidebar-presets-for-your-workspace` 及 NN/g `recognition-and-recall`，不重複計新篇。後三篇中的 sidebar presets 亦見 AUTO-08。下列三篇在本次讀取的清冊與逐檔 slug 核對中未發現先前同篇；跨歷史所有未索引材料的全域去重總數仍待獨立稽核。
- 本輪 canonical key 以官方 help slug 為準，去掉語系前綴（`/en-gb/` 等）、query、fragment；**同一 URL 不因語系或多種觀點而變成多篇**。每篇只計一個文字閱讀與一個首次反例分析，不把同一篇的多段落當成多輪。
- 外部來源於 2026-10-26 取得可讀主要正文。三篇頁面未提供可核實的逐篇最後更新日期，故一律記 `published_or_updated=UNKNOWN`；不以網站 crawl 時間代替發表日期。

## 1. AUTO22-S01｜Manage your Library

- **URL**：https://www.notion.com/en-gb/help/manage-your-library
- **canonical**：`notion-help:manage-your-library`；**標題**：Manage your Library；**作者／類型**：Notion 官方 Help；**領域**：導覽、搜尋、資訊架構、誤刪風險。
- **本輪實讀覆蓋**：文章主要正文 web 行 106–170；逐節讀取「How to access Library」「Customise your sidebar」「What you’ll see in the Library」「Find pages faster」「Manage multiple pages at once」。正文短，未逐張解讀示意圖片及實際登入測試。狀態 `R1 / MAIN_BODY_READ + INDEPENDENT_COUNTEREXAMPLE_1`，**不是** `FULL_DEEP_PASS`。
- **原始主張**：Library 可按 Teamspaces、Recents、Favourites、Shared、Private 等分區瀏覽，搜尋頁名與過濾；側欄隱藏某區後仍能從 Library 找到；Library 可批次移動、刪除頁面、移除收藏與修改圖示。
- **假設**：只要把治療所首頁項目從側欄移除，便等同於該項已不存在，且能安全批次清理。
- **反例 A**：移除側欄區塊僅改導覽顯示，Library 仍能存取；對使用者明確要求「真正刪除」的舊設計，隱藏並不符合要求。反之，批次刪除頁面會對真實內容產生破壞，不能把導覽整理當成批次刪除授權。
- **反例 B**：Recents/Favourites 取決於個人使用情境，不能證明所有角色看到同一組任務入口。只靠 Library 搜尋會增加必須記住頁名的負擔；使用者要求的「同類資料同頁直接顯示」不能以搜尋入口取代。
- **更新認識**：側欄可見性、頁面實體存在、實際權限、批次刪除是四種不同操作；本輪僅作辨識，**沒有對治療所頁面提出已核准變更**。
- **待核**：圖片逐張、手機與桌機、批次移動後子頁權限、角色差異、實際操作步數；第2–10次完整閱讀未執行。

## 2. AUTO22-S02｜People profiles

- **URL**：https://www.notion.com/en-gb/help/people-profiles
- **canonical**：`notion-help:people-profiles`；**標題**：People profiles；**作者／類型**：Notion 官方 Help；**領域**：成員可見性、隱私、跨裝置差異。
- **本輪實讀覆蓋**：文章主要正文 web 行 106–163；逐節讀取「View someone's profile」「Update your profile」「Turn off hover cards and people profiles for a workspace」。未實際使用成員／訪客帳號，也未逐張分析示意圖片。狀態 `R1 / MAIN_BODY_READ + INDEPENDENT_COUNTEREXAMPLE_1`，非完整深讀。
- **原始主張**：People profiles 對所有方案的 workspace **members** 可用，**mobile 不可用**；guests 無法檢視或使用這些 member profile/hover card；成員個人檔案可能顯示主要協作者、所屬 Teamspaces、近期活動。Workspace owner 可在 General/People 關閉 Profiles 或 Hover cards。
- **假設**：將心理師資料欄設為 Person，就能以所有裝置一致、所有角色一致的方式呈現成員資訊，且 Person 屬性本身可作為安全邊界。
- **反例 A**：member/guest 可用性不同，mobile 又不支援 profile；如果日常流程仰賴 hover card 查詢，手機和訪客情境會失效。
- **反例 B**：檔案中的團隊、近期活動等資訊可見性與業務紀錄的資料存取權不是同一件事；不能因能看見成員 profile 就推論可看見其個案或財務紀錄，亦不能把 hover card 當作職務授權證明。
- **更新認識**：區分「人員身分展示」與「角色／資料存取權限」，也要分開驗證桌面與手機；目前未判定本所實際啟用狀態或是否有隱私問題。
- **待核**：真實 workspace 的角色權限、顯示內容、設定權益、示意圖片、mobile 版本；第2–10次未執行。

## 3. AUTO22-S03｜Notion Agent

- **URL**：https://www.notion.com/en-gb/help/notion-agent
- **canonical**：`notion-help:notion-agent`；**標題**：Notion Agent；**作者／類型**：Notion 官方 Help；**領域**：AI協作、權限、內容變更、文件一致性。
- **本輪實讀覆蓋**：正文 web 行 106–360，包含「How to work」「What your Agent can do」「What your Agent can't do」「Personalise」「Switch chat mode」「Pin」「Chat history」「Feedback」與 FAQs。部分非PDF嵌入及影片未播放，所有外部整合、付費權益與真人操作未測。狀態 `R1 / MAIN_BODY_AND_FAQ_READ + INDEPENDENT_COUNTEREXAMPLE_1`，非完整深讀。
- **原始主張**：個人 Notion Agent 使用提問者自己的內容權限；可讀資料庫、在授權範圍內建立或編輯頁面／部分資料庫設定、協助分析；不能變更分享權限或工作區層級設定，也不能建立新 database automations、templates、layouts 或 advanced properties（如 formulas/rollups/buttons）。若 Agent 指示頁允許其他人編輯，其他人可能改變其後續行為。
- **假設**：只要有 Notion Agent，就能無需核實地自動維護補助資料模型，且其權限／功能與先前研究的共享 Custom Agents 完全相同。
- **反例 A（角色邊界）**：本篇說個人 Notion Agent 依提問者權限，AUTO-18 的共享 Custom Agents 則有其獨立授權主體；兩類 Agent 不可混用推論。即使 Agent 有建立資料庫 View 的能力，也不代表它能核准政府補助或保證業務唯一性。
- **反例 B（指示頁供應鏈）**：如果多位工作人員可編輯 Agent 的指示頁，其中一位的變更可能改變其他人後續對 Agent 的預期；「指示文件可見」不等於「指示不會被修改」。
- **來源內部張力（需後續確認）**：正文在能力段落寫 `Create, edit, and evaluate formulas`（web 行256），但限制段落緊接寫 `can't create ... advanced properties like formulas`（web 行263）。可能是在說編輯既有公式與建立新公式屬不同操作，但原文用詞不足以確定全部能力邊界。登記 `SOURCE_INTERNAL_AMBIGUITY`，不得自行選取其中一句宣稱公式可自動建立或修改。
- **更新認識**：個人 Agent／共享 Custom Agent、資料查詢／正式寫入、建議／核准、可編輯指示／受控規格是不同維度。這是研究結論，**不表示本所已啟用 Notion Agent，也未要求變更任何業務頁面**。
- **待核**：官方能力矛盾後續修訂、方案權益、模型費用、影片、真實跨角色權限、實際公式操作、變更記錄；第2–10次未執行。

## 4. 交叉反證與嚴格進度

- Library 可找回側欄隱藏的內容，但不代表真正刪除；People profiles 是成員協作顯示，不是資料授權；Notion Agent 可依權限操作資料，但不能當成法規判斷或跨系統交易完整性的保證。
- 新增候選且經當期清冊與 slug 交叉查核的獨立官方文章：**3篇**；每篇一輪可讀正文閱讀與新反例：**3次**；本輪既有文章的獨立完整複讀：**0次**；本輪達成10/10完整深讀：**0篇**。
- **累積可稽核10/10達標仍 0／10,000篇**。全域唯一來源精確總數未完成跨所有檔案完整機器去重，故不提供虛構總數。圖片、影片、付費實帳、權限、手機操作與效能均未完整驗證。
- 沒有對 Notion、GAS、Cloud Run、Session、業務資料、頁面、資料庫、View、Formula、Relation 或權限進行任何寫入；沒有開始重新設計。手動與排程可同時繼續，但須共享 main 最新 SHA 並避免重複。
