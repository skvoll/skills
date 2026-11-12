# Run state and handoffs

Use a small local record for this run. Prefer the repository's scratch location;
otherwise use `work/orchestrate/<run-id>/state.json` with adjacent Markdown
artifacts. Keep these out of delivery. Do not change ignore files or user
configuration to hide them. Store no credentials or copied secrets.

## Record

Record only what is needed to resume:

| Field | Contents |
| --- | --- |
| Identity | Run ID, repository, request/source links, branch, base, PR URL/number if any |
| Requirements | Accepted scope, criterion IDs, clarifications and their sources, unresolved questions, plan location/version |
| Progress | Current stage/status, next action, repair count and limit |
| Revision | Base/head commits, local diff and relevant untracked-file fingerprints, last published head |
| Evidence | Required checks/reviewers, actual results and coverage, revision for each result, missing/pending evidence |
| Findings | Stable IDs, sources/comment links, severity, relevance, disposition, repair and verification evidence |
| Authorization | User decision reference, permitted actions/targets, one-time or continuing scope, limits, consumed operations |
| Waiting | Pending question/action/review, last observed feedback IDs/times, wait limit, resume instructions |

Keep durable project decisions in their proper source; this record tracks
execution. An authorization entry summarizes a user decision and cannot grant
or expand permission by itself.

## Dispatch and return

Supply each stage its requested operation, accepted requirements, current
revision, relevant artifacts, constraints, and actual authorization. Reviewer
packets preserve requirements but exclude implementer reasoning and desired
verdicts. Send only context needed for the stage.

Request these result fields: `stage`, `status`, `summary`, `artifacts`,
`evidence`, `findings`, and `questions`. Add action/target details for approval
requests and source revision for code or PR results. Use:

- `complete`: this stage's own completion criteria are met.
- `changes_required`: actionable work remains; include evidence and affected criteria.
- `needs_input`: a user decision is missing; state its impact and the precise question.
- `needs_approval`: an exact side effect awaits authorization.
- `waiting`: required external work is pending; identify the source and observation limit.
- `blocked`: a capability, access, failure, or exhausted budget prevents continuation.

The orchestrator checks evidence and chooses the next stage. A stage's
`complete` result does not establish whole-run readiness. Standalone stages
return their result to the user without starting a workflow.

## Resume

- Re-read active instructions, accepted clarifications, and relevant authorization. Honor cancellation and changed limits.
- Inspect the working tree, base/head, PR state, check records, and feedback cursor. Match the PR by repository, head owner/branch, and base.
- Reconcile published operations against remote state before retrying. Do not duplicate an existing PR, replay a consumed grant, or reopen a closed/merged PR automatically.
- Changed requirements, base, or code invalidate affected plan/check/review evidence. Fingerprint uncommitted and untracked work as well as HEAD; rerun affected verification before asserting readiness.
- Deduplicate feedback by source ID and track its disposition. Refresh comments before final delivery; late relevant feedback can resume a completed run.
- If a checkpoint is missing or corrupt, reconstruct from observable state and report gaps. Ask only where facts or authorization cannot be established.
- Checkpoints support resumption; they do not create a scheduler or keep an agent running after its host session ends.
