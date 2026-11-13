# Run state and handoffs

Keep one small local record in repository scratch, otherwise
`work/orc/<run-id>/state.json`, with purpose-named artifacts such as `plan.md`,
`review.md`, and `validation.md`. Reuse the location on resume; exclude it from
delivery without changing ignore files/configuration. Store no credentials or
copied secrets. Durable decisions belong at their source.

## Record only resumption evidence

| Field | Contents |
| --- | --- |
| Identity | Run/repository, request links, branch/base, PR |
| Requirements | Scope, criterion IDs, sourced clarifications, plan version, unresolved questions |
| Progress | Stage/status, next action, repair count/limit |
| Revision | Base/head, local diff and relevant untracked fingerprints, last published head |
| Evidence/findings | Required/actual checks and reviewers, coverage/revisions, gaps; browser URL/environment, served revision, deployment, steps/results/artifacts; stable issue IDs, sources, severity, relevance, disposition, repair/verification evidence |
| Authority | User decision reference, actions/targets, one-time/continuing scope, limits, consumed operations |
| Skills | Exact default/candidate sources and identities, discovery context, role/helper scope, source versions, approved/declined/pending decisions, worker allowlists |
| Observation | Owner/transport/handles/scopes, cadence/deadline, fetch/next-check times, per-source received versions and acknowledged cursors, undelivered events/dispositions, unfinished work and resume point |

Records summarize user decisions; they grant no authority.

## Dispatch and return

Send self-contained stage inputs: operation, complete accepted requirements/criteria,
revision, relevant authoritative artifacts, constraints, actual grants, and exact
skill identities/scopes/prior decisions. Preserve the outside-skill approval
boundary through descendants. Keep role separate from replacement identity.
Reviewer packets omit implementer reasoning and desired verdicts. Reference
accessible artifacts instead of replaying history; omit no decisive requirement.

Request `stage`, `status`, `summary`, `artifacts`, `evidence`, `findings`, and
`questions`. Add source revision for code/PR results, exact targets/effects for
approval, and events/coverage/unfinished handles for partial observations.

| Status | Meaning |
| --- | --- |
| `complete` | This stage's own criteria met, not whole-run readiness |
| `changes_required` | Actionable work remains; give evidence and criteria |
| `needs_input` | Missing user decision; give impact and precise question |
| `needs_approval` | Exact outside skill/use or effect awaits authority |
| `waiting` | Required evidence pending, no actionable result; identify sources/deadline |
| `blocked` | Capability/access/failure/budget prevents continuation |

Pending work cannot suppress validated blockers. Receiving evidence, triaging a
finding, and verifying a repair are distinct. The controller chooses successors;
standalone stages return to the user.

## Resume

- Reread instructions, requirements, grants, cancellation, and limits. Revalidate skill sources/scopes; reuse unchanged approvals/declines, never pending decisions.
- Inspect tree, base/head, PR, checks, feedback cursors, and handles. Match PR by repository, head owner/branch, and base. Reconcile uncertain writes before retrying; duplicate no PR or watcher, replay no consumed grant, reopen nothing automatically.
- Changed requirements/base/code invalidate affected evidence. Fingerprint uncommitted/untracked work too; unchanged HEAD is insufficient.
- Replay unacknowledged events by source ID/version, preserving edited IDs. Keep the original deadline; refresh feedback before final delivery. Late relevant feedback can reopen a completed run.
- Reconstruct missing/corrupt checkpoints from actual state; disclose gaps and ask only for unresolved facts/authority. Checkpoints create no scheduler or execution after the host session ends.
