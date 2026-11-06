---
name: onboard
description: Teach a source-backed model of a repository or subsystem, its tradeoffs, and how to make and verify a change. Inspect without implementing.
---

# Onboard

Teach enough to predict behavior, locate a change, and verify it.

Handoffs: use available `explain`; otherwise concise, faithful English.

## Orient

- Use the current repository unless named otherwise. Honor scope, experience, and time budget; default to a competent newcomer and a five-minute briefing.
- Read guidance and status. Establish purpose from entrypoints, interfaces, manifests, and representative tests; verify docs against source.
- Distinguish committed design from working changes. Sample history for maintenance hotspots without overlooking stable core behavior.
- In monorepos, map shared boundaries and focus on a relevant package.
- Follow callers, references, and tests selectively; skip generated/vendor trees unless relevant. Stop once the central path, recurring patterns, and maintenance example are supported.

## Trace and explain

- Trace actual entrypoint → decisions → data/state → dependencies → observable output, plus one consequential alternate or failure path.
- Show detection, surviving state, and caller-visible effects. For declarative projects, trace source to consumed artifact; invent no runtime.
- Identify ownership, dependency direction, caller obligations, hidden complexity, and cross-file coordination.
- Explain recurring patterns in project vocabulary: examples, purpose, cost, extension, and meaningful exceptions. Distinguish conventions from one-off choices.
- Ground design intent in decisions, comments, or history; label inference. Anchor consequential claims to source locations and explain stale-doc discrepancies.
- Connect invariants, lifecycle, ordering, precedence, compatibility, and external boundaries to concrete breakage and enforcing checks where relevant.

## Teach a change

- Walk through a small hypothetical extension: starting point, example to follow, touched contracts/files, naive mistake, expected outcome, and verification.
- Recover commands from configuration, CI, and docs; distinguish executed checks from inspected commands and explain coverage or missing tests.
- Lead the lesson with purpose and mental model, then the trace, tradeoffs, and example. Use a small diagram only when helpful.
- End with scope/gaps, prioritized reading stops and what each teaches, maintenance traps, optional exercise, and specific follow-up topics. Do not require exercise answers.

Inspect without editing, installing, bootstrapping, or contacting live services;
check any optional command's effects first. Write a document only when requested.
The lesson is not an unsolicited redesign or a claim of exhaustive coverage.
