# Working on skvoll/skills

Portable workflows distributed through the Vercel Skills CLI.

- Follow the [working agreement](docs/working-agreement.md).
- For every instruction change or new skill, read the [authoring process](docs/instruction-authoring.md) before editing and complete it before handoff.
- Edit `skills/`, not installed copies or user configuration.
- Use the upstream installer; add no custom adapters.

## Validation

Check metadata, local links, independent packaging, instruction consistency,
context cost, and affected [behavioral cases](docs/validation-cases.md). Run:

```sh
npx skills add . --list
git diff --check
```

No dependencies, build, or automated tests exist. Test installation only in a
disposable project with isolated user state; never alter real agent settings.
