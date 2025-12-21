# TODO (Global)

## Current status

- Docs-first bootstrap completed (global docs + initial playbooks).
- No MCP servers implemented yet.
- No CDK app or AWS deployments yet.

## Partially done (where to look)

- Global structure and safety rules: `README.md`, `RULES.md`, `START_HERE.md`, `MANIFEST.md`
- Playbook workflow/template: `playbooks/playbook-for-playbooks/`
- Headless services playbook skeleton: `playbooks/headless-services-mundane-business-apps/`

## Repo foundation

- [x] Establish the “playbook for playbooks” as the default workflow.
- [ ] Refine the playbook template (required sections + naming) in `playbooks/playbook-for-playbooks/README.md`.
- [ ] Decide whether to add a static docs generator now (or stay Markdown-only initially).
- [ ] Add an initial MCP server implementation in `mcp/` (with local run instructions).
- [ ] Add CDK app skeleton in `infra/` with account/region/prefix guardrails (and document in `DEPLOYING.md` / `DEPLOYMENTS.md`).
- [ ] Add lightweight CI checks (markdown linting / link check / secret scanning) appropriate for a public repo.

## Playbooks

- [ ] Flesh out the first playbook: “Headless services for mundane business applications” (keep domain-agnostic initially).
- [ ] Add a “prompt library” approach (shared prompts + per-playbook prompts).
- [ ] Define a standard “definition of done” checklist for playbooks (in `QA.md`).

## Ops hygiene

- [ ] Define a redaction process for any accidental secret exposure.
- [ ] Standardize deployment record format in `DEPLOYMENTS.md`.

## Known issues / blockers / gotchas

- In this Codex sandbox, Git operations that write under `.git/` may require escalated permissions (commit/push). If blocked, use your normal terminal or rerun with escalation.

## Open questions

- CDK language and layout (TypeScript vs Python).
- MCP server language conventions (TypeScript vs Python vs mixed).
