## Permissions

- Preserve user work. Inspect exact targets before destructive actions.
- Reuse authorization already granted; ask only for a missing boundary.
- Ordinary local development permits inspection, edits, dependencies, builds, tests, and project execution. Inspect scripts and hooks first.
- Start or stop services and change local data only when clearly project-owned and disposable.
- Other side effects—including Git mutations, remote writes, messages, deployment, publication, global packages, sudo, and user/OS configuration—require explicit authorization or an invoked workflow covering them.
- A tool, script, documented command, or reversible action grants no authority. Local commands can have remote effects.
- Never assume shared data is disposable or bypass protections.
- If ownership or scope is unclear, finish independent work, then state the action, purpose, persistent effects, and required permission. Wait before acting.
- Invoking a skill authorizes only its stated scope under active restrictions. Reading, editing, reviewing, or mentioning it does not invoke it.

## Design

- Build for current needs with the fewest useful concepts.
- Group related behavior; separate independent responsibilities and state.
- Keep dependencies and changes local behind meaningful boundaries.
- Add abstraction only for a demonstrated need; layer count does not establish modularity.
- Follow existing decisions; explain competing tradeoffs and revisit assumptions when evidence changes.
- Prefer small structural improvements over workarounds. Keep refactoring proportional to the task.

These are design guidelines, not a required architecture or methodology.
