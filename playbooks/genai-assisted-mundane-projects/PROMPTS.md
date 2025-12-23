# Prompts: GenAI‑Assisted Mundane Projects

These prompts are designed to produce consistent, safe artifacts for a “mundane project” and keep GenAI grounded in the project’s canonical docs.

## Global guardrails (paste into every prompt)

- This repo is public: never output secrets; use placeholders like `REDACTED`, `example.com`, `000000000000`.
- Prefer explicit assumptions; mark uncertainty as `UNCONFIRMED`.
- Always reference and update the project’s canonical docs:
  - `CONTINUITY.md` (goal/state/open questions)
  - `CONTEXT_MEMORY.md` (stable decisions/facts)
  - `RULES.md` (non-negotiables)
- If AWS is involved:
  - Always use `--profile playbook`
  - Verify account `926943999684`
  - Use region `us-east-2`
  - Prefix all stacks/resources with `playbook`
  - Never propose broad destructive commands; scope to `playbook*` only

## Prompt: Capture my baseline workflow (interview → summary)

**Goal:** Convert my answers into a concise, reusable “baseline workflow” we can refine.

**Output format:**
- `## My definition of “mundane project”`
- `## My default stack(s)`
- `## My typical lifecycle (plan → build → deploy → day‑2)`
- `## What GenAI should do vs must not do`
- `## Open questions (UNCONFIRMED)`

Paste:

> Ask me the minimum set of questions to understand my typical “mundane project” workflow.  
> Then produce the summary in the requested output format, suitable for pasting into `NOTES.md` in my repo.

## Prompt: Draft a Project Brief (v0)

**Goal:** Produce a 1–2 page project brief from a few bullets.

**Output format (Markdown):**
- Title
- Problem statement
- Users/stakeholders
- Outcomes (success criteria)
- Non-goals
- Constraints (time/budget/compliance/data/latency/team)
- Risks + unknowns (mark `UNCONFIRMED`)
- Operational expectations (support model, data retention, audit)
- Next actions (top 5)

Paste:

> Using the guardrails above, draft a Project Brief from these inputs:  
> <paste inputs>  
> Keep it concise and mark unknowns as `UNCONFIRMED`.

## Prompt: Turn a Project Brief into an initial TODO backlog

**Goal:** Generate a prioritized backlog with acceptance criteria.

**Output format:** `TODO.md` with `P0/P1/P2`, each item includes: what + where + acceptance criteria.

Paste:

> Given this Project Brief, produce an initial `TODO.md` backlog with P0/P1/P2.  
> Each item must include acceptance criteria and any required validation/rollback notes.

## Prompt: Generate ADRs for key decisions

**Goal:** Make implicit architecture choices explicit.

**Output format:** 3–7 ADRs in Markdown, each with:
- Context
- Decision
- Alternatives considered
- Consequences
- Status (Proposed/Accepted)

Paste:

> Based on this Project Brief and current constraints, propose 3–7 ADRs for the key decisions.  
> Keep them short and mark anything uncertain as `UNCONFIRMED`.

## Prompt: Draft deploy + rollback runbook (docs-only)

**Goal:** Produce a safe runbook that can be executed later.

**Output format:** Markdown runbook with:
- Preconditions / access checks
- Build steps (TBD if unknown)
- Deploy steps (TBD if unknown)
- Validation / smoke tests
- Rollback steps (must be explicit)
- Post-deploy checklist

Paste:

> Draft a deploy + rollback runbook for this project.  
> If details are unknown, write `TBD` sections and list the exact questions needed to fill them in.

## Prompt: Day‑2 operations checklist (weekly/monthly)

**Goal:** Keep mundane projects healthy with a small routine.

**Output format:**
- Weekly checklist
- Monthly checklist
- “After incident” checklist

Paste:

> Create a day‑2 operations checklist for this project.  
> Keep it minimal and practical; include where to look for evidence (logs, dashboards, alerts), even if you must write `TBD`.

