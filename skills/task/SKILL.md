---
name: task
description: Plan and implement a software change, then validate it locally. Use for features, fixes, or changes to code, configuration, and documentation.
---

# Task

Leave a working, validated change that meets the user's request. This workflow
covers local implementation; delivery requires its own authorization.

## Establish the outcome

Read applicable repository instructions and inspect status, relevant diffs, and
the affected implementation. Use supplied requirements, issues, or examples to
identify observable acceptance criteria. Preserve unrelated work, including
changes that were already present when the task began.

Find the boundary where the behavior can be implemented and verified. For a bug,
reproduce the failure or gather evidence that distinguishes likely causes before
choosing a fix. For documentation, identify the reader, the decision the text
should change, and how the reader discovers it.

Resolve routine choices from the repository. Ask a focused question only for a
decision that materially changes the outcome and cannot be inferred. State a
short plan covering implementation, necessary documentation or tests, and checks
that will demonstrate completion.

## Implement in verifiable increments

Work through one observable behavior at a time. Use existing interfaces and
dependencies where they fit. When a regression test is useful, make it expose
the failure before implementing the fix; assert behavior through a stable
interface rather than mirroring private implementation details. Documentation
or other low-impact edits may need structural checks and review instead.

Choose the fewest concepts needed for the requirement. Add abstractions only
when they simplify a demonstrated problem. Consider errors, lifecycle, security,
accessibility, performance, and compatibility where relevant. Verify consequential
API or platform assumptions against current primary documentation and installed
versions.

Run the relevant check after a meaningful increment and use its result to guide
the next step. Update documentation when behavior, commands, or durable decisions
change. Keep reusable guidance at its existing source.

## Complete the change

Review the full intended diff against each acceptance criterion. Run required
repository checks, widening validation when the affected surface warrants it.
Remove accidental edits and temporary artifacts created by this task without
disturbing other work. Investigate failures without weakening checks; identify
pre-existing or environment failures separately.

Finish when the requested behavior and relevant documentation agree and local
validation supports the result. Report what changed, checks and results, and any
remaining uncertainty. Leave the implementation in the working tree; do not
automatically invoke another workflow.
