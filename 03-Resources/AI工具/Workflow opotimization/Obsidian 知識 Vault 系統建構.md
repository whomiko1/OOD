---
date: 2026-05-10
tags:
  - AI工具
author: "@cyrilXBT"
source: ""
---

# How to Build an Obsidian Knowledge Vault That Gets Smarter Every Day

## 核心論點

大多數 Obsidian vault 是「輸入設計」、沒有「輸出設計」——只有 inbox，沒有 feedback loop，最終淪為有好資料夾的墳場。真正的第二大腦需要自動回饋：資訊流入、Claude 連結、洞察每日浮現。

## 系統架構（四層）

| 層 | 工具 | 功能 |
|----|------|------|
| 捕獲層 | Readwise、Airr、Whisper、Telegram Bot | 自動收集，零手動分類 |
| 管道層 | N8N | 自動路由到正確 Obsidian 資料夾 |
| 儲存層 | Obsidian | 永久儲存，markdown 本地存檔 |
| 智能層 | Claude | 連結、模式識別、每日簡報 |

## 五資料夾結構

```
Inbox/     → 所有自動捕獲的暫存區
Notes/     → 處理後的文章、highlight、Podcast clip
Ideas/     → 自己的思考、語音轉錄
Projects/  → 進行中的專案
CLAUDE.md  → Claude 的上下文指令檔
```

## 關鍵實踐

- **每日簡報**：N8N 每天早上 6 點讓 Claude 讀近 24 小時 inbox + 近 7 天 notes，輸出「3 個連結 + 1 個模式 + 1 個值得思考的問題」到 inbox
- **每週合成**：15 分鐘與 Claude 對話——找浮現的論點、矛盾點、知識盲區、本週最高槓桿行動
- **CLAUDE.md**：根目錄必備，記錄身份、現有專案、vault 結構、對 Claude 的期望，每週一更新

## 複利效應

- 1 個月：實用工具
- 3 個月：Claude 開始連結 8 週前遺忘的筆記
- 6 個月：有一份完整的思想演變紀錄

## 待研究

- [ ] N8N × Telegram Bot 建立流程
- [ ] Readwise Obsidian 原生整合設定
- [ ] 每日簡報 N8N prompt 實作
