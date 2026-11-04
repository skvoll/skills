---
name: pact
description: Add or refresh shared rules, including the No Side Effects Policy, in a project's AGENTS.md. Use when the user asks to apply pact or install these rules in a project.
---

# Pact

Embed the complete bundled rules in the project's persistent instructions.

## Scope

- Running pact authorizes this local instruction edit only.
- Installing, reading, or editing the skill does not apply its rules.
- Commits, pushes, global configuration, and other side effects need separate authorization.
- Use the named project; otherwise use the current repository root, or working directory outside a repository.
- Target that project's `AGENTS.md`.
- Do not follow links outside the project without authorization for the destination.

## Inspect

- Read all of [assets/rules.md](assets/rules.md), including future additions.
- Read applicable instructions and the target `AGENTS.md`.
- Check for conflicting project rules and customizations before editing.
- For conflicts, explain the exact disagreement and ask how to resolve it.
- Report equivalent rules outside a pact block. Do not duplicate or silently take them over.
- For incomplete or duplicate markers, ask rather than guessing replacement boundaries.

## Add or refresh

Copy the full rule text verbatim between these markers:

```markdown
<!-- pact:start -->
<!-- pact:end -->
```

- Create `AGENTS.md` if absent; otherwise append the block.
- If one complete block exists, update it in place.
- If it already matches, leave the file unchanged.
- Keep exactly one block. Preserve all content outside it.
- Embed the rules themselves; an import or link would depend on the skill remaining installed.

## Verify

- Review the diff for complete rules, one block, and unchanged surrounding content.
- Report the target and outcome: added, refreshed, already present, or blocked.
- Future rule updates reach a project when the installed skill is updated and pact runs again.
