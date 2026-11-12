# Optional history cleanup

Read when delivery history contains misleading messages, fixups, duplicates, or
corrections that obscure review. Multiple coherent commits need no squash.

- Resolve the integration base; inspect `git log --graph --oneline --decorate <base>..HEAD` and relevant diffs. Distinguish previously squash-merged work.
- Show exact commit IDs and the proposed sequence. Offer **Keep history (default)** or the concrete cleanup through supported host UI, with numbered-text fallback. Install no UI dependency.
- Cancellation or no answer keeps history. Prior authorization counts only when it covers this exact rewrite. Do not perform cleanup merely because delivery was approved.
- For published history, explain collaborator/review effects and obtain explicit rewrite and force-push approval.
- Before approved cleanup, recheck the worktree and local/remote tips, preserve a recoverable original tip, and exclude unrelated commits.
- Use authorized force-with-lease against the observed remote tip; preserve concurrent work. Never bypass protections.
- Verify the resulting tree and rerun affected checks. Changed commit identities invalidate revision-bound review evidence even when the tree is unchanged; return the new revision to the caller for review before final delivery.
