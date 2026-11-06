---
name: task
description: Analyze a change, get approval for a clear plan, then implement and validate it locally. Use for code, configuration, or documentation tasks.
---

# Task

Analyze → propose → clarify → approve → implement → verify.

Handoffs: use available `explain`; otherwise concise, faithful English.

## Analyze

- Read the request, accepted clarifications, repository guidance, status, and relevant diffs. Preserve unrelated work and staging.
- Derive observable acceptance criteria; find the implementation and verification boundaries.
- For bugs, reproduce or gather distinguishing evidence. For docs, identify the reader, decision, and discovery path.
- Resolve facts from source. Reserve consequential unknowns for plan review unless they block analysis.
- Stay read-only: no edits, installs, generation, or state-changing services. Put required setup or reproduction mutations in the plan.

## Propose and clarify

- Show the goal, findings, ordered steps, affected areas, assumptions, risks, and scope limits.
- Pair each outcome with acceptance criteria and its validation check, including needed docs or tests.
- Scale the plan to the task; clear tickets and tiny edits still need one.
- Ask only unresolved questions that change the outcome. Offer concrete tradeoffs and accept comments.
- Incorporate answers and show the final plan. Clarification answers do not authorize implementation.

## Approve

- Offer **Approve and implement / Revise with comments / Pause** through supported host UI, CLI, or connected agent capabilities; otherwise use numbered text choices.
- With ACP, follow the negotiated capabilities. Displaying a plan or switching modes is not user approval.
- Wait for explicit approval of the presented version. Defaults, silence, cancellation, timeout, and unavailable input do not count; report the pending gate if input is impossible.
- Revisions need a revised plan and approval. Once approved, resolve routine in-scope choices without repeated questions.
- Pause affected work for material changes to scope, behavior, risk, or acceptance criteria.

## Implement and verify

- Follow the approved plan in observable, checked increments; keep progress visible.
- Use existing interfaces where suitable; check affected error paths, lifecycle, security, accessibility, performance, and compatibility.
- Verify consequential API assumptions against current primary sources and installed versions.
- When a regression test helps, see it fail for the expected reason, then fix behavior through a stable interface. Do not mirror private structure.
- Use structural review for low-impact documentation changes. Update durable guidance at its source.
- Run required checks; broaden only for affected surfaces. Diagnose failures without weakening checks; distinguish pre-existing defects and environment limits.
- Review the final diff against the plan. Remove only task-created accidents and temporary artifacts.
- Report changes, validation, and uncertainty. Leave work local; approval does not authorize delivery or unrelated side effects.
