# Instruction authoring

Apply to every skill addition or edit, including follow-up corrections.

## Write

- Use plain words, active verbs, and short rules. Give each statement one job: an action, condition, check, or boundary.
- Merge semantic duplicates; give each rule one authoritative home. Remove filler, generic advice, narration, and repeated cautions.
- Separate requirements from suggestions. Preserve permissions, exceptions, failure handling, stopping conditions, and evidence.
- Use task-based, agent-neutral artifact names. Keep host-specific names only where an interface requires them.

## Place

| Content | Home |
| --- | --- |
| Entry and checks | `AGENTS.md` |
| Collaboration | `docs/working-agreement.md` |
| Authoring | This file |
| Shared permissions/design | `skills/pact/assets/rules.md` |
| Procedure | `skills/<name>/SKILL.md` |
| Substantial conditional detail | That skill's `references/` |
| Presentation | `skills/explain/SKILL.md` |
| Installation/discovery | `README.md` |

Each independently installed skill needs its own scope, inputs, procedure, and
completion criteria; root guidance is not installed. Keep essential boundaries
local. Link optional skills with a minimal fallback; never share files through
cross-package links. Reading or editing a skill does not invoke it.

Use UTF-8 Markdown and YAML `name`/`description`. Match directory names with
lowercase letters, digits, and single hyphens, at most 64 characters. Descriptions
must be specific, nonempty, and at most 1024 characters; procedures belong in the
body. Link references directly with their read condition. Verify host extensions
and changing external assumptions against [primary sources](sources.md).
Instructions do not enforce a sandbox.

## Complete every change

1. Inspect related skills and callers. Apply transferable lessons at their owner; avoid overlapping workflows or copying local rules everywhere.
2. Map retained requirements, then consolidate before adding rules. Add behavior only for an established need with a useful validation case.
3. Read back the complete affected instructions. Remove duplication, contradictions, vague wording, unnecessary concepts, and stale placeholders.
4. Compare word counts with the task's starting state and Git base, including references. Relocation is not a reduction. Justify any net growth by missing required behavior after consolidation; never trade correctness for a word target.
5. Run `AGENTS.md` checks and affected [cases](validation-cases.md). Use authorized isolated evaluation when useful; never mutate real Git/remote state to test prose.
6. Repeat the density check after corrections, before declaring readiness or preparing delivery. Report counts and executed validation; structural checks do not prove agent behavior.
