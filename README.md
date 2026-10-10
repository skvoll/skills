# skvoll/skills

Portable workflows for AI coding agents, installed with the
[Vercel Skills CLI](https://github.com/vercel-labs/skills).

## Install

Run this in the project where you want the skills:

```sh
npx skills add skvoll/skills
```

The CLI lets you choose skills and agents. To install all skills for
Codex and Claude Code without prompts:

```sh
npx skills add skvoll/skills --skill '*' --agent codex claude-code --yes
```

Add `--global` to make them available across projects. Preview the collection
with `npx skills add skvoll/skills --list`, or select one with `--skill task`.
Node.js 22.20 or newer is required by the tested CLI version.

## Workflows

| Skill     | Use it for                                           | Result                                                             |
| --------- | ---------------------------------------------------- | ------------------------------------------------------------------ |
| `pact`    | Adding shared rules to a project                     | The No Side Effects Policy and other bundled rules in `AGENTS.md`. |
| `task`    | Implementing a feature, fix, or documentation change | A locally validated change.                                        |
| `refine`  | A requested final pass on an existing implementation | A corrected and simplified local change.                           |
| `deliver` | Explicitly requested delivery of prepared work       | Commit, push, PR checks/review, and merge when permitted.          |

Invoke skills with your agent's syntax, such as `$task` in Codex or `/task` in
Claude Code. Delivery must be explicitly invoked; reading or editing its skill
does not authorize Git or remote changes. Active repository instructions and
permissions still apply.

Each directory under `skills/` is self-contained. Installation copies skill
content and creates agent links (or copies with `--copy`). It does not install
global instructions, MCP servers, or agent configuration. Run `/pact` (or `$pact`
in Codex) to add our shared rules to your project's `AGENTS.md`. It preserves
existing instructions and updates its own marked block when run again.

The rule source is [pact's bundled rules](skills/pact/assets/rules.md). Add future
shared rules there; update the installed skill and rerun pact to apply them to a
project. The broader [working agreement](docs/working-agreement.md) remains
repository documentation and is not copied by pact.

Manage project installations with:

```sh
npx skills list
npx skills update
npx skills remove pact task refine deliver
```

For global installations, use `npx skills list --global`,
`npx skills update --global`, and `npx skills remove --global pact task refine deliver`.
See the [CLI documentation](https://github.com/vercel-labs/skills) for other agents
and options.

## Development

Edit `skills/<name>/SKILL.md` and keep any supporting files inside that skill's
directory. Read [AGENTS.md](AGENTS.md) and the
[authoring guide](docs/instruction-authoring.md) before changing guidance.

This repository contains Markdown skills and documentation. There are no package
dependencies, build steps, or test scripts. Review skill metadata, instructions,
and relative links, then preview local discovery without installing:

```sh
npx skills add . --list
```

## License

UNLICENSED. All rights reserved.
