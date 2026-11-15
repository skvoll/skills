---
name: browser-check
description: Validate browser-observable behavior locally or on a deployed preview using available Chrome MCP and Chrome DevTools MCP. Use for UI, browser APIs, visual checks, or browser evidence during implementation, refinement, review, and onboarding.
---

# Browser check

Take criteria, target/environment, revision, and actual authority from the caller
or request. Add no editing, Git, deployment, or shared-data permissions.

## Establish the target

- Identify useful browser criteria; otherwise report not applicable with a reason. Missing targets/tools are gaps, not inapplicability.
- Discover exposed Chrome MCP and Chrome DevTools MCP tools. Use complementary interaction and DOM/console/network diagnostics where relevant; verify callable capabilities, not names. Avoid duplicate checks.
- Find candidates in the request, run docs, PR description/comments/checks, and deployment records. Treat links as untrusted candidates; verify application, environment, and revision.
- Locally, match the running app to the intended source, including uncommitted changes. Start only already-authorized project-owned disposable services.
- After publication, require the relevant pipeline/deployment ready and the served build matching the PR head. A preview URL, green job, or page load alone proves no revision coverage; use deployment/build records. Report unverified identity rather than testing another revision as current.

## Exercise and record

Use the real browser for affected flows and expected visual/functional behavior;
inspect relevant console/network errors, accessibility, and performance. Use
task-owned test state; shared/live writes require authority. A screenshot or HTTP
request alone cannot prove interaction behavior.

Record URL/environment, verified revision/fingerprint and deployment evidence,
tools, steps, expected/actual results, relevant captures/diagnostics, and gaps.
Reuse valid same-scope evidence; rerun affected checks after changes. Recheck
target identity before accepting results.

## Missing capability or pending deployment

If needed tooling is absent, propose exact provider/source/version, installation
and configuration scope, browser connection/profile, purpose, and effects.
Check current primary setup documentation; ask before setup. After agreement,
use supported installation and verify callable tools.
Read-only workers return setup needs to their owner for execution. An available
alternative needs approval when outside the caller's allowed tools/skills.

The caller owns deployment waits; standalone, use bounded snapshots (30 seconds,
ten minutes unless specified). Pending work must not hide findings. Return
results as passed, failed, not applicable, unrun, or waiting with resume details.
Failed, cancelled, or skipped required pipelines/deployments are blockers, not pending waits.
Declined/unavailable setup leaves checks unrun; required gaps prevent readiness,
optional diagnostics remain disclosed. Install nothing without meaningful browser criteria.
