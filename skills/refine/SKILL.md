---
name: refine
description: Review and improve an existing implementation, then validate it locally. Use when the user invokes refine for a final pass on a prepared change.
---

# Refine

Leave the prepared change correct, understandable, and ready for delivery.
Invocation authorizes local edits and validation, not Git or remote mutations.

## Recover intent and scope

Read repository guidance and supplied requirements or linked issues. Inspect
the branch, staged and unstaged changes, relevant untracked files, and the
complete intended diff against its base. Separate it from unrelated user work.
Infer the narrowest supported intent when no specification is given; the
implementation itself is not proof of what the user wanted.

If there is no prepared change, report that fact. If a missing product decision
prevents a correction, explain the choice while continuing independent review.
Broad redesign or new behavior needs a separate implementation request.

## Review from two perspectives

First check the result against the requirement: missing behavior, regressions,
boundary cases, failure paths, and compatibility. Then check the design:
unnecessary concepts, duplicated logic, lifecycle or resource mistakes, and
departures from repository conventions. Include security, accessibility, and
performance where affected. These are review lenses, not mandatory agent roles.

Verify consequential API or platform assumptions against current primary sources
and installed versions. Reuse existing abstractions where they help, and remove
layers that add no useful boundary. Optimize for clear responsibilities and
control flow rather than line count.

## Correct and validate

Apply concrete in-scope improvements directly. Preserve intended behavior and
unrelated work. Use tests at observable interfaces to protect meaningful fixes;
avoid tests that merely encode internal structure. Run relevant repository
checks after changes and explain failures without suppressing them.

Re-read the resulting diff against the original requirement. Finish when it
satisfies the task, the remaining complexity has a purpose, and validation
supports the result. Report important fixes and checks, or say that no edits
were warranted. State material blockers and leave the result in the working
tree. Do not automatically invoke delivery.
