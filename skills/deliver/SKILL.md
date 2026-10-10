---
name: deliver
description: Commit and push a prepared change, follow its PR checks and review, and merge when permitted. Use only when the user explicitly invokes deliver.
---

# Deliver

Carry the prepared change through the repository's delivery workflow and verify
its final state. Reading, rewriting, or discussing this skill does not activate it.

## Authorization

Explicit invocation authorizes, for this intended change only: creating a
delivery branch when needed; staging and committing; pushing; creating or
updating its PR; monitoring checks and reviews; triggering checks required by
the normal workflow; committing and pushing narrow delivery fixes; and normal
merge when protections and reviews permit it without separate human approval.
Existing user constraints and environment restrictions still apply.

This excludes force-pushing, rewriting existing history, discarding user work,
bypassing checks or reviews, changing settings or secrets, and unrelated messages,
releases, deployments, publications, or infrastructure work. If the workflow
crosses an additional boundary, prepare the local work and request only the
missing authorization.

## Prepare the delivery

Read repository instructions, contribution guidance, validation commands, and PR
templates. Inspect the branch, remotes, upstream, staged and unstaged diffs,
relevant untracked files, and the full intended change against its base. Check
for an existing PR and follow repository branch and commit conventions.

Identify exact files or hunks to deliver. Preserve unrelated changes and existing
staging; if the work cannot be separated safely, explain the overlap before
changing Git state. If no prepared change exists, report that instead of
manufacturing a commit.

Apply the repository's versioning policy before the delivery commit. When a
version bump is required, inspect whether this change already contains it,
update the package manifest and corresponding lockfile together, and include
them with the intended change. Do not create a second bump for the same delivery
or let a version command implicitly create a tag or commit.

Run required local validation and inspect the final staged diff. Include only
the intended change and required release metadata. Prefer one coherent commit;
follow repository conventions when independently reviewable units need more.
Write a subject that describes the behavior or outcome.

## Submit and observe

Push to the intended remote and branch. Create or update the PR if that is the
repository's normal workflow. Describe the problem and resulting behavior,
validation performed, and any real migration or reviewer concern. Respect the
template; avoid development transcripts and empty sections.

Inspect checks, review decisions, mergeability, and protections for the current
PR head. Monitor at reasonable intervals using available waiting facilities.
After a new push, reassess checks and approvals for that revision; a previous
green result does not establish that the new head is ready.

## Resolve delivery blockers

Diagnose failures before editing. For a narrow defect caused by this change,
correct it, run relevant checks, review and commit the correction, push, then
resume observation. Evaluate review feedback against the task before applying
it. Retry a transient check only with evidence that a retry is justified.

Never weaken tests or protections to get a green result. Stop for a decision when
a blocker requires new behavior, substantial redesign, unrelated work, unavailable
credentials, or additional authority. Recommend implementation or refinement when
appropriate; do not invoke another workflow on the user's behalf. Unchanged
pending CI or review is a reason to wait, not a failure. If monitoring cannot
continue, report the exact pending dependency.

## Verify completion

Merge only when the current head satisfies required checks, approvals, and
repository rules and no separate human decision is required. Use the normal
merge method and verify the resulting remote state. Do not assume success from
a command's exit status alone or perform unrelated post-merge cleanup.

For a documented direct-push workflow, verify that the intended remote branch
contains the commit and report any required checks. Otherwise, completion means
a verified merge; a pushed branch or open PR is an intermediate state.

Report the commit, PR when applicable, check/review status, delivery fixes, and
the verified outcome or precise remaining dependency.
