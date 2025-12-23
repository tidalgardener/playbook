# Playbook: Playbook for Playbooks

This is the “master playbook” for creating, discussing, and maintaining playbooks in this repo so they stay consistent, shareable, and easy to operationalize.

## Current status

- Draft v0: establishes the workflow and templates, but still needs refinement.
- Intended to be the default starting point for creating/refactoring playbooks in this repo.

## Goals

- Make new playbooks fast to start and easy to iterate.
- Keep playbooks consistent across projects (where it makes sense).
- Ensure outputs are safe for a public repo (no secrets) and safe for AWS (strict scoping).

## Quickstart

### Create a new playbook

1. Pick a name and create the folder: `playbooks/<kebab-case-name>/`.
2. Create the baseline files:
   - `README.md` — the playbook (steps + checklists)
   - `TODO.md` — backlog (content gaps, examples, tooling opportunities)
   - `PROMPTS.md` — prompts/templates for agentic workflows
   - `NOTES.md` — decision log / scratchpad (optional)
3. Add the playbook to `PLAYBOOKS.md`.
4. Run the repo checklist in `QA.md` before calling it “done”.

### Refactor an existing draft

1. Make the workflow explicit (step-by-step, not guidance-only).
2. Add validation/rollback steps and a definition-of-done checklist.
3. Extract prompts into `PROMPTS.md` and backlog items into `TODO.md`.
4. Run the checklist in `QA.md`.

## How we work (iteration workflow)

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

1. **Redact first (public repo)**:
   - Remove/replace anything sensitive with placeholders like `REDACTED`, `example.com`, `000000000000`.
2. **Land it quickly**:
   - Paste the draft into the target playbook’s `README.md` (don’t “perfect” it before it’s in version control).
3. **Record provenance** (recommended):
   - In `NOTES.md`, add: date, source tool, and what changed from the original draft.
4. **Normalize into this repo’s shape**:
   - Convert vague guidance into explicit steps, checks, and rollback guidance.
   - Pull “future work” into `TODO.md` (keep `README.md` runnable).
   - Pull reusable agent prompts into `PROMPTS.md`.
5. **Apply safety rules**:
   - If AWS is involved, link to `RULES.md` and include the required `--profile playbook` / account / region / prefix guardrails.
6. **Quality gate**:
   - Run the checklist in `QA.md` and the playbook’s own DoD checklist.

## Playbook folder template

Create a folder under `playbooks/` with:

- `README.md` — the playbook itself (usable steps + checklists).
- `TODO.md` — playbook backlog (content + tooling + examples).
- `PROMPTS.md` — prompts/templates for agentic workflows.
- `NOTES.md` — decision log / scratchpad (optional).

## README template (required + optional)

Minimum required sections (keep naming close to this for consistency):

- Title + 1–2 sentence intent
- `## Current status`
- `## Outcomes` and `## Non-goals`
- `## Assumptions` / `## Constraints`
- `## Step-by-step workflow` (agent-friendly)
- `## Validation` and `## Rollback`
- `## Definition of done` (checklist)
- `## Prompts` (link to `PROMPTS.md`)

Optional sections (use when relevant):

- `## Architecture` / `## Reference architecture`
- `## Data model`
- `## Security`
- `## Observability`
- `## Operations` (deploy/runbooks)
- `## Known limitations / open questions`

Starting template:

```md
# Playbook: <Title>

<1–2 sentence intent.>

## Current status

- Draft v0 / In progress / Stable

## Outcomes

- …

## Non-goals

- …

## Assumptions / constraints

- This repo is public: no secrets.
- If AWS is involved: follow `RULES.md` (profile/account/region/prefix).
- …

## Step-by-step workflow

1. …

## Validation

- …

## Rollback

- …

## Definition of done

- [ ] …

## Prompts

See `PROMPTS.md`.
```

## Safety rules (must link)

Every playbook that touches AWS must explicitly link to `RULES.md` and include:

- `--profile playbook`
- account `926943999684`
- region `us-east-2`
- prefix `playbook*`
- no broad destructive operations

## Playbook review checklist

Use this when reviewing a playbook PR or preparing to share it externally.

- [ ] Clear audience, outcomes, and non-goals.
- [ ] Assumptions/constraints are explicit (including what is *not* covered).
- [ ] Steps are runnable (commands/inputs/expected outputs), not aspirational.
- [ ] Validation exists at multiple points (not only at the end).
- [ ] Rollback guidance is safe and scoped (especially for AWS).
- [ ] Terminology is consistent; undefined jargon is removed.
- [ ] Prompts in `PROMPTS.md` include guardrails and a clear output format.
- [ ] No secrets, private URLs, or sensitive identifiers are present (public repo).

## Examples: turn guidance into runnable steps

- Bad: “Deploy the service.”
  - Good: “Run `cdk synth`, then `cdk diff`, then `cdk deploy <explicit-stack-name>`; verify outputs in `DEPLOYMENTS.md`.”
- Bad: “Make sure AWS is configured.”
  - Good: “Run `aws sts get-caller-identity --profile playbook` and verify account `926943999684`.”
- Bad: “Test the API.”
  - Good: “Call `curl -i <endpoint>`; verify status code and response shape; include one failure case.”

## When to add tooling (MCP) vs keep docs-only

Prefer docs-only unless tooling materially improves repeatability.

Good reasons to add an MCP server:

- A step requires repeated external lookups (APIs/docs) or structured validation.
- A workflow is easy to get wrong without automation (scaffolds, linting, schema checks).
- The playbook depends on “live” state (cloud resources, deployments) and needs safe tooling wrappers.

Good reasons to stay docs-only:

- It’s a one-off decision or low-frequency manual step.
- Automation would encode too many assumptions before the playbook stabilizes.

## When to deploy to AWS vs keep it local

Prefer local by default; deploy only when the playbook’s value depends on real infrastructure.

Deploy to AWS when:

- The playbook’s steps require AWS-managed behavior (IAM, API Gateway auth, DynamoDB access patterns).
- You need a real endpoint for integration testing or demos.

Stay local when:

- You’re still exploring requirements, data model, or API shape.
- You can validate most logic with unit tests and local emulation.

## Decisions (and rationale)

- Keep playbooks Markdown-first to maximize shareability; add tooling/deployments only when it clearly improves outcomes.
- Separate durable facts (`CONTEXT_MEMORY.md`) from session notes (`SESSION_HANDOFF.md`) to keep “memory” clean.

## Known limitations / open questions

- How strictly to standardize playbook section headings vs allow variation.
- Whether to introduce a static docs generator now or stay Markdown-only longer.
