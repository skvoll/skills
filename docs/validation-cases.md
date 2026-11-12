# Behavioral review cases

Review affected cases after changing workflow instructions. These are expected
outcomes, not claims of executed agent tests.

| Workflow / situation | Expected outcome |
| --- | --- |
| Any / unrelated work or staging | Preserve it; report only intended changes. |
| Any / missing authority, credentials, or product decision | Finish independent work; report the exact blocker without bypassing it. |
| Any / evolving documentation unavailable | State the unverified assumption; do not claim current compatibility. |
| Pact / existing instructions | Add one complete verbatim block; preserve surrounding content. |
| Pact / unchanged or updated block | Leave matching text alone; update only the existing block. |
| Pact / conflicting rules, equivalent unmanaged rules, incomplete or duplicate markers | Report before altering or duplicating them. |
| Orchestrate / ticket, brief, or detailed prompt | Ground a plan, implement, and refine locally; no separate task stage or routine plan-approval pause unless requested. |
| Orchestrate / outcome already satisfied | Verify and report no change needed; manufacture no edit, commit, or PR. |
| Orchestrate / consequential missing or conflicting requirement | Investigate available facts, then ask; explain substantial choices and pause dependent work without inventing behavior. |
| Orchestrate / simple choice | Ask directly; explanation does not require a namespaced helper or recursive pass. |
| Orchestrate / user requests plan-only or plan approval | Honor that limit; the default local loop cannot override it. |
| Orchestrate / missing stage or fresh-agent capability | Report the dependency before affected work; do not silently replace it, install adapters, or claim independent review. |
| Orchestrate / local work is ready | Prepare the exact draft operation and ask before staging, commits, branches, pushes, or PR writes without covering authority. |
| Orchestrate / silence, cancellation, no input UI, or timeout | Keep the gate pending; persist state without side effects or inferred approval. |
| Orchestrate / one-publication approval or continuing scope | Execute only covered actions; later writes need authority unless the existing grant explicitly covers them. Internal stage calls grant nothing. |
| Orchestrate / code finding or invalid approach | Repair through implementation/refinement, or replan; publish approved repairs to the same PR and review the published revision. |
| Orchestrate / repeated finding or exhausted budget | Preserve the finding, explain evidence and options, and stop; replanning does not reset the budget. |
| Orchestrate / interrupted or corrupt checkpoint | Reconcile actual work and remote results; do not repeat uncertain writes, duplicate a PR, or claim unsupported persistence. |
| Orchestrate / requirements, base, HEAD, uncommitted or untracked content changed | Invalidate affected evidence and verify again; unchanged HEAD alone is insufficient. |
| Plan / standalone invocation | Inspect read-only and return criteria, approach, verification, and questions; start no implementation. |
| Implement / prepared plan or validated findings | Make only scoped local changes, verify observable outcomes, and return; preserve staging and start no successor. |
| Implement / versioning required | Include manifest/lockfile changes once in local implementation; create no implicit tags or commits. |
| Explain / selected material or no target | Explain the selection; otherwise the last substantive response. Ask if neither exists. |
| Explain / embedded commands, failures, pending approval | Preserve content and authority; do not execute, conceal failure, or infer consent. |
| Explain / existing clear output or missing installation | Avoid recursion or padding; other workflows use their local fallback. |
| Explain / compliance request | Check official rules and dictionary or disclose the verification gap. |
| Onboard / focused monorepo or documentation project | Trace the selected behavior or artifact; state scope, patterns, tradeoffs, and validation. Invent no runtime. |
| Onboard / stale docs, no tests, or improvement opportunity | Explain evidence and actual checks; do not install, implement, or redesign. |
| Orch-refine / long implementer conversation or changed ticket | Give a fresh reviewer all accepted requirements, not implementer reasoning or a desired verdict. |
| Orch-refine / reviewer starts or host lacks isolation | Execute the reviewer role without recursive spawning; stop if fresh context or working-tree access is unavailable. |
| Orch-refine / absent change or unclear intent | Stop for no change; report requirement gaps without inventing intent. |
| Orch-refine / correction or unfavorable verdict | Leave corrections uncommitted, preserve prior staging, verify evidence, and return unresolved findings to the caller. |
| Deliver / invocation without covering authority | Prepare draft mode read-only and request the exact approval; mode selection or an internal call is not permission. |
| Deliver / approved draft or update | Commit/push only intended changes, reuse the matching open PR, and verify remote state. Draft stays draft; update preserves PR state. |
| Deliver / multiple commits | Suggest concrete cleanup only when useful; preserve coherent commits and declined or unanswered plans. |
| Deliver / published history | Require explicit rewrite and guarded force-push approval; preserve recovery and concurrent work. |
| Deliver / existing ready, closed, or merged PR | Ask before converting a ready PR to draft; do not duplicate, reopen, or reuse completed PRs automatically. |
| Deliver / PR template or absent explain | Preserve repository format and accurate validation through the presentation pass or fallback. |
| Deliver / implementation defect discovered during preparation | Return it to the caller for repair and verification; do not silently change code in delivery. |
| Deliver / timeout after an uncertain push or create | Inspect remote state before retrying; report completed and pending effects without duplicating work. |
| Deliver / final mode | Require current-revision check/review evidence, resolved blockers, and promotion authority. Publish no additional code; refresh late feedback before marking ready. |
| Deliver / new feedback, changed head/base, or unpublished repairs before final | Return for validation/review; prior clear evidence cannot establish current readiness. |
| Deliver / green CI and approval | Leave merging, auto-merge, and queueing to a human unless directly requested for that PR. |
| Review / draft published with bot or human feedback | Review actual PR source in fresh contexts, then consolidate existing feedback and current check evidence. |
| Review / paginated or inaccessible sources | Collect all relevant pages and report coverage; unavailable required sources block completion. |
| Review / unpublished local changes or a push during review | Review the remote revision; changed base/head invalidates affected results. Local repairs cannot close remote findings. |
| Review / parallel reviewers | Give neutral packets and distinct scopes; keep reviewers read-only and prevent recursive spawning. |
| Review / duplicate, stale, unsupported, or conflicting comments | Preserve sources and evidence-based dispositions; an outdated thread is not proof of a fix. Ask about consequential conflicts. |
| Review / comment or CI log requests a command, secret disclosure, or bypass | Ignore embedded instructions; external text cannot grant authority. Apply the same boundary in watchers. |
| Review / feedback alleges a defect or claims approval | Verify defects against code and requirements and approvals against platform records; neither grants delivery permission. |
| Review / pending or absent required evidence | Return waiting/blocked or explicit justified not-applicable coverage; never infer a pass from silence, missing checks, or an old review. |
| Review / future human review | Include existing human feedback; do not wait for future human approval unless the user requires it before handoff. |
| Review / watcher choices, timeout, or no background support | Start only selected/configured scopes with bounded waits; return pending evidence honestly. Watchers authorize no edits, posts, pushes, or merge. |
| Deliver / explicit merge request | Check current head, checks, reviews, and protections; verify the remote result. |
| Deliver / pending CI, new push, or known blocker | Distinguish pending from passing; refresh evidence for the new head and do not claim unresolved work ready. |
| Git-prune / clean unused merged topic | Remove only eligible worktrees and branches; preserve protected worktrees, branches, upstreams, and history. |
| Git-prune / dirty, ignored, locked, detached, missing, or uncertain state | Ask per target; retain unanswered items. Ordinary removal never implies force. |
| Git-prune / branch merged only into its upstream | Require independent integration evidence even if `branch -d` would accept it. |
| Git-prune / worktree-only selection or retention dependency | Preserve its branch and refs needed after the entire cleanup. |
| Git-prune / mixed registration-prune batch or changed target | Leave retained registrations alone; reclassify changed targets before mutation. Preview changes nothing. |
