---
name: session-handoff
description: Write a concise handoff so another session or agent can continue existing work. Use only when the user explicitly requests a handoff.
disable-model-invocation: true
---

# Session handoff

Capture the context another agent needs to continue, not a transcript of everything discussed. Use normal session resume or compaction when no transfer is needed.

## Establish the current state

Use the current conversation and relevant existing artifacts. If the user names a different session or a next task, tailor the handoff to it. Report missing context rather than inventing decisions or searching unrelated private logs.

Inspect the repository identity, absolute workspace path, branch, HEAD, and working-tree status where applicable. Distinguish committed work from uncommitted and untracked changes, and existing user work from changes made in this session. If ownership is uncertain, say so.

Keep inspection read-only. Do not commit, stash, move or copy source changes, change branches, create worktrees, or alter session ownership just to prepare a handoff. Apply the [session-worktree rules](../../instructions/worktrees.md) when describing how implementation can continue; a handoff does not itself authorize sharing a writable workspace.

## Write the handoff

Include only what is relevant:

- **Goal and decisions:** intended outcome, agreed constraints, and consequential choices.
- **Current state:** completed work, remaining work, blockers, and workspace identity. Make uncommitted changes and ownership uncertainty explicit.
- **Evidence:** checks actually run and their results, separate from proposed checks or inferred conclusions. Reference existing specs, issues, commits, diffs, and diagnostic artifacts by path or URL rather than duplicating them.
- **Next action:** the next useful step, unresolved questions, and any required access or approval. Suggest skills only when they would help that step; do not assume previous browser approval applies to a different session or scope.

Separate confirmed facts, user decisions, and unverified assumptions. Redact credentials and sensitive personal or customer information. Refer to private configuration by purpose or location only when needed; do not embed its contents.

Save one Markdown file outside the repository by default, using the OS temporary directory and a unique descriptive filename. Honor a user-specified destination, but do not overwrite an existing file without approval. Temporary files may expire; say so when durable storage matters.

Return the absolute path and a short description of the handoff's focus. Writing the file does not start a new session, transfer workspace ownership, or authorize implementation or publication.
