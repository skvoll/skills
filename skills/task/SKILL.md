---
name: task
description: Plan and implement a software change, then validate it locally. Use for features, fixes, or changes to code, configuration, and documentation.
---

# Task

Leave a working, locally validated change that meets the request.

## Scope

- Implement locally. Delivery needs separate authorization.
- Read repository guidance, status, relevant diffs, and affected code.
- Preserve existing staging and unrelated user work.

## Define done

- Turn requirements, issues, and examples into observable acceptance criteria.
- Find where to implement the behavior and where to verify it.
- For bugs, reproduce the failure or gather evidence before choosing a fix.
- For documentation, identify the reader, the decision, and the discovery path.
- Resolve routine choices from repository evidence.
- Ask only about missing decisions that materially change the outcome.
- State a short plan: implementation, needed docs or tests, and completion checks.

## Implement

- Finish and check one observable behavior at a time.
- Use existing interfaces and dependencies where they fit.
- Choose the fewest concepts that solve the problem.
- Add an abstraction only when it simplifies a demonstrated need.
- Consider errors, lifecycle, security, accessibility, performance, and compatibility where affected.
- Verify consequential API and platform assumptions against current primary sources and installed versions.

## Validate each increment

- When a regression test helps, see it fail for the expected reason before fixing the code.
- Test behavior through stable interfaces. Do not mirror private implementation.
- Use structural checks and review for documentation or other low-impact edits.
- Run the relevant check after a meaningful increment. Let the result guide the next step.
- Update docs when behavior, commands, or durable decisions change.
- Keep reusable guidance at its authoritative source.

## Finish

- Review the full intended diff against every acceptance criterion.
- Run required repository checks. Widen validation when the affected surface warrants it.
- Investigate failures without weakening checks. Separate existing defects from environment failures.
- Remove only accidental edits and temporary artifacts created by this task.
- Confirm behavior, documentation, and validation agree.
- Report changes, checks, results, and material uncertainty.
- Leave the result in the working tree. Do not automatically invoke another workflow.
