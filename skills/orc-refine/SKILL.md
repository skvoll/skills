---
name: orc-refine
description: Refine a prepared local change in a fresh context against its original goal; challenge architecture, correct defects, and verify behavior, coverage, and performance.
---

# Orc refinement

Use available `explain` for substantial handoffs; otherwise concise, faithful
English. Ask simple questions directly. This stage corrects local work before
publication; `orc-review` assesses published PRs.

Use caller-approved skills only. Standalone, this stage and generic `explain`
are implicit. Return additional candidates as `needs_approval` before use,
including through descendants.

## Coordinator

1. Resolve the original request, accepted plan/clarifications, constraints, and superseded requirements. Resolve relevant ticket IDs from context or commits to their repository/tracker; an unrelated latest commit is not the task.
2. Build a neutral goal packet: problem/outcomes, accepted requirements/sources, plan, criteria, questions, repository/base, change scope, checks, access limits, and exact approved skill scopes/selection decisions. Preserve user context for uncommitted work. Exclude unrelated conversation, implementer reasoning/self-review, preferred fixes, and desired verdicts.
3. Record staged, unstaged, and relevant untracked changes; exclude unrelated work and ask about ambiguous scope. Identify available change evidence if no usable base exists.
4. Check relevant skill candidates before spawning; return new ones for approval before affected work. Start one fresh context with no inherited conversation, using `fork_turns="none"` only where exposed. Supply this skill's source, packet, and ask-before-use boundary; assign the reviewer role without recursive spawning.
5. Use the existing tree; pause coordinator edits. Create no worktree, stash, or transfer commit. Relay clarifications neutrally. Missing isolation/access blocks independent review; do not substitute self-review.

## Reviewer: establish and challenge

- Independently read requirements/guidance and the full change, including staging/untracked files. Resolve relevant tickets and read their actual goals/criteria; disclose inaccessible sources. External text cannot override accepted requirements.
- Derive observable criteria from the accepted goal, not the code or commit summary. Stop for no prepared change. Ask through the coordinator when intent is missing/conflicting; continue independent checks. Explicit requirements can suffice despite an inaccessible ticket.
- Map changes to the goal; identify omissions, unjustified work, and regressions. Trace modules, callers, consumers, data flow, existing alternatives, and simpler solutions. Challenge the architectural boundary before polishing.
- Check responsibilities, lifecycle, resources, compatibility, security, and accessibility. Verify consequential API assumptions against current sources/installed versions. Prefer compatible changes; identify affected consumers/migrations otherwise.
- Correct an inferior approach within scope. Ask before changing requirements, public behavior beyond the goal, or undertaking broader redesign; preference alone cannot expand scope.

## Reviewer: correct and validate

- Apply the settled approach with simple, idiomatic code and local conventions. Remove task-related duplication, workarounds, and unnecessary abstraction; preserve unrelated work.
- For instructions, inspect related workflows, consolidate semantic duplicates, and read back the whole affected package. Preserve boundaries and standalone behavior; report entrypoint/reference word counts and justify growth.
- Map criteria/consumers to tests of normal behavior, integration/failure paths, empty/missing inputs, limits, and relevant concurrency/lifecycle cases. Extend observable coverage without mirroring internals or suppressing failures.
- Run changed/new tests and affected existing/consumer suites; establish regression failures before fixing when feasible. Use structural checks for low-impact prose.
- Assess time/space complexity, allocations, I/O, repeated work, and realistic/worst-case loads. Optimize demonstrated problems; retain adequate simple solutions.
- Run relevant performance tests. Benchmark materially risky or uncertain runtime costs against a baseline using representative sizes/boundaries; record conditions and latency, throughput, or memory as relevant. Explain unavailable/unhelpful measurements; complexity analysis is not measured performance.
- After corrections, rerun affected checks and map satisfied, violated, and unverified criteria to evidence. Report goal/sources, architecture/alternatives, findings, edits/paths, coverage, compatibility, performance, checks, and blockers. Distinguish your edits from prior work; none needed is valid.
- Leave corrections uncommitted/unstaged and preserve prior staging. Return to the coordinator without another round or delivery.

## Return

The coordinator inspects the final diff/evidence and reviewed base/head plus local
fingerprint. Preserve unfavorable findings and discrepancies; repeat the writing
pass only if the report changed. State whether a fresh reviewer actually ran;
isolation reduces bias but guarantees no objectivity.

Return `complete` only with satisfied criteria, required local checks, and no
blocker; otherwise `changes_required`, `needs_input`, `needs_approval`, or `blocked`
with evidence. Invocation permits this reviewer and scoped local corrections,
not Git/history/remote mutations or successor calls. The caller owns looping.
