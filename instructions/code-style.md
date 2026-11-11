# Code style

Follow repository-specific instructions and established code style first. Apply these preferences where the repository leaves a choice.

## Organization

- Group related declarations instead of interleaving unrelated setup, values, helper functions, and behavior. Separate logical groups with blank lines.
- Place module-level constants near the top. Keep derived values near their dependencies.
- Prefer a clear reading order, not a rigid template. Keep related code together when splitting it by declaration type would make it harder to follow.

## State models

- Avoid implicit state machines: workflows whose states and transitions must be inferred from interacting flags, nullable values, or scattered conditions.
- Prefer named states and explicit transitions when they clarify the lifecycle and prevent invalid combinations. A state-machine library is not required.
- Keep a simpler representation when its mental model is easier to follow than an explicit state machine. Do not add machinery merely to make state explicit.

## Types

In statically typed code:

- Reuse existing types when they represent the same contract.
- Prefer inferred types when they are clear and precise. Avoid redundant type annotations.
- Add explicit types where they clarify a contract, constrain inference, or prevent unintended widening.
