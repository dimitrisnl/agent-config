# Architecture workflow: adaptation notes

Imported from [mattpocock/skills](https://github.com/mattpocock/skills/tree/4ae2317ddb22b046e26455e4f9c9b3aaaf62212d/skills) at commit `4ae2317ddb22b046e26455e4f9c9b3aaaf62212d`, under the retained [MIT license](LICENSE).

Included dependencies:

- [`codebase-design`](../codebase-design/SKILL.md), including its deepening and alternative-design references.
- [`grilling`](../grilling/SKILL.md), rather than substituting our `clarify-before-build` adaptation. Its workflow body is unchanged, but discovery is now explicit-only so it acts as a supporting workflow rather than a competing automatic clarification option. Architecture review still loads it explicitly.
- [`domain-modeling`](../domain-modeling/SKILL.md), adapted to require authorization before document edits, including file-creation instructions in its format references.

Upstream provider-specific display metadata was omitted. The OpenCode command is named `/my/architecture-review`. Apart from `grilling`, the supporting skills retain upstream automatic-discovery settings. Local changes to `SKILL.md` and `HTML-REPORT.md`:

- Rename upstream `improve-codebase-architecture` to `architecture-review` so the skill ID matches its command and describes review rather than implementation.
- Require approval in the shared workflow before opening reports, loading browser skills, or operating browsers, including direct skill invocation.
- Replace Tailwind and Mermaid CDN scripts with inline CSS and static SVG. Reports render offline without JavaScript, include a restrictive content-security policy, and require escaping repository-derived text.
- Propose domain-document changes unless the user has authorized edits; follow the session-worktree rules before writing them.

This workflow delegates exploration and writes an HTML report outside the repository. It can update glossary and decision docs during the follow-up discussion only with authorization. It is not a read-only diff review.

Review upstream updates against this revision; do not modify imported files speculatively or substitute local adaptations without recording the change here.
