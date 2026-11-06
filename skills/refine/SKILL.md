---
name: refine
description: Independently review a prepared change in a fresh agent context; return validated, uncommitted corrections and a clear report.
---

# Refine

A fresh reviewer checks the change against the user's requirements.

Handoffs: use available `explain`; otherwise concise, faithful English.

## Coordinator

1. Prepare a neutral packet: original request, ticket, accepted plan and clarifications, repository path, base, scope, checks, and access limits. Preserve user wording and source links.
2. Record staged, unstaged, and relevant untracked work; mark unrelated files out of scope. Ask about ambiguous scope.
3. Exclude conversation history, implementer reasoning, self-review, preferred fixes, and desired verdicts.
4. Start a separate context with no inherited conversation; use `fork_turns="none"` only where exposed. Supply the packet and this skill's location; direct the child to the reviewer role, not another spawn.
5. Use the existing working tree and pause coordinator edits to reviewed files. Create no worktree, stash, or transfer commit.
6. Relay necessary user clarifications neutrally. If fresh context or working-tree access is unavailable, report the blocker; do not substitute self-review.

## Reviewer

- Read requirements and repository guidance; inspect branch, full diff against the base, staging, and relevant untracked files independently.
- Derive criteria from the complete accepted requirement set, not implementation intent or commit messages.
- Stop if no prepared change exists. For missing or conflicting requirements, ask through the coordinator and continue only checks independent of that uncertainty.
- Check behavior: omissions, regressions, boundaries, failure paths, compatibility, and affected security, accessibility, or performance.
- Check design: responsibilities, control flow, duplication, lifecycle, resources, and repository conventions. Verify consequential API assumptions with current sources and installed versions.
- Apply concrete in-scope corrections; reserve new behavior and broad redesign for a separate task.
- Validate through observable interfaces; use structural review for low-impact docs. Do not encode internals in tests or suppress failures.
- Recheck the full result against acceptance criteria. Report satisfied, violated, and unverified requirements with evidence.
- Return findings, corrections and paths, executed checks/results, and blockers. Separate your edits from prior work; say when none were needed.
- Clarify the report through the handoff pass. Leave corrections uncommitted and unstaged; preserve pre-existing staging.

## Return

- The coordinator checks the resulting diff and reported evidence before forwarding the report.
- Preserve unfavorable findings and disclose unsupported claims or discrepancies. Reapply the writing pass only if the report changes.
- State whether a fresh reviewer actually ran. Separation reduces carry-over bias; it cannot guarantee objectivity.
- Invocation permits the reviewer and local corrections, not staging, Git history changes, remote mutations, another review, or delivery.
