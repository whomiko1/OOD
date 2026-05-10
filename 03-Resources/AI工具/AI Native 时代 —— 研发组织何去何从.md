---
date: 2026-05-08
tags:
  - AI工具
author: 阿里技术
source: https://www.bestblogs.dev/article/8c2c877a
---

# AI Native 时代 —— 研发组织何去何从

## 摘要

文章基于作者在阿里内部的访谈调研和行业观察，系统分析了 AI 对研发组织的深层影响。

核心论点：
- AI 不是新工具，而是新协作主体，其特性与人类形成镜像反面
- 组织形态将从 Org Chart 演变为 Execution Graph，最小单元从「人+关系网」变为「任务+上下文+权限+工具」
- 新瓶颈是「信息形态的人形偏置」——员工沦为「人肉中间件」
- 管理塌缩不是管理消失，是管理重新选择位置
- Architect 是新组织的最高杠杆点
- 「Death of ego」有边界：三类工作（执行/优化/创新）需不同治理方式

## 主要内容

**1. AI 不是新工具，而是新协作主体**
人有沟通衰减、需要激励、会疲劳、有上下文切换成本、记忆有限；AI 在这些方面恰好相反。导致过去围绕「人形约束」设计的组织原则（康威定律、人月神话）开始失效。

**2. 从 Org Chart 到 Execution Graph**
当 AI 能行动、调用工具、执行 workflow 时，公司不再能被 org chart 描述，而变成把人、Agent、数据、权限、工具当作同等节点的活的网络。核心问题从「谁拥有」变为「意图如何路由和治理」。重组成本可从季度级压至周级。

**3. 新瓶颈：信息形态的人形偏置**
系统为人设计而非为 AI 设计，信息隐性化、非结构化、缺失。员工需要手动从各系统导出数据、复制粘贴进 AI、再把输出搬回业务系统，成为「人肉中间件」。

**4. 管理塌缩**
十项管理职能命运分化：战略传导等可被系统替代，重大决策下沉到 DRI，激励、辅导、文化建设不可替代。新角色 **Architect** 是最高杠杆点，负责将组织隐性 know-how 翻译成 AI 可消化形态。

**5. Platform 三柱架构**
- 柱 1 · Agent Platform Group：runtime 标准、权限、日志、可观测、评估 harness、安全部署
- 柱 2 · Domain Teams：3-5 人垂直功能小组，对结果负责
- 柱 3 · Risk and Oversight：免疫系统，不是官僚刹车

**6. Death of ego 有边界**
- 执行类：杀防御性 ego，全透明
- 优化类：抑制 ego，留批判空间
- 创新类：保护半成形想法，维护生产性 ego
- 一刀切 = 执行高效 + 创新死亡

---

## 全文

### 前言

我们最近做了一份内部访谈，问几位深度使用 AI 的工程师"你日常时间分配的变化"：
- 写代码的占比：30% → 5%
- 和 Agent 对话的占比：5% → 60%
- 查问题的时间下降一半以上
- 纯编码效率提升 10 倍，但端到端需求交付效率只提升 2 到 3 倍

更值得停下的是节奏：一个工程师上午 10 点上线新功能、中午做 A/B 测试、下午 3 点根据数据下线、5 点上线更好的版本。同一天。这是过去 6 周才能完成的迭代。

### 01 两千年的协调问题史

组织演化持续了两千年，本质都在解决同一件事：**信息怎么路由**。

罗马军团把军队拆成嵌套结构；1806 年普鲁士建立"总参谋部"，这是中层管理的雏形；1840 年代美国铁路画出世界上第一张组织架构图。两千年里有一件事没变：组织演化的核心约束是人的"管理跨度"（3-8 人）。

### 02 组织的形态来自哪里：人的镜像

- 康威定律：模块边界不可避免地与团队边界重合
- 人月神话：沟通成本随人数指数增长
- 专业岗位：人的注意力是稀缺资源
- manager 评价制：员工产出不可观测，让「信息上最近的人」代理评估

这些都是人这个生物的协作物理学。

### 03 AI 不是新工具，是新协作主体

AI 的特点正好和人形成镜像反面：
| 人类 | AI |
|------|-----|
| 沟通衰减 | 无衰减 |
| 需要激励 | 不需要 |
| 会疲劳有情绪 | 没有 |
| Context switching 成本高 | 极小 |
| 记忆和注意力有限 | 几乎无限 |

真正 AI Native 团队的共同形态：
- **底层 Harness 层**：代码、测试、流水线、文档，越结构化越好，AI 主导
- **上层 Hive Mind 层**：对话、试错、idea 涌现，越松散越好，人主导

### 04 从 Org Chart 到 Execution Graph

"Once AI becomes agentic, the organization stops being accurately described by an org chart. It becomes an execution graph." — Ken Huang

- 旧问题：ownership（谁拥有这件事？）
- 新问题：routing + governance（意图如何路由？什么约束让行动是安全的？）

组织最小单元从「人+关系网」变为「任务+上下文+权限+工具」，重组成本从季度级压到 week 级。

### 05 人既是瓶颈，也是兜底

人既是协作的瓶颈，也是协作的兜底。

整个研发系统长期容忍大量不规范、不结构化、不完整的信息，只要人足够聪明、勤奋、熟悉，缺陷不会上升为瓶颈。当 AI 接管执行之后，AI 没有"猜"和"问老王"的能力，需要结构化、可查询、可执行、确定性的信息。

**新瓶颈的真相**：不是 AI 能力不够，是系统的信息形态不够。

### 06 新瓶颈：信息形态的人形偏置

AI 友好的 5 个维度：
1. 测试完备性
2. 环境完备性
3. 架构合理性（无循环依赖、无跨服务隐式调用）
4. 端到端测试可执行性
5. 文档充分性

Harness 复利：一旦跑起来，AI 接管的工作越多，失败信号越丰富，Harness 优化得越快。早建好 Harness 的公司会在某个临界点之后突然加速。

#### 6.1 管理塌缩

十项管理职能的命运分化：
- **可被系统替代**：战略传导、信息聚合、资源协调、日常决策
- **形态在变**：重大决策（下沉到 DRI）、冲突调解（总量随团队变小减少）
- **不可替代**：激励、辅导、招聘退出、文化建设
- **新出现**：意图教练、身份重建、虚无对抗

**Architect** = 把组织隐性 know-how 翻译成 AI 可消化形态的人。一个 Architect 的产出会被 N 个 agent 复用。

**Agent 作为新员工类别**：需要 onboarding、scoping、supervision、offboarding，但有四个危险不对称：可被无限复制、同时 brilliant 又 brittle、compliance-blind by default、fast enough to fail at scale。

#### 6.2 Platform 三柱架构

- **柱 1 · Agent Platform Group**：中央团队，runtime 标准、权限、日志、可观测、评估 harness、安全部署
- **柱 2 · Domain Teams**："Own outcomes rather than models"，3-5 人垂直功能小组
- **柱 3 · Risk and Oversight**："An immune system rather than a bureaucratic brake"

6 项基本功：枚举 agents、权限纪律、梯度自治、日志、评估 harness、事故响应。

#### 6.3 三类工作 / 三种治理

| 工作类型 | ego 治理方式 |
|---------|------------|
| 执行类 | 全透明，杀防御性 ego |
| 优化类 | 抑制 ego，留批判空间 |
| 创新类 | 保护半成形想法，维护生产性 ego |

**生产性 ego 的价值**：困难问题需要数月级持续注意力、凌晨 2 点的执着、在公开场合显得愚蠢的勇气——AI 当前架构上做不到，transformer 是 stateless 的。

### 07 三个案例

1. **先锋**：3-5 人小团队按垂直功能划分，沟通从需求评审驱动转向成果评审驱动，决策权与开发权分离
2. **全员**：普通员工已大量用 AI，但还卡在「人肉中间件」阶段
3. **反例**：可见性 ≠ 被看见。代码 commit 都在（可见性）但管理者没在汇报里念名字（没有被看见）

### 08 转型的真实代价

三个问题：

**培养断裂**：旧路径 day 1 写简单代码 → 设计系统 → 定战略，新路径里这条线断了。入门级岗位可能消失；全行业不招 day 1，三五年后 senior 池开始枯竭。

**蒸馏焦虑**：员工意识到「我说的越多被替代得越快」，关键知识开始藏匿，Harness 工作无法完成。

**行业级负反馈环**：senior 池被慢慢消耗、Architect 储备越来越薄，整个行业的判断力被同步抽空。

### 09 还没解决的

1. AI 的信任度（高风险环节人工审核跟不上）
2. 绩效评价体系失效（旧依据失效，新依据未建立）
3. 3-5 人小团队是临时最优还是终态
4. AI 知识资产继承（员工调教好的 agent，人走时怎么办）

### 10 几条关键判断

1. Harness 工作是组织未来速度的复利本金，早晚投入差距是指数级
2. AI Native 转型不是又一次 reorg，是让组织未来不再需要痛苦的 reorg
3. 解决 Architect 的激励问题：给身份、给权力、给资源
4. 分辨节点类型：执行节点全透明 + 死防御性 ego；创新节点保护性环境 + 维护生产性 ego
5. 开始做 agent 名册，你不可能治理你叫不出名字的东西

---

## References

1. Jack Dorsey & Roelof Botha, *From Hierarchy to Intelligence*, Block Inside, March 2026
2. Melvin E. Conway, *How Do Committees Invent?*, Datamation, April 1968
3. Frederick P. Brooks Jr., *The Mythical Man-Month*, Addison-Wesley, 1975
4. Ken Huang, *What is an Agentic AI Native Organization?*, Substack, February 2026
5. Peter Pang, *Why Your "AI-First" Strategy Is Probably Wrong*, X (Twitter), April 2026
6. Steve Yegge, *The Anthropic Hive Mind*, Medium, February 2026
