# Codex Bootstrap Prompt Pack (AWS Serverless “Mundane” Services)

This repo contains a reusable bootstrap prompt + playbooks for building pragmatic, serverless, business-automation services on AWS (API + CLI + docs), with strong continuity and supportability.

## Files

- `BOOTSTRAP_PROMPT.txt` — the bootstrap prompt. Copy/paste it as-is. Do not edit it in-place; treat it as a stable, reusable artifact.
- `BUSINESS_SPEC_MINIMAL.txt` — minimal Business Spec outline (required sections only); copy/paste at the end of the bootstrap prompt.

## Assumptions & prerequisites

These prompts assume the following is true **before you start**:

### Agent/tooling
- You are using **Codex** (or a similar agentic development tool) with permission to:
  - read/write files in the target folder
  - run shell commands
  - install dependencies
  - create commits and push to GitHub  
  If the agent needs manual approvals for each action, this workflow becomes painfully slow.

### Model + reasoning configuration
- The model is **GPT‑5.2 or better** (recommended: GPT‑5.2 Pro), configured for **very high reasoning**.
- You are using **API-key billing** (not a capped consumer plan), so the agent is not blocked by message/token limits mid-session.

### GitHub auth (SSH)
- GitHub access is via **SSH**, using SSH keys/certificates already present on the development machine.
- The repo’s remote should be SSH (not HTTPS), and the agent should not switch auth methods.

### Machine/runtime expectations
- The development machine is configured **not to sleep** during work sessions.
- It can run unattended for long stretches (deploys, integration tests, build steps, dependency installs).

### OpenAI API account readiness (avoid mid-refactor failures)
- Codex is authenticated to the correct **OpenAI API account**.
- The project has **GPT‑5.2** enabled.
- You have sufficient credit headroom (recommend: **a few hundred dollars** reserve).
- **Auto top‑up is enabled** (example policy: add **$100** whenever balance drops below **$50**).  
  The goal is to avoid running out of funds mid-refactor or during multi-step deploy/test runs.

### Platform exceptions (call out early)
- The default architecture assumes AWS-first, serverless foundations.
- If the project is a **Shopify app** (or another product better suited to **Vercel** or a different hosting/runtime model), explicitly capture that in the **Business Spec** up front (including why, deployment targets, and constraints).

## How requirements are introduced (iterative by default)

Unless you explicitly state otherwise, this workflow assumes you will introduce requirements **incrementally**:
- First run: the agent should **set up structure and documentation** (contracts, spec scaffolding, continuity ledger, repo layout).
- The agent should **not** start building the actual system until enough requirements are captured to avoid thrash.
- Small projects are allowed to be “one paragraph and go”—but the agent should still set up minimal structure to keep work supportable.

## Business Spec outline (paste at the end of the bootstrap prompt)

> The bootstrap prompt should end with this outline and a note that more requirements are coming.  
> The agent should treat this as the initial requirements capture structure and avoid “starting the build” prematurely.

### BUSINESS SPEC (Minimum required)
1. **Problem statement**
2. **Users / actors** (human + agentic)
3. **Goals / success criteria**
4. **Non-goals**

### BUSINESS SPEC (Optional sections — the agent can propose/fill in)
5. **Core workflows** (happy paths)
6. **Edge cases & negative cases** (failures, retries, idempotency, partial failure)
7. **Data model (high level)** (entities, keys, access patterns)
8. **Interfaces & contracts**
   - HTTP API (OpenAPI YAML)
   - Direct Lambda payloads (YAML schema)
   - Events/queues/messages (YAML schema)
   - CLI surface area (commands + JSON output)
9. **Security & access model**
10. **Performance requirements (inputs, not afterthought)**
    - latency targets, throughput, concurrency, payload limits, data volume assumptions
11. **Observability & operations**
    - logs/metrics/traces/events, debug toggles, support without console
12. **Testing & QA plan**
    - smoke → integration (real AWS) → E2E → performance
13. **Deployment assumptions**
    - current phase account/profile/region/domain (single environment at a time)

**Note:** More requirements will be added shortly. Until then, focus on setting up the internal structure (docs, schemas, ledgers, repo scaffolding) so new requirements can be captured cleanly as we go.
