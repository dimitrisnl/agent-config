---
name: review-code
description: Review a diff for verified bugs, maintainability problems, missed reuse, test gaps, and inaccurate claims. Use for code reviews, regression checks, and comprehensive change reviews.
---

# Review code

Review correctness and maintainability together. Prefer a small set of verified, actionable findings over speculative warnings or cosmetic nits.

## Scope and safety

Read repository instructions and review conventions. Establish the requested diff, base, head, and uncommitted changes; ask if the target is ambiguous. Inspect neighboring implementations and affected callers. All review passes must inspect the same snapshot; recheck stale evidence if files or revisions change.

Review read-only: do not edit files, write repository notes, implement fixes, or run checkout, switch, reset, stash, or other commands that change the shared checkout. Run tests only when their side effects are understood and acceptable; do not install dependencies or update snapshots.

For small or tightly coupled changes, apply all lenses in one pass. For independent areas, delegate only when the user or invocation authorizes it and the tool supports it. Give each reviewer the same exact scope, relevant instructions, lens, and read-only constraints. Prefer a restricted reviewer profile when available; do not require a particular model.

## Correctness and test coverage

- Authorization and access control.
- State transitions, validation, and invalid persisted data.
- Response status, error class, and payload changes.
- Omitted, default, nil/null, empty, and zero-value inputs.
- Races, retries, ordering, partial updates, and non-atomic flows.
- Tests that pass without exercising the behavior they claim to protect.

Before reporting a bug, establish a reachable trigger, trace the consequence, and rule out guards or caller contracts that make it impossible. Use a targeted test or reproduction when practical; otherwise state the code evidence and what remains untested. A test gap alone is not proof of a production defect.

## Maintainability and reuse

Working behavior does not excuse a structural regression. Be ambitious about simplification: look for changes in ownership or representation that delete concepts, branches, modes, wrappers, or layers rather than spreading complexity across more files.

- **Branching:** flag scattered feature checks, special cases, and nullable modes that tangle unrelated flows. Show a simpler representation or ownership boundary instead of prescribing an abstraction without a concrete benefit.
- **Abstraction value:** question pass-through helpers, identity wrappers, generic machinery hiding a simple shape, and speculative extensibility without a real caller requirement.
- **Types and boundaries:** inspect unnecessary optionality, broad types, repeated casts, and silent fallbacks that obscure invariants. Distinguish variable inputs from missing contracts.
- **File growth:** crossing 1,000 lines in a non-generated file is a decomposition signal, not proof of a problem. Identify a cohesive boundary or explain why the size is justified.
- **Canonical ownership:** keep behavior in the layer that owns it. Search for existing helpers, constants, fixtures, assertions, and patterns when assessing new equivalents.
- **Orchestration:** flag avoidable serialization or partial updates only when a simpler parallel or atomic flow is practical, accounting for ordering, callbacks, and failure behavior.

For a reuse finding, cite the existing symbol's path and line, show that it fits the use case, explain meaningful differences, and give a concrete replacement. Similar names or common matcher syntax are not proof of duplication. Count callers only when adoption or compatibility matters. A drift-detection test between two copies is a reason to investigate deleting a copy, not automatically to preserve both.

Verify design concerns against callers and repository conventions. An alternative is actionable only when it demonstrably reduces concepts, branches, coupling, or maintenance work without losing behavior. Prioritize structural regressions and concrete simplifications over naming nits.

## Claim verification

Check new or rewritten user-facing prose against the implementing code, including default and omitted-input paths. Existing comments and neighboring documentation are claims to check, not evidence.

## Reconcile and report

Verify delegated findings yourself, combine duplicates, and resolve conflicting evidence. Rank severity as critical, high, medium, or low based on actual impact; do not inflate test-only weaknesses into production defects.

Group findings as **Verified bugs**, **Maintainability findings**, **Test gaps**, and **Documentation findings**, with explicit counts. Omit empty secondary sections, but say plainly when no bugs are verified.

Each finding needs severity, a changed path and line range, concrete evidence, its consequence, and an actionable correction. Bugs also need a reachable triggering condition. Include reuse evidence where applicable. State checks run, limitations, and when no actionable findings were verified. Be direct without being rude.

For a follow-up, inspect the fix diff, confirm the original facts survived the rewrite, check new claims, and compare severity with the previous report when available. Revisit unchanged areas only when the fix affects them; do not restart an endless full-diff review loop.
