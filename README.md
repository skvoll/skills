# skvoll/skills

Portable agent workflows, installed with the [Vercel Skills CLI](https://github.com/vercel-labs/skills).

## Install

Use Node.js 22.20 or newer. In the target project:

```sh
npx skills add skvoll/skills
```

To install every skill for Codex and Claude Code without prompts:

```sh
npx skills add skvoll/skills --skill '*' --agent codex claude-code --yes
```

Add `--global` for user-wide installation. Preview with `--list`; select with
`--skill <name>`. Installation copies skill directories and creates agent links
(or copies with `--copy`), not global instructions, MCP servers, or configuration.

## Use

Invoke with your host's syntax: `$task` in Codex or `/task` in Claude Code.

| Skill | Outcome |
| --- | --- |
| `pact` | Shared rules embedded in project instructions. |
| `task` | Approved plan, implementation and validation, then automatic refinement. |
| `refine` | Goal-driven fresh-context architecture review, tested local corrections, and performance assessment. |
| `deliver` | A PR ready for human review, with optional history cleanup and independent CI/comment watchers. |
| `onboard` | A source-backed maintainer lesson; optionally focus on a subsystem. |
| `explain` | Clear explanations and human-facing handoffs. |
| `git-prune` | Confirmed local branch/worktree cleanup; `preview` inspects only. |

Read a skill for its procedure and permissions. Reading or installing one does
not invoke it. Delivery leaves merging to a human unless directly requested.
Presentation uses available `explain` guidance, with a standalone fallback.

Manage installations with `npx skills list`, `npx skills update`, and
`npx skills remove <name>`. Add `--global` for global installations.

## Develop

Read [AGENTS.md](AGENTS.md). Each skill is independently installed from
`skills/<name>/SKILL.md`; support files stay inside its directory.
[Authoring rules](docs/instruction-authoring.md) define wording and validation.
[Pact's rules](skills/pact/assets/rules.md) are the shared-policy source; update
its installation and rerun pact to apply future changes to another project.
Maintainer docs under `docs/` are not installed.

## License

UNLICENSED. All rights reserved.
