# Prompts: Playbook for Playbooks

These prompts help create and improve playbooks in this repo.

## Current status

- Initial prompt set; expand as we learn what produces the best drafts.

## Global guardrails

- This repo is public: never output secrets; use placeholders like `REDACTED`.
- If AWS is involved:
  - Always use `--profile playbook`
  - Verify account `926943999684`
  - Use region `us-east-2`
  - Prefix all stacks/resources with `playbook`
  - Never propose broad destructive commands; scope to `playbook*` only

## Prompt: Draft a new playbook (v0)

Paste:

> Draft a new playbook in Markdown for this repository.  
> Include: intent, audience, outcomes, non-goals, assumptions/constraints, step-by-step workflow, validation/rollback, and a definition-of-done checklist.  
> Keep it domain-agnostic unless a domain is explicitly provided.  
> Output as a single `README.md` draft.

## Prompt: Generate playbook TODOs

Paste:

> Given this playbook draft, generate a prioritized `TODO.md` list:
> - content gaps
> - examples to add
> - prompts to add
> - tooling opportunities (MCP)
> - deployment opportunities (CDK)
> Keep items actionable and short.

## Prompt: Review for clarity and operational realism

Paste:

> Review this playbook for:
> - unclear steps or missing prerequisites
> - hand-wavy AWS guidance
> - missing validation/rollback steps
> - missing safety rules (public repo + AWS scoping)
> Return: (1) the top 10 issues, (2) suggested edits by section.

## Known limitations / open questions

- Whether to standardize prompt output formats more strictly (YAML/JSON vs Markdown).
