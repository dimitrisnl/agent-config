# Test-driven development: adaptation notes

Adapted from Matt Pocock's [tdd skill](https://github.com/mattpocock/skills/tree/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d/skills/engineering/tdd), including its `tests.md` and `mocking.md` references, at commit `4ae2317ddb22b046e26455e4f9c9b3aaaf62212d`. The original [MIT license](LICENSE) is retained.

## Local changes

- Use the full name `test-driven-development` and require explicit invocation.
- Consolidate the testing and mocking guidance into one workflow without the `codebase-design` skill dependency.
- Follow repository conventions for routine test boundaries; ask for approval only when the choice has consequential trade-offs.
- Restore refactoring as part of the red–green–refactor cycle, with tests rerun afterward.
- Treat mocking and interface guidance as defaults, not blanket bans. Allow contract-relevant assertions on requests, ordering, calls, and persistence.
- Distinguish behavior failures from broken setup, avoid manufactured red results, and report validation limits honestly.
- Follow shared session-worktree and browser-approval rules rather than defining another copy.

Review upstream changes manually against this revision and preserve intentional differences; no automatic sync is configured.
