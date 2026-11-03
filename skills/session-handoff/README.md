# Session handoff: adaptation notes

Adapted from Matt Pocock's [handoff skill](https://github.com/mattpocock/skills/blob/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d/skills/productivity/handoff/SKILL.md) at commit `4ae2317ddb22b046e26455e4f9c9b3aaaf62212d`. The original [MIT license](LICENSE) is retained.

## Local changes

- Rename the workflow to `session-handoff` and keep it explicit-only, for transferring work rather than replacing ordinary resume or compaction.
- Record workspace, branch, revision, uncommitted changes, and ownership uncertainty without moving or committing work.
- Separate confirmed decisions and observed checks from assumptions and proposed validation.
- Keep the summary proportional and suggest other skills only when relevant to the next action.
- Preserve the outside-repository temporary-file default, allow an explicit destination, and avoid overwriting existing files.
- Make workspace transfer and browser approval explicit rather than treating the handoff as permission to continue anywhere.

Review upstream changes manually against this revision and preserve intentional differences; no automatic sync is configured.
