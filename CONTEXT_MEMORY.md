# Context Memory

Stable facts and decisions that should persist across sessions.

## Repository

- Repo purpose: sandbox for shareable playbooks + prompts + MCP tooling + (optional) static docs + AWS-backed deployments.
- This repo is public: do not commit secrets.
- Primary orientation doc: `START_HERE.md`.
- Meta workflow playbook: `playbooks/playbook-for-playbooks/` (default process for creating/iterating playbooks).

## AWS (hard constraints)

- AWS account: `926943999684`
- Region: `us-east-2` (where applicable)
- AWS CLI profile: `playbook` (always use `--profile playbook`)
- Naming/tagging: everything must be prefixed with `playbook`
- Safety: destructive operations must be strictly limited to `playbook*` resources only.

## Tooling available in this Codex environment

- MCP `aws_docs` for AWS documentation lookup.
- MCP `shopify-dev-mcp` for Shopify docs/schema validation (only when relevant).
- MCP `openai` for structured drafting/checking (no secrets).

## Environment constraints (Codex sandbox)

- Git operations that write inside `.git/` may be blocked without escalated permissions.

## Conventions

- Prefer kebab-case for folder names (example: `headless-services-mundane-business-apps`).
- Keep playbooks practical: assumptions, steps, checklists, validation, and safe rollbacks.

## Current decisions

- Default reference architecture for the headless services playbook: API Gateway + Lambda + DynamoDB.
- Running example domain: TBD; start with a “master playbook” approach (domain-agnostic first).
