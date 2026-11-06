## No Side Effects Policy

- Default to denying changes outside ordinary development in the current workspace.
- Honor permission already granted for the task. Check its scope before asking again.

| Action                                                                                                                                                      | Default boundary                                                                                                                        |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| Read files, inspect Git, inspect available remote information                                                                                               | Allowed when relevant to the task.                                                                                                      |
| Edit repository files; install project dependencies; build, test, lint, format, generate code; run the local application                                    | Allowed within the task. Understand scripts and hooks before running them. Normal package downloads and incidental caches are included. |
| Start or stop project processes; change local development databases, containers, or services                                                                | Allowed only when clearly project-owned and disposable. Verify ownership and data scope first.                                          |
| Stage or commit; create/delete branches or tags; pull, merge, rebase, cherry-pick, amend, reset, stash, clean, restore; change Git configuration or remotes | Requires explicit authorization for the operation or a workflow that includes it.                                                       |
| Push; change PRs, issues, reviews, CI state, releases, repository settings, or permissions                                                                  | Requires explicit authorization for the operation or a workflow that includes it.                                                       |
| Deploy, publish, upload, send messages, mutate external services or shared infrastructure                                                                   | Requires explicit authorization covering the destination and action.                                                                    |
| Use sudo; install global/system packages; modify OS configuration, unrelated user files, other projects, or unrelated processes                             | Requires explicit authorization.                                                                                                        |

### Check the boundary

- A script name, documented command, reversible action, or available tool does not grant permission.
- Local commands that write remotely or change user-level configuration still cross the boundary.
- Never assume shared, staging, or production data is disposable.

### Preserve work

- Inspect exact targets before destructive actions. Preserve existing user work.
- Do not discard, overwrite, or clean unrelated state.
- If scope or ownership is unclear, finish independent local work first.
- Then state the proposed action, purpose, and persistent changes; request authorization.
- Wait before acting. Never bypass environment approval or protection.

### Invoke deliberately

- Explicit skill invocation authorizes only its described actions, subject to active instructions and environment restrictions.
- Reading, editing, reviewing, or mentioning a skill does not invoke it.
- `task` and `refine` cover local work. `deliver` defines the delivery boundary.

## Evolutionary Software Architecture

Build what is needed today. Keep future changes local and inexpensive.
These are design guidelines, not a required methodology.

### Locality

- Keep related behavior together behind clear boundaries.
- Make a change in one area without spreading it across unrelated components.

### Coupling and cohesion

- Group related responsibilities. Separate independent ones.
- Avoid dependencies between unrelated concerns.

### Abstraction

- Start with simple, concrete implementations.
- Add abstraction when it solves a demonstrated need.
- Modularity does not depend on interface or layer count.

### Scope

- Use the fewest concepts that meet current requirements.
- Avoid speculative generalization and premature extensibility.

### Architectural integrity

- Follow existing decisions and patterns. Explain competing approaches and tradeoffs.
- Revisit a decision when evidence warrants it.

### Refactoring

- Prefer small structural improvements over accumulated workarounds.
- Keep refactoring proportional to the task. Avoid unrelated rewrites.
