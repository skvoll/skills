---
name: refine
description: Review and improve an existing implementation, then validate it locally. Use when the user invokes refine for a final pass on a prepared change.
---

# Refine

Make a prepared change correct, clear, and ready for delivery.

## Recover intent

- Invocation authorizes local edits and validation, not Git or remote mutations.
- Read repository guidance, requirements, and linked issues.
- Inspect the branch, staging, unstaged changes, relevant untracked files, and full intended diff against its base.
- Separate the intended change from unrelated user work.
- Infer the narrowest supported intent when no specification exists. Code alone does not prove intent.
- If no prepared change exists, report that fact and stop.
- Ask only when a missing product decision blocks a correction. Continue independent review.
- Leave broad redesign and new behavior for a separate implementation request.

## Check behavior

- Compare the result with the requirement.
- Look for missing behavior, regressions, boundary cases, failure paths, and compatibility breaks.
- Check security, accessibility, and performance where affected.
- Verify consequential API and platform assumptions against current primary sources and installed versions.

## Check design

- Remove unnecessary concepts, duplicate logic, and layers without a useful boundary.
- Check lifecycle, resource ownership, and repository conventions.
- Reuse existing abstractions where they help.
- Optimize for clear responsibilities and control flow, not line count.

## Correct and verify

- Apply concrete, in-scope improvements directly.
- Preserve intended behavior and unrelated work.
- When a regression test helps, check behavior through an observable interface.
- Use structural checks and review for documentation or other low-impact edits.
- Avoid tests that encode internal structure.
- Run relevant repository checks. Explain failures without suppressing them.
- Re-read the diff against the original requirement.
- Finish when the task is satisfied, remaining complexity has a purpose, and validation supports the result.
- Report important fixes and checks, or say no edits were warranted.
- State blockers. Leave the result in the working tree without invoking delivery.
