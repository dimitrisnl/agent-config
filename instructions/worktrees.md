# Session worktrees

- Each independent primary coding session needs its own Git worktree and branch before implementation, even when another session is working on the same feature. Do not share a writable workspace between independent sessions.
- If already working in a Git worktree, validate its path, branch, intended base, existing changes, and ownership, then reuse it when suitable for this session. Do not create another worktree unnecessarily. Create one only when no suitable isolated workspace exists; being on a feature branch alone does not establish isolation or ownership.
- Resume a session in its existing worktree rather than creating a fresh one. Check its recorded location, branch, and existing work first. A new or forked conversation does not inherit another session's workspace ownership; verify a separate assignment or an explicit transfer before reusing it.
- Establish the intended base and inspect existing changes first. If the task depends on uncommitted work in another checkout, ask how to carry it forward; do not move, stash, or commit it implicitly.
- Follow the repository's worktree location and branch conventions. Verify an in-repository location is ignored. If Git, a usable base, or a safe location is unavailable, explain the blocker and ask before implementing elsewhere.
- Report the absolute workspace path and branch before editing. Keep implementation commands and session working directories in that worktree; do not reset or overwrite an existing branch to make it fit.
- Read-only review, research, and scouting do not require a new worktree. Delegated read-only reviewers may inspect the parent session's workspace; independently writing agents need their own. Honor an explicit user request to work in a particular existing checkout instead.
- At handoff, report whether work is ongoing or complete and where its changes remain. Preserve the workspace; cleanup is a separate, explicitly approved action, not a consequence of session completion.
