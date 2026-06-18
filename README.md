# Everyone AI Agent Marketplace

AI Agent plugin & skill marketplace for product managers. Discover, install, and share PM-focused plugins and skills across Claude Code, Codex, and any AI agent that supports them.

> **Why "everyone"?** Because everyone is a product manager - this marketplace is built for product people.

📖 [中文文档](docs/zh-CN.md)

## Quick Start

### Option 1: Plugin System (Claude Code, Codex, etc.)

For agents that support the plugin marketplace protocol:

**Claude Code:**
```sh
/plugin marketplace add https://github.com/nixihz/everyone.git
/plugin install everyone@everyone-pm
```

**Codex:**
```sh
codex plugin marketplace add https://github.com/nixihz/everyone.git
codex plugin add everyone@everyone-pm
codex plugin add product-design@everyone-pm
```

### Option 2: Direct Skills (Any AI Agent)

If your agent does not support plugins, you can use skills directly:

```sh
# Using npx (recommended)
npx skills add plugins/everyone/skills/prototype-ascii

# Or copy SKILL.md files to your agent's skills directory
```

Each skill is a self-contained `SKILL.md` file - no build step required.

## Test Installation

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

For the Claude-only smoke test, you can also run `task test`.

## Registered Plugins

### Claude Code Marketplace

| Plugin | Version | Source | Description |
| ------ | ------- | ------ | ----------- |
| everyone | 0.1.0 | Everyone PM | Product manager productivity toolkit for AI Agents - wireframing, prototyping, research, and workflow automation |

### Codex Marketplace

| Plugin | Version | Source | Description |
| ------ | ------- | ------ | ----------- |
| everyone | 0.1.0 | Everyone PM | Product manager productivity toolkit for AI Agents - wireframing, prototyping, research, and workflow automation |
| product-design | 0.1.42 | Codex official by OpenAI | OpenAI Product Design plugin for Codex - explore, audit, and prototype product ideas |

### everyone Plugin Details

**Dependencies**

- None

**MCP Servers**

- None

**LSP Servers**

- None

**Agent Skills**

| Skill                  | Description                                                                          |
| ---------------------- | ------------------------------------------------------------------------------------ |
| prototype-ascii        | ASCII wireframe design tool for rapid UI prototyping                                 |
| prd                    | Generate, update, review, and maintain requirement documents (PRD, user stories, scope, acceptance criteria) |
| llm-wiki               | Incrementally build and maintain a Markdown-based local LLM Wiki for persistent knowledge compilation |
| social-signal-research | Build source-backed X/Twitter research packets for PM decisions                      |

### prototype-ascii Usage

Use this skill when the user requests "prototype design", "wireframe".

```
# Example: Login page wireframe
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

Usage: Describe your UI requirements in the conversation, and the skill will automatically generate an ASCII wireframe.

### prd Usage

Use this skill when the user needs to draft, update, or review product requirement documents. Supports PRD, user story packs, scope statements, acceptance criteria, and requirement reviews in Atlassian-style Markdown.

Example tasks:
- "Write a PRD for the login feature"
- "Review this requirement doc for gaps"
- "Convert these notes into user stories"
- "Update the PRD with the new design decisions"

### llm-wiki Usage

Use this skill when the user wants to build or maintain a continuously compiled knowledge base. Supports ingesting raw material, querying existing knowledge, linting for gaps, and updating the wiki schema.

Example tasks:
- "Ingest these articles into my wiki"
- "What do we know about X from the wiki?"
- "Check the wiki for stale or contradictory content"
- "Update the schema so new pages follow this structure"

### social-signal-research Usage

Use this skill when a product manager needs X/Twitter conversation evidence for demand, objections, customer language, competitor chatter, or launch messaging.

Example tasks:
- "Research X/Twitter signals for developer complaints about unreliable webhooks"
- "Find customer language around AI research assistants for PMs"
- "Compare competitor complaints before we test this positioning"

### product-design Plugin Details

Product Design is an official Codex plugin by OpenAI. This marketplace currently ships the upstream `0.1.42` version through `.agents/plugins/marketplace.json` and keeps its Codex plugin manifest at `plugins/product-design/.codex-plugin/plugin.json`.

Example Codex tasks:
- `@Product Design Help me get started`
- `@Product Design Turn this product idea into three visual directions`
- `@Product Design Clone this URL into an editable prototype`

## Developing Plugins and Skills

Each plugin should live under `plugins/<plugin-name>/`. Use the manifest that matches the agent ecosystem you want to support:

```text
my-plugin/
├── .codex-plugin/
│   └── plugin.json       # Codex plugin manifest
├── .claude-plugin/
│   └── plugin.json       # Claude Code plugin manifest
├── commands/             # Optional slash commands
├── agents/               # Optional agent definitions
├── skills/               # Optional skills with SKILL.md files
├── hooks/                # Optional agent event hooks
├── .mcp.json             # Optional MCP servers
└── .lsp.json             # Optional LSP servers
```

Codex marketplace entries are declared in `.agents/plugins/marketplace.json`. Claude Code marketplace entries are declared in `.claude-plugin/marketplace.json`.

## References

- Create plugins https://code.claude.com/docs/en/plugins-reference#skills
- Publish marketplace https://code.claude.com/docs/en/plugin-marketplaces
- Install from marketplace https://code.claude.com/docs/en/discover-plugins#add-from-other-git-hosts
- Skills https://code.claude.com/docs/en/skills
