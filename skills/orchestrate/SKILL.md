---
name: orchestrate
description: Turn a ticket, brief, or detailed prompt into a locally verified change, then an approved draft PR and review-driven repairs. Coordinate orch-plan, orch-implement, orch-refine, orch-deliver, and orch-review; ask before uncovered side effects.
---

# Orchestrate

Own stage selection, questions, approvals, repair budgets, and resumption.
Stages return results; they do not launch their successors.

Use the generic `explain` skill for plans, substantial decisions, and reports;
otherwise use concise, faithful English. Ask simple questions directly.

## Start or resume

- Accept a ticket, description, prompt, or existing run/PR context. Read relevant sources and repository guidance; preserve unrelated work and staging.
- Resolve the repository, request, and intended outcome from evidence. Ask about consequential unknowns instead of inventing requirements.
- Locate all five stage skills. Report missing stages before dependent work; do not silently replace them or install tools/configuration.
- Read [run state and handoffs](references/run-state.md). Establish or resume one run record; inspect current local and remote state before trusting saved results.
- Invocation permits ordinary local development and read-only review, including stage reviewers. It grants no staging, commits, branch/worktree changes, pushes, PR writes, messages, or merge authority.
- Stage calls inherit the run's actual authorization. Calling `orch-deliver` internally grants no additional permission. Respect user limits such as plan-only or stop-before-publication.

## Local loop

1. Call `orch-plan` with the full request and accepted clarifications. Resolve missing decisions through the user; continue independent investigation while waiting.
   If evidence shows the requested outcome already holds, verify and report no change needed; do not manufacture a change or PR.
2. Present the grounded plan through `explain`. Continue into local implementation under this invocation unless the user requires plan approval; clarification is never approval for an unrelated action.
3. Call `orch-implement`, then `orch-refine`. Pass the plan, acceptance criteria, current change, and relevant evidence.
4. Route remaining implementation findings back to `orch-implement`; replan when evidence invalidates the approach. Ask before changing intended scope or behavior.
5. Declare local readiness only when acceptance criteria are supported, required local checks pass, and blocking findings or consequential questions are resolved. Missing or unrun evidence cannot establish readiness.

## Approve and deliver

- Have `orch-deliver` prepare the concrete operation in `draft` mode, or `update` for the existing PR. Preparation is read-only.
- Present the change, check results, exact Git/remote actions, target, and persistent effects. Without covering authorization, ask: **Locally this is ready. Should I publish the draft PR?** Adapt the wording for an update or final delivery.
- Record the user's exact scope. Approval for one publication does not cover future pushes, reviewer requests/comments, thread resolution, or draft promotion unless explicitly included. Reuse a broader grant within its limits.
- Silence, defaults, cancellation, timeout, and unavailable input do not grant approval. Save the pending action and stop dependent work. Never treat approval to publish as approval to fix a newly discovered product ambiguity.
- On approval, execute the prepared delivery and verify its result. Reconcile uncertain outcomes before retrying; retain the same branch and matching open PR.

## PR loop

1. After draft publication or an update, call `orch-review` against the actual PR revision. Gather its fresh reviews, external feedback, and check results.
2. Return actionable code findings to `orch-implement`, then `orch-refine` and verification, using the existing plan. Return approach gaps to planning; route consequential requirement conflicts to the user through `explain`.
3. Publish repairs through the delivery gate, then review the updated PR. A local repair does not resolve a finding on an unchanged remote revision.
4. For required pending evidence, use supported bounded waits. On timeout or unavailable monitoring, checkpoint and report waiting/blocked status; never infer success or promise unsupported background work.
5. Call `orch-deliver` in `final` mode only when current-revision evidence is complete, blocking findings are resolved, and final delivery is authorized. Refresh feedback before promotion; new material findings reopen the loop.
6. Report the PR, delivered revision, verification, review coverage, and remaining limitations. End at ready for human review. Merging is outside this run.

## Stop and recover

- Use a user-specified repair budget, otherwise three corrective cycles across the run. Count each return for repairs or replanning, batching findings; exclude the initial pass. Replanning does not reset the budget. Stop earlier when the same blocker recurs without new evidence or progress.
- On exhaustion, missing capability, or conflicting requirements, use `explain` to show evidence, attempted repairs, options, and the decision needed. Do not weaken criteria or discard findings to finish.
- Checkpoint after every stage, approval, external result, and pause. Never repeat an uncertain write or reuse stale review evidence merely because a saved stage says complete.
