---
name: git-prune
description: Clean up outdated local Git branches and linked worktrees, using interactive checklists or radio choices when deletion is uncertain. Use for repository housekeeping or removing merged worktrees and branches.
---

# Git Prune

Remove confirmed outdated local branches and linked worktrees. Resolve uncertain
targets through interactive choices.

## Authority

- Invocation authorizes normal removal of confirmed outdated linked worktrees, confirmed merged local branches, and confirmed stale worktree registrations.
- Scope includes this repository's registered worktrees outside the current directory, subject to active instructions and environment permissions.
- Reading, editing, or discussing this skill does not invoke cleanup.
- Preview and dry-run requests authorize inspection and a proposed plan only.
- Do not delete remote branches, fetch, prune remote-tracking refs, change configuration, or switch branches.
- Do not discard work, reset, stash, run `git clean`, collect garbage, expire objects, or recursively delete directories.
- This workflow does not run `git prune`.
- Force needs explicit authorization for the exact target and consequences. Generic cleanup or ordinary removal approval is insufficient.

## Inventory

- Read applicable instructions. Resolve the target repository and common Git directory.
- Inspect only that repository and its registered worktrees.
- Record and protect both the current and main worktrees.
- Use `git worktree list --porcelain -z` and `git for-each-ref` over `refs/heads/`.
- Preserve full paths, ref names, and commit IDs with structured output.
- Do not parse whitespace-separated columns or pipe branch names into bulk deletion.
- Inspect every candidate. Show exact branch/path, tip, proposed action, evidence, and risk.

## Establish integration

- Choose the integration base from project guidance, the user's choice, or an unambiguous default branch.
- Do not assume the current feature branch is the base.
- Protect default, integration, established long-lived, and user-retained branches.
- Ask before deleting when the base or branch purpose is unclear.
- Record each candidate's tip, upstream, integration reachability, and associated worktrees.
- Find local branches used as upstreams by retained branches; keep those upstreams.
- Check ancestry with `git merge-base --is-ancestor` on recorded commit IDs.
- Distinguish exit 1 (not an ancestor) from command failure.
- Age, absent upstreams, matching names, and closed PRs do not prove safe deletion.
- Squash or rebase merges need evidence covering the current tip and a user decision when ancestry cannot prove integration.
- Remote-tracking refs may be stale. Use read-only remote or PR information when needed; do not fetch implicitly.
- Unproven freshness or integration makes a candidate uncertain.

## Inspect worktrees

- Inspect staged and unstaged changes, untracked and ignored files, submodules, locks, worktree-specific refs, and in-progress Git operations.
- Resolve metadata through Git; a worktree may have a `.git` file rather than a directory.
- For a resolved `worktree_path`, inspect status without refreshing the index:

```sh
git --no-optional-locks -C "$worktree_path" status \
  --porcelain=v1 -z --untracked-files=all --ignored --ignore-submodules=none
```

- Normal clean status does not prove ignored files disposable.
- Check active use. A merged branch or old commit does not prove abandonment.
- A missing path may be moved, inaccessible, or on an unmounted device.
- Before removing a worktree or registration, prove its HEAD and worktree-specific refs remain reachable from refs retained after the entire cleanup.
- Its own reflog and other deletion candidates do not establish preservation.

## Classify

### Confirmed outdated

- A disposable topic branch with its tip reachable from the integration base.
- Its linked worktree, if clean, unused, unlocked, and with preserved history.
- Worktree removal also requires disposable ignored contents, no submodules needing preservation, and no in-progress operation.
- A stale registration needs evidence of intentional worktree removal; an absent path alone is insufficient.

### Keep

- Current and main worktrees, protected branches, and active worktrees.
- Branches checked out in retained worktrees or used as local upstreams by retained branches.
- Explicit user keep decisions and their dependencies take priority over automatic eligibility.
- Never switch or detach a retained worktree, or change tracking, to enable deletion.

### Uncertain

- Ambiguous integration, purpose, or use; local-only commits or detached history.
- Dirty or locked worktrees, unexplained ignored files, submodules, or missing paths.
- Any failed inspection.
- Preserve these until a decision resolves the uncertainty.

For a preview or dry run, report classifications and proposed actions, then stop.

## Ask about uncertain targets

- Use the host's interactive question UI.
- Prefer independent checkbox targets, initially unchecked, with exact names and consequences.
- With single-choice UI, offer applicable choices per target: “Keep (recommended)”, “Remove worktree only”, or “Remove worktree and local branch”.
- For a branch alone, offer “Keep” and “Delete local branch”.
- Explain uncertainty and data at risk. Batch within host limits without a blanket deletion choice.
- Keep worktree removal and branch deletion separately selectable.
- A keep or worktree-only decision overrides automatic branch eligibility.
- Retaining a worktree requires retaining its checked-out branch; offer only valid combinations.
- If force is needed, ask separately and name the exact operation and work at risk.
- Without interactive UI, request selected numbers from a numbered checklist. Do not install UI dependencies.
- Cancellation, no answer, or an unselected target means keep. A timeout is not approval.
- Complete independent confirmed cleanup while waiting; do not mutate uncertain targets.

## Recheck before each mutation

- Recheck the exact target, tip, integration evidence, registration, status, locks, and retention dependencies.
- Confirm preservation refs survive every planned removal.
- Reclassify changed targets. Obtain a fresh decision where needed.
- Run from a retained worktree. Quote exact arguments and use option terminators where supported.

## Remove

- Remove eligible or specifically approved worktrees with `git worktree remove <path>`.
- Honor keep and worktree-only decisions.
- Delete branches only when independently eligible or specifically approved, and absent from all remaining worktrees.
- Use `git branch -d -- <branch>`.
- Keep the independent integration check: `-d` checks upstream or HEAD, which may differ from the chosen base.
- On refusal, diagnose. Do not automatically force, use `-D`, unlock, or bypass Git safeguards.

## Prune registrations

- Inspect `git worktree prune --dry-run --verbose`.
- Pruning is repository-wide. Proceed only when every listed entry is confirmed or specifically approved.
- Use the same explicit expiration cutoff in preview and execution, if any.
- Recheck the dry run immediately before execution. Never broaden the cutoff implicitly.
- If the batch includes a retained item, leave it alone and report the limitation.
- Do not edit Git administrative files to work around the batch boundary.

## Verify

- Re-list worktrees and local branches.
- Verify intended removals and unchanged retained worktrees and branches.
- Report removed paths, branches and former commit IDs, pruned registrations, and kept or blocked items with reasons.
- State that worktree contents were deleted. Do not promise reflog recovery, especially for untracked or ignored files.
- If nothing qualifies, report that no cleanup was needed.
