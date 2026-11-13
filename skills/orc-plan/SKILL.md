---
name: orc-plan
description: Investigate a request and return a grounded plan, acceptance criteria, checks, and unresolved decisions. Use standalone or as orc's read-only planning stage.
---

# Orc planning

Plan without implementing; return to the caller.
Use available `explain` for substantial handoffs; otherwise concise, faithful
English. Ask simple questions directly.

Use caller-approved skills only. Standalone, this stage and available `explain`
and `browser-check` helpers are implicit. Return additional candidates as `needs_approval` before use,
including through descendants.

## Investigate

- Read the request, accepted clarifications, guidance, status, diffs, and existing plan. Preserve unrelated work and staging.
- Resolve target and intended outcome from sources. Gather distinguishing evidence for bugs; identify reader and decision for docs.
- Trace affected callers, consumers, related workflows, and rule owners. Reuse existing contracts; identify transferable changes within scope. Verify consequential API assumptions against primary sources and installed versions.
- Stay read-only: no edits, installs, generation, Git mutations, or state-changing services. Identify authority needed for setup/reproduction.
- Separate requirements, facts, and unresolved choices. Ask only when uncertainty changes scope, behavior, criteria, or approach; continue independent investigation.

## Return the plan

- State goal, sources, ordered steps, affected areas, scope, and material tradeoffs.
- Give observable criteria stable IDs and pair each with checks, including regression/docs coverage. Derive required local/remote checks from repository configuration and user decisions; identify external reviewers and completion signals. Future human review is the handoff unless required earlier.
- Plan applicable local/preview Chrome MCP/Chrome DevTools MCP checks with available `browser-check`; include criteria, source/served revision evidence, and setup gaps. Missing tools need exact source/version, setup/profile scope and effects from current primary docs for agreement, authorized setup and callable verification. Planning remains read-only.
- Identify effects, missing authority, and contextual skill candidates with exact source and proposed use. Keep unapproved choices pending.
- Incorporate accepted answers. Return one criterion/check mapping, evidence, and precise questions.
- Return `complete` when the outcome and approach are grounded; otherwise `needs_input`, `needs_approval`, or `blocked` with the missing evidence/decision. Start no successor or implementation.
