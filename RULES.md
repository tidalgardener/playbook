# Rules (Non‑Negotiable)

## Current status

- This file is the source of truth for safety rules.
- Nothing is deployed yet; CDK scaffolding is pending.

## Public repo: no secrets

- Do not commit secrets (API keys, tokens, private URLs, access keys, credentials, session cookies).
- If a secret is discovered in text, logs, or examples, redact it immediately and rotate it outside this repo.
- Prefer obvious placeholders: `REDACTED`, `example.com`, `000000000000`, `***`.

## AWS safety (hard rules)

This AWS account is shared with other work. Any action must be scoped to *playbook-only* resources.

- Always use `--profile playbook`.
- Always verify the AWS account is `926943999684` before any deploy/destroy.
- Default region is `us-east-2`; verify region where applicable.
- Every AWS stack/resource/tag/name must be prefixed with `playbook`.
- Destructive actions (delete/destroy/reset/nuke):
  - Must be explicitly limited to `playbook*` resources/stacks only.
  - Never use broad operations that can affect non-playbook resources (for example: “destroy all”, account-wide deletes, blanket nukes).
  - Double-check target stack names and prefixes before executing.

## Infrastructure as Code

- Use AWS CDK for deployments.
- Prefer predictable stack naming: `playbook-<domain>-<env>` (example: `playbook-headless-dev`).
- Capture every deployed stack and endpoint in `DEPLOYMENTS.md`.

## Playbook organization

- Each playbook lives in `playbooks/<playbook-name>/`.
- Each playbook maintains its own `TODO.md`.
- Global work lives in root `TODO.md` and `NEXT_STEPS.md`.
- Keep `CONTEXT_MEMORY.md` stable and factual; keep session details in `SESSION_HANDOFF.md`.

## Known limitations / open questions

- CDK guardrails (account/region assertions, stack naming enforcement) are not implemented yet.
- No automated secret scanning/CI is configured yet.
