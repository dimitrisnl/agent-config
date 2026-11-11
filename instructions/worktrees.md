# Session worktrees

- Use a Git worktree and branch for implementation unless the user explicitly requests another checkout.
- When resuming a feature, reuse its existing worktree. Check its branch and existing changes; ask if unsure which worktree to use. Do not share a writable worktree with another active coding session.
- Preserve existing changes. Do not move, stash, or overwrite existing work without approval.
- Keep edits, tests, and development servers pointed at the selected worktree.
- Read-only review, research, and scouting do not need a worktree.
- When feature work is complete and pushed, suggest removing its worktree. Check for uncommitted or unpushed work and ask before removing it; never remove it automatically.
