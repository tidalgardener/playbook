# MCP Servers

This folder contains MCP (Model Context Protocol) servers used by agentic tooling.

## Current status

- No MCP server implementations yet; only templates/placeholders exist.

## Structure

Each server lives in its own folder:

- `mcp/<server-name>/README.md` — what it does, how to run locally, how to configure
- `mcp/<server-name>/` — implementation (language/framework varies)

## Expectations

- No secrets in code or docs (this repo is public).
- If a server needs AWS, deployments must be done via CDK in `infra/` and must follow `RULES.md` (profile/account/region/prefix).

## Known limitations / open questions

- Decide MCP server language/framework conventions (TypeScript vs Python vs mixed).
