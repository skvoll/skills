---
name: deliver
description: Commit and push a prepared change, follow its PR checks and review, and merge when permitted. Use only when the user explicitly invokes deliver.
---

# Deliver

Carry a prepared change through delivery and verify its final remote state.

## Authority

- Only explicit invocation activates delivery. Reading, editing, or discussing this skill does not.
- For the intended change, invocation authorizes a delivery branch, staging, commits, pushes, and PR creation or updates.
- Monitor reviews and checks. Trigger checks required by the normal workflow.
- Commit and push narrow delivery fixes.
- Merge normally when protections and reviews permit it without separate human approval.
- Active user constraints and environment restrictions still apply.
- Do not force-push, rewrite existing history, discard user work, or bypass checks or reviews.
- Settings, secrets, unrelated messages, releases, deployments, publications, and infrastructure work need separate authorization.
- Prepare independent local work before requesting any missing authority.

## Inspect

- Read repository instructions, contribution guidance, validation commands, and PR templates.
- Inspect branch, remotes, upstream, staged and unstaged diffs, relevant untracked files, and the full intended change against its base.
- Check for an existing PR. Follow branch and commit conventions.
- Select exact files or hunks. Preserve unrelated changes and existing staging.
- If changes cannot be separated safely, explain the overlap before changing Git state.
- If no prepared change exists, report that; do not manufacture a commit.

## Prepare

- Follow repository versioning policy before committing.
- If a bump is required, check whether it already exists. Update the manifest and corresponding lockfile together.
- Never duplicate a bump or let a version command create an implicit tag or commit.
- Run required local validation. Inspect the final staged diff.
- Include only the intended change and required release metadata.
- Prefer one coherent commit; use independently reviewable units when repository conventions require them.
- Describe the behavior or outcome in the commit subject.

## Submit

- Push to the intended remote and branch.
- Create or update the PR when that is the normal workflow.
- Describe the problem, resulting behavior, validation, and real migration or reviewer concerns.
- Follow the PR template. Omit development transcripts and empty sections.

## Observe the current head

- Inspect checks, review decisions, mergeability, and protections for the current PR head.
- Monitor at reasonable intervals using available waiting facilities.
- After every push, reassess checks and approvals for that revision.
- A previous green result does not validate a new head.
- Unchanged pending CI or review calls for waiting, not a speculative fix.
- If monitoring cannot continue, report the exact pending dependency.

## Resolve blockers

- Diagnose failures before editing.
- For a narrow defect caused by this change: fix, check, review, commit, push, and resume observation.
- Evaluate review feedback against the task before applying it.
- Retry transient checks only when evidence supports a retry.
- Never weaken tests or protections for a green result.
- Stop for a decision when a blocker needs new behavior, substantial redesign, unrelated work, credentials, or additional authority.
- Recommend implementation or refinement when appropriate; do not invoke it on the user's behalf.

## Verify completion

- Merge only when the current head meets required checks, approvals, and repository rules, with no separate human decision pending.
- Use the normal merge method. Verify resulting remote state beyond command exit status.
- Do not perform unrelated post-merge cleanup.
- For a documented direct-push workflow, verify the remote branch contains the commit and report required checks.
- Otherwise, completion means a verified merge. A push or open PR is intermediate.
- Report commit, PR if applicable, checks, review status, delivery fixes, and the verified outcome or precise dependency.
