# CONTINUITY

Canonical, compaction-safe briefing for continuing work in this repo.

## Goal (incl. success criteria)

- Maintain a public, docs-first repo of reusable playbooks + prompts that make it easy to run “mundane” software projects with GenAI assistance across build/deploy/day-2 operations.
- Success criteria (TBD): at least one playbook is “runnable” (explicit steps, validation, rollback, DoD) for defining and operating a typical mundane project; guardrails and prompts are reusable across projects.

## Constraints/Assumptions

- Public repo: no secrets (see `RULES.md`).
- Docs-only focus for now: do not add code scaffolds/implementations in this session; document approaches, prompts, and workflows instead.
- AWS guardrails (hard): `--profile playbook`, account `926943999684`, region `us-east-2`, prefix everything `playbook*`, no broad destructive operations.
- Deployments (when they exist) are via AWS CDK under `infra/`; deployed stacks/outputs recorded in `DEPLOYMENTS.md`.
- Current repo state is docs-first bootstrap: no MCP server implementations and no CDK app yet.

## Key decisions

- Start domain-agnostic and operationally “boring” by default; add concrete example domains later (TBD).
- Headless services default reference architecture: API Gateway + Lambda + DynamoDB.
- For mundane service projects, the Business Spec minimum required sections are: problem statement, users/actors, goals/success criteria, non-goals (other sections are optional and can be drafted by the agent).
- Keep durable facts in `CONTEXT_MEMORY.md`; keep session-specific details in `SESSION_HANDOFF.md`.

## State: Done / Now / Next

- Done:
  - Global docs + structure bootstrapped; initial playbooks drafted.
  - Placeholders exist for `mcp/` and `infra/` (no implementations yet).
  - Created new playbook skeleton: `playbooks/genai-assisted-mundane-projects/` (docs + prompts; needs your workflow captured).
  - Added reusable bootstrap prompt folder: `playbooks/mundane-service-bootstrap/BOOTSTRAP_PROMPT.txt`.
  - Added assumptions/prereqs for the prompt pack: `playbooks/mundane-service-bootstrap/README.md`.
- Git:
  - Committed and pushed to `main` (2025-12-23).
- Now:
  - Capture your baseline “mundane project” definition + workflow (Q&A) and refine `playbooks/genai-assisted-mundane-projects/`.
- Next:
  - Refine `playbooks/headless-services-mundane-business-apps/` as one concrete “mundane project” architecture path.
  - Add a shared prompt pack / templates that can be copied into any new project repo (docs-only).
  - Decide later whether MCP/CDK code should exist in this repo, or remain documented-only.

## Open questions (mark as UNCONFIRMED if needed)

- UNCONFIRMED: What you mean by “mundane project” (typical domains, team size, delivery cadence).
- UNCONFIRMED: Default tech stack expectations (language/runtime/hosting) vs keeping it stack-agnostic.
- UNCONFIRMED: Preferred GenAI workflow (what you do manually vs want automated; tools used).
- UNCONFIRMED: CDK language/layout choice (TypeScript vs Python) and conventions.
- UNCONFIRMED: MCP server language/framework conventions (TypeScript vs Python vs mixed).
- UNCONFIRMED: Whether to add a static docs generator (or stay Markdown-only longer).
- UNCONFIRMED: Whether to add a concrete running example domain for the headless services playbook.
- UNCONFIRMED: Auth default for the headless services playbook (Cognito vs external IdP).

## Working set (files/ids/commands)

- Orientation: `START_HERE.md`, `README.md`, `MANIFEST.md`
- Canonical safety: `RULES.md`, `QA.md`
- Memory + handoff: `CONTEXT_MEMORY.md`, `SESSION_HANDOFF.md`, `RECAP.md`
- Global tracking: `TODO.md`, `NEXT_STEPS.md`, `PLAYBOOKS.md`
- Deployment docs: `DEPLOYING.md` (workflow) + `DEPLOYMENTS.md` (record). (No `DEPLOYMENT.md` file in repo.)
- Active playbook: `playbooks/genai-assisted-mundane-projects/README.md`, `playbooks/genai-assisted-mundane-projects/PROMPTS.md`, `playbooks/genai-assisted-mundane-projects/TODO.md`, `playbooks/genai-assisted-mundane-projects/NOTES.md`
- Bootstrap prompt (copy/paste): `playbooks/mundane-service-bootstrap/BOOTSTRAP_PROMPT.txt`
- Business Spec minimal outline (copy/paste): `playbooks/mundane-service-bootstrap/BUSINESS_SPEC_MINIMAL.txt`
- Prompt pack README: `playbooks/mundane-service-bootstrap/README.md`
- Commands:
  - `git status -sb`
  - `rg -n \"playbook\" -S .`
