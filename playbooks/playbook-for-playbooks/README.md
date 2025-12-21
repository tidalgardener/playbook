# Playbook: Playbook for Playbooks

This is the “master playbook” for creating, discussing, and maintaining playbooks in this repo so they stay consistent, shareable, and easy to operationalize.

## Current status

- Draft v0: establishes the workflow and templates, but still needs refinement.
- Intended to be the default starting point for creating/refactoring playbooks in this repo.

## Goals

- Make new playbooks fast to start and easy to iterate.
- Keep playbooks consistent across projects (where it makes sense).
- Ensure outputs are safe for a public repo (no secrets) and safe for AWS (strict scoping).

## How we work (workflow)

1. **Start with an outline (v0)** using ChatGPT/other tools:
   - Goal, audience, assumptions, constraints, and definition of done.
2. **Convert into repo structure**:
   - Create `playbooks/<name>/` with `README.md`, `TODO.md`, and `PROMPTS.md`.
3. **Iterate via sessions**:
   - Update `SESSION_HANDOFF.md` (what changed + next actions).
   - Update `CONTEXT_MEMORY.md` only for stable facts/decisions.
4. **Quality gate**:
   - Run the checklist in `QA.md` and the playbook’s own DoD checklist.
5. **Operationalize (optional)**:
   - If the playbook needs tooling or deployments, add MCP servers in `mcp/` and CDK in `infra/` following `RULES.md`.

## Capturing ChatGPT Pro “v0 drafts”

When you generate a “v0 draft” elsewhere (ChatGPT Pro, other tools):

- Paste the draft into the target playbook’s `README.md` as a starting point.
- Add a short “Draft notes” section (date + source tool + what changed) in that playbook’s `NOTES.md` (optional but recommended).
- Convert vague guidance into:
  - explicit steps
  - validation commands/checks
  - rollback guidance
  - a definition-of-done checklist

## Playbook folder template

Create a folder under `playbooks/` with:

- `README.md` — the playbook itself (usable steps + checklists).
- `TODO.md` — playbook backlog (content + tooling + examples).
- `PROMPTS.md` — prompts/templates for agentic workflows.
- `NOTES.md` — decision log / scratchpad (optional).

## README template (recommended sections)

- Title + 1-paragraph intent
- Outcomes / non-goals
- Assumptions / constraints (including environment)
- Default architecture/patterns (if any)
- Step-by-step workflow (agent-friendly)
- Validation and rollback
- Definition of done (checklist)
- Prompts (links to `PROMPTS.md`)

## Safety rules (must link)

Every playbook that touches AWS must explicitly link to `RULES.md` and include:

- `--profile playbook`
- account `926943999684`
- region `us-east-2`
- prefix `playbook*`
- no broad destructive operations

## Decisions (and rationale)

- Keep playbooks Markdown-first to maximize shareability; add tooling/deployments only when it clearly improves outcomes.
- Separate durable facts (`CONTEXT_MEMORY.md`) from session notes (`SESSION_HANDOFF.md`) to keep “memory” clean.

## Known limitations / open questions

- How strictly to standardize playbook section headings vs allow variation.
- Whether to introduce a static docs generator now or stay Markdown-only longer.
