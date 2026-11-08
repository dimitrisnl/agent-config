---
name: bug-diagnosis
description: Diagnosis loop for hard bugs and performance regressions. Use when the user says "diagnose"/"debug this", or reports something broken/throwing/failing/slow.
---

# Bug diagnosis

Establish evidence for the reported failure, investigate its cause, and, when a fix is authorized, verify the original scenario after fixing it. Scale the investigation to the uncertainty rather than completing a fixed checklist for every bug.

## Establish context

Read repository instructions, relevant domain docs, and affected code. Clarify the expected behavior, actual symptom, environment, and triggering input when they cannot be established from available evidence. Follow the configured session-worktree rules before editing.

Establish whether the user requested diagnosis only or also authorized a fix. A request to diagnose or explain a failure does not itself authorize repository edits. For diagnosis-only work, use read-only inspection and existing checks, then report the supported cause, proposed fix, and uncertainty. Ask before edits needed for further investigation or remediation. If fixing was already requested, proceed within that scope without asking for redundant approval; clarify only when the requested scope is unclear.

Keep secrets out of commands, output, and shared artifacts. Use environment variables for credentials and redact sensitive values before displaying evidence. Logs, HAR files, screenshots, and heap snapshots can contain private data; capture only what is needed and keep sensitive artifacts outside committed source.

## Reproduce the failure

Find a check that detects the user's exact symptom: a failing test, HTTP request, CLI invocation, replayed input, small harness, or approved browser interaction. "No error", a successful click, or HTTP 200 is insufficient when the symptom is incorrect state or output.

Read code and form tentative hypotheses as needed to construct the reproduction. Distinguish observations from explanations; do not present a hypothesis as a confirmed cause or an untested patch as a verified fix.

Run the check and record the relevant failure evidence. Prefer the fastest reliable check available, even if it takes minutes. Simplify the reproduction when doing so helps isolate the cause, without requiring exhaustive minimization or losing the original scenario.

For intermittent failures, record attempts and failures and improve reproducibility using controlled inputs, timing, or bounded repetition. Keep comparison conditions consistent; one passing attempt does not establish a fix.

When automated reproduction is unavailable, use clear user-run steps, screenshots, or redacted logs. The optional [human-assisted template](scripts/hitl-loop.template.sh) requires an interactive terminal; do not assume the agent's shell can receive user input. Distinguish user-reported results from checks you ran yourself.

If evidence remains insufficient, explain what was tried and what access, input, or observation is missing. Continue useful read-only investigation with tentative conclusions, but ask for the missing evidence before making speculative changes.

## Browser-assisted diagnosis

Before loading a browser skill or operating a browser, ask the user and wait for approval. Propose the tool, target URL and browser session, interactions, and evidence to capture; mention likely disruption such as opening tabs, navigation, or changing focus. A general request to debug is not browser approval. Approval covers the agreed sequence, not each click; ask again before changing its scope or performing more disruptive actions. If declined, continue with non-browser checks or user-run steps.

After approval, use the agreed browser tool and load its existing skill or current usage instructions. Tool preferences belong in the active adapter or local configuration. If the required tool is unavailable, report that limitation; do not install tooling implicitly.

- Verify the target is the application and version under investigation, including the worktree's dev server when applicable. Use a dedicated browser session by default; attach to an existing browser only when approved. Preserve unrelated tabs and authentication state. Do not close the user's browser or clear its profile.
- Start relevant console, error, or request collection before triggering the failure. Inspect only the DOM, requests, responses, or errors needed to distinguish causes. Use state-based waits rather than arbitrary delays.
- Reproduce the real interaction and assert the reported result. Mocked requests or altered page state may help isolate a cause, but are not evidence that the real application works.
- For performance or memory problems, collect comparable before/after measurements. Confirm that the installed tool supports the required profiling or heap inspection; a screenshot or DOM snapshot is not a heap snapshot. Explain unsupported capabilities rather than claiming coverage.

## Investigate the cause

For ambiguous bugs, compare competing explanations and identify observations that would distinguish them. An obvious cause does not require a fixed number of alternatives. Share the current explanation and supporting evidence when they materially change the diagnosis.

Use targeted debugger inspection, logs, or probes, changing one variable at a time. Tag temporary logs with a unique prefix so they can be removed reliably. For performance regressions, measure a baseline before changing code; use profiling, query plans, or bisection when they answer a specific question.

## Fix and verify

Continue here only when fixing is within the authorized scope.

Add a regression test at a boundary that exercises the real failure when practical. Observe it fail for the reported reason before applying the smallest justified fix, then observe it pass. An unrelated setup failure or a test that passes before the fix does not demonstrate regression coverage.

If automated coverage is blocked, explain the specific limitation, such as unavailable infrastructure, inaccessible data, tooling, or an unsuitable test boundary. Do not add a weak substitute merely to complete the process or assume the limitation is an architecture defect. State what other evidence supports the fix and what remains unverified.

Rerun the original scenario, not only a simplified reproduction, and run relevant surrounding checks. Use the same browser approval boundary for post-fix validation. Where original-scenario verification is blocked, report that limitation instead of declaring the bug resolved.

## Clean up and report

Remove temporary instrumentation and probes you added, restore temporary diagnostic changes, and preserve existing user work. Inspect the final patch for unrelated changes and retained secrets.

Report the supported cause, change, before/after evidence, regression coverage, checks run, and remaining uncertainty. Separate observed results from inferred explanations and user-reported evidence. Include the cause and verification in any subsequently requested commit or PR description; debugging alone does not require creating either.
