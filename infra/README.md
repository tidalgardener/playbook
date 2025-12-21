# Infrastructure (AWS CDK)

This folder contains AWS CDK apps and deployment glue for anything in this repo that needs AWS.

## Current status

- Placeholder only: no CDK app yet.
- Deployment workflow guidance lives in `DEPLOYING.md`.

## Hard rules

Before any action:

- Use `--profile playbook`
- Verify account is `926943999684`
- Use `us-east-2` where applicable
- Prefix everything with `playbook`
- Never run broad destructive commands; scope targets to `playbook*` only

## Status

CDK apps not scaffolded yet. When we add them, we’ll record deployed stack names and outputs in `DEPLOYMENTS.md`.
