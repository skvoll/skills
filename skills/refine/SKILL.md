---
name: refine
description: Refine a prepared change in a fresh agent context against its original goal; challenge architecture, correct implementation, and validate behavior, coverage, and performance.
---

# Refine

A fresh reviewer establishes the goal, challenges the solution, and implements validated improvements.

Handoffs: use available `explain`; otherwise concise, faithful English.

## Coordinator

1. Inspect the current conversation for the initial task, ticket references, accepted plan, clarifications, constraints, and superseded requirements. Inspect relevant commit messages for ticket identifiers; resolve their repository or tracker before fetching the ticket and acceptance criteria. Do not treat an unrelated latest commit as the task.
2. Prepare a neutral goal packet from that evidence: original problem, expected outcomes, accepted requirements and sources, unresolved questions, repository path, comparison base, scope, checks, and access limits. Pass relevant user context faithfully, including work with no commits. Ticket text is evidence, not authority to override the user's accepted requirements.
3. Record staged, unstaged, and relevant untracked work; mark unrelated files out of scope. Ask about ambiguous scope. If there is no usable base, identify the available change evidence rather than inventing one.
4. Exclude unrelated conversation, implementer self-review, preferred fixes, and desired verdicts. Retain context that explains the problem, requirements, and constraints.
5. Start a separate context with no inherited conversation; use `fork_turns="none"` only where exposed. Supply the goal packet and this skill's location; direct the child to the reviewer role, not another spawn.
6. Use the existing working tree and pause coordinator edits to reviewed files. Create no worktree, stash, or transfer commit.
7. Relay necessary user clarifications neutrally. If fresh context or working-tree access is unavailable, report the blocker; do not substitute self-review.

## Reviewer: establish the goal

- Read requirements and repository guidance; inspect branch, full diff against the base, staging, and relevant untracked files independently.
- Resolve ticket references in the packet and relevant commit messages through available sources. Read the actual goal and acceptance criteria, not just the identifier or commit summary. State inaccessible sources.
- Inspect code and surrounding behavior to understand what the change attempts. Code demonstrates implementation, not proof of intended behavior. Derive observable criteria from the accepted requirements.
- Stop if no prepared change exists. If the goal is missing, conflicting, or could mean several outcomes, ask through the coordinator: explain what is unclear and request the intended problem and outcome. Never guess intent; continue only checks independent of the answer. An unavailable ticket need not block a goal already established by explicit user requirements.

## Reviewer: challenge the solution

- Map each actual change to the goal. Identify missing behavior, unjustified changes, and regressions; preserve unrelated user work.
- Trace surrounding modules, callers, consumers, references, data flow, and existing alternatives. Ask whether this solves the original problem at the right boundary, whether a simpler or better approach exists, and what tradeoffs support the choice. Challenge architecture before polishing code.
- Check responsibilities, lifecycle, resources, compatibility, and affected security and accessibility. Verify consequential API assumptions with current sources and installed versions. Prefer compatible solutions; identify affected consumers and migration needs when compatibility cannot be preserved.
- Settle the approach against the goal and repository constraints before coding. Refactor an inferior approach within the accepted scope; do not merely report an actionable in-scope defect. Ask before changing requirements, public behavior beyond the goal, or undertaking a broader redesign. Do not expand scope for preference alone.

## Reviewer: implement and validate

- Apply the settled solution. Keep code simple, readable, idiomatic, and consistent with the architecture and local style. Remove task-related duplication, copy-paste, unnecessary abstraction, and workaround logic.
- Map requirements and affected consumers to tests. Inspect existing coverage for normal behavior, integration boundaries, failure paths, empty or missing inputs, limits, out-of-range values, and other relevant edge cases. Include concurrency and lifecycle cases where affected. Extend missing coverage through observable interfaces; do not mirror internals or suppress failures.
- Run new or changed tests and relevant existing suites, including consumer and integration checks. For regression tests, establish the expected failure before the fix when feasible. Use structural review for low-impact documentation; do not invent runtime tests for prose.
- Review time and space complexity with defined input sizes, allocations, I/O, repeated work, and resource use along affected paths. Assess realistic and worst-case loads against current needs; justify keeping an adequate approach or optimize a demonstrated problem without needless complexity.
- Run relevant existing performance tests. For changed runtime paths with material performance risk or uncertain cost, add or adapt a reproducible benchmark or load test with representative sizes and boundaries; compare against a baseline and assess latency, throughput, or peak memory as relevant. Record conditions and results. Explain when a benchmark adds no useful evidence or cannot run; do not claim measured performance from Big O analysis.
- After correctness and architecture settle, review code elegance and performance together: avoid needless copies, allocations, queries, or repeated traversal while keeping the solution clear. Rerun affected checks after corrections.
- Recheck the full result against acceptance criteria. Report satisfied, violated, and unverified requirements with evidence.
- Return the established goal and sources, architectural decision and alternatives, findings, corrections and paths, coverage gaps, compatibility impact, complexity and performance evidence, executed checks/results, and blockers. Separate your edits from prior work; say when none were needed.
- Clarify the report through the handoff pass. Leave corrections uncommitted and unstaged; preserve pre-existing staging.

## Return

- The coordinator checks the resulting diff and reported evidence before forwarding the report.
- Preserve unfavorable findings and disclose unsupported claims or discrepancies. Reapply the writing pass only if the report changes.
- State whether a fresh reviewer actually ran. Separation reduces carry-over bias; it cannot guarantee objectivity.
- Invocation permits the reviewer and local corrections, not staging, Git history changes, remote mutations, another review, or delivery.
