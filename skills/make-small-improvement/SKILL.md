---
name: make-small-improvement
description: Find or complete one bounded maintenance task justified by repository guidance, tooling, and comparable code. Use for incremental migrations, inconsistent naming, local simplification, or test improvements.
---

# Make a small improvement

- Inspect repository guidance, tooling, and comparable code to identify one useful maintenance task in the requested area.
- Candidates include supported migrations, inconsistent internal naming, unnecessary complexity, and demonstrably weak tests.
- Explain the evidence that makes the change appropriate for this repository. Distinguish an established convention from a proposed direction. No change is better than speculative churn.
- If the direction is unclear, ask before implementing. Do not infer a migration policy merely from mixed styles or newer files.
- Complete one bounded change, preserve behavior and external contracts, and verify it using the repository's existing checks. Check consumers and required side effects before renaming or deleting code.
- Report the change, checks run, and any remaining uncertainty. Leave changes uncommitted.
