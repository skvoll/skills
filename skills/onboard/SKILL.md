---
name: onboard
description: Teach a future maintainer how the current repository works through source-backed architecture, execution paths, design tradeoffs, and change guidance. Use for fast, deep codebase onboarding or understanding an unfamiliar subsystem.
---

# Onboard

Teach a mental model the user can use to predict behavior, locate changes, and verify them.

## Scope

- Inspect files and Git without changing them.
- Do not implement recommendations, install dependencies, or invoke other workflows.
- Write an onboarding document only when requested.
- Respect active instructions and existing work. Inspect commands before optional local execution.
## Set the audience

- Use the current repository unless another target is named.
- Honor the user's subsystem, time budget, and experience level.
- Otherwise assume a competent developer new to the project; aim for a five-minute first briefing.
- Resolve discoverable facts yourself. Avoid a generic interview.

## Find the central path

- Read repository instructions and inspect status.
- Establish purpose from entrypoints, manifests, public interfaces, and representative tests.
- Treat docs, glossaries, and architecture decisions as leads; verify them against source.
- Distinguish committed design from working-tree changes.
- Identify the core behavior and the concepts needed to understand it.
- Sample recent history for maintenance hotspots without losing rarely changed central behavior.
- In a monorepo, map shared boundaries and trace a relevant package. State the scope.
## Bound exploration

- Follow references, callers, and tests selectively.
- Skip generated, vendored, and dependency trees unless they explain a relevant boundary.
- Stop expanding once evidence supports the core path, recurring patterns, and a maintenance example.
- Name important gaps rather than hiding uncertainty or reading every file.

## Trace behavior

- Follow one representative behavior from its actual entrypoint to observable output.
- Show decisions, state changes, data transformations, and dependencies.
- Trace a consequential failure or alternate path: detection, surviving state, and caller-visible result.
- Anchor transitions to real symbols and source locations.
- For a library, trace a public call; for a CLI, a command.
- For declarative or documentation projects, trace source to the consumed artifact. Do not invent a runtime.

## Explain the design

- Identify responsibility and state ownership, dependency direction, and caller obligations.
- Show where interfaces hide complexity and where changes require coordination.
- Use project vocabulary before generic pattern labels.
- For each consequential recurring pattern, show examples, purpose, cost, and extension points.
- Separate repeated conventions from one-off choices. Include exceptions that affect maintenance.
- Ground intent in decisions, history, or comments. Label inferred rationale and its evidence.
- Identify invariants and the code or checks that enforce them.
- Where relevant, cover precedence, ordering, lifecycle, compatibility, and external boundaries.
- Connect each risk to a concrete trigger and consequence.

## Walk through a change

- Choose a small hypothetical change tied to the user's goal or a common extension point.
- Show where it starts, which example to follow, and which contracts and files it touches.
- Explain a plausible naive mistake and its consequence.
- Describe the expected result and verification through existing interfaces. Do not make the edit.
- Recover development commands from configuration, CI, and docs.
- Distinguish executed checks from inspected commands; state coverage and limits.
- If automated tests are absent, explain the actual validation boundary.
- Do not require project bootstrapping or live-service access for the lesson.

## Teach in layers

- Lead with purpose and a compact mental model. A directory summary alone is not a lesson.
- Use a small diagram when it clarifies ownership, dependencies, or flow.
- Explain the traced behavior, decisive patterns, tradeoffs, and maintenance example.
- Keep the first briefing focused. Link deeper details instead of dumping files.
- Anchor consequential architectural claims to source; use clickable line links where supported.
- Separate observations, inferred intent, unknowns, and stale-document discrepancies.
- Explain what each mechanism means for the user's next decision.
## Finish the lesson

- Give a prioritized reading path, maintenance traps, and an optional prediction or change-location exercise.
- Do not gate the briefing on exercise answers.
- Offer specific follow-up topics; deepen them on request using gathered evidence.
- Report scope and material unknowns. Avoid claims of exhaustive coverage or unsolicited redesign.

Done means the user can explain central behavior, recognize conventions and their
limits, locate a plausible change, and identify how to check it.
