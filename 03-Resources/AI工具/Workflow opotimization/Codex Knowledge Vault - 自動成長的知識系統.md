---
date: 2026-05-10
tags:
  - AI工具
  - agent
  - 個人知識管理
author: 未知（X 上流傳）
---

# Codex Knowledge Vault：每天自動變聰明的知識系統

## 核心問題：Context Debt（上下文債務）

每次新對話都從零開始，AI 不知道你的歷史、技術棧、目標。
不斷重新解釋自己 = 生產力稅。

解法：從「聊天視窗」轉向「持久知識層」。
Obsidian vault 不是圖書館，是 AI 助理的大腦。

---

## 5 層神經結構

| 層 | 檔案/資料夾 | 定位 |
|----|------------|------|
| 全局變數 | `AGENTS.md` | AI 第一個讀的主檔。你是誰、2026 目標、不可違反規則 |
| 暫存區 | `inbox/` | 所有新內容先丟這，無需手動分類 |
| 知識庫 | `notes/` | 處理過的事實、API schema、研究摘要（個人維基） |
| 原創思維 | `ideas/` | **最重要**。你獨特的邏輯與觀點，防止 AI 給通用答案 |
| 工作區 | `projects/` | 進行中的工作，緊鄰 notes/ 讓 AI 即時引用舊知識 |

**關鍵原則：為機器組織，不為人類組織。**

---

## 被動擷取：讓管道做工作

### X（Twitter）書籤自動化
```
Navigate to my X Bookmarks.
Extract content of every thread saved in last 24 hours.
Strip ads and engagement bait.
Convert core insights to Markdown: YYYY-MM-DD-X-Insights.md
Save to /inbox.
```

### YouTube 待看清單自動化
```
Access YouTube 'Watch Later' list.
For every video added today, pull full transcript.
Summarize the technical 'How-To' or 'Big Idea'.
Save individual Markdown files to /inbox.
```

---

## 每日 / 每週自動進化

### 每日進化 Prompt（Daily Brief）
三個動作：
1. **記憶強化**：從新內容識別需要內化的技術模式
2. **策略轉移**：新資訊是否暗示更好的執行方式？標記矛盾點
3. **立即行動**：今天最高槓桿的任務是什麼？→ 存入 `DAILY-BRIEF.md`

### 每週自我管理 Prompt（Firmware Upgrade）
三個動作：
1. **新興論點**：這週掌握了什麼高階技能或概念？
2. **架構演化**：重組資料夾以反映當前理解層次
3. **韌體升級**：重寫 `AGENTS.md` 的核心邏輯，整合本週所學

---

## Freshman Rule：準確優於自信

隨著 vault 成長，agent 會走捷徑。防止方法：

- **引用來源**：技術決策必須連結到 `/notes` 中的具體檔案，沒有就承認在猜
- **Plan-First**：動手前先寫 3 句「作戰計畫」，基於 `AGENTS.md`
- **禁止假設**：任務與 3 個月前的筆記矛盾時，停下來問人，不要自作聰明

---

## 和 Garry Tan 方案的對比

| 面向 | Garry Tan（GBrain） | 本文（Codex Vault） |
|------|-------------------|-------------------|
| 工具 | 自建 OpenClaw + GBrain | Obsidian + Codex |
| 資料量 | 100,000 頁 | 從小開始 |
| 自動化 | 100+ cron jobs | Computer Use 抓書籤 |
| 技能系統 | Skillify 元技能 | Prompt 模板 |
| 適合對象 | 工程師，願意自建系統 | 一般使用者，低門檻入門 |
