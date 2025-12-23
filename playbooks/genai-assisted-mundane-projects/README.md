# Playbook: GenAI‑Assisted Mundane Projects

Define a typical “mundane” software project and keep it set up so GenAI can reliably help across planning, build, deployment, and day‑2 operations — primarily by maintaining the right docs, prompts, and checklists.

## Current status

- Draft v0.
- Next: capture *your* current “mundane project” definition + workflow and fold it into this playbook.

## Outcomes

- A repeatable way to define a new project (scope, constraints, success) without over-engineering.
- A minimal “AI-ready” documentation set that keeps GenAI grounded and safe.
- A standard prompt pack that produces consistent artifacts (briefs, ADRs, TODOs, runbooks).
- Day‑2 operational routines (checklists + runbooks) that GenAI can assist with.

## Non-goals

- Building code in this repository (this repo is docs/playbooks/prompts).
- Picking a single tech stack for all projects (we can add “default stacks” later).
- Using GenAI with secrets or private identifiers (public repo; use `REDACTED`).

## Assumptions / constraints

- This repo is public: no secrets. Use placeholders like `REDACTED`, `example.com`, `000000000000`.
- If AWS is involved, follow `RULES.md` (profile/account/region/prefix; no broad destructive ops).
- This playbook is intentionally stack-agnostic until you choose a default stack.

## Step-by-step workflow

### 0) Capture your baseline (we will improve from here)

Answer these in chat (bullets are fine). We’ll store the distilled version in `NOTES.md` and update this playbook:

- What counts as a “mundane project” for you (examples + what it excludes)?
- Typical team size and timeline?
- Default stack(s) you reach for (languages, frameworks, hosting, DB)?
- How you normally start: what do you write first (docs, tickets, diagrams, code)?
- How you deploy (even roughly) and how you handle environments (dev/stage/prod)?
- What “day‑2” looks like: monitoring, on-call (if any), incident handling, backups, migrations?
- What you *want* GenAI to do vs what must stay human-owned?

### 1) Define the project in one page (Project Brief)

Create a short “Project Brief” (1–2 pages) that becomes the anchor artifact for everything else.

Include:

- Problem statement + who it’s for
- Outcomes (success criteria) and non-goals
- Constraints (time, budget, compliance, latency, data, team)
- “Good enough” definition (what shipping v1 means)
- Primary risks + unknowns
- Operational expectations (uptime, support model, data retention, audit needs)

### 2) Choose a default project shape (“track”)

Pick one track as the **default** for this project (you can change later):

- **Headless service** (APIs + background jobs) — see `playbooks/headless-services-mundane-business-apps/`
- **Web app** (UI + API) — TBD (documented later)
- **Integration / automation** (sync jobs + webhooks) — TBD (documented later)

Capture your choice in the project brief as an explicit decision.

### 3) Create the “AI-ready” doc set (minimum viable project memory)

In the *target project repo* (not this repo), create a small set of canonical docs so GenAI has stable grounding:

- `START_HERE.md` — read order, how to run, current focus
- `CONTINUITY.md` — canonical ledger (goal/state/open questions/working set)
- `CONTEXT_MEMORY.md` — stable facts/decisions (no session notes)
- `RULES.md` — non-negotiables (security, safety, naming, deployment guardrails)
- `TODO.md` — backlog (P0/P1/P2 with acceptance criteria)
- `QA.md` — how to test + release checklist
- `DEPLOYMENT.md` (or `DEPLOYING.md`) — deploy/rollback steps + environments
- `SESSION_HANDOFF.md` — optional if you use “sessions” for work chunks

If you want a standard layout, keep these under `docs/` and link them from the repo root.

### 4) Install the prompt pack (so GenAI outputs consistent artifacts)

In the target project repo, add a `PROMPTS.md` (or a `prompts/` folder) that includes:

- Guardrails (no secrets; data handling rules; deployment safety)
- Standard output formats (Markdown templates, checklists, ADR format)
- Role prompts (PM/architect/engineer/SRE) that always refer back to `CONTINUITY.md`

Use (and customize) `PROMPTS.md` in this playbook.

### 5) Generate the initial backlog and architecture decisions (docs, not code)

Use GenAI to draft:

- Initial `TODO.md` (P0/P1/P2), with acceptance criteria
- One or more ADRs for the core choices (hosting, DB, auth, observability)
- A release plan and a minimal “day‑2 operations” plan

Then review as a human and make the decisions explicit.

### 6) Document build/deploy/ops workflows (runbooks)

Write runbooks as if a future-you (or GenAI) must execute them safely:

- Local setup + how to run
- Deployment steps (with preflight checks) and rollback steps
- Data migrations/backups/restore (if applicable)
- Observability: logs, metrics, alerts, dashboards
- Incident checklist + escalation + postmortem template

### 7) Run the day‑2 loop (keep the project “AI-friendly”)

Cadence (adjust as needed):

- Before each work session: update `CONTINUITY.md` and re-state Goal/Now/Next/Open Questions.
- Weekly: prune `TODO.md`, promote decisions into `CONTEXT_MEMORY.md`, update runbooks after real incidents.
- After any deploy: update deployment records and validate rollback still works (document-only unless you’re actually deploying).

## Validation

- [ ] Project Brief exists and is current.
- [ ] “AI-ready” doc set exists and has a clear read order.
- [ ] Prompt pack includes guardrails + output formats (and references canonical docs).
- [ ] Runbooks include validation steps and safe rollback steps.
- [ ] No secrets/private identifiers appear in any docs (public repo hygiene).

## Rollback

- Docs-only changes: revert via git (keep changes small and reviewable).
- Deployment changes (if you later deploy): ensure every runbook has explicit rollback steps and “stop the bleeding” guidance before complex recovery.

## Definition of done

For this playbook (repo-level):

- [ ] Captured your baseline workflow and updated this playbook accordingly.
- [ ] Added a reusable prompt pack for the full lifecycle (plan/build/deploy/ops).
- [ ] Linked at least one concrete “track” playbook (headless services is the first).

For a new project using this playbook:

- [ ] Project Brief + canonical docs + prompt pack exist.
- [ ] Backlog has P0 items with acceptance criteria.
- [ ] Deploy/rollback and incident runbooks exist (even if “TBD” for steps you haven’t exercised yet).

## Prompts

See `PROMPTS.md`.

