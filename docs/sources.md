# Source notes

Use primary sources for compatibility; examples inspire style, not authority.
Review dates describe past checks. Recheck affected assumptions before changing
formats, invocation, loading, or host integration.

| Source | Recorded decision |
| --- | --- |
| [Agent Skills specification](https://agentskills.io/specification) | Portable frontmatter and self-contained directories; reviewed 2026-10-09 and 2026-10-20. |
| [Vercel Skills CLI](https://github.com/vercel-labs/skills) | Delegate discovery and installation upstream. Version 1.7.2 passed discovery and isolated installation on 2026-10-09; 1.7.6 passed discovery during this work. Neither is a repository dependency. |
| [AGENTS.md](https://agents.md/) and [Codex loading](https://developers.openai.com/codex/guides/agents-md) | Repository instructions have host-specific loading behavior. |
| [Codex skills](https://developers.openai.com/codex/skills), [authoring](https://developers.openai.com/blog/rethinking-skills-and-prompts-for-gpt-6-astra) | Verify current host support; prefer focused, actionable instructions. |
| [Claude skills](https://code.claude.com/docs/en/skills), [memory](https://code.claude.com/docs/en/memory) | Review on 2026-10-09 recorded direct AGENTS.md support at 2.1.277 and broader sessions at 2.1.281, subject to enabled support and instruction precedence; no CLAUDE.md wrapper. Reverify before relying on this. |
| [ub-mode](https://github.com/unclebob/ub-mode/blob/master/SKILL.md) | Short grouped statements inspired presentation on 2026-11-04; its tools, logs, Git, and cleanup policies were not adopted. |
| [Matt Pocock's skills](https://github.com/mattpocock/skills) | Focused workflows and conditional references inspired structure; no required interviews, integrations, or orchestration. |
| [Architecture workflow](https://github.com/mattpocock/skills/blob/main/skills/engineering/improve-codebase-architecture/SKILL.md), AI Hero [codebase design](https://www.aihero.dev/skills-codebase-design) and [domain modeling](https://www.aihero.dev/skills-domain-modeling) | Reviewed 2026-10-10 for source-backed onboarding, maintenance hotspots, tradeoffs, and project vocabulary; no redesign, glossary, ADR, or report requirement. |
| Git [worktree](https://git-scm.com/docs/git-worktree), [branch](https://git-scm.com/docs/git-branch), [status](https://git-scm.com/docs/git-status), [refs](https://git-scm.com/docs/git-for-each-ref) | Reviewed 2026-10-20 with Git 2.50.1: independent ancestry checks, ignored-file inspection, local upstream dependencies, retained-history proof, and non-mutating status. |
| [Git log](https://git-scm.com/docs/git-log), [gh pr ready](https://cli.github.com/manual/gh_pr_ready), [gh pr checks](https://cli.github.com/manual/gh_pr_checks) | Upstream sources and installed help checked 2026-11-06 for history review, draft promotion, and opt-in CI watching. |
| ACP [v1 plans](https://github.com/agentclientprotocol/agent-client-protocol/blob/main/docs/protocol/v1/agent-plan.mdx), [v2 plans](https://github.com/agentclientprotocol/agent-client-protocol/blob/main/docs/protocol/v2/agent-plan.mdx), [session modes](https://github.com/agentclientprotocol/agent-client-protocol/blob/main/docs/protocol/v1/session-modes.mdx) | Reviewed 2026-11-06: plan payloads differ; mode guidance points toward session config. Use exposed capabilities, not hard-coded protocol calls. Plan display does not enforce approval. |

Fresh-context refinement uses the host's available isolation mechanism;
`fork_turns="none"` applies only where exposed. Context separation reduces
carry-over bias, not all bias. No persistent-agent or UI capability is assumed.
