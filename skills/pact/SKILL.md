---
name: pact
description: Embed or refresh the complete bundled rules in a project’s AGENTS.md while preserving existing instructions.
---

# Pact

Handoffs: use available `explain`; otherwise concise, faithful English.

## Inspect

- Read all [bundled rules](assets/rules.md), applicable guidance, and the target `AGENTS.md`.
- Use the named project; otherwise the repository root, or current directory outside Git. Links outside the project need destination authorization.
- Report conflicting customizations, equivalent unmanaged rules, or incomplete/duplicate markers before changing them. Do not guess boundaries or take over existing rules.

## Apply

- Invocation authorizes only this local instruction edit; installation or discussion does not apply rules or authorize their described side effects.
- Embed the full rule text verbatim between `<!-- pact:start -->` and `<!-- pact:end -->`.
- Create the file if absent; append only if no block exists. Refresh a single complete block in place; leave matching text unchanged.
- Preserve everything outside the block. An embedded copy must work after the skill is removed.

## Verify

Check the diff: complete rules, exactly one block, unchanged surrounding text.
Report the target and outcome: added, refreshed, unchanged, or blocked. Future
rule updates apply when the installed skill is updated and pact runs again.
