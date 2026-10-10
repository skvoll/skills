---
name: onboard
description: Teach a future maintainer how the current repository works through source-backed architecture, execution paths, design tradeoffs, and change guidance. Use for fast, deep codebase onboarding or understanding an unfamiliar subsystem.
---

# Onboard

Give the user a working mental model they can use to predict behavior, locate a
change, and verify it. Optimize for time to understanding: explain the few
mechanisms that unlock the repository, then deepen them with concrete examples.
README and directory summaries are orientation, not the finished lesson.

This is an explanation workflow. Inspect files and Git without changing them;
do not implement recommendations, install dependencies, or invoke other workflows.
Write an onboarding document only if requested. Respect active instructions and
existing work; inspect commands before any optional local execution.

## Find the learning spine

Use the current repository unless the user names another target. Read applicable
instructions, inspect status, and establish the repository's purpose from its
entrypoints, manifests, public interfaces, and representative tests. Use docs,
glossaries, and architecture decisions as leads, then check them against source.
Distinguish committed design from current working-tree changes.

Honor a named subsystem, time budget, or experience level. Otherwise assume a
competent developer new to this project and aim for a first briefing readable in
about five minutes. Resolve discoverable facts yourself; do not delay the lesson
with a generic interview.

Identify the core behavior and the concepts it depends on. Sample recent history
to find active maintenance areas, but keep the central path in view even if it
changes rarely. In a monorepo, map shared boundaries briefly and trace a relevant
package; state the scope instead of pretending to cover every package.

Search selectively and follow references, callers, and tests. Skip generated,
vendored, and dependency trees unless they explain a relevant boundary. Stop
widening exploration when you can support the core path, recurring patterns,
and a realistic maintenance example. Name important gaps rather than reading
every file or hiding uncertainty.

## Reconstruct how it works

Trace a representative behavior from its actual entrypoint through decisions,
state or data transformations, dependencies, and observable output. Follow a
consequential failure or alternate path too: where is it detected, what state
survives, and what does the caller observe? Cite actual symbols and source
locations at the transitions. For a library, trace a public call; for a CLI, a
command; for a declarative or documentation repository, trace how source becomes
a consumed artifact. Do not invent an application runtime.

Explain the architectural boundaries: who owns which state or responsibility,
which direction dependencies flow, and what callers must know. Show where an
interface hides complexity and where maintainers must coordinate across files.
Explain abstractions in the repository's own vocabulary before giving them a
generic design-pattern label.

Extract the patterns that actually recur. For each consequential pattern, show
representative source examples, the problem it solves, its cost, and how to
extend it. Distinguish a repeated convention from a one-off implementation;
include an exception when it changes how a maintainer should work. Ground design
intent in decisions, history, or comments where available. Otherwise label the
rationale as an inference and explain what evidence supports it.

Surface the invariants a future change could break, with the code or checks that
enforce them. Where relevant, include configuration precedence, ordering,
lifecycles, compatibility, and boundaries around external dependencies. Connect
risks to a concrete trigger and consequence; avoid a generic audit checklist.

## Teach through a maintenance example

Choose a small hypothetical change aligned with the user's goal or a common
extension point. Walk through where it starts, which existing example to copy,
which contracts and dependent files it touches, and what would go wrong with a
plausible naive approach. Explain the expected outcome and how a maintainer
would verify it through the project's existing interfaces. Do not make the edit.

Recover development and validation commands from project configuration, CI, and
development docs. Distinguish checks you ran from commands merely inspected, and
describe each check's coverage and limits. If the repository has no automated
tests, state its actual validation boundary. Onboarding should not require
bootstrapping the project or contacting live services.

## Deliver a layered lesson

Lead with the repository's purpose and a compact mental model of its behavior.
Use a small diagram when it makes ownership, dependencies, or flow clearer.
Then teach the traced behavior, decisive patterns and tradeoffs, and the
maintenance example. Keep the first briefing focused; attach source pointers
and deeper explanations where the user can follow them without a file dump.

Use clickable file links with line numbers where supported. Every consequential
architectural claim needs a source anchor; distinguish observations, inferred
intent, and unknowns. Treat stale docs as a discrepancy to explain. Teach what
each mechanism means for the user's next decision, not just what files contain.

Finish with a prioritized reading path explaining what each stop teaches, the
main maintenance traps, and a small prediction or change-location exercise the
user can try. Make the exercise optional; do not gate the briefing on answers.
Offer specific follow-up topics drawn from gaps or complex boundaries. Deepen
those on request using the evidence already gathered.

The lesson is complete when the user can explain the central behavior, recognize
the key conventions and their limits, locate a plausible change, and identify
how to check it. Report exploration scope and material unknowns; do not claim
exhaustive coverage or turn the lesson into an unsolicited redesign.
