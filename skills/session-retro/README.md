# Session retro: adaptation notes

Adapted from Matt Pocock's [retro skill](https://github.com/mattpocock/skills/blob/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d/skills/engineering/retro/SKILL.md) at commit `4ae2317ddb22b046e26455e4f9c9b3aaaf62212d`. The original [MIT license](LICENSE) is retained.

## Local changes

- Rename the workflow to `session-retro` and keep it explicit-only.
- Limit the report to up to three recommendations tied to observed session evidence; zero findings is valid.
- Keep inspection read-only and require a separate request before editing instructions, checks, configuration, or documentation.
- Prefer fixing existing tooling or removing confusing guidance over adding more rules and documents.
- Remove the `writing-for-agents` dependency and assumptions about separate reviewer agents or `CODING_STANDARDS.md`.
- Bound log inspection to the selected session and distinguish proposed validation from checks actually performed.

Review upstream changes manually against this revision and preserve intentional differences; no automatic sync is configured.
