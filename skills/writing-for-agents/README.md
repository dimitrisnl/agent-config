# Writing for agents: adaptation notes

Adapted from Matt Pocock's [writing-for-agents skill](https://github.com/mattpocock/skills/tree/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d/skills/productivity/writing-for-agents) at commit `4ae2317ddb22b046e26455e4f9c9b3aaaf62212d`, under the retained [MIT license](LICENSE).

## Local changes

- Add a concrete writing/review procedure that follows the user's requested scope and editing mode.
- Replace specialist vocabulary with direct guidance on actions, references, terminology, and completion evidence.
- Treat compression and positive phrasing as heuristics, preserving explicit requirements and safety boundaries.
- Replace exhaustive completion gates and speculative model-behavior explanations with proportional checks and observed validation.
- Correct the mechanics reference: automatic discovery, explicit loading, and permissions are distinct and tool-dependent. OpenCode-specific behavior is documented in the adapter.

Automatic discovery remains enabled; this is not an always-loaded instruction or a request to rewrite every document. Provider-specific display metadata was omitted. Review upstream changes against this revision and preserve intentional differences.
