---
name: implement-with-tdd
description: Implement agreed behavior through failing tests, minimal implementation, and green-test refactoring. Use only when the user explicitly requests test-driven development.
disable-model-invocation: true
---

# Implement with TDD

Implement one behavior at a time, completing its test–implementation–refactor cycle before starting the next.

- Establish the next required behavior and follow existing test conventions.
- Write one focused behavior test. Derive expected results from requirements or independently worked examples, not the implementation's algorithm.
- Run it and confirm it fails because the behavior is missing or wrong. Setup failures do not count; investigate tests that already pass.
- Implement the smallest maintainable change that satisfies the requirement. Run the test again and confirm it passes without weakening its assertions.
- Refactor while tests are green, then rerun affected checks.
- Repeat for the next behavior, including relevant failure and boundary cases.
- Test observable contracts. Use real collaborators where practical and doubles where justified; mocked integrations do not prove live compatibility.
- Run relevant surrounding tests and repository-required checks before finishing. Report observed red/green results, checks run, and verification gaps. If tests cannot run, report the blocker rather than claiming completion.
