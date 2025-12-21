# Manifest

This repo is organized around a small set of global docs plus per-playbook folders.

## Current status

- Docs-first bootstrap: structure is in place, but there is no MCP server code and no CDK app yet.

## Decisions (and rationale)

- Keep a small set of global “memory” docs (`CONTEXT_MEMORY.md`, `SESSION_HANDOFF.md`) so work can continue across sessions cleanly.

## Known limitations / open questions

- CDK app language/layout is not chosen yet.
- CI checks (markdown lint/link check/secret scanning) are not configured yet.

## Top-level docs

- `README.md` — repo overview and entry points.
- `START_HERE.md` — quickest orientation and workflow pointers.
- `RECAP.md` — durable milestone log (high-level).
- `RULES.md` — hard rules (public repo, AWS safety).
- `CONTEXT_MEMORY.md` — stable facts/decisions across sessions.
- `SESSION_HANDOFF.md` — current working state and handoff notes.
- `TODO.md` — global backlog.
- `NEXT_STEPS.md` — immediate next actions.
- `QA.md` — shared checklists and validation steps.
- `PLAYBOOKS.md` — index of playbooks.
- `DEPLOYMENTS.md` — what’s deployed to AWS.
- `DEPLOYING.md` — deployment workflow and safety guidance.

## Top-level folders

- `playbooks/` — per-playbook deep dives, prompts, and TODO lists.
- `mcp/` — MCP servers and tooling.
- `infra/` — AWS CDK and deployment-related code.
