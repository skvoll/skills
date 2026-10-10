# Working on skvoll/skills

This repository distributes portable agent workflows through the Vercel Skills
CLI. Edit `skills/`; installed files and links under a user's home directory are
outputs, not development targets.

Read [the working agreement](docs/working-agreement.md) for the side-effect
policy. Before changing agent-facing Markdown, read
[the authoring guide](docs/instruction-authoring.md).

## Repository constraints

- Each immediate child of `skills/` is a self-contained skill. Keep its directory
  name aligned with the frontmatter name. Supporting files belong inside that
  directory, linked with relative paths that survive installation.
- Keep workflows portable across agents. Use the upstream CLI for discovery
  and installation; do not add a custom installer or adapters.
- Keep maintainer documentation and optional instruction examples in `docs/`.
  They are not installed or automatically loaded by the Skills CLI.
- Preserve existing user edits and workflow permission boundaries. Reading or
  editing a skill does not invoke it.

## Validation

Review frontmatter, directory/name agreement, instruction consistency, and local
links. Run `npx skills add . --list` to check discovery and `git diff --check` for
whitespace errors. This collection has no package dependencies, build, or test
suite.

If installation behavior needs checking, use the upstream CLI in a disposable
project with isolated user state. Do not install globally or change real user
configuration as a routine check.
