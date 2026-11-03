---
name: writing-for-agents
description: Write or review agent-facing instructions, skills, and supporting documents for clear actions, useful constraints, and maintainable references. Use when the requested task concerns documents agents consume.
---

# Writing for agents

Help write or improve the requested document that agents consume: instructions, a skill, or supporting reference material. Follow the user's requested mode: suggest changes when reviewing; edit when asked to edit. Do not expand a document task into a repository-wide audit.

## Procedure

1. **Establish the purpose.** Identify the target document, intended agent, tasks it supports, and behavior it should change. Ask when the target or requested mode is unclear.
2. **Read relevant evidence.** Inspect existing instructions and linked references. Check tool-specific claims against current documentation and repository configuration; report uncertainty when they cannot be verified.
3. **Find actionable problems.** Look for ambiguous actions, conflicting rules, duplicated guidance, stale claims, missing references, and unnecessary detail. Explain the consequence rather than treating length alone as a defect.
4. **Propose or make the smallest useful change.** Apply the writing guidance below while preserving meaningful scope, safety, and verification requirements. When writing a skill, also read [SKILL-MECHANICS.md](SKILL-MECHANICS.md).
5. **Check the result.** Verify links and loading conditions, remove contradictions, and confirm that important constraints survived. Where practical, exercise the instructions on a representative task, including a relevant edge case. Distinguish static inspection from observed agent behavior.
6. **Report concisely.** For a review, give actionable findings with the relevant passage, consequence, and suggested correction. For edits, explain consequential changes and what was checked. State limitations; report no actionable findings when appropriate.

## Writing guidance

- **Use concrete actions and completion conditions.** Say what to inspect, change, or report, and what evidence establishes completion. Define enough evidence for the task, not an exhaustive gate for every step. Replace "be thorough" with a checkable requirement where one is needed.
- **Keep each rule in one place.** Reference existing guidance instead of maintaining copies. Keep related actions, explanations, and exceptions together.
- **Say when to read linked material.** A reference should identify its purpose and the condition that makes it relevant. Keep essential instructions visible; move specialized detail behind a reference only when it simplifies the common path.
- **Keep always-loaded guidance focused.** Include broadly applicable constraints and useful navigation. Put task-specific procedures in skills or references. Split a document only when the parts have distinct uses; file count is not a quality target.
- **Prefer clarity over compression.** Use consistent terms and define unfamiliar ones. Keep explicit requirements when a shorter phrase would hide their meaning. Examples should clarify a difficult decision, not repeat straightforward instructions.
- **Prefer positive directions where clear.** Retain explicit prohibitions for important safety and scope boundaries. Wording choices are heuristics, not guarantees about model behavior.
- **Document what the environment does not explain.** Preserve non-obvious conventions, reasons, and gotchas. Point to configuration or commands for facts that can be found cheaply instead of copying values that may drift.
- **Remove guidance for a reason.** Cut obsolete rules, repetition, and filler that adds no useful constraint. Do not assume safety rules are redundant merely because an agent should normally follow them. Test uncertain changes before treating them as improvements.
