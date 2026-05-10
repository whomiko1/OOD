---
tags:
  - AI工具
  - 教程
source: 微信公众号·卡兹克
date: 2026-05-10
---

# 从0开始，在国内用上 Claude Code 的终极保姆教程

> 作者：卡兹克（tashi）
> 核心观点：Claude Code 是目前最好的 Agent 框架，即使不用 Claude 原生模型，搭配国产模型效果也很好，且不需要外国手机号、Visa 卡，甚至不需要魔法。

---

## 一、安装 Claude Code

### 1. Mac

#### 有魔法
```bash
curl -fsSL https://claude.ai/install.sh | bash
```
安装后若提示 `~/.local/bin` 未加入 PATH，按提示执行输出的 `echo` 命令，再验证：
```bash
claude --version
```

#### 无魔法（用 Homebrew）

**Step 1 — 安装 Homebrew**
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
按提示回车，等待完成后将 Homebrew 加入路径变量（按终端输出的命令执行）。

**Step 2 — 安装 Claude Code**
```bash
brew install --cask claude-code@latest
```
> 注意：公众号排版会破坏格式，建议手敲或让 AI 修正后再粘贴。

安装完成后输入 `claude` 验证。

---

### 2. Windows

#### 前置条件：安装 Git
Claude Code 在 Windows 上依赖 Git Bash 执行命令，必须先装 Git。
```powershell
winget install Git.Git
```

#### 有魔法
```powershell
irm https://claude.ai/install.ps1 | iex
```

#### 无魔法
```powershell
winget install Anthropic.ClaudeCode
```

安装完成后输入 `claude` 验证。

---

## 二、接模型

> 有 Claude 账号可直接登录，以下为国内无账号的通用方案。

推荐使用 **CC Switch** 工具来管理和切换模型，比单独接一个模型更灵活。

### 1. Mac — 安装 CC Switch
```bash
brew tap farion1231/ccswitch
brew install --cask cc-switch
```

### 2. Windows — 安装 CC Switch
从 GitHub Releases 下载安装包：
```
https://github.com/farion1231/cc-switch/releases
```
（无法访问 GitHub 则回复公众号关键词 `cc` 获取本地安装包）

下载后双击一路 Next 安装完成。

### 3. 配置模型（Mac/Windows 相同）

1. 打开 CC Switch
2. 在 Claude 栏点右上角 **+**，新增模型配置
3. 选择模型（示例：GLM 国内版）
4. 填写 **API Key** 和模型名称（其他字段自动填充）
5. 点击右下角 **添加**

> 推荐国产模型：GLM-5.1（效果最接近 Claude Opus 4.6）、MiniMax M2.7、Kimi K2.5

---

## 三、启动 Claude Code

```bash
claude
```

**首次启动初始化流程：**
1. 选择颜色主题（之后可用 `/theme` 修改）
2. 阅读安全提示（回车确认）
3. 启用推荐终端设置（换行快捷键 + Visual Bell 提醒）
4. 确认当前目录信任（选择"是"）

**切换模型：**
在 CC Switch 配置好后，在 Claude Code 内执行 `/model` 切换。

---

## 四、日常使用技巧

### 跳过权限确认（推荐开发时使用）
```bash
claude --dangerously-skip-permissions
```

### 进入指定项目目录启动
```bash
cd /path/to/your/project   # 或直接把文件夹拖进终端
claude
```
> 在项目目录下启动可减少上下文污染，让模型更专注、更聪明。

---

## 五、写 CLAUDE.md（重要）

### 什么是 CLAUDE.md
从上到下分层穿透的约束体系：
- **全局** `~/.claude/CLAUDE.md` — 所有项目都生效，定义你是谁、协作原则
- **项目** `项目目录/CLAUDE.md` — 只在该项目生效，定义具体约定

> 长度控制：超过 80 行开始遗漏，**绝对不超过 200 行**。

### 全局 CLAUDE.md 模板

```markdown
## 关于我
[你的名字 / 身份 / 职业背景，非程序员的话一定要写出来]。
我用 Claude Code 做 [具体用途 1] 和 [具体用途 2]。

## 思维原则
所有决策从问题本质出发，不因「惯例如此」照搬。
回到问题本身：要解决什么？最直接的路径是什么？从零设计会怎么做？
不要谄媚。不要夸我的想法好、不要说「这是个很好的问题」、不要开头加「当然可以」。
给我真实判断，方案有问题直接指出来。发现更好的做法直接说，不用等我问。

## 约束先行
无论开发项目还是知识管理项目，第一步永远是建规则：新项目先写 CLAUDE.md，新目录先定结构约定（什么放哪、怎么命名、何时清理）。
没有规范的工作空间不动手。已有规范的项目，严格遵守其 CLAUDE.md 中的约定。需要调整规范时先改文档、再改实践，不要反过来。

## 沟通方式
- 默认中文，代码、命令、变量名用英文
- 结论先行，再给理由，不要先铺垫背景
- 遇到模糊需求，先给最合理的方案，再问要不要调整
- 不要问「你确定要这样吗」，除非命中下方红线

## 自主边界（红线，必须先问我）
以下操作即使在 auto-accept 模式下也必须停下来问我：
- 删除文件、目录或 git 历史
- 修改 .env、密钥、token、CI/CD 配置
- 数据库 schema 变更或数据迁移
- git push、git rebase、git reset --hard、强制推送
- 安装新的全局依赖或修改系统配置
- 公开发布（npm publish、部署到生产、发文章等）

## 通用工程纪律
- 改完主动跑验证（具体命令见各项目 CLAUDE.md），不要只改不验
- 不要为了让代码跑起来注释掉报错或加绕过标记，找根本原因
- 密钥、token、密码不进代码、不进 commit、不进日志
- 大改动前先在 Plan Mode 出方案，我确认后再动手
```

### 项目 CLAUDE.md
不需要自己写，直接在项目目录下打开 Claude Code，把需求和关注点告诉它，让它生成一份即可。

---

## 相关链接
- CC Switch Releases: https://github.com/farion1231/cc-switch/releases
- 智谱 GLM 一键配置：`npx @z_ai/coding-helper`
