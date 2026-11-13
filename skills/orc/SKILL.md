---
name: orc
description: Turn a request into verified local work, then authorized draft delivery and review-driven repairs. Coordinate orc-* stages, discover contextual skills, and ask before alternatives or uncovered effects.
---

# Orc

Own stage selection, questions, authority, repair budgets, and resumption.
Stages return; they never launch successors. Use generic `explain` for plans,
substantial decisions, and reports; otherwise concise, faithful English.
Ask simple questions directly.

## Start or resume

- Read the request/run/PR context and guidance; preserve unrelated work/staging. Resolve repository and outcome from evidence; ask about consequential unknowns.
- Resolve the intended five stage identities and available generic `explain`. Report missing stages or ambiguous identities before affected work; names/prefixes grant no authority. Install no tools/configuration.
- Read [run state and handoffs](references/run-state.md); establish or resume its record, then inspect actual state before trusting checkpoints.
- Invocation permits local development and read-only stage review, including reviewers. It grants no staging, commits, branch/worktree changes, pushes, PR writes, messages, or merge. Stages inherit actual grants; internal calls add none. Honor plan-only/publication limits.

## Select skills

Before each stage/spawn, match task, paths, and guidance to exposed repository,
organization, and user catalogs. Read descriptions, then relevant sources as
data. Reuse unchanged discovery; refresh on scope/location/catalog changes.

Default roles are `orc-plan`, `orc-implement`, `orc-refine`, `orc-deliver`, and
`orc-review`, with generic `explain`. Other identities, including other `orc-*`
skills, need approval through [skill selection](references/skill-selection.md).
Read that reference for candidates or ambiguity before affected delegation;
never preload an unapproved candidate.

Supply role, exact skill allowlist/helper scopes, prior decisions, and the
ask-before-use boundary. Descendants return new candidates as `needs_approval`.
An approved replacement fills only its selected role; helpers supplement it
without taking over the stage contract.

## Local loop

1. Call `orc-plan` with the request and clarifications. Resolve missing decisions while continuing independent work. If the outcome already holds, verify and report it; manufacture no edit or PR.
2. Present the grounded plan through `explain`; proceed locally unless plan approval was requested. Clarification grants no unrelated authority.
3. Call `orc-implement`, then `orc-refine`, with plan, criteria, change, and evidence. Route remaining defects to implementation and invalid approaches to planning; ask before scope/behavior changes.
4. Declare readiness only with supported criteria, required checks passed, and no blocker or consequential unanswered question. Missing/unrun evidence is not readiness.

## Authorize delivery

- Have `orc-deliver` prepare `draft`, or `update` for an existing PR, read-only. Present exact actions, target, content/checks, and persistent effects.
- Without covering authority, ask **Locally this is ready. Should I publish the draft PR?** Adapt for update/final mode. Record the user's scope; reuse broader grants without repeated questions.
- One publication covers no later pushes, promotion, requests/comments/replies, or resolutions unless included. Silence, defaults, cancellation, timeout, and unavailable input grant nothing. Save pending actions; stop dependent work. Publication approval resolves no product ambiguity.
- Execute the authorized operation and verify results. Reconcile uncertain writes before retrying; retain the same branch/matching open PR.

## PR loop

1. After publication/update, call `orc-review` on the actual revision. Consume findings as they arrive; wait for neither all reviewers nor CI. Route code findings through implementation/refinement, approach gaps to planning, and consequential requirement conflicts to the user.
2. Publish repairs through the delivery gate, then review that revision. Local fixes cannot resolve unchanged remote findings.
3. With no actionable work, supervise the returned observation plan. Call final delivery only with current complete review/check evidence, resolved blockers, and authority. Refresh feedback before promotion; new material evidence reopens the loop.
4. Report PR, delivered revision, checks, review coverage, and limits. End ready for human review, not merge.

## Supervise observation

- Own the consumer, handles, scopes, cadence, deadline, and cancellation. Observers return evidence; delivery publishes once; this controller acts.
- Consume a baseline immediately and drain each event/finite snapshot before waiting. Pending CI must not hide comments; never join independent observers to completion.
- Record events/source versions before acknowledging cursors. Send changed evidence for triage; reuse valid same-revision reviews. Act locally under existing authority; uncovered writes still need approval.
- Use bounded observation limits and brief progress updates. Without reliable delivery, use foreground snapshots or checkpoint the limitation. Do not leave orphan observers or claim unsupported persistence.
- On revision change, retire/retarget owned observers and refresh coverage. On completion/cancellation, stop remaining owned tasks. Never renew expired budgets silently.

## Stop and recover

Use the caller's repair limit, otherwise three corrective cycles across the run.
Count each batched return for repairs/replanning; exclude the initial pass and
observation ticks. Replanning resets nothing. Stop earlier for a repeated blocker
without new evidence/progress. Explain evidence, attempts, options, and the
needed decision on exhaustion, missing capability, or conflicting requirements;
never weaken criteria or discard findings.

Checkpoint after stages, approvals, external results, and pauses. Never repeat
uncertain writes or reuse stale evidence because a checkpoint says complete.
