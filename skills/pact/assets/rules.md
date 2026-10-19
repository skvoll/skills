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

## Evolutionary Software Architecture

Build only what is needed today, but structure it so that tomorrow's changes
remain local, understandable, and inexpensive. Use these principles as
guidelines for engineering judgment; no particular architecture, methodology,
or design pattern is required.

- **Locality of change:** Prefer clear module boundaries and encapsulated
  responsibilities so changes stay as local as reasonably possible. Avoid
  unnecessary changes propagating across unrelated components.
- **Low coupling, high cohesion:** Keep related functionality together and
  minimize dependencies between independent components. Avoid tying business
  logic to implementation details; introduce explicit boundaries where they
  provide practical value.
- **Progressive abstraction:** Start with simple concrete implementations.
  Introduce abstractions when actual requirements justify them; avoid
  speculative generalization and premature extensibility. Modularity does not
  depend on the number of interfaces or abstraction layers.
- **Minimal viable architecture:** Implement only current requirements with
  the simplest maintainable design that allows reasonable evolution. Minimize
  boilerplate, indirection, and infrastructure; do not optimize for hypothetical
  requirements or add abstractions for theoretical purity. Simplicity and
  maintainability support each other.
- **Continuous architectural integrity:** Keep new features consistent with
  existing architectural decisions and reuse established patterns when
  appropriate. Justify competing approaches and reevaluate existing boundaries
  as requirements evolve.
- **Refactoring over workarounds:** Treat refactoring as a normal part of
  evolution. Prefer small, controlled refactoring over accumulated workarounds
  or preserving unsuitable structures merely to avoid changing existing code.
  Keep it proportional to the task; avoid unrelated rewrites or broad
  restructuring.
