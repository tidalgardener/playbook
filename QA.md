# QA

## Current status

- QA is currently a checklist-only baseline.
- No automated CI is configured yet.

## Playbook quality checklist

- [ ] Clear goal and audience.
- [ ] Explicit assumptions and constraints.
- [ ] Inputs/outputs and success criteria defined.
- [ ] Step-by-step flow that an agent (or human) can follow.
- [ ] Validation steps (tests, queries, sanity checks).
- [ ] Rollback/safe failure guidance.
- [ ] Security and data handling guidance (no secrets).

## AWS safety checklist (before any deploy/destroy)

- [ ] Using `--profile playbook`.
- [ ] Confirm `aws sts get-caller-identity --profile playbook` shows account `926943999684`.
- [ ] Confirm region is `us-east-2` where applicable.
- [ ] All stacks/resources/tags/names are prefixed `playbook`.
- [ ] Run `cdk diff` before `cdk deploy`.
- [ ] Never run broad destructive commands; targets must be explicitly listed and prefixed `playbook*`.

## Redaction checklist (public repo)

- [ ] Replace secrets with `REDACTED` and remove sensitive context.
- [ ] Remove or regenerate any logs/artifacts containing secrets.
- [ ] Rotate compromised credentials outside this repo.

## Known limitations / open questions

- Decide whether to add CI checks (markdown lint/link check/secret scanning) now or later.
