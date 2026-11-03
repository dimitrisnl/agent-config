---
name: test-driven-development
description: Implement agreed features or fixes through a failing behavior test, minimal implementation, and green-test refactoring. Use only when the user explicitly requests test-driven development.
disable-model-invocation: true
---

# Test-driven development

Build the agreed behavior one small test-and-implementation cycle at a time. This is an implementation workflow, not a test-coverage audit or a substitute for deciding what the feature should do.

## Establish scope and test boundaries

Read repository instructions, relevant code and tests, and existing test commands. Follow the [session worktree rules](../../instructions/worktrees.md) before editing. Establish the next behavior, expected outcome, and practical validation approach; clarify consequential unknowns before implementing them.

Choose a public or stable boundary that exercises behavior callers care about. Follow established repository conventions for routine choices. Ask the user when choosing the boundary changes the design, coverage, cost, or confidence in a consequential way; do not require approval for every test. State important coverage limitations.

Use the repository's existing tooling. Inspect test side effects before running checks, and keep external services and data isolated. Browser-driven validation follows the [browser approval requirements](../bug-diagnosis/SKILL.md#browser-assisted-diagnosis).

## Red: demonstrate the missing behavior

Write one focused test for the next observable behavior. Derive expected results independently from the implementation: an agreed requirement, known-good literal, or worked example. Do not repeat the implementation's algorithm in the assertion.

Run the test and inspect its failure. Confirm it fails because the required behavior is missing or wrong, not because fixtures, dependencies, or infrastructure are broken. If it already passes, inspect what it proves and whether the behavior already exists; do not manufacture a failure just to complete the cycle.

If the test cannot run, report the blocker rather than claiming a red result. Fix setup within the authorized scope or ask for what is missing before proceeding with unverified implementation.

## Green: implement only this behavior

Write the smallest maintainable change that satisfies the test and agreed requirement. Run the test again and confirm it passes. Do not weaken assertions, skip checks, add speculative features, or change expectations merely to accommodate incorrect behavior.

Keep each cycle coherent: one behavior, its test, and its implementation. Do not write an entire feature's tests against imagined interfaces before learning from the first cycle. A behavior may need several assertions or changes across multiple files.

## Refactor while green

Once the test passes, simplify the code and tests without changing behavior. Remove duplication or unnecessary indirection when doing so improves the current design. Rerun affected tests after refactoring; keep broader architectural changes outside the cycle unless separately agreed.

Repeat red–green–refactor for the next behavior. Include relevant failure paths and boundary cases, not only the happy path.

## Keep tests meaningful

Prefer real internal collaborators and mock external boundaries such as third-party APIs, time, or randomness where practical. Follow repository conventions and justify exceptions when isolation or unavailable infrastructure requires internal doubles. A mocked integration verifies our handling of the simulated contract, not compatibility with the live provider.

Assert observable outcomes rather than private structure. Request payloads, call counts, ordering, or persisted state are valid assertions when they are part of the contract being tested, not merely incidental implementation details. Await asynchronous work and ensure failed assertions fail the test itself.

Run relevant surrounding tests and repository-required checks before reporting completion. Separate regressions, pre-existing failures, and infrastructure blockers. Report implemented behaviors, red/green evidence, checks actually run, and coverage limitations; do not imply full-suite or live-provider validation when neither ran.
