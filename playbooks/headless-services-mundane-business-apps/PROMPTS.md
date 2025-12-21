# Prompts: Headless Services for Mundane Business Applications

These prompts are designed for agentic workflows. Keep outputs practical, testable, and safe.

## Current status

- Baseline prompt set; tuned for a domain-agnostic workflow.
- Default reference architecture: API Gateway + Lambda + DynamoDB.

## Global guardrails (include in every prompt)

- This repo is public: never output secrets; use placeholders like `REDACTED`.
- AWS hard rules:
  - Always use `--profile playbook`
  - Verify account `926943999684`
  - Use region `us-east-2`
  - Prefix all stacks/resources with `playbook`
  - Never propose broad destructive commands; scope to `playbook*` only

## Prompt: Define a vertical slice

**Goal:** turn a vague business need into a shippable vertical slice.

Paste:

> You are designing a backend vertical slice for a mundane business app.  
> Provide: domain entities, roles/permissions, state machine (if any), invariants, API resources/endpoints, and acceptance criteria.  
> Keep the initial slice small (1 workflow), but production-quality.  
> Include non-functional requirements (SLOs, auditability, retention) only if explicitly required.  
> Output in Markdown with headings and a final checklist.

## Prompt: Choose an AWS reference architecture

Paste:

> Given this domain slice and constraints (team size, expected traffic, reporting needs), choose an AWS architecture.
> Default to **API Gateway + Lambda + DynamoDB** unless constraints clearly require something else.
> Provide: rationale, risks, operational burden, and a minimal AWS component diagram (text/mermaid).  
> Include explicit naming/tagging guidance using the `playbook` prefix.

## Known limitations / open questions

- Whether to standardize API conventions across all playbooks (error model, pagination) in a shared prompt pack.

## Prompt: Draft an API contract

Paste:

> Draft an API contract for the chosen slice. Include:
> - resources and endpoints
> - request/response examples
> - pagination/filtering conventions
> - error model (codes + examples)
> - idempotency strategy for unsafe operations
> Prefer boring, explicit JSON shapes over cleverness.

## Prompt: Generate CDK skeleton (safe)

Paste:

> Generate an AWS CDK skeleton for the chosen architecture. Requirements:
> - Region: us-east-2
> - Account: 926943999684 (include a guard/assertion)
> - All stack/resource names prefixed with `playbook`
> - No broad destroy/nuke instructions
> - Include outputs for key endpoints/ARNs
> Provide the file tree and short instructions to synth/diff/deploy using `--profile playbook`.
