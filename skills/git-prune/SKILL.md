---
name: git-prune
description: Clean confirmed outdated local branches and linked worktrees; prompt per uncertain target. Preview without mutation when requested.
---

# Git Prune

Handoffs: use available `explain`; otherwise concise, faithful English.

## Scope

- Invocation permits ordinary removal of confirmed outdated local branches, linked worktrees, and stale registrations in this repository, including registered external paths under active permissions.
- Preview/dry run inspects only. Reading or editing this skill invokes nothing.
- Exclude remote branches/refs, fetching, configuration, branch switching, resets, stashes, `git clean`, garbage collection, object expiry, and recursive filesystem deletion. Never run `git prune`.
- Force requires explicit approval of the exact operation, target, and consequences; ordinary cleanup/removal consent is insufficient.

## Inventory

- Read guidance; resolve the repository/common Git directory and only its registered worktrees.
- Use `git worktree list --porcelain -z` and structured `git for-each-ref` output over `refs/heads/`. Preserve exact paths, refs, and commit IDs; never parse whitespace columns or bulk-pipe deletion targets.
- Protect current/main worktrees, default/integration/long-lived/user-retained branches, and local upstreams of retained branches. Never detach, switch, or alter tracking to enable deletion.
- Establish integration from guidance, the user's base, or an unambiguous default—not the current feature branch by assumption.
- For every candidate, record tip, upstream, associated worktrees, integration evidence, proposed action, and risk.
- Check recorded tips with `git merge-base --is-ancestor`; distinguish non-ancestor exit 1 from errors. Age, missing upstreams, names, and closed PRs do not prove integration.
- Squash/rebase merges need current-tip evidence and user choice where ancestry is insufficient. Remote-tracking refs can be stale; use read-only remote evidence without implicit fetch. Unknown purpose/base/freshness remains uncertain.

## Inspect worktrees

Resolve metadata through Git, not assumed `.git` directories. For each path:

```sh
git --no-optional-locks -C "$worktree_path" status \
  --porcelain=v1 -z --untracked-files=all --ignored --ignore-submodules=none
```

Check staged/unstaged, untracked/ignored contents, submodules, locks, operations,
worktree-specific refs, and active use. Clean status, a merged branch, or age does
not prove disposability. Missing paths may be moved, inaccessible, or unmounted.

## Classify and decide

- **Eligible:** disposable topic with tip integrated, or its clean, unused, unlocked worktree with disposable ignored contents and no submodule/operation needing preservation. Stale registration needs evidence of intentional removal, not absence alone.
- **Keep:** protected/active items, checked-out branches of retained worktrees, local upstreams, and explicit keep decisions.
- **Uncertain:** ambiguous purpose/integration/use, local-only or detached history, dirty/locked/submodule/unexplained ignored/missing state, or failed inspection.
- Before removing worktree or registration, prove HEAD and worktree-specific refs remain reachable after the entire cleanup. Its own reflog or another deletion candidate is insufficient.
- Show the complete classification. Preview stops here.
- Ask per uncertain target with exact consequences: unchecked boxes, or **Keep / Worktree only / Worktree and branch**; branches alone get **Keep / Delete**. Use numbered text if needed; install no UI dependency.
- Offer only valid combinations. Keeping a worktree retains its branch; worktree-only keeps the branch despite automatic eligibility. Separate force approval from ordinary removal.
- Cancellation, silence, and unselected items mean keep. Complete independent eligible cleanup while waiting.

## Execute and verify

- Before each mutation, recheck exact tip, integration, registration, status, locks, and retention dependencies. Changed evidence requires reclassification and fresh consent where needed.
- Work from a retained worktree with quoted exact arguments and option terminators where supported.
- Use `git worktree remove <path>` and independently eligible/approved `git branch -d -- <branch>` only after its final worktree is gone. Keep the independent integration check: `-d` checks upstream or HEAD.
- Diagnose refusal; do not automatically force, unlock, or bypass safeguards.
- Recheck `git worktree prune --dry-run --verbose` immediately before pruning. All listed entries must be eligible/approved; preserve the identical expiration cutoff. If any retained item appears, skip the entire batch; never edit Git administrative files manually.
- Re-list branches/worktrees; verify removals and unchanged retained state. Report paths, branches/former tips, pruned registrations, and kept/blocked items—or no eligible work.
- State deleted contents and recovery limits; never promise reflog recovery of untracked/ignored files.
