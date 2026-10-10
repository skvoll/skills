# Maintaining instructions and skills

Read this guide when changing this collection's agent-facing Markdown or skill
packaging. It records authoring decisions for future requests; it is not installed
with the skills.

## Put guidance where it is needed

| Content                                              | Source                                      | Audience and loading                                                         |
| ---------------------------------------------------- | ------------------------------------------- | ---------------------------------------------------------------------------- |
| Shared rules                                         | `skills/pact/assets/rules.md`               | Bundled with pact; copied into a project's `AGENTS.md` when pact runs.       |
| Broader working agreement                            | `docs/working-agreement.md`                 | Repository guidance; links to the shared rules rather than duplicating them. |
| A task-specific workflow                             | `skills/<name>/SKILL.md`                    | Discovered by name and description; read when applicable.                    |
| Substantial conditional details                      | A skill's `references/` directory           | Link from the skill with a clear condition for reading.                      |
| Repeatable deterministic operations or output assets | A skill's `scripts/` or `assets/` directory | Add only when the workflow needs them.                                       |
| Repository constraints                               | Root `AGENTS.md`                            | Future work on this repository; read directly by supported agents.           |
| Rationale, maintenance standards, and source notes   | `docs/`                                     | Maintainers; link from the relevant entrypoint.                              |
| Installation and usage                               | `README.md`                                 | People installing this collection with the Skills CLI.                       |

Keep each rule in one authoritative place. Skills must state their own permission
boundary and respect the consumer's active instructions; the optional working
agreement is not installed alongside them. Pact's bundled rule file is the
authoritative source for the No Side Effects Policy and future shared rules.
Add new rules there so pact includes them without changing its procedure.
Root guidance applies only to this repository.

The Skills CLI discovers `skills/<name>/SKILL.md` and installs each skill
directory independently. It does not install root guidance, files in `docs/`,
MCP configuration, or host settings. Skill references must travel inside their
skill directory and use relative links. A link back into this checkout will not
survive installation elsewhere.

## Write for decisions

Give each skill one recognizable job, concrete inputs, an actionable workflow,
and a verifiable completion condition. Keep descriptions short enough to make
selection easy. Include exclusions when they distinguish likely neighboring
requests; put the procedure in the body.

Prefer instructions that change a decision: where to inspect, what evidence is
needed, what outcome to produce, and when to stop. Replace repeated persona
claims and generic quality advice with repository constraints or observable
checks. Use direct language and headings that help navigation.

Separate requirements from recommendations. Use mandatory wording for actual
invariants, such as preserving user work or verifying the current PR revision.
Keep routine implementation choices flexible. A reference repository's preferred
interview process, agent topology, or test style is not automatically a collection
requirement. Resolve discoverable facts before asking the user.

Use a supporting reference only when it meaningfully reduces irrelevant context.
State when to open it and link directly; avoid chains of index files. Short
skills can be self-contained. Add a new skill only for a distinct recurring task,
not as another name for an existing workflow.

## Format and invocation

Use UTF-8 Markdown with YAML frontmatter containing `name` and `description`.
The name matches the directory, uses lowercase letters, digits, and single
hyphens, and is at most 64 characters. Descriptions are nonempty and at most
1024 characters; these specification limits are ceilings, not length targets.
See the [Agent Skills specification](https://agentskills.io/specification).

Keep shared skills portable. Native invocation metadata is host-specific:
verify each host's documented support and the Skills CLI before adding it.
The current shared skills use the portable frontmatter fields and prose gates;
these are behavioral instructions, not a sandbox or enforced permission system.

`pact` adds or refreshes bundled rules in a project's `AGENTS.md`; installing it
alone does not apply those rules. `task` handles implementation. `refine` handles
an explicitly requested final pass over existing work. `deliver` handles explicitly requested delivery and
defines its authorized mutations. Neither implementation nor refinement should
automatically start delivery. Mentioning a skill in a review, editing its file,
or asking how it works does not activate that workflow.

## Validate a change

1. Check frontmatter, directory/name agreement, relative links, and the absence
   of unfinished placeholders. Use an available skill validator, but inspect
   which format and host extensions it actually supports.
2. Read the affected instructions together. Check for contradictory permissions,
   duplicated requirements, and references that cannot resolve after installation.
3. Walk through realistic requests using the cases below. For changes to triggers
   or authority, use isolated behavioral evaluation when available and authorized;
   compare observed actions with the expected boundary. Do not exercise real
   commits, pushes, or remote services just to test prose.
4. Run the checks in `AGENTS.md`: review metadata and self-contained links, check
   discovery through the upstream CLI, and inspect whitespace with Git. There
   is no local build or test suite. If installation needs checking, use disposable
   projects and isolated user state for Codex and Claude Code. Compare installed
   content with source. Conflict handling and recovery belong to the upstream
   installer; this collection does not implement them.
5. Report which checks were mechanical, which were manual, and which behavior
   remains untested. Formatting success alone does not establish agent behavior.

| Example request or situation                                               | Expected behavior                                                          |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| "Use pact" with existing project instructions                              | Add the bundled rules once; preserve existing content.                     |
| Run pact again, then update its bundled rules and rerun                    | An unchanged block stays unchanged; updated rules replace that block only. |
| Pact finds conflicting custom rules or incomplete markers                  | Report the conflict before overwriting; do not add a duplicate block.      |
| "Use task to fix this bug" with an unrelated dirty file                    | Investigate, implement, and validate locally; preserve the unrelated file. |
| "Explain how deliver works" or "Rewrite all skills"                        | Read or edit the skill; do not stage, commit, push, or open a PR.          |
| "Use refine on this change"                                                | Improve the prepared change locally; report if no prepared change exists.  |
| "Use deliver" in this repository with a prepared change                    | Commit and push through the applicable PR workflow; no package bump.       |
| A new push after green checks, or CI still pending                         | Reassess the current head and wait; do not claim a verified merge.         |
| Required human review, missing credentials, or a broad redesign needed     | State the specific dependency; do not bypass it or expand scope.           |
| A request relies on changed host features and current docs are unavailable | State the unverified assumption and use supported local evidence.          |

When a recurring failure warrants a rule, update its existing source and add a
meaningful scenario. Avoid accumulating a new universal prohibition after every
one-off mistake. Preserve durable decisions and reasons, not session transcripts.

## Recheck current standards

Baseline reviewed: **2026-10-09**. This is a dated source check, not a promise that
the guidance stays current. Before future changes to skill formats, discovery,
invocation controls, instruction loading, or recommended authoring patterns,
reopen the relevant primary sources and compare them with supported host
versions. Also revisit assumptions after host/model upgrades or a demonstrated
behavioral failure. Do not require broad research for an unrelated wording edit.

Use the specification for portable format requirements, host documentation for
actual host behavior, and community repositories for design inspiration:

- [Vercel Skills CLI](https://github.com/vercel-labs/skills): source discovery,
  installation scope, agent selection, and copying skill directories. Rechecked
  on **2026-10-09** against the README, discovery implementation, and npm version
  **1.7.2**. Use a flat `skills/<name>/SKILL.md` collection and delegate
  installation to the CLI. Global instructions and host configuration are no
  longer distributed. Version 1.7.2 passed discovery and isolated installation
  checks during migration; it is not a repository dependency. Record the CLI
  version used when rechecking compatibility.
- [Agent Skills specification](https://agentskills.io/specification): portable
  metadata and supporting-resource structure.
- [AGENTS.md](https://agents.md/): repository instruction conventions.
- [OpenAI skills documentation](https://developers.openai.com/codex/skills) and
  [instruction loading](https://developers.openai.com/codex/guides/agents-md):
  Codex discovery, invocation settings, and instruction scope.
- [OpenAI authoring guidance](https://developers.openai.com/blog/rethinking-skills-and-prompts-for-gpt-6-astra):
  concise descriptions and revisiting instructions as model capabilities change.
- [Claude Code skills](https://code.claude.com/docs/en/skills) and
  [memory/instructions](https://code.claude.com/docs/en/memory): host extensions
  and instruction loading. Rechecked on **2026-10-09**: direct `AGENTS.md`
  support starts at v2.1.277, with broader session support at v2.1.281. This
  repository uses that support without a `CLAUDE.md` import wrapper. It requires
  the built-in support to be enabled and no project or ancestor Claude instruction
  file taking precedence under the default setting.
- [Matt Pocock's skills](https://github.com/mattpocock/skills), especially
  [writing-for-agents](https://github.com/mattpocock/skills/blob/main/skills/productivity/writing-for-agents/SKILL.md)
  and [tdd](https://github.com/mattpocock/skills/blob/main/skills/engineering/tdd/SKILL.md):
  inspiration for conditional references, focused workflows, and testing behavior
  through interfaces. This collection adapts these ideas without requiring that
  collection's interviews, integrations, or agent orchestration.

Record the date, relevant source, compatibility impact, and resulting decision
when a recheck changes guidance. If sources are inaccessible, record what remains
unverified; do not label remembered advice as the latest standard. Rechecking
does not authorize dependency upgrades, installation, or remote changes.
