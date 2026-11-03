---
name: session-retro
description: Review a coding session for evidence-backed improvements to agent instructions, navigation, checks, and tooling. Use only when the user explicitly requests a session retrospective.
disable-model-invocation: true
---

# Session retro

Suggest improvements to how future agent sessions work, not another review of the application code. Recommend changes first; this workflow does not authorize implementing them.

## Establish the evidence

Use the session the user identifies, or the current conversation by default. Read the available conversation, tool results, and relevant instructions or configuration to establish what happened. Inspect existing checks before proposing new ones. Keep inspection read-only; do not edit files, run setup, change configuration, publish, or operate a browser.

Limit investigation to the selected session and directly relevant sources. If an older session or necessary evidence is unavailable, ask for its location or report the limitation rather than searching unrelated private logs. Distinguish observed events from inferred causes and redact sensitive details.

## Find useful improvements

Look for concrete friction or mistakes in the session:

- **Navigation:** repeated searches, hidden dependencies, or missing entry points that a short pointer could address.
- **Checks:** mistakes a practical automated check could have caught, including existing checks that were missed, unwired, or broken.
- **Instructions:** conflicting, duplicated, stale, or ineffective guidance. Prefer clarifying or removing an existing rule over adding another.
- **Tooling and access:** unnecessary repeated calls, excessive output, unreliable workflows, or missing information that prevented verification. Do not claim token or time savings without evidence.

Tie every recommendation to something observed in this session and explain why the proposed change would address it. Do not turn the retrospective into a general repository audit or assume a missing tool, document, or separate reviewer is itself a problem.

Prefer the smallest durable remedy. Use an existing deterministic check for mechanical mistakes where practical; reserve prose instructions for conventions and judgment that tooling cannot reasonably enforce. Propose new documentation only when an existing source cannot carry the guidance clearly.

## Report and stop

Present up to three high-confidence recommendations, ordered by expected impact. For each, include the observed issue and evidence, proposed change and target, and how the improvement could be checked. Proposed validation is not a check already performed.

Zero recommendations is a valid outcome. State evidence limitations and stop after the report. Do not create a retrospective file, add rules, or apply fixes unless the user separately requests them.
