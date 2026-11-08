# Bug diagnosis: adaptation notes

Adapted from Matt Pocock's [diagnosing-bugs skill](https://github.com/mattpocock/skills/tree/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d/skills/engineering/diagnosing-bugs) at commit `4ae2317ddb22b046e26455e4f9c9b3aaaf62212d`. The original [MIT license](LICENSE) is retained.

## Local changes

- Rename the workflow to `bug-diagnosis` to match the collection's task-oriented naming.
- Allow tentative investigation before reproduction, while keeping hypotheses distinct from confirmed causes.
- Distinguish diagnosis-only requests from authorized fixes. Keep diagnosis-only work free of repository edits and ask before expanding into instrumentation or remediation; do not repeat approval when fixing was already requested.
- Scale the process to uncertainty instead of requiring a fixed hypothesis count, exhaustive minimization, or seconds-fast checks.
- Allow user-run steps and captured evidence; the interactive helper script is optional and unchanged.
- Explain specific regression-test limitations without automatically blaming architecture or adding weak substitute tests.
- Add browser-assisted diagnosis, requiring approval before loading a browser skill or operating a browser. Keep tool selection in adapters or local configuration rather than the shared workflow.
- Remove motivational rhetoric and unsupported guarantees; retain evidence-driven verification, secret redaction, and instrumentation cleanup.

Provider-specific display metadata was not imported. Review upstream changes manually against this revision and preserve intentional differences; no automatic sync is configured.
