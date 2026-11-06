# Authoring rules

## Wording

- Use the fewest words that preserve the decision.
- Use plain words, active verbs, and short statements.
- Give each statement one job; group related jobs under useful headings.
- Keep a sentence only if it changes an action, condition, check, or boundary.
- Merge statements doing substantially the same work, even when phrased differently. Treat roughly 80% overlap as a consolidation signal, not a mechanical score.
- Give each rule one authoritative home. Elsewhere, link or name it; do not paraphrase it again.
- Remove filler, repeated cautions, generic advice, and historical narration. Preserve exceptions and evidence that affect behavior.
- Separate requirements from suggestions. Do not shorten away permissions, failure handling, or stopping conditions.

## Ownership

| Content | Home |
| --- | --- |
| Repository entrypoint and required checks | `AGENTS.md` |
| Collaboration | `docs/working-agreement.md` |
| Authoring | This file |
| Shared permissions and design rules | `skills/pact/assets/rules.md` |
| Workflow procedure | `skills/<name>/SKILL.md` |
| Conditional workflow detail | That skill's `references/` |
| Human-facing presentation | `skills/explain/SKILL.md` |
| Installation and discovery | `README.md` |

Root guidance is not installed. Each skill must carry its essential scope,
inputs, procedure, and completion criteria. A short reference to an optional
skill is an invocation hook, not a second copy of its rules. Retain only the
fallback needed when that skill is absent. Never link outside an installed
skill directory to share implementation files.

## Structure

- Give each skill one distinct purpose. Add no overlapping workflows.
- Use UTF-8 Markdown and YAML `name` and `description` frontmatter.
- Match the directory name: lowercase letters, digits, and single hyphens; at most 64 characters.
- Keep descriptions nonempty, at most 1024 characters, and specific enough for discovery. Put the procedure in the body.
- Use references only for substantial conditional detail; link directly and state when to read them.
- Prefer portable prose. Verify host extensions before adopting them; instructions are not an enforced sandbox.
- Editing or explaining a skill does not invoke it. Preserve each workflow's authority and handoff.

## Review

1. Map each old requirement to its new home. Remove repeated wording, not behavior.
2. Review for contradictions, unnecessary concepts, missing exceptions, and unresolved placeholders.
3. Check metadata, links, and independent packaging; run the checks in `AGENTS.md`.
4. For workflow changes, walk through the relevant [cases](validation-cases.md). Use isolated behavioral evaluation when available and authorized; never mutate real Git or remote state merely to test prose.
5. Report word counts and validation honestly. Structural checks do not prove agent behavior.

Consult [source notes](sources.md) when changing format, host behavior, or external
assumptions.
Add a new rule only for a recurring failure, at its existing source, with a useful
validation case. Do not accumulate universal cautions after isolated mistakes.
