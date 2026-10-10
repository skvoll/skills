---
name: pact
description: Add or refresh shared rules, including the No Side Effects Policy, in a project's AGENTS.md. Use when the user asks to apply pact or install these rules in a project.
---

# Pact

Add the bundled rules to the project's persistent agent instructions. Installing
this skill alone does not apply the rules; running it edits the target project.

## Read and scope

Read all of [assets/rules.md](assets/rules.md). It is the complete rule set to
install, including future additions; do not select only the side-effect section.

Use the project the user names, otherwise the current repository root (or the
working directory if there is no repository). Read its applicable instructions
and existing `AGENTS.md` before editing. Default to that project's `AGENTS.md`,
not user-level or global configuration. Do not follow a link outside the target
project without authorization for that destination.

## Add or refresh

Copy the full rule text verbatim into `AGENTS.md` between these markers:

```markdown
<!-- pact:start -->
<!-- pact:end -->
```

Create `AGENTS.md` if absent. Otherwise append the block, preserving existing
content. If a single complete pact block already exists, update that block in
place; if it already matches, leave the file unchanged. Never append a second
copy. Do not replace the document, rewrite unrelated instructions, or remove
rules outside the block.

Check for conflicting project instructions or local customizations before
replacing an existing block. Preserve project-specific constraints; if they
conflict with the bundled rules, explain the exact conflict and ask how to
resolve it. Likewise, do not guess replacement boundaries for incomplete or
duplicate markers. Existing equivalent rules outside a pact block should be
reported rather than duplicated or silently taken over.

Embed the rules themselves, not an import or link into this installed skill.
The resulting instructions must work without the skill remaining installed.
Applying pact authorizes this local instruction edit, not the side effects
described in the rules or any commit, push, or global configuration change.

## Verify

Review the resulting diff. Confirm the rules are complete, there is only one
pact block, and content outside it is unchanged. Report the target file and
whether rules were added, refreshed, already present, or blocked by a conflict.
Future rule changes take effect in a project when the user updates the installed
skill and runs pact again.
