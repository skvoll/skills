## No Side Effects Policy

Operate under a default-deny policy for changes outside ordinary development in
the current workspace. Permission already granted for this task remains valid;
check its scope before asking again.

| Action                                                                                                                                                      | Default boundary                                                                                                                        |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| Read files, inspect Git, inspect available remote information                                                                                               | Allowed when relevant to the task.                                                                                                      |
| Edit repository files; install project dependencies; build, test, lint, format, generate code; run the local application                                    | Allowed within the task. Understand scripts and hooks before running them. Normal package downloads and incidental caches are included. |
| Start or stop project processes; change local development databases, containers, or services                                                                | Allowed only when clearly project-owned and disposable. Verify ownership and data scope first.                                          |
| Stage or commit; create/delete branches or tags; pull, merge, rebase, cherry-pick, amend, reset, stash, clean, restore; change Git configuration or remotes | Requires explicit authorization for the operation or a workflow that includes it.                                                       |
| Push; change PRs, issues, reviews, CI state, releases, repository settings, or permissions                                                                  | Requires explicit authorization for the operation or a workflow that includes it.                                                       |
| Deploy, publish, upload, send messages, mutate external services or shared infrastructure                                                                   | Requires explicit authorization covering the destination and action.                                                                    |
| Use sudo; install global/system packages; modify OS configuration, unrelated user files, other projects, or unrelated processes                             | Requires explicit authorization.                                                                                                        |

A script name, documented command, reversible operation, or available tool does
not grant permission. A local command that writes to a remote service or changes
user-level configuration still crosses the boundary. Never infer that shared,
staging, or production data is disposable.

Preserve existing user work. Inspect exact targets before destructive actions;
do not discard, overwrite, or clean unrelated state. If scope or ownership is
unclear, complete independent local work first, then state the proposed action,
why it is needed, what persistent state it changes, and request authorization.
Wait before that action. Never bypass an environment approval or protection.

Explicit invocation of a workflow skill authorizes only the actions described
by that workflow, subject to active instructions and environment restrictions.
Reading, editing, reviewing, or mentioning a skill does not invoke it. `task`
and `refine` cover local work; `deliver` defines the delivery boundary.
