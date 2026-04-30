# Everyone AI Agent Marketplace

AI Agent plugin & skill marketplace for product managers. Discover, install, and share PM-focused plugins and skills across Claude Code, Codex, and any AI agent that supports them.

> **Why "everyone"?** Because everyone is a product manager — this marketplace is built for product people.

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
plugin marketplace add https://github.com/nixihz/everyone.git
plugin install everyone@everyone-pm
```

### Option 2: Direct Skills (Any AI Agent)

If your agent does not support plugins, you can use skills directly:

```sh
# Using mpx (recommended)
mpx skills add plugins/everyone/skills/prototype-ascii

# Or copy SKILL.md files to your agent's skills directory
```

Each skill is a self-contained `SKILL.md` file — no build step required.

## Test Installation

```sh
# Method 1: Manual
claude plugin uninstall everyone@everyone-pm
claude plugin marketplace remove everyone-pm

claude plugin marketplace add `pwd`
claude plugin marketplace update everyone-pm
claude plugin install everyone@everyone-pm

# Method 2: Using Taskfile (recommended)
task test
```

## Registered Plugins

| Plugin | Description |
| ------ | ----------- |
| everyone | Product manager productivity toolkit for AI Agents — wireframing, prototyping, and workflow automation |

### everyone Plugin Details

**Dependencies**

- None

**MCP Servers**

- None

**LSP Servers**

- None

**Agent Skills**

| Skill           | Description                                                                          |
| --------------- | ------------------------------------------------------------------------------------ |
| prototype-ascii | ASCII wireframe design tool for rapid UI prototyping                                 |
| prd             | Generate, update, review, and maintain requirement documents (PRD, user stories, scope, acceptance criteria) |
| llm-wiki        | Incrementally build and maintain a Markdown-based local LLM Wiki for persistent knowledge compilation |

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

## References

- Create plugins https://code.claude.com/docs/en/plugins-reference#skills
- Publish marketplace https://code.claude.com/docs/en/plugin-marketplaces
- Install from marketplace https://code.claude.com/docs/en/discover-plugins#add-from-other-git-hosts
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
