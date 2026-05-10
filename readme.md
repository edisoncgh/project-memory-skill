# Project Memory Skill

> Maintain persistent project-level memory across AI coding sessions — never lose context again.

---

## What It Does

Project Memory gives AI coding assistants a **persistent memory system** stored as markdown files in `.memory/` at the project root. It tracks:

- **Session history** — one file per conversation turn, tagged and searchable
- **Long-term knowledge** — architecture decisions, user preferences, conventions, patterns
- **Working context** — active files, pending tasks, blockers, next steps

This means after a break, the AI can recall exactly where you left off — what files you were editing, what decisions you made, what you were about to do next.

## Core Capabilities

| Capability | Description |
|---|---|
| Session Recall | At session start, reads index + context + knowledge, summarizes prior state |
| Vibe Coding Mode | Every 3-5 turns, auto-saves working state for long iterative sessions |
| Tag-Based Search | Sessions indexed with tags (`#auth`, `#bug`, `#decision`, `#vibe-coding`) |
| Auto-Pruning | When >20 sessions, oldest 5 archived into knowledge and removed |
| Template-Driven | Structured `.memory/` layout ensures consistency across sessions |
| Privacy-Aware | Never stores API keys, passwords, tokens, or secrets |

## Memory Layout

```
.memory/
├── index.md                  # Session index with summaries and tags
├── knowledge.md              # Long-term knowledge, decisions, preferences
├── context.md                # Current working state snapshot
└── sessions/
    ├── 20260209-143022.md    # Per-turn session files
    └── ...
```

## When to Use

Add this skill to your AI coding tool (Claude Code, OpenCode, Cursor, etc.) when:

- Working on multi-session, multi-turn development tasks
- Doing "vibe coding" — iterative, conversational development
- You want the AI to remember project conventions and decisions
- You frequently switch between features and need context continuity
- You need to recall "what did we decide about X?" across sessions

## Quick Start

1. Copy `project-memory/` into your AI tool's skills directory
2. In your first session with a project, say: "Initialize project memory"
3. The AI creates `.memory/` and starts tracking
4. From then on, the AI reads memory at session start automatically

---

# Project Memory Skill（项目记忆技能）

> 跨 AI 编程会话维护持久化的项目级记忆 — 再也不会丢失上下文。

---

## 它能做什么

Project Memory 为 AI 编程助手提供了一个**持久化记忆系统**，以 markdown 文件形式存储在项目根目录的 `.memory/` 中。它追踪：

- **会话历史** — 每个对话轮次一个文件，带标签、可搜索
- **长期知识** — 架构决策、用户偏好、编码约定、常用模式
- **工作上下文** — 当前活动文件、待办任务、阻塞项、下一步计划

这意味着休息回来后，AI 能准确回忆起你上次做到哪了 — 在编辑哪些文件、做了什么决定、接下来准备做什么。

## 核心能力

| 能力 | 说明 |
|---|---|
| 会话回溯 | 会话开始时读取索引 + 上下文 + 知识，总结之前的状态 |
| 氛围编程模式 | 每 3-5 轮自动保存工作状态，适配长时间迭代式开发 |
| 标签搜索 | 会话按标签索引（`#auth`、`#bug`、`#decision`、`#vibe-coding`） |
| 自动归档 | 会话超过 20 个时，最早 5 个自动归档到知识库并移除 |
| 模板驱动 | 结构化的 `.memory/` 布局确保跨会话一致性 |
| 隐私保护 | 绝不存储 API 密钥、密码、令牌或机密信息 |

## 记忆目录布局

```
.memory/
├── index.md                  # 含摘要和标签的会话索引
├── knowledge.md              # 长期知识、决策、偏好
├── context.md                # 当前工作状态快照
└── sessions/
    ├── 20260209-143022.md    # 每轮会话文件
    └── ...
```

## 适用场景

将此技能添加到你的 AI 编程工具中（Claude Code、OpenCode、Cursor 等），当你：

- 进行多会话、多轮次的开发任务
- 进行"氛围编程"——迭代式、对话式开发
- 希望 AI 记住项目约定和决策
- 经常切换功能模块，需要上下文连续性
- 需要跨会话回溯"我们在 X 上做了什么决定？"

## 快速开始

1. 将 `project-memory/` 复制到你的 AI 工具 skills 目录
2. 在项目的首个会话中说："初始化项目记忆"
3. AI 会创建 `.memory/` 并开始追踪
4. 此后，AI 会在此后每次会话启动时自动读取记忆
