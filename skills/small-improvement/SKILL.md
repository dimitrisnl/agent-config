---
name: small-improvement
description: Find or complete one bounded, behavior-preserving maintenance task backed by the target repository's conventions. Use for small refactors, legacy naming cleanup, incremental migrations, unused code, and test hygiene.
---

# Small improvement

Find or complete one small maintenance task that advances an established repository convention without changing observable behavior. Prefer no patch over speculative churn.

## Modes and authority

Accept `local` (default) or `scout`, optionally followed by a target area or maintenance priority.

- **local:** select and implement one cleanup, leaving an uncommitted patch in an isolated workspace.
- **scout:** inspect only and recommend one candidate in the response; do not edit files or create state, branches, or worktrees.

Neither mode authorizes commits, publication, CI tending, or deployment. The former `pr` mode and size budgets are not supported; explain this if requested rather than silently treating them as a target area. Do not create persistent backlogs, locks, or scheduled work.

## Establish the maintenance policy

Read the target repository's instructions, applicable nested rules, lint configuration, migration guidance, and relevant neighboring code. Honor user-specified priorities. Discover the toolchain and checks rather than assuming a language or framework.

The repository or user defines the desired convention; this skill executes it. If the direction is ambiguous or conflicting, propose a policy for approval before enforcing it. A migration needs an explicit request or documented initiative, not just the presence of newer files nearby.

## Select one useful change

Inspect a relevant area, not the entire codebase by default. Choose one complete, reviewable unit with a concrete benefit, known consumers, and a practical validation plan. It may span several files when consumers must change together.

- **Incremental migration:** migrate a small module only when supported by repository policy and tooling. Preserve runtime behavior and provide real types; changing an extension or suppressing diagnostics is not sufficient.
- **Naming and placement:** apply established internal conventions and update consumers. Preserve external fields, persisted keys, public contracts, and framework-discovered names; account for filesystem case collisions.
- **Unused code:** establish that private code has no consumers or required side effects, including dynamic registration and discovery. Lack of imports alone is not proof.
- **Local simplification:** remove demonstrated duplication or unnecessary indirection without introducing a new architecture.
- **Test hygiene:** fix a concrete testing weakness without weakening assertions, adding arbitrary waits, or compensating with unrelated mocks.

Exclude generated or vendored files, incidental formatting, dependency upgrades, product decisions, shared-contract redesigns, and incomplete first steps. Report discovered behavior bugs separately instead of expanding the cleanup. Stop with no patch when no useful, safe candidate is established.

## Implement safely

In `scout`, stop after selecting a candidate and reporting its evidence and validation plan.

For `local`, inspect status, branch, existing worktrees, and related pending work before editing. Establish the intended base; ask if it is ambiguous. Preserve pre-existing changes and avoid overlapping cleanup work. Resume an existing patch only when requested and its ownership and scope are verified.

Follow the [session worktree rules](../../instructions/worktrees.md) for implementation. Use this session's workspace rather than creating another for each cleanup. Do not automatically delete existing branches, worktrees, or state.

Run relevant baseline checks in that workspace before making the selected change. Complete the cleanup and its necessary consumer updates without widening the scope to unrelated diagnostics.

## Validate and report

Discover validation commands from repository instructions, manifests, and CI. Check their side effects before running them; do not install new tooling, flush shared services, or run deployment commands. Run resource-intensive checks sequentially unless the repository supports safe parallel execution.

Run repository-required checks and change-relevant lint, type checks, and tests. Verify references and resolution after renames, reachability after deletions, and build or discovery behavior when affected. Compare failures against the baseline. Zero matched tests and timeouts are not passes; do not weaken contracts or suppress checks to obtain green results.

Review the complete patch for correctness and unnecessary complexity, run `git diff --check`, and fix verified findings within scope. Report blocked checks and limitations without claiming validation that did not run.

Report the selected change and policy evidence, workspace and branch when created, checks and results, and any remaining blocker. Leave local changes uncommitted. For `scout` or a skipped run, report the candidate or why no suitable work was found; no persistent record is required.
