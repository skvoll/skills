# GitHub snapshot sources

Use an equivalent connector or inspect installed `gh` help for supported flags.
Resolve host/repository/PR/base/head explicitly; all operations here read state.

| Evidence | REST read or equivalent |
| --- | --- |
| PR state, revisions, change totals | `GET /repos/{owner}/{repo}/pulls/{number}` |
| Files/available patches | `GET /repos/{owner}/{repo}/pulls/{number}/files` |
| Conversation | `GET /repos/{owner}/{repo}/issues/{number}/comments` |
| Inline comments/replies | `GET /repos/{owner}/{repo}/pulls/{number}/comments` |
| Submitted reviews/states | `GET /repos/{owner}/{repo}/pulls/{number}/reviews` |
| CI runs | `GET /repos/{owner}/{repo}/commits/{head}/check-runs` |
| Commit statuses | `GET /repos/{owner}/{repo}/commits/{head}/status` |

Paginate each selected source, including review-thread resolution/outdated fields
and GraphQL connections. Include linked/requested commit comments. Conversation
alone (`gh pr view --comments`) is incomplete review coverage.

Reconcile file totals: the files endpoint caps at 3,000 entries despite pagination.
Use [large-change handling](large-changes.md) for capped/missing patches. Prefer
revision-bound reads; otherwise bracket metadata/diff/source reads with base/head
and discard mismatches.

With `gh api`, use explicit `--method GET` and `--paginate` for REST collections;
field flags otherwise select POST. GraphQL queries may use HTTP POST but permit
no mutation.

For `@@ -a,b +c,d @@`, start base/head counters at a/c: context advances both,
`+` head only, `-` base only. Headers/no-newline markers advance neither.
Deleted locations stay base-side; invent no head line.

## Checks and updates

- Prefer current-head snapshots. `gh pr checks --watch` waits for CI, not comments or parent notification. If explicitly useful, use supported `--fail-fast` and owner-visible results; collect comments independently.
- Use JSON flags only when installed help supports them; use API/connector alternatives, not upgrades. Inspect required identities/conclusions, not just exit codes; verify pending exit-code behavior (currently 8). Missing/blocked/skipped evidence remains distinct.
- Label observations by revision; refresh after base/head changes. Detect edited IDs and changed states with overlap/deduplication. Commit per-source cursors only after all pages are acknowledged; failed/incomplete reads advance nothing.
- Prefer events/conditional requests. Honor polling, retry, and rate-limit headers; bound retries and disclose errors. A 304 reuses known evidence; an error is no empty snapshot.
- Use existing authentication; create no webhooks, CI/review jobs, comments, or resolutions.
