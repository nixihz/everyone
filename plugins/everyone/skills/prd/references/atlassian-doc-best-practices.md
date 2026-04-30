# Atlassian-Style Requirements Best Practices

Use this reference when drafting, updating, or reviewing requirement documents in an Atlassian-style workflow.

## Core philosophy

- Treat the document as a living alignment artifact, not a one-time approval package
- Prefer shared understanding over exhaustive early specification
- Use one page as the main entry point, then link interviews, mockups, Jira items, and deep technical material
- Make scope boundaries explicit to reduce scope creep
- Keep the document current as implementation, learning, and decisions evolve
- Involve product, design, and engineering in discovery instead of having the PM write everything alone

## Confluence PRD 5-step workflow

Use this lighter workflow when creating or expanding a PRD collaboratively:

1. Cover basic information
2. List goals and success metrics
3. Record assumptions and response options
4. Attach supporting documents
5. Anticipate open questions and scope creep

Map the five steps into these practical checks:
- Fill status, owner, target release, core team, and linked delivery artifacts
- Preserve Confluence/Jira style affordances in wording when the target system supports them, such as date fields, linked Jira items, and team mentions
- Tie the work to business goals and measurable outcomes
- Write down user, business, and technical assumptions explicitly
- Use requirement option tables when multiple solution directions or requirement interpretations need comparison
- Consolidate supporting diagrams, research, designs, and linked issues
- Track open questions, answers, answer dates, and explicit out-of-scope items

## PRD recommended structure

Use this 8-part structure as the default backbone:

1. Project details
2. Team goals and business goals
3. Background and strategic fit
4. Assumptions
5. User stories with success metrics
6. User interaction and design
7. Open questions or pending decisions
8. Out of scope

Useful section expansions:
- `Project Details` can include participants, status, target release, and linked epic/work items
- `Background and Strategic Fit` should answer why this work matters now
- `User Stories and Success Metrics` should tie requirement statements to value and measurement
- `User Interaction and Design` should link design exploration after team discussion, not before it
- `Open Questions / Pending Decisions` should remain visible until resolved
- `Out of Scope` should state what is intentionally excluded for this delivery

## PRD anti-patterns

These are warning signs that the PRD process is unhealthy:

- Writing an extremely detailed specification before engineering exploration begins
- Treating the document as a sign-off artifact instead of a collaboration surface
- Freezing requirements because people already approved an older version
- Hiding changes, decisions, or updates outside the team's view
- Having the product owner write the document alone without design or engineering participation
- Spreading related requirement state across multiple systems with no single source of truth
- Failing to define out-of-scope items, which invites hidden scope creep

## PRD benefits and challenges

Common benefits of a well-maintained PRD:
1. One page, one entry point for the full long-form story
2. Additional agility because the format can adapt to need
3. Enough background and detail through linked supporting material
4. A living story connected to delivery status
5. Collective intelligence through open contribution
6. Rich visual and embedded context that improves communication
7. Collaboration across PM, design, engineering, and other stakeholders

Common challenges to watch:
1. The document may become outdated after implementation changes
2. Participation may remain weak if the organization lacks documentation culture

Practical tips:
- Do not manage related work across disconnected systems if one page can serve as the entry point
- Keep the doc agile and revise stories as the team learns
- Prefer a one-page dashboard style overview with links out to details

## User stories and acceptance criteria

### Story format

Use:

`As a [user role], I want [goal] so that [value/reason]`

### 3C principle

- `Card`: the concise written story
- `Conversation`: the collaboration that clarifies details
- `Confirmation`: the acceptance criteria that define story completion

### Acceptance criteria rules

- Make each criterion clear
- Make each criterion testable
- Prefer measurable conditions where possible
- Avoid vague adjectives without observable checks
- Write criteria for behavior and outcome, not just UI appearance

Example:
- Wishlist button is clearly visible on the product page
- Confirmation prompt appears after adding an item
- Wishlist can store up to 50 items
- Wishlist data is retained for 30 days after user logout

### Acceptance criteria vs DoD

- `Acceptance Criteria` applies to whether this specific story is complete and correct
- `DoD` applies to the team-wide quality bar for any delivered work

Do not use one as a substitute for the other.

## Scope statement guidance

Use a scope statement to define boundaries, exclusions, and deliverables.

Use this 5-step drafting flow:
1. Define the project objective with SMART framing
2. List concrete deliverables
3. Build a work breakdown structure
4. State explicit out-of-scope items
5. Capture constraints such as time, budget, staffing, and dependencies

Include:
- SMART objective
- tangible deliverables
- WBS or equivalent breakdown
- explicit in-scope items
- explicit out-of-scope items
- constraints such as budget, timeline, staffing, policy, or dependencies

If the initiative is still being justified, add project charter framing:
- Is this project worth doing
- What business goal does it serve
- Who are the stakeholders

## Software design document guidance

When the requirement work also needs technical design context, use this structure:

1. Introduction and overview
2. System architecture
3. Data design
4. Interface design
5. Component design
6. UI design
7. Assumptions and dependencies
8. Glossary

Emphasize:
- clarity and concise wording
- diagrams or visuals for complex systems
- consistent terminology
- traceability from requirements to design choices
- centralized access and maintainability

## Quality checklist

Before finalizing or refreshing a document, confirm:

- The problem and objective are specific enough to explain why the work exists
- Success metrics exist or are explicitly marked as pending
- Facts, assumptions, decisions, risks, and open questions are clearly separated
- In-scope and out-of-scope are both present when scope matters
- User stories include value, not only functionality
- Acceptance criteria are testable
- Open questions are listed explicitly instead of being buried in prose
- Stakeholders, owners, or decision-makers are visible when relevant
- Terminology is consistent across sections
- The document can be updated incrementally without structural pain
