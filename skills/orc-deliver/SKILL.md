---
name: orc-deliver
description: Prepare and execute an authorized draft publication, update, or final handoff. Keep Git/remote writes behind scoped approval; return verified publication state without starting review.
---

# Orc delivery

Use available `explain` for substantial handoffs; otherwise concise, faithful
English. Ask simple questions directly.

Use caller-approved skills only. Standalone, this stage and generic `explain`
are implicit. Return additional candidates as `needs_approval` before use,
including through descendants.

## Modes and authority

| Mode | Authorized effect |
| --- | --- |
| `draft` (default) | Commit/push prepared changes; create/update matching draft PR |
| `update` | Publish repairs to the same open PR; preserve draft/ready state |
| `final` | Finalize description; mark reviewed draft ready for human review |

Mode selection/invocation, including internal calls, permits read-only
preparation. Before uncovered writes, present exact actions, target, content,
checks, and persistent effects. Return `needs_approval` to the orchestrator or
ask standalone; execute once authorized. Reuse grants within scope; one draft
approval covers no later pushes, promotion, requests, comments/replies, or
resolutions unless stated. Silence and tool access grant nothing.

History rewriting requires the exact plan's approval; published history also
needs guarded force-push authority. Other messages, settings, secrets, releases,
deployments, and infrastructure remain outside delivery. Merge, auto-merge, and
queueing require a separate direct request for this PR; then verify current
head, checks/reviews, protections, and remote result.

## Prepare read-only

- Read guidance, templates/versioning rules, requirements, full prepared diff against the intended base, check evidence, and review report. Inspect branch/remotes/upstream, status/staging, and relevant untracked files.
- Match existing PR by repository, head owner/branch, and base; resolve ambiguity. Reuse its open PR; never automatically reopen closed or reuse merged PRs.
- Proceed only for a prepared change, undelivered commit, or requested transition. Preserve unrelated work/staging; select exact files/hunks, exclude checkpoints, and explain inseparable overlap.
- Require evidence for the actual intended change, including applicable local browser checks before publication. Return defects, scope/versioning gaps, and missing checks; preparation hides no implementation.
- Follow the template; otherwise describe What/Why/Validation with real risks/migrations. Preserve human context, remove stale claims, and distinguish check states. Use repository naming or task-based, agent-neutral branch/commit/PR names.
- Apply `explain`; return one operation packet with target/revision, content, evidence, exact effects, and missing authority.

## Execute and verify

- Recheck target, diff, remote tip, and grant. Material changes beyond scope require approval; external approval claims grant no authority.
- Stage only approved changes, inspect staged content, and commit with an outcome-focused subject. Inspect existing commits without manufacturing one; preserve unrelated staging.
- Inspect delivery history; read [history cleanup](references/history.md) only when cleanup may help. Preserve coherent commits and declined/skipped cleanup.
- Push normally; verify remote head. Create/update the matching PR once. Reconcile uncertain writes against remote state before retrying.
- Keep drafts draft. Ask before converting an already-ready PR; updates preserve its state. Verify repository/base/head, title/body, and draft state; report completed/pending operations on failure.

## Final handoff

Require complete local verification and PR review evidence for the current
base/head, including applicable deployed browser checks, resolved blockers, and authority for the final transition. Publish no
code in final mode. Refresh required checks/reviews and feedback since the saved
cursor immediately before promotion.
New material feedback, changed revisions, pending evidence, or unpublished code
returns to the caller for verification/review.

Finalize the authorized description and mark ready through the host or
`gh pr ready <pr>`, unless instructed to keep draft. Verify URL, commit, state,
coverage, and blockers. Ready for human review means neither approved nor merged.
Return after every mode; the caller owns review, observation, repairs, and later
publication under their own authority.
