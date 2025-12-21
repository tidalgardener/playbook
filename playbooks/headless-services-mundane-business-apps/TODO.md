# TODO: Headless Services for Mundane Business Applications

## Current status

- Draft skeleton exists; content expansion is pending.
- Default AWS reference architecture is API Gateway + Lambda + DynamoDB.

## Playbook content

- [ ] Decide whether to add a concrete running example domain (optional).
- [ ] Add API design conventions (pagination, filtering, error model, idempotency keys).
- [ ] Add DynamoDB modeling guide (access patterns first) + examples.
- [ ] Add Postgres modeling guide (migrations, constraints, reporting) + examples (as an alternative path).
- [ ] Add async job patterns (SQS, retries, DLQ, idempotency).
- [ ] Add observability defaults (log fields, metrics, alarms).
- [ ] Add security defaults (Cognito/OIDC, IAM boundaries, KMS, audit logs).
- [ ] Add deployment section (CDK structure, environments, safe destroy).

## Assets

- [ ] Add diagrams (sequence + component) for the default architecture.
- [ ] Add a “starter kit” code example folder (once language choice is made).

## Open questions

- Do we ship a “minimal reference implementation” (code + CDK) or stay documentation-only longer?
