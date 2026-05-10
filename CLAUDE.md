## 專案概述
這是一個 Obsidian 知識管理 vault，使用 Templater 和 Dataview 插件。
語言：繁體中文為主，英文用於代碼、命令、變量名。

## 目錄結構（什麼放哪）
```
Daily Notes/     → 每日筆記，檔名格式 YYYY-MM-DD.md
Books/           → 書籍閱讀筆記
Meetings/        → 會議記錄
Projects/        → 副業 / 長期項目追蹤
03-Resources/    → 工具教程、參考資料（子資料夾依主題命名）
Templates/       → 模板，不直接放內容，僅供 Templater 引用
```

## 命名規範
- Daily Notes：`YYYY-MM-DD.md`（例：`2026-05-10.md`）
- 書籍：`書名.md`
- 會議：`YYYY-MM-DD 會議主題.md`
- 專案：`專案名稱.md`
- 資源筆記：`主題描述.md`，放入對應子資料夾

## Frontmatter 規範
每份筆記必須有 frontmatter，依類型套用對應欄位：

| 類型 | 必填欄位 |
|------|---------|
| 所有筆記 | `date`, `tags` |
| 書籍 (`#book`) | + `author`, `rating`, `status: reading/done` |
| 專案 (`#project`) | + `status: active/done`, `deadline` |
| 會議 (`#meeting`) | 無額外欄位 |
| 每日 (`#daily`) | 無額外欄位 |

## Tags 規範（Dataview 依賴這些 tag 運作）
- `#daily` — 每日筆記
- `#book` — 書籍
- `#project` — 專案
- `#meeting` — 會議
- `#dashboard` — 儀表板（排除在 Dataview 一般查詢外）
- `#AI工具` — AI 工具相關資源

## 模板使用
新增筆記時，優先套用 Templates/ 下對應模板，保持欄位一致性。
- Templater 語法：`2026-05-10` 等，Claude 修改模板時不要破壞這些語法。
- Dataview 查詢塊（\`\`\`dataview ... \`\`\`）只能讀取，不要手動填入 Dataview 塊的內容。

## 操作紅線
- 不刪除任何筆記，除非我明確指定檔名並確認
- 不修改 Templates/ 下的模板，除非我明確要求
- 不更動 .obsidian/ 資料夾（插件設定）
- 不重構目錄結構，除非先出方案讓我確認

## 常用任務
- **新增資源筆記**：在 03-Resources/ 對應子資料夾下建立，加正確 frontmatter
- **整理資料**：幫我摘要、重新格式化既有筆記內容，保留原始資料夾位置
- **搜尋內容**：用 Grep 在 vault 內搜尋關鍵字
