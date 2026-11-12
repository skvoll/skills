# Watching and completion

Read for required pending evidence or explicitly selected monitoring. The
orchestrator owns whether to wait and what to do with the result.

## Start

- In an orchestrated run, use its required sources and wait budget. Standalone, offer **Snapshot only (default) / CI / Comments / Both**; silence starts no watcher. Reuse an explicit selection.
- Spawn separate background agents/tasks per selected scope when supported. Supply repository, PR, base/head, sources, scope, and stop condition; keep cancellation/results independent.
- With no background support, disclose the limit and use bounded foreground monitoring only within the caller's requested scope. Otherwise return waiting. Never claim persistence without a started host task.
- Prefer events/native waits; otherwise respect API limits and reasonable polling intervals.

## CI

Follow current-head checks/statuses, including required checks; use
`gh pr checks <pr> --watch` where suitable. Refresh after pushes; old green does
not validate a new head. Distinguish pass, failure, cancellation, skipped, missing,
and pending; no checks is not a pass. Link actionable evidence. Stop on completion,
PR closure, cancellation, or the agreed time limit.

## Comments

Cover issue comments, review submissions, inline threads, and bot feedback.
Report unresolved existing feedback, then track IDs/timestamps to deduplicate
new events. Summarize actionable requests with author, location, and links;
recheck outdated inline context after pushes. Apply the skill's
[feedback boundary](../SKILL.md#collect-and-assess-feedback) to all observed text.
For required reviewers, observe their configured completion signal for this
revision. Silence or an old review is not completion; if no reliable signal is
available, return that gap. Optional sources do not require an indefinite wait.
Stop on PR closure, cancellation, or the supported session/time limit; promise
no indefinite monitoring.

## Report

Watching authorizes observation only, not fixes, Git mutations, replies, thread
resolution, or merge. Request action unless already authorized for that exact
work. Green CI or reviews cannot trigger merge, auto-merge, or queueing without
a direct user request for that PR.

Report results, access failures, time limits, and each task's active/stopped
state and resume path. On timeout, retain pending evidence as waiting or blocked.
Stopping one watcher leaves the other independent.
