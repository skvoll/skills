# Working on skvoll/skills

Portable workflows distributed through the Vercel Skills CLI.

- Follow the [working agreement](docs/working-agreement.md).
- Before editing instructions, read the [authoring rules](docs/instruction-authoring.md).
- Edit `skills/`, not installed copies or user configuration.
- Use the upstream installer; add no custom adapters.

## Validation

Review metadata, local links, instruction consistency, and relevant
[behavioral cases](docs/validation-cases.md). Run:

```sh
npx skills add . --list
git diff --check
```

There are no dependencies, build, or automated tests. Test installation only in
a disposable project with isolated user state; never alter real agent settings.
