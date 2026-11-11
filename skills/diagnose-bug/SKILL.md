---
name: diagnose-bug
description: Reproduce reported failures, investigate their cause, and verify fixes. Use when the user asks to diagnose or debug, or reports something broken, failing, or slow.
---

# Diagnose a bug

- A request to diagnose or explain does not authorize a fix. Investigate and report; edit only when the requested scope includes it.
- Establish expected behavior, the actual symptom, and triggering conditions. Inspect available evidence before asking for missing information.
- Confirm you are testing the correct application, version, and checkout. Follow the configured worktree rules before editing.
- Reproduce the actual failure with the smallest reliable check, without losing the original scenario. A successful request or absence of errors does not prove the output or state is correct.
- If direct reproduction is unavailable, use user-run steps or redacted evidence. Distinguish user-reported results from checks you ran. Explain missing evidence rather than making speculative changes; continue useful read-only investigation.
- Separate observations from hypotheses. Use targeted checks to distinguish plausible causes; scale investigation to the uncertainty.
- For intermittent failures, record attempts and failures under controlled conditions. For performance issues, collect comparable before/after measurements. One passing attempt does not establish a fix.
- Make the smallest justified fix. Where practical, add a regression test and confirm it fails for the reported reason before the fix, then passes after it. A setup failure or test that already passed is not regression evidence.
- If regression coverage is blocked, explain the limitation rather than adding a weak substitute.
- Rerun the original scenario and relevant surrounding checks. Mocked interactions test the simulated contract, not whether the real integration works. State anything that remains unverified.
- Remove temporary diagnostics, preserve existing work, and keep secrets out of commands, output, and committed artifacts.
- Report the supported cause, change, verification, and remaining uncertainty.
