# Recap

High-level progress log for the repository. Keep this brief and durable (major milestones and decisions). Session-by-session details belong in `SESSION_HANDOFF.md`.

## Current status

- Repo bootstrap complete; next work is deepening playbooks and scaffolding MCP/CDK.
- Nothing deployed to AWS yet.

## Known limitations / open questions

- CDK app language/layout is not chosen yet.
- CI checks are not configured yet.

## 2025-12-21

- Bootstrapped repo structure (global docs, playbooks folder, MCP/infra placeholders).
- Added first playbook: headless services for mundane business applications (default AWS: API Gateway + Lambda + DynamoDB).
- Added “playbook for playbooks” to standardize how we create and iterate on playbooks.
- Added `START_HERE.md` and `DEPLOYING.md` to make onboarding and AWS workflow explicit (CDK still pending).

## 2025-12-22

- Added `CONTINUITY.md` as the canonical session ledger (goal/state/open questions).
- Started a new playbook: GenAI-assisted mundane projects (`playbooks/genai-assisted-mundane-projects/`).
- Added a copy/paste bootstrap prompt for mundane service projects (`playbooks/mundane-service-bootstrap/BOOTSTRAP_PROMPT.txt`).
