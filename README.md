# Agent config

Personal instructions and workflows for coding agents, kept separate from machine configuration and any one agent tool.

The reusable material lives in `instructions/` and `skills/`. Tool-specific loading instructions live in `adapters/`. Dotfiles can handle installation and machine-specific paths without owning another copy of the content.

## Contents

| Path | Purpose |
| --- | --- |
| `instructions/writing.md` | Conversational technical writing for PR descriptions and summaries |
| `instructions/worktrees.md` | One dedicated worktree per primary coding session, reused on resume |
| `skills/clarify-before-build/SKILL.md` | Explicitly requested clarification of implementation decisions before coding |
| `skills/code-review/SKILL.md` | One read-only review covering correctness, maintainability, reuse, tests, and claims |
| `skills/bug-diagnosis/SKILL.md` | Evidence-driven debugging with reproduction and regression checks |
| `skills/architecture-review/SKILL.md` | Architecture survey with an offline HTML report and guided design discussion |
| `skills/codebase-design/`, `skills/grilling/`, `skills/domain-modeling/` | Architecture vocabulary and discussion workflows; domain-document edits require authorization |
| `skills/prototype/SKILL.md` | Throwaway logic demos and alternative UI designs, with approval before implementation or publication |
| `skills/session-handoff/SKILL.md` | Explicitly requested context transfer to another session or agent |
| `skills/session-retro/SKILL.md` | Explicitly requested, evidence-backed suggestions for improving future sessions |
| `skills/small-improvement/SKILL.md` | Find or complete one behavior-preserving maintenance task backed by repository policy |
| `skills/test-driven-development/SKILL.md` | Explicitly requested feature or fix implementation using red–green–refactor |
| `skills/writing-for-agents/SKILL.md` | Practical writing and review guidance for agent-facing instructions and skills |
| `adapters/opencode/README.md` | Loading these files in OpenCode |
| `adapters/opencode/commands/` | Thin commands installed under `/my/` for the shared skills |
| `adapters/opencode/agents/reviewer-readonly.md` | Restricted reviewer profile available to the review workflow |

## What belongs here

- **Instructions:** short preferences that should apply automatically in their stated scope.
- **Skills:** task-specific workflows with clear triggers, constraints, verification, and output.
- **Scripts:** deterministic operations, when there is an actual operation worth automating.
- **Adapters:** the configuration or thin wrappers a particular tool needs to load the shared content.

Store a workflow once. Keep tool names, configuration paths, and tool-specific invocation syntax in adapters rather than embedding them throughout the shared guidance.

The skills use Markdown with `name` and `description` frontmatter. Other agents may need a different discovery path or an adapter; this repository does not assume identical loading behavior across tools.

## Public and private

Keep credentials, internal URLs, impersonation steps, customer details, private project context, and live tool configuration outside this repository. Use a private local instruction file for those details and configure your tool to load it separately.

Do not copy an entire live config directory into this repository. Ignore rules are a precaution, not a substitute for inspecting what will be published.

## Current status

Code review contains all review criteria in one skill. Small improvement supports discovery-only and local implementation, without commits or publication. Maintenance priorities belong in the target repository. Each primary coding session owns a worktree and returns to it on resume; cleanup is manual.

Nothing here installs itself or changes live configuration. The OpenCode adapter has not been behavior-tested. Add other adapters only when needed.

Imported and adapted skills include local notes with the upstream revision, any intentional differences, and the original license notice. The [architecture import notes](skills/architecture-review/README.md) also track its supporting skills.

## Improving a workflow

1. Identify a concrete failure or repeated task.
2. Update the smallest relevant instruction or skill; avoid adding the same rule in several places.
3. Exercise it on a representative task. Include an edge case where it should decline to act or report no findings.
4. Record what was actually checked. Do not treat an untested prompt as a demonstrated behavior guarantee.

Before publishing, inspect all files and staged changes for private information.

## License

[MIT](LICENSE). Adapted third-party skills retain their upstream copyright and license notices in their own directories.
