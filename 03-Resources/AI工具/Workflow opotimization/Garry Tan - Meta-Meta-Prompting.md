---
date: 2026-05-10
tags:
  - AI工具
  - agent
  - 個人知識管理
source: https://x.com/garrytan
author: Garry Tan（Y Combinator CEO）
---
整理
# Meta-Meta-Prompting：讓 AI Agent 真正運作的秘密

## 核心架構：Fat Skills, Thin Harness

| 層 | 說明 |
|----|------|
| **Thin Harness**（薄外殼） | 只負責路由，不含業務邏輯。OpenClaw / Hermes Agent |
| **Fat Skills**（厚技能） | 100+ 個 markdown 技能檔，每個專注一件事 |
| **Fat Brain**（厚資料） | 100,000 頁結構化知識庫，每人、每會議、每本書各有一頁 |
| **Models**（可替換） | Opus 4.7 1M（精準）、GPT-5.5（召回）、DeepSeek V4-Pro（創意） |

**關鍵原則：模型是引擎，技能與資料才是車。**

---

## 三個核心應用

### 1. Book Mirror（書籍鏡像）
- 對每個章節跑子 agent，同時做兩件事：
  1. 摘要作者觀點
  2. 將每個觀點映射到自己的實際生活（引用真實腦頁）
- 輸出：雙欄格式，左欄作者觀點、右欄個人對應
- 品質保障：跨模型交叉評估（cross-modal eval）抓事實錯誤

### 2. Meeting Prep（會議準備）
- 自動拉取：對方的腦頁、公開立場、傳記重點、個人相關紀錄
- 輸出：不只是事實整理，還有「對話切入角度」
- 效果：2 分鐘內完成完整準備包

### 3. Skillify（元技能）
- 發現重複工作流程 → 說「skillify this」
- 系統自動：提取可重複模式 → 寫成技能檔 → 註冊進 resolver
- 技能可組合：book-mirror 呼叫 brain-ops、enrich、cross-modal-eval、pdf-generation

---

## Brain 的資料結構

每頁格式：
1. **Compiled Truth**（頂部）：當前最佳理解
2. **Append-only Timeline**（時間軸）：事件按時序記錄
3. **Raw Data Sidecars**：原始來源資料

覆蓋對象：人物、公司、會議、書籍、文章、想法

---

## 複利邏輯

- 每次會議 → 更新相關人物與公司頁
- 每本書 → 第 20 本鏡像知道前 19 本的內容
- 每個技能改進 → 所有使用該技能的工作流同步受益
- 100 個 cron jobs 每天 24/7 自動更新

---

## 如何開始

1. **選擇一個薄外殼**：OpenClaw、Hermes Agent 或自建
2. **用 GBrain 建立腦庫**：一個指令安裝，39 個內建技能
3. **先做一件真實的事**：不要先規劃架構，先做，再 skillify
4. **持續使用 + 看輸出**：用 cross-modal eval 找錯，把修正烤進技能

---

## 開源資源

- **GStack**：程式技能框架（87,000+ stars）
- **GBrain**：知識基礎設施 + 技能包
- **OpenClaw / Hermes Agent**：執行環境
- GitHub: `github.com/garrytan/gbrain`
