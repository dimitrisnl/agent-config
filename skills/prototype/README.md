# Prototype: adaptation notes

Imported from Matt Pocock's [prototype skill](https://github.com/mattpocock/skills/tree/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d/skills/engineering/prototype) at commit `4ae2317ddb22b046e26455e4f9c9b3aaaf62212d`, under the retained [MIT license](LICENSE).

Provider-specific display metadata was omitted. The skill retains upstream automatic discovery. Local changes to `SKILL.md`, `LOGIC.md`, and `UI.md`:

- Require approval in shared guidance before opening prototypes, loading browser skills, or operating browsers, including direct skill invocation.
- End with the local prototype, findings, and a recommendation rather than automatically implementing the decision, committing a preservation branch, or updating an issue.
- Require explicit approval for production implementation, commits, pushes, and issue updates; choosing a variant is not authorization for those actions.

The workflow writes throwaway code to answer a logic or UI question. It is not production implementation or a test-driven workflow.

Review upstream changes against this revision and record any intentional content changes here.
