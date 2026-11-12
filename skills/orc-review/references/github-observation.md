# GitHub snapshot sources

Use an available connector with equivalent coverage; otherwise inspect installed
`gh` help before choosing flags. Every operation here reads state. Resolve the
host, repository, PR, and head explicitly instead of relying on the current branch.

## Cover each selected source

| Evidence | REST read or equivalent connector field |
| --- | --- |
| PR state and base/head | `GET /repos/{owner}/{repo}/pulls/{number}` |
| Conversation comments | `GET /repos/{owner}/{repo}/issues/{number}/comments` |
| Inline comments and replies | `GET /repos/{owner}/{repo}/pulls/{number}/comments` |
| Submitted reviews and review states | `GET /repos/{owner}/{repo}/pulls/{number}/reviews` |
| CI check runs | `GET /repos/{owner}/{repo}/commits/{head}/check-runs` |
| Commit statuses | `GET /repos/{owner}/{repo}/commits/{head}/status` |

Follow every page and preserve each response's coverage. For thread resolution
or outdated status, use the platform's review-thread fields with their own
pagination. Include commit comments or other feedback sources when linked or
requested. A conversation-only view, such as `gh pr view --comments`, does not
establish complete review coverage.

For REST through `gh api`, use explicit `--method GET` and `--paginate` for
collections. Adding field flags otherwise changes the default method to POST.
For GraphQL, use read-only queries and paginate each relevant connection;
HTTP POST carrying a query does not authorize a mutation.

## Read checks without blocking feedback

- Prefer a single current-head check snapshot. `gh pr checks --watch` watches CI only and normally waits for checks to finish; it is not a comment observer or a parent-notification mechanism.
- Use `--json` only if installed help exposes it. Otherwise use supported PR check fields or API/connector snapshots; do not install an upgrade to satisfy an assumed flag.
- If an isolated CI watch is explicitly useful, use supported `--fail-fast` and an owner-visible result channel. Keep comment collection independent and return the first relevant failure; do not wait for unrelated successful jobs.
- Inspect required check identities and actual conclusions, not just process exit status or an empty list. Current CLI versions may return exit code 8 for pending checks; verify installed behavior. Report missing/blocked/skipped evidence distinctly.

## Avoid lost or stale updates

- Fetch base/head around observation and label results with their revision. A changed revision requires refresh before action or completion.
- Re-read edited IDs and changed review/check states. Use overlapping update windows plus deduplication where incremental filtering exists; commit per-source cursors only after all fetched pages are acknowledged. Never advance a cursor on an incomplete/failed read.
- Prefer available event notifications; when polling, use conditional requests where supported and honor `x-poll-interval`, `Retry-After`, and rate-limit reset headers. Bound retries and surface access or transport errors. A 304 reuses a known snapshot; an error is not an empty successful snapshot.
- Fetch evidence through the existing authenticated integration. Do not create webhooks, trigger CI/review jobs, post comments, or resolve threads as part of observation.
