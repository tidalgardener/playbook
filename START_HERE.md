# Start Here

## What this repo is

This is a public sandbox repository for:

- Playbooks (Markdown) for agentic workflows
- Prompts/templates intended to be reused across projects
- MCP servers (tools agents can call)
- AWS CDK infrastructure (when a playbook needs deployments)

## Current status

- Repo is in **bootstrap** phase: docs + structure exist, but there is **no MCP server code** and **no CDK app** yet.
- Two playbooks exist in draft form:
  - `playbooks/playbook-for-playbooks/` (meta workflow + templates)
  - `playbooks/headless-services-mundane-business-apps/` (domain-agnostic skeleton; default AWS architecture chosen)

## Read in this order

1. `RULES.md` — non-negotiables (public repo, AWS safety)
2. `playbooks/playbook-for-playbooks/README.md` — how we create/iterate on playbooks in this repo
3. `PLAYBOOKS.md` — playbook index
4. `TODO.md` and `NEXT_STEPS.md` — what to do next
5. `SESSION_HANDOFF.md` — where we left off last session

## If you are starting a new playbook

- Create `playbooks/<playbook-name>/` (kebab-case).
- Add:
  - `README.md` (playbook)
  - `TODO.md` (backlog)
  - `PROMPTS.md` (agent prompts)
- Add it to `PLAYBOOKS.md`.

## If you are adding AWS/CDK

Follow `RULES.md` strictly:

- Use `--profile playbook`
- Verify account `926943999684`
- Use region `us-east-2`
- Prefix all stacks/resources with `playbook`
- Never run broad destructive commands; scope to `playbook*` only

## If you are adding an MCP server

- Put it under `mcp/<server-name>/`.
- Document local run + configuration in that folder’s `README.md`.
- If it needs AWS, deployments must be via CDK under `infra/` and recorded in `DEPLOYMENTS.md`.

## Known limitations / open questions

- CDK app structure and language choice are not decided yet.
- No CI is configured yet (markdown lint/link check/secret scanning).
- Git operations inside this Codex sandbox may require escalated permissions (see `SESSION_HANDOFF.md`).

