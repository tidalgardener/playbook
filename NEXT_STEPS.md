# Next Steps

Immediate next actions to keep momentum.

## Current status

- Two draft playbooks exist; repo is still docs-first and not yet wired to code/deployments.

## Next actions (priority order)

1. Finalize the workflow for folding ChatGPT Pro “v0 drafts” into repo playbooks in `playbooks/playbook-for-playbooks/README.md`.
2. Expand the headless services playbook into a deeper, step-by-step guide (still domain-agnostic): `playbooks/headless-services-mundane-business-apps/README.md`.
3. Decide CDK language/layout and scaffold the first CDK app under `infra/` with strict account/region/prefix guardrails.
4. Implement the first MCP server under `mcp/` (even a minimal “hello tool”) and document local run/config.
5. Add basic CI suitable for a public docs-first repo (markdown lint/link check/secret scanning).

## Known issues / gotchas

- Git commit/push from inside this Codex sandbox may require escalated permissions (see `SESSION_HANDOFF.md`).
