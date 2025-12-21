# Deploying (AWS)

## Current status

- Nothing is deployed yet.
- No CDK app exists yet under `infra/` (this file is a placeholder so deployment guidance has a stable home).

## Hard safety rules

Before any AWS action:

- Use `--profile playbook`
- Verify account is `926943999684`
- Use region `us-east-2` where applicable
- Prefix all stacks/resources/tags/names with `playbook`
- Never use broad destructive operations; scope targets to `playbook*` only

## When CDK is added (expected workflow)

1. Verify identity:
   - `aws sts get-caller-identity --profile playbook`
2. Confirm region (as applicable): `us-east-2`
3. Synthesize and review:
   - `cdk synth`
   - `cdk diff`
4. Deploy explicit stacks only:
   - `cdk deploy <explicit-playbook-stack-name>`
5. Record stack names, outputs, and endpoints in `DEPLOYMENTS.md`.

## Destroy / cleanup (only if explicitly needed)

- Never destroy “everything”.
- Only target stacks/resources prefixed `playbook*`.
- Prefer explicit stack names over wildcards.
- Record what was destroyed in `DEPLOYMENTS.md` (and why).

## Open questions

- CDK language (TypeScript vs Python) and project layout.
- Whether to support multiple environments (`dev/stage/prod`) from day one.

