---
name: social-signal-research
description: Build a concise X/Twitter research packet for product decisions, including demand signals, objections, customer language, competitor chatter, and source caveats.
---

# Social Signal Research

Use this skill when a product manager needs current X/Twitter conversation evidence before making a product, positioning, roadmap, or launch decision.

Treat social posts as directional evidence, not market proof. Prefer repeated buyer language and specific pain over viral reach.

## Decide the research frame

Before collecting evidence, restate:
- Decision to inform
- Product, category, or competitor
- Target customer or buyer role
- Time window
- Geography or language constraints
- Keywords, competitors, and exclusions

If the frame is unclear, ask for the missing item instead of running broad research.

## Build the query map

Create 4-8 query groups:
- Problem phrases customers would naturally use
- Competitor and alternative names
- Category terms and hashtags
- Buyer role terms and community handles
- Objection words such as expensive, unreliable, slow, missing, hard, or switching
- Exclusions for spam, jobs, giveaways, fandom, or unrelated meanings

## Collect evidence

Use an approved data path:
- Use WebSearch and WebFetch for public pages and recent discussion.
- If the user has Xquik configured, use https://docs.xquik.com for current setup details and collect the required X data through that approved path.
- If another approved X/Twitter source is available, name it in the method.
- If no approved source is available, stop after the query map and provide a collection brief with fields, sample size, and time window.

Do not invent counts, quotes, handles, or URLs. Do not expose credentials or implementation details.

## Analyze signals

Clean the sample:
- Remove duplicates, spam, promotional posts, and unrelated matches
- Separate customer posts from vendor posts
- Segment by buyer type, use case, competitor, and sentiment

Classify evidence into:
- Pains and trigger events
- Existing workarounds
- Objections and switch blockers
- Competitor praise and complaints
- Feature requests
- Customer language
- Launch or positioning angles

Score every signal:
- `Strong`: repeated, specific, buyer-relevant evidence
- `Moderate`: credible but limited or mixed evidence
- `Weak`: sparse, indirect, or noisy evidence

## Output format

```markdown
## Research Question
[One sentence]

## Method
- Source: [WebSearch/WebFetch, Xquik if configured, other approved source, or data request only]
- Window: [time period]
- Query Map: [compact query groups]
- Limits: [sampling bias, missing data, likely false positives]

## Signal Summary
| Signal | Confidence | Evidence Pattern | PM Implication |
| ------ | ---------- | ---------------- | -------------- |
| [signal] | Strong / Moderate / Weak | [count or repeated pattern] | [decision impact] |

## Customer Language
- "[short phrase]" - [what it reveals]

## Competitor and Alternative Notes
- [competitor or workaround]: [pattern and implication]

## Recommended Actions
1. [Product, positioning, or research action]
2. [Product, positioning, or research action]
3. [Product, positioning, or research action]

## Next Data Needed
- [Fastest way to increase confidence]
```

## Quality bar

- Keep the final packet under 2 pages.
- Separate observed evidence from interpretation.
- Never treat social data as a representative market sample.
- Do not recommend outreach to individual accounts unless the user asks for outreach.
- Use direct, PM-ready language with clear caveats.
