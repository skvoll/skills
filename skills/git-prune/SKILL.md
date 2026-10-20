---
name: git-prune
description: Clean up outdated local Git branches and linked worktrees, using interactive checklists or radio choices when deletion is uncertain. Use for repository housekeeping or removing merged worktrees and branches.
---

# Git Prune

Clean up all confirmed outdated local branches and linked worktrees in the
target repository. Resolve uncertain candidates through interactive choices.
Despite the name, this workflow does not run `git prune` or expire Git objects.

## Authorization and scope

A request to run this cleanup authorizes normal removal of confirmed outdated
linked worktrees, deletion of confirmed merged local branches, and pruning of
confirmed stale worktree registrations in this repository. This includes its
registered linked worktrees outside the current directory, subject to active
instructions and environment permissions. Reading, editing, or discussing this
skill does not invoke cleanup. A preview or dry-run request authorizes inspection
and a proposed plan only.

Remote branch deletion, fetching or pruning remote-tracking refs, changing
configuration, switching branches, and discarding user work are outside this
scope. Do not run resets, stashes, `git clean`, garbage collection, or recursive
filesystem deletion as cleanup shortcuts. Force deletion needs explicit
authorization for the exact target and its consequences; a generic cleanup
request or a normal "remove" selection does not grant that authority.

## Inventory and evidence

Read applicable repository instructions. Resolve the target repository and its
common Git directory; inspect only that repository and its registered worktrees.
Record the current and main worktrees so both remain protected. Inventory with
`git worktree list --porcelain -z` and `git for-each-ref` over `refs/heads/`.
Use structured output and preserve full paths, ref names, and commit IDs; do not
parse whitespace-separated columns or pipe branch names into bulk deletion.

Determine the integration base from project guidance, the user's chosen base,
or an unambiguous default branch. Do not assume the current feature branch is
the integration base. Protect the default and integration branches, branches
explicitly retained by the user, and established long-lived branches. If the
base or a branch's purpose is unclear, ask before deleting affected candidates.

For each candidate, inspect its tip, upstream, reachability from the integration
base, and associated worktrees. Identify local branches used as upstreams by
branches that will be retained. Use `git merge-base --is-ancestor` with the
recorded commit IDs to establish merged history. Distinguish exit status 1
(not an ancestor) from a command failure. Commit age, a missing upstream,
matching names, or a closed PR alone cannot establish safe deletion. Squash or
rebase merges need additional evidence covering the current tip and a user
decision when ancestry does not prove integration.

Local remote-tracking refs may be stale. Use available read-only remote or PR
information when needed; do not fetch implicitly. If freshness or integration
cannot be established, classify the item as uncertain rather than guessing.

For each existing worktree, inspect staged and unstaged changes, untracked and
ignored files, submodules, locks, worktree-specific refs, and in-progress Git
operations. Resolve worktree metadata through Git commands rather than assuming
each worktree has a `.git` directory. For a resolved `worktree_path`, inspect
status without the optional index refresh:

```sh
git --no-optional-locks -C "$worktree_path" status \
  --porcelain=v1 -z --untracked-files=all --ignored --ignore-submodules=none
```

A clean normal status does not establish that ignored files are disposable.
Check for signs of active use; do not infer abandonment solely from a merged
branch or old commit date. A missing path might be moved, inaccessible, or on
an unmounted device.

## Classify and resolve uncertainty

Show a compact inventory with each candidate's exact branch/path, tip, proposed
action, evidence, and any risk. Evaluate the entire inventory, not just the
first few candidates. Classify items as:

- **Confirmed outdated:** a disposable topic branch whose tip is reachable
  from the integration base, or its clean, unused, unlocked linked worktree.
  Worktree removal also requires that any ignored contents are known disposable
  and no submodules or in-progress operation need preservation. Before removing
  a worktree or its registration, verify that its HEAD and worktree-specific
  refs remain reachable from refs retained after the entire cleanup. Its own
  reflog or another candidate scheduled for deletion does not establish this.
  A stale registration requires evidence that the worktree was intentionally
  removed, rather than just an absent path.
- **Keep:** current/main worktrees, protected branches, active worktrees, and
  branches still checked out in retained worktrees or used as local upstreams
  by retained branches. Never switch or detach a retained worktree, or change
  tracking configuration, to make a branch deletable.
- **Uncertain:** ambiguous integration, purpose, use, local-only commits,
  detached history, unexplained ignored contents, dirty or locked worktrees,
  submodules, missing paths, or failed inspection. Preserve these pending a
  decision.

Apply keep decisions and dependencies before automatic eligibility. For a
preview or dry run, report the classifications and proposed actions, then stop
without executing cleanup.

Use the host's interactive question UI for uncertain items. Prefer a checkbox
list for independent targets, all initially unchecked, labeled with exact
targets and consequences. Where only single-choice questions are available,
use radio choices per target: "Keep (recommended)", "Remove worktree only",
or "Remove worktree and local branch", as applicable. For a branch alone,
offer "Keep" and "Delete local branch". Batch questions within host limits;
do not collapse different risks into a blanket "delete everything" choice.

Explain the uncertainty and any data that removal would lose in the question.
Keep worktree removal and branch deletion independently selectable. A decision
to keep an item or remove only its worktree overrides automatic eligibility;
retain its branch. If force would be required, use a separate, explicit choice
naming that operation and the work at risk; ordinary removal approval must not
escalate to force. Offer only valid combinations: retaining a worktree requires
retaining its checked-out branch.

When no interactive UI is available, present a numbered checklist and request
selected numbers in text. Never install a UI dependency for this workflow.
Cancellation, no reply, or an unselected item means keep. An elapsed timeout
is not approval. Complete independent confirmed cleanup while decisions are
pending; wait before acting on uncertain targets.

## Execute and verify

Before each mutation, recheck the exact target, recorded tip, integration
evidence, worktree registration, status, locks, and retention dependencies.
Confirm that commits relied on for preservation will survive all planned
removals. If anything changed, reclassify it and obtain a fresh decision where
necessary. Run from a retained worktree and use quoted exact arguments with
option terminators where supported.

Remove eligible or specifically approved linked worktrees with
`git worktree remove <path>`. Honor explicit keep and worktree-only decisions;
otherwise delete their branches only when independently eligible or specifically
approved. Delete eligible or specifically approved local branches with
`git branch -d -- <branch>` only after confirming they are not checked out in
any remaining worktree. This command checks upstream or HEAD, which may differ
from the chosen integration base: retain the independent integration check.
If removal or deletion refuses, inspect the reason; do not automatically retry
with `--force` or `-D`, unlock a worktree, or bypass Git safeguards.

For stale registrations, inspect `git worktree prune --dry-run --verbose`.
Pruning is repository-wide: execute only when every entry in its dry run is
confirmed or specifically approved. If using an expiration cutoff, keep the
same explicit cutoff in preview and execution; never broaden it implicitly.
Recheck the dry run immediately before pruning. If it includes an item to keep,
leave the batch alone and report the limitation rather than editing Git's
administrative files manually.

Re-list worktrees and local branches. Verify intended removals and that retained
worktrees and branches are unchanged. Report removed paths, branch names and
their former commit IDs, registrations pruned, and items kept or blocked with
reasons. Explain that worktree contents were deleted; do not promise recovery
through reflogs, especially for untracked or ignored files. If nothing qualifies,
report that no cleanup was needed.
