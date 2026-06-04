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
codex plugin marketplace add https://github.com/nixihz/everyone.git
codex plugin add everyone@everyone-pm
codex plugin add product-design@everyone-pm
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

### Claude Code

```sh
claude plugin uninstall everyone@everyone-pm
claude plugin marketplace remove everyone-pm

claude plugin marketplace add "$(pwd)"
claude plugin marketplace update everyone-pm
claude plugin install everyone@everyone-pm
```

### Codex

```sh
codex plugin remove everyone@everyone-pm || true
codex plugin remove product-design@everyone-pm || true
codex plugin marketplace remove everyone-pm || true

codex plugin marketplace add .
codex plugin add everyone@everyone-pm
codex plugin add product-design@everyone-pm
```

Claude Code 的快速冒烟测试也可以直接运行 `task test`。

## 已注册插件

### Claude Code Marketplace

| 插件 | 版本 | 来源 | 描述 |
| ---- | ---- | ---- | ---- |
| everyone | 0.1.0 | Everyone PM | 面向 AI Agent 的产品经理效率工具集 —— 线框图、原型设计、工作流自动化 |

### Codex Marketplace

| 插件 | 版本 | 来源 | 描述 |
| ---- | ---- | ---- | ---- |
| everyone | 0.1.0 | Everyone PM | 面向 AI Agent 的产品经理效率工具集 —— 线框图、原型设计、工作流自动化 |
| product-design | 0.1.42 | OpenAI Codex 官方 | OpenAI Product Design Codex 插件 —— 探索、评审并实现可交互产品原型 |

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

### product-design 插件详情

Product Design 是 OpenAI 出品的 Codex 官方插件。当前 marketplace 集成的是上游 `0.1.42` 版本，通过 Codex marketplace 清单 `.agents/plugins/marketplace.json` 发布，并保留 Codex 插件清单 `plugins/product-design/.codex-plugin/plugin.json`。

示例任务：
- `@Product Design Help me get started`
- `@Product Design Turn this product idea into three visual directions`
- `@Product Design Clone this URL into an editable prototype`

## 开发新插件与技能

### 插件结构

每个插件需要放在 `plugins/<plugin-name>/` 下，至少包含：

```
my-plugin/
├── .codex-plugin/
│   └── plugin.json       # Codex 插件清单
├── .claude-plugin/
│   └── plugin.json       # Claude Code 插件清单
├── commands/             # 可选：斜杠命令
├── agents/               # 可选：Agent 定义
├── skills/               # 可选：Skills（独立的 SKILL.md 文件）
├── hooks/                # 可选：Agent 事件钩子
├── .mcp.json             # 可选：MCP 服务器
└── .lsp.json             # 可选：LSP 服务器
```

Skill 是最通用的格式 —— 任何 AI Agent 都能读取 `SKILL.md` 文件，无论是否支持完整的插件协议。

Codex marketplace 条目维护在 `.agents/plugins/marketplace.json`，Claude Code marketplace 条目维护在 `.claude-plugin/marketplace.json`。

开发完成后，让 AI 优化一版：

```
参照 https://code.claude.com/docs/en/plugins-reference，检查并修复插件问题。
```

## 参考

- 创建插件 https://code.claude.com/docs/en/plugins-reference#skills
- 发布市场 https://code.claude.com/docs/en/plugin-marketplaces
- 从市场安装插件 https://code.claude.com/docs/en/discover-plugins#add-from-other-git-hosts
- Skills https://code.claude.com/docs/en/skills
