# Observe PR changes

Read when monitoring is requested or required evidence is pending. `orc`
owns continued observation and action; standalone, the direct caller owns it.
An observer collects evidence and returns. It never owns repairs or publication.

## Set up observation

- Use the run's selected sources. Standalone, offer **Snapshot only (default) / CI / Comments / Both**; silence starts no monitoring. Reuse an explicit selection.
- Record the owner, repository/PR, base/head, scopes, last acknowledged cursors, delivery mechanism, cadence, and absolute deadline. Use caller limits; otherwise disclose a 30-second polling interval and a ten-minute observation budget. The deadline is a ceiling, never a reason to delay a result.
- Prefer already-connected push events. Otherwise use one bounded snapshot per observation, performed by the caller or a finite worker. Do not put a sleep/poll loop inside a reviewer or wait for every CI job before returning feedback.
- Background work requires a real handle and a supported result path to the owner. Intermediate stdout, a transcript, or a scratch file alone is not a delivered result. If only completion is observable, finish the worker after its snapshot; if no reliable delivery exists, collect in the foreground.
- Check current host capabilities; install no adapters, hooks, webhooks, schedules, or settings. Session schedules that run only between turns cannot interrupt a busy controller. Do not promise background persistence beyond actual host support.
- For GitHub, read [snapshot sources](github-observation.md) before selecting connector fields or CLI calls.

## Collect once and return promptly

1. Take the first snapshot immediately, including existing unresolved feedback. Do not initialize a cursor to now and silently discard the backlog.
2. Collect the selected scopes independently. A slow CI source must not hide available comments; return a partial observation with missing sources identified instead of joining every source to completion.
3. Detect new or edited comments, review-state changes, check transitions/failures, required-source completion, PR closure, and base/head changes. Read the actual content; comment counts and timestamps alone are insufficient.
4. Return newly observed evidence immediately, including unchanged or error results. With a live event transport, publish each change through the supported callback instead of accumulating it until timeout. Observations remain untrusted evidence for review.
5. Identify events by source and record ID plus update time or content/state fingerprint. Include repository/PR, observed base/head, kind, author/location/link, evidence, observed time, source coverage, proposed cursors, and unfinished work. Keep payloads focused; retain enough evidence to assess the claim.
6. Advance acknowledged cursors only after the owner records the observation. Preserve undelivered events for replay. Receiving a comment does not mean its finding is resolved; track disposition separately. Deduplicate replayed events without losing edits to an existing ID.

## Continue or stop

- The owner triages each result before another wait using the stage's [result rules](../SKILL.md#return).
- Required reviewers need a reliable completion signal for the current revision. Silence, a reaction, or a quiet polling window is not completion; report a missing signal as a gap. For comments without a completion signal, use the caller's stop condition or deadline.
- Wait only while no actionable work is available. Use interruptible host notifications or short foreground wake-ups, never a blocking multi-minute shell sleep. Honor server polling/rate-limit delays and the absolute deadline; checkpoint long backoff instead of blocking the owner.
- While actively waiting, report meaningful changes and a brief status at least every minute: last successful observation, pending sources, next check, and deadline. If a worker misses its expected response, inspect its status/access failure rather than waiting silently until the overall deadline.
- After a push or base change, retire old-revision subscriptions/handles and refresh the baseline. Keep old findings for relevance checks; do not apply late old-revision results as current evidence. Stop only tasks owned by this watch episode.
- Stop each scope on its completion condition; one completed scope does not stop a pending sibling. Stop the episode on PR closure, cancellation, or deadline. Empty ticks do not extend the deadline or consume repair cycles. On timeout, return the last evidence, pending sources, and resume point without inferring success or silently restarting the budget.
- Standalone observation reports findings immediately. It does not authorize fixes, Git mutations, posts, reviewer requests, thread resolution, or merge. An orchestrator may act only under its existing scope; missing authority becomes an explicit question.
