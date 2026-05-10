---
date: 2026-05-10
tags:
  - AI工具
  - multi-agent
  - 框架
source: https://github.com/lidangzzz/goal-driven/blob/main/readme_cn.md
---

# Goal-Driven 多智能體框架

## 核心概念

框架由四個元素構成：

| 元素 | 角色 |
|------|------|
| **Goal（目標）** | 系統的最終任務目標 |
| **Criteria（標準）** | 判定任務完成的明確條件 |
| **Subagent（子智能體）** | 持續執行問題求解 |
| **Master Agent（主智能體）** | 監督流程、評估是否達成 Criteria |

## 運作方式

啟動後，Master Agent 建立 Subagent 並指示其持續朝 Goal 推進。Master Agent 週期性地：
1. 檢查 Subagent 的活動狀況
2. 評估是否已滿足 Criteria
3. 條件達成才允許流程結束

## 適用場景

高度複雜、耗時、邏輯密集、但**可被明確評估成功與否**的任務：
- 編譯器設計
- 數學定理證明
- 資料庫架構設計
- 系統級設計挑戰

## 實際案例

| 項目 | 耗時 |
|------|------|
| 用 C++ 實作 TypeScript 編譯器 | 約 100 小時 |
| 用 Rust 實作 SQLite | 約 30 小時 |

## 注意事項

- 會消耗大量時間與 LLM tokens，使用前需確認有足夠的 API 資源
- 核心設計原則：目標導向 + 可驗證的完成標準，缺一不可
