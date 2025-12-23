# Playbook

This repository is a sandbox for building and sharing playbooks and prompts for generative AI / agentic tooling. It’s intentionally a mix of:

- Plain Markdown docs (shareable, copy-pasteable playbooks)
- MCP protocol servers (tooling that agents can call)
- Static docs pages (optional, later)
- AWS-backed deployments (when a playbook needs real infrastructure)

This repo is public. Do not commit secrets.

## Current status

- Bootstrapped docs-first structure (no MCP server implementations yet).
- No AWS infrastructure is deployed yet; CDK app not scaffolded yet.
- Four draft playbooks exist; see `PLAYBOOKS.md`.

## Start Here

- `START_HERE.md` — the quickest path to orienting yourself
- `RULES.md` — non-negotiables (public repo, AWS safety rules)
- `CONTINUITY.md` — canonical session ledger (goal/state/open questions)
- `PLAYBOOKS.md` — index of playbooks
- `TODO.md` — global backlog
- `NEXT_STEPS.md` — immediate next actions
- `RECAP.md` — durable milestone log
- `CONTEXT_MEMORY.md` — stable facts/decisions to carry across sessions
- `SESSION_HANDOFF.md` — current working state + handoff notes
- `DEPLOYMENTS.md` — what’s deployed to AWS (CDK stacks, endpoints, notes)
- `DEPLOYING.md` — deployment workflow and safety guidance (placeholder until CDK exists)
- `QA.md` — shared checklists and quality gates
- `MANIFEST.md` — what each top-level file/folder is for

## Repository Layout (current)

- `playbooks/` — one folder per playbook (each with its own README/TODO/etc.)
- `mcp/` — MCP servers (local + deployable tooling)
- `infra/` — AWS CDK applications and deployment glue

## AWS Safety (hard rules)

When we use AWS, we always:

- Use `--profile playbook`
- Verify account is `926943999684`
- Use region `us-east-2` (where applicable)
- Prefix all stacks/resources/tags/names with `playbook`
- Never run broad destructive commands; limit scope to `playbook*` only

## Known limitations / open questions

- CDK app layout and implementation language are not chosen yet.
- CI checks are not configured yet (markdown lint/link check/secret scanning).
- In this Codex sandbox, Git operations that write under `.git/` may require escalated permissions (see `SESSION_HANDOFF.md`).
