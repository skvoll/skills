---
name: deliver
description: Commit a prepared change and create or prepare a PR for human review. Offer history cleanup and separate opt-in CI/comment watchers; merge only on direct request.
---

# Deliver

Prepare a PR for human review. A human clicks merge unless directly requested otherwise.

Handoffs: use available `explain`; otherwise concise, faithful English.

## Authority

- Explicit invocation permits a delivery branch, staging, commits, normal pushes, and creation/preparation of the intended PR, including draft promotion.
- History rewriting needs approval of the exact plan; published history also needs force-push authorization.
- Watchers are separate opt-ins. Green CI, approval, or completed delivery never authorizes merge, auto-merge, or queueing.
- Only a direct user request to merge that PR permits agent merging: check current head, required checks/reviews, and protections; merge normally and verify remote state.
- Preserve user work and staging. Never bypass protections. Unrelated messages, settings, secrets, releases, deployments, and infrastructure need separate authority.

## Inspect and commit

- Read guidance, contribution/versioning rules, checks, and PR templates. Inspect status, branch, remotes, upstream, staging, relevant untracked files, and full diff against the intended base.
- Find an existing PR by repository, head owner/branch, and base, not worktree path. Inspect state, description, checks, and feedback; ask about ambiguous targets.
- Reuse the matching open PR. Do not automatically reopen closed PRs or reuse merged ones; identify undelivered work and propose a new PR where needed.
- Stop if no local change, undelivered commit, or PR needing preparation exists.
- Select exact hunks; explain inseparable overlap before Git mutations. Validate locally and inspect staged content.
- Apply required versioning once, updating manifest and lockfile together without implicit tags/commits.
- Commit intended changes with an outcome-focused subject. Already committed work needs inspection, not an artificial commit.

## Offer history cleanup

- After committing, inspect delivery history with `git log --graph --oneline --decorate <base>..HEAD` and diffs. Resolve the integration base and distinguish prior squash-merged work.
- Identify misleading messages, fixups, duplicates, and corrections obscuring review. Multiple coherent commits need no squash.
- When useful, show exact commit IDs and proposed sequence; offer **Keep history (default)** or that cleanup through host UI/CLI, with numbered-text fallback. Install no UI dependency.
- Cancellation or no answer keeps history; never rewrite pending approval. Prior instructions count only for the exact plan.
- For published history, explain collaborator/review effects and obtain explicit rewrite and force-push approval.
- Before approved cleanup, recheck worktree and tips, preserve a recoverable original tip, and exclude unrelated commits. Use authorized force-with-lease against the observed remote tip; preserve concurrent work.
- Verify the approved tree and rerun affected checks afterward.

## Describe and publish

- Follow the PR template; otherwise use **What / Why / Validation**, adding real risks or migration notes only when relevant.
- Describe the concrete problem and final behavior, with a small before/after example if useful. Preserve human-authored context; ask about conflicts.
- Remove stale claims, placeholders, empty sections, and development transcripts. Distinguish passed, failed, skipped, unrun, and pending checks.
- Apply the handoff pass to the description before publication; retain repository format.
- Push and verify the remote head. Create or update the matching PR without duplicates; verify base, head, title, description, and scope.
- Finish draft preparation, then mark ready through the host or `gh pr ready <pr>`. Honor explicit keep-draft instructions and report that exception.
- Inspect current-head checks, mergeability, and unresolved feedback once; this snapshot starts no watcher.
- Fix narrow delivery defects, validate, commit, push, and refresh context. Diagnose failures without weakening checks or fabricating approvals/thread resolution.
- Report unresolved conflicts, failures, blocking feedback, credentials, or decisions without claiming readiness. Pending CI may coexist with review; wait only if requested or required before handoff.

## Handoff

- Report URL, commit, readiness, blockers, and check snapshot. Review-ready does not mean approved, green, or merged.
- Offer **Neither (default) / CI only / Comments only / Both**, using independent unchecked choices or text fallback. Honor an existing explicit preference without asking again.
- Silence/cancellation leaves unrequested watchers off and does not block handoff. Read [watcher instructions](references/watchers.md) only for selected scopes.
- State which watchers actually started. Leave no unrequested polling loop running.
