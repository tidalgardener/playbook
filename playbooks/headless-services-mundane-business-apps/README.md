# Playbook: Headless Services for Mundane Business Applications

Build reliable, boring, cost-conscious backend services for everyday business workflows (CRUD + approvals + scheduling + notifications + reporting), optimized for maintainability and predictable operations.

## Current status

- Draft skeleton (domain-agnostic).
- Default reference architecture chosen: **API Gateway + Lambda + DynamoDB** (low ops, predictable cost).
- No starter code or CDK app exists yet in this repo.

## Outcomes

- A repeatable approach to design and ship headless services quickly.
- Standard patterns for auth, data modeling, APIs, background jobs, observability, and deployments.
- A “definition of done” checklist that keeps scope sane and production-ready.

## Non-goals

- Building consumer-scale social apps.
- Over-engineering (microservices, event sourcing) without clear requirements.

## Assumptions

- AWS is the runtime environment; deployments use CDK.
- Follow `RULES.md` for account/region/profile/prefix safety.
- This playbook starts domain-agnostic; we can add a running example domain later.

## When to use this playbook

- You have a business domain with forms + workflows + users/roles.
- You need an API for a UI, integrations, automations, or reporting.
- You care about operational simplicity and cost transparency.

## System shape (reference)

Typical “boring business app” backends have:

- **API surface**: REST (often) or GraphQL (sometimes), plus webhooks.
- **Auth**: OIDC/Cognito (preferred) or JWT validation via an IdP.
- **Data store**: DynamoDB for simple entities/workflows, or Postgres when relational reporting/constraints matter.
- **Async work**: queues + workers (email, exports, integration sync).
- **Observability**: structured logs, metrics, traces, alarms.

## Architecture options (AWS patterns)

Pick based on traffic shape, team familiarity, and data needs.

### Option A (default): API Gateway + Lambda + DynamoDB

- Good for: spiky traffic, low ops, simple entities, predictable cost.
- Watch for: complex relational queries, heavy reporting.

### Option B: ALB/API Gateway + ECS/Fargate + Postgres (RDS/Aurora)

- Good for: long-running workloads, heavier libraries, relational domains.
- Watch for: higher baseline cost and ops surface.

### Option C: Hybrid

- Lambda for API + ECS worker for heavy async tasks.

## Delivery approach (pragmatic steps)

1. **Define the slice**: one workflow end-to-end (entities, roles, states, success criteria).
2. **Design the API**: resources, idempotency, pagination, error model, versioning.
3. **Model the data**: primary access patterns first; keep reporting needs explicit.
4. **Implement the happy path**: one vertical slice with validation + auth + persistence.
5. **Add async workflows**: outbox/queue, retries, dead-letter handling.
6. **Harden**: observability, rate limits, alarms, least-privilege IAM, backups.
7. **Automate**: CDK deploys, CI checks, smoke tests.

## Definition of done (starter checklist)

- [ ] API has a documented contract (examples + error cases).
- [ ] AuthN/AuthZ implemented with least privilege.
- [ ] Data model supports required queries and migrations (if applicable).
- [ ] Background jobs are retryable and idempotent.
- [ ] Logs are structured; key metrics/alarms exist; tracing enabled where possible.
- [ ] IaC (CDK) can deploy from scratch; `cdk diff` is clean/reviewed.
- [ ] No secrets in repo; config via parameters/secrets manager (referenced, not stored).

## Prompts

See `PROMPTS.md` for reusable agent prompts for:

- Designing a domain slice
- Selecting an AWS reference architecture (default: API Gateway + Lambda + DynamoDB)
- Generating an API contract
- Producing CDK skeletons (guardrails included)

## Decisions (and rationale)

- Default to API Gateway + Lambda + DynamoDB to keep ops and cost predictable for “boring business app” workloads.
- Keep the playbook domain-agnostic initially so it can be reused across many business contexts.

## Known limitations / open questions

- Auth default (Cognito vs external IdP + JWT) is not decided yet.
- No reference domain slice is documented yet (intentionally deferred).
- No code examples, CDK stacks, or MCP tooling exist yet.
