# Everyone AI Agent 市场

面向产品经理的 AI Agent 插件与技能市场。在 Claude Code、Codex 及任何支持插件或技能的 AI Agent 中，发现、安装和分享产品效率工具。

> **为什么叫 "everyone"？** 因为，人人都是产品经理 — 本市场专为产品人员打造。

## 快速开始

### 方式一：Plugin 系统（Claude Code、Codex 等）

适用于支持插件市场协议的 Agent：

**Claude Code：**
```sh
/plugin marketplace add https://github.com/nixihz/everyone.git
/plugin install everyone@everyone-pm
```

**Codex：**
```sh
plugin marketplace add https://github.com/nixihz/everyone.git
plugin install everyone@everyone-pm
```

### 方式二：Skill 直装（任意 AI Agent）

如果你的 Agent 不支持插件系统，可以直接使用 Skills：

```sh
# 使用 npx（推荐）
npx skills add plugins/everyone/skills/prototype-ascii

# 或将 SKILL.md 文件复制到 Agent 的 skills 目录
```

每个 Skill 都是一个独立的 `SKILL.md` 文件 —— 无需构建，任何 AI Agent 都能直接读取。

## 测试安装

```sh
# 方式一：手动执行
claude plugin uninstall everyone@everyone-pm
claude plugin marketplace remove everyone-pm

claude plugin marketplace add `pwd`
claude plugin marketplace update everyone-pm
claude plugin install everyone@everyone-pm

# 方式二：使用 Taskfile（推荐）
task test
```

## 已注册插件

| 插件 | 描述 |
| ---- | ---- |
| everyone | 面向 AI Agent 的产品经理效率工具集 —— 线框图、原型设计、工作流自动化 |

### everyone 插件详情

**依赖要求**

- 无

**MCP 服务器**

- 无

**LSP 服务器**

- 无

**Agent Skills**

| Skill | 描述 |
| ----- | ---- |
| prototype-ascii | ASCII 线框图设计工具，用于快速创建 UI 原型 |
| prd | 生成、更新、评审和维护需求文档（PRD、用户故事、范围说明书、验收标准） |
| llm-wiki | 增量构建和维护基于 Markdown 的本地 LLM Wiki，实现知识的持续编译与沉淀 |

### prototype-ascii 使用方法

当用户请求"原型设计"、"线框图"或"wireframe"时使用此技能。

```
# 示例：登录页面线框图
┌─────────────────────────────────┐
│                                 │
│         ┌─────────────────┐     │
│         │     Login       │     │
│         └─────────────────┘     │
│                                 │
│  ┌──────────────────┐           │
│  │ Username         │           │
│  └──────────────────┘           │
│                                 │
│  ┌──────────────────┐           │
│  │ Password         │           │
│  └──────────────────┘           │
│                                 │
│        [ Login ]                │
│                                 │
│    No account? [Register] →     │
│                                 │
└─────────────────────────────────┘
```

使用方式：在对话中描述 UI 需求，技能会自动生成 ASCII 线框图。

### prd 使用方法

当用户需要起草、更新或评审产品需求文档时使用此技能。支持 PRD、用户故事包、范围说明书、验收标准和需求评审，采用 Atlassian 风格的 Markdown 格式。

示例任务：
- "为登录功能写一份 PRD"
- "评审这份需求文档有哪些缺失"
- "把这些笔记整理成用户故事"
- "根据新的设计决策更新 PRD"

### llm-wiki 使用方法

当用户希望构建或维护一个持续编译的知识库时使用此技能。支持摄入原始资料、查询已有知识、检查知识库中的漏洞或矛盾、以及更新 wiki 结构规范。

示例任务：
- "把这些文章摄入到我的 wiki"
- "从 wiki 中总结我们关于 X 的知识"
- "检查 wiki 中是否有过时或矛盾的内容"
- "更新 schema，让新页面遵循这个结构"

## 开发新插件与技能

### 插件结构

每个插件需要放在 `plugins/<plugin-name>/` 下，至少包含：

```
my-plugin/
├── .claude-plugin/
│   └── plugin.json       # 必需：插件清单
├── commands/             # 可选：斜杠命令
├── agents/               # 可选：Agent 定义
├── skills/               # 可选：Skills（独立的 SKILL.md 文件）
├── hooks/                # 可选：Agent 事件钩子
├── .mcp.json             # 可选：MCP 服务器
└── .lsp.json             # 可选：LSP 服务器
```

Skill 是最通用的格式 —— 任何 AI Agent 都能读取 `SKILL.md` 文件，无论是否支持完整的插件协议。

开发完成后，让 AI 优化一版：

```
参照 https://code.claude.com/docs/en/plugins-reference，检查并修复插件问题。
```

## 参考

- 创建插件 https://code.claude.com/docs/en/plugins-reference#skills
- 发布市场 https://code.claude.com/docs/en/plugin-marketplaces
- 从市场安装插件 https://code.claude.com/docs/en/discover-plugins#add-from-other-git-hosts
- Skills https://code.claude.com/docs/en/skills


```
┌────────────────────────────────────────────────────────────────────────┐
│  Strategy Management Center                          [Admin] (JD)      │
├────────────────────────────────────────────────────────────────────────┤
│                                                                        │
│  ┌────────────────────────────────────────────────────────────────────┐│
│  │  Strategy Query                                                    ││
│  └────────────────────────────────────────────────────────────────────┘│
│                                                                        │
│  Strategy Name                                                         │
│  ┌─────────────────────────────────┐                                   │
│  │ Enter strategy name...          │                                   │
│  └─────────────────────────────────┘                                   │
│                                                                        │
│  Status                  Strategy Type            Created At           │
│  ┌──────────────┐       ┌──────────────┐       ┌──────────────┐        │
│  │ All Status  ▾│       │ All Types   ▾│       │ Select Date ▾│        │
│  └──────────────┘       └──────────────┘       └──────────────┘        │
│                                                                        │
│        [ Search ]    [ Reset ]                                         │
│                                                                        │
├────────────────────────────────────────────────────────────────────────┤
│                                                                        │
│  ┌────────────────────────────────────────────────────────────────────┐│
│  │  Strategy List                              [+ New Strategy]       ││
│  └────────────────────────────────────────────────────────────────────┘│
│                                                                        │
│  ┌────────┬─────────────┬──────────┬──────────┬───────────┬─────────┐  │
│  │ □      │ Strategy    │ Strategy │ Status   │ Created   │ Actions │  │
│  │        │ Name        │ Type     │          │ At        │         │  │
│  ├────────┼─────────────┼──────────┼──────────┼───────────┼─────────┤  │
│  │ ☑      │ User Profile│ Audience │ (12) [On]│ 2026-03-01│[Edit]   │  │
│  │        │ Strategy    │ Package  │          │           │[Delete] │  │
│  ├────────┼─────────────┼──────────┼──────────┼───────────┼─────────┤  │
│  │        │ Interest    │ Tag      │ (8) [On] │ 2026-02-28│[Edit]   │  │
│  │        │ Preference  │          │          │           │[Delete] │  │
│  ├────────┼─────────────┼──────────┼──────────┼───────────┼─────────┤  │
│  │        │ Behavior    │ Algorithm│ (3) [Pause]│2026-02-25│[Edit]  │  │
│  │        │ Analysis    │          │          │           │[Delete] │  │
│  ├────────┼─────────────┼──────────┼──────────┼───────────┼─────────┤  │
│  │        │ Conversion  │ Model    │ (5) [Draft]│2026-02-20│[Edit]  │  │
│  │        │ Prediction  │          │          │           │[Delete] │  │
│  └────────┴─────────────┴──────────┴──────────┴───────────┴─────────┘  │
│                                                                        │
│  ◀  1  2  3  ...  10  ▶      Total 86    20 per page                   │
│                                                                        │
└────────────────────────────────────────────────────────────────────────┘
```
