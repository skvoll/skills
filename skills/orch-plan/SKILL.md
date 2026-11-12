---
name: orch-plan
description: Investigate a ticket or description and produce an evidence-backed implementation plan with acceptance criteria, validation, and explicit unresolved decisions. Use standalone or as orchestrate's planning stage.
---

# Orchestration planning

Investigate and plan without implementing. Return to the caller.
Use available `explain` for the plan and substantial questions; otherwise
concise, faithful English. Ask simple questions directly.

## Investigate

- Read the full request, accepted clarifications, repository guidance, status, relevant diffs, and existing plan if resuming. Preserve user work and staging.
- Resolve the target and intended outcome from supplied context and sources. For bugs, gather reproduction or distinguishing evidence; for docs, identify the reader and decision.
- Trace implementation and verification boundaries. Verify consequential API assumptions against current primary sources and installed versions.
- Stay read-only: no edits, installs, generation, Git mutations, or state-changing services. Put necessary setup or reproduction mutations in the plan with their required authority.
- Distinguish user requirements, repository facts, and unresolved choices. Do not fill gaps with vague assumptions. Ask when uncertainty changes scope, behavior, acceptance criteria, or the approach; continue independent investigation.

## Plan and return

- State the goal, source-backed findings, ordered steps, affected areas, scope limits, and material tradeoffs. Scale detail to the task.
- Give observable acceptance criteria stable IDs and pair each with a validation check. Include needed documentation or regression coverage.
- Identify required local/remote checks from repository configuration and user decisions. Record requested external reviewers and available completion signals; human review is the final handoff unless explicitly required earlier.
- Identify side effects and any unresolved authorization; planning grants none.
- Incorporate accepted answers and update the plan. Return the plan, evidence, criteria/check mapping, and precise unresolved questions.
- Report `complete` only when the intended outcome and approach are sufficiently grounded to implement. Otherwise return `needs_input` or `blocked`, with the affected work identified.
- Stop after the plan. The caller owns implementation and any user-requested approval gate; invoking this skill alone does not start coding.
