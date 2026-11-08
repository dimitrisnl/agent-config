# Architecture workflow: adaptation notes

Imported from [mattpocock/skills](https://github.com/mattpocock/skills/tree/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d/skills) at commit `4ae2317ddb22b046e26455e4f9c9b3aaaf62212d`, under the retained [MIT license](LICENSE).

Included dependencies:

- [`codebase-design`](../codebase-design/SKILL.md), including its deepening and alternative-design references. Deepening now requires checking preserved behaviour coverage before deleting old tests and treats test changes as a signal to inspect, not proof of overcoupling.
- [`grilling`](../grilling/SKILL.md), rather than substituting our `clarify-before-build` adaptation. Discovery is explicit-only so it acts as a supporting workflow rather than a competing automatic clarification option. The interview now uses manageable rounds and stops when consequential in-scope decisions are resolved or explicitly deferred; exhaustive exploration requires a user request. Architecture review still loads it explicitly.
- [`domain-modeling`](../domain-modeling/SKILL.md), adapted to require authorization before document edits, including file-creation instructions in its format references.

Upstream provider-specific display metadata was omitted. The OpenCode command is named `/my/architecture-review`. Apart from `grilling`, the supporting skills retain upstream automatic-discovery settings. Local changes to `SKILL.md` and `HTML-REPORT.md`:

- Rename upstream `improve-codebase-architecture` to `architecture-review` so the skill ID matches its command and describes review rather than implementation.
- Require approval in the shared workflow before opening reports, loading browser skills, or operating browsers, including direct skill invocation.
- Replace Tailwind and Mermaid CDN scripts with inline CSS and static SVG. Reports render offline without JavaScript, include a restrictive content-security policy, and require escaping repository-derived text.
- Propose domain-document changes unless the user has authorized edits; follow the session-worktree rules before writing them.
- Require code and caller evidence for candidates, distinguish observations from proposed benefits, and allow a no-findings result without manufacturing a recommendation or starting an interview.
- Describe supporting-skill loading by ID rather than assuming a tool name or slash-command syntax.

This workflow delegates exploration and writes candidate reports outside the repository. A no-findings result stays in the conversation unless the user requested a report file. It can update glossary and decision docs during the follow-up discussion only with authorization. It is not a read-only diff review.

Review upstream updates against this revision; do not modify imported files speculatively or substitute local adaptations without recording the change here.
