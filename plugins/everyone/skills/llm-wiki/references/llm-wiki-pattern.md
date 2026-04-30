# LLM Wiki Pattern Reference

## Purpose

Read this file when you need to explain "why maintain the knowledge base this way," supplement pattern background, or elevate a schema from operational rules to design rationale.

## Core Idea

Traditional document Q&A is more like RAG: retrieve raw material on demand and assemble answers on the fly. It works, but knowledge never accumulates; every query rediscovers and recombines from scratch.

LLM Wiki does something different: insert a layer of LLM-maintained Markdown wiki between raw material and questions. When new material arrives, the LLM does not merely "index it for later retrieval"; it integrates the information into the existing knowledge structure, updates entity pages, revises topic summaries, marks conflicts between old and new, strengthens cross-page links, and lets synthesized conclusions evolve.

The key is not "retrieval" but "persistent compilation." Knowledge is organized once and continuously maintained, instead of being derived from zero every time.

## Why It Works

- Cross-document synthesis compounds: subsequent questions can build directly on existing conclusions.
- Contradictions, stale information, and missing links surface early, instead of being discovered only by accident during a query.
- High-value analysis does not disappear into chat history; it precipitates into pages that can be cited again.
- Humans no longer bear the most tedious maintenance burden, focusing instead on selecting sources, asking questions, and making judgments.

## Three-Layer Architecture

### Raw Material Layer

- Typical location: `raw/`
- Content: Articles, papers, podcast notes, meeting minutes, images, tables, data files
- Principle: Immutable, traceable, source of truth for the knowledge base

### Wiki Layer

- Typical location: `wiki/`
- Content: Summary pages, concept pages, entity pages, topic pages, comparison pages, resource pages
- Principle: Fully maintained by the LLM, structured result of accumulated knowledge

### Schema Layer

- Typical files: `AGENTS.md`, `CLAUDE.md`
- Content: Directory structure, naming conventions, page templates, ingest/query/lint workflow
- Principle: Not knowledge content itself, but the operating agreement for "how the LLM maintains this knowledge base"

## Three Operation Types

### Ingest

Incorporate new material into the wiki. Typical actions:

1. Read the material.
2. Identify key conclusions, concepts, entities, frameworks, and conflicts.
3. Write a source summary.
4. Update related pages.
5. Fill in links and sources.
6. Update `index.md`.
7. Append `log.md`.

A single source may trigger updates across 10+ pages. That is precisely where LLM Wiki delivers value.

### Query

Ask the wiki, not the raw material. Read `index.md` to find pages, then read relevant pages and synthesize an answer. If the answer itself has long-term value, write it back into the wiki as a new topic, comparison, or resource page.

### Lint

Run periodic health checks, focusing on:

- Contradictory conclusions
- Stale claims invalidated by newer material
- Orphaned pages
- High-frequency concepts without dedicated pages
- Missing cross-links
- Knowledge gaps worth filling

## Index and Log

### `index.md`

This is the content-oriented main entry. Suitable for listing:

- Page links
- One-sentence summaries
- Optional metadata such as date, source count, tags

At moderate scale, a well-maintained `index.md` is often sufficient for navigation. There is no rush to build full RAG infrastructure.

### `log.md`

This is the time-oriented running record, recommended to be append-only. With a consistent title format, recent activity can be retrieved with shell tools, e.g.:

`## [2026-04-02] ingest | Article Title`

## Applicable Scenarios

- Personal growth and self-management
- Long-cycle research topics
- Reading companion wiki
- Team internal knowledge base
- Competitive analysis, due diligence, travel planning, course notes, deep dives into interests

Any scenario where "knowledge accumulates over time" fits this pattern.

## Practical Tips

- Use Obsidian Web Clipper to convert web pages into Markdown.
- Download images locally to avoid future link rot; review images separately when visual context is needed.
- Use Obsidian Graph View to observe hubs, clusters, and orphans.
- When dynamic lists are needed, keep Dataview-friendly fields in page frontmatter.
- Treat the entire wiki as a git repository for version history and rollback.
- At larger scale, consider local Markdown search tools such as `qmd`.

## Relationship with RAG

LLM Wiki does not replace RAG; it moves "knowledge maintenance" forward in the pipeline. RAG can still serve as a supplementary search capability, but the core value comes from this continuously evolving wiki layer: knowledge is not temporarily assembled, but already organized, linked, and persisted.
