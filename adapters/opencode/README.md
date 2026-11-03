# OpenCode adapter

The shared files remain in this repository. OpenCode can load instruction files and discover skills from explicitly configured paths, so no copied content or installer is needed for this initial setup.

## Opt-in configuration

Merge the following entries into your global `~/.config/opencode/opencode.jsonc`. Replace `/absolute/path/to/agent-config` with the clone's actual location. Preserve unrelated settings and any private instruction entries.

```jsonc
{
  "$schema": "https://opencode.ai/config.json",
  "instructions": [
    "/absolute/path/to/agent-config/instructions/writing.md",
    "/absolute/path/to/agent-config/instructions/worktrees.md",
  ],
  "skills": [
    "/absolute/path/to/agent-config/skills",
  ],
}
```

Keep private instructions in a separate file outside this repository and add its path to `instructions` if needed.

If your private instructions already contain the writing guidance, consolidate them when you adopt this setup rather than keeping two maintained copies. This repository has not changed your live configuration.

## Existing skills

Check for existing skill IDs before adding the skill directory. OpenCode V2 gives explicitly configured skill sources precedence over automatically discovered skill directories; these versions can therefore replace same-ID local skills at load time without deleting their files. Enable this deliberately. This repository now provides one review skill, `code-review`; adopting it does not remove older review skills or commands from live configuration.

In OpenCode V2, `disable-model-invocation: true` hides a skill from automatic discovery but leaves it registered and explicitly loadable by ID, subject to permissions. It does not prohibit another workflow from explicitly loading it. Discovery controls are not permission boundaries.

## Commands and reviewer profile

The `commands/` directory contains thin wrappers installed under the `/my/` namespace: `/my/architecture-review`, `/my/clarify-before-build`, `/my/code-review`, `/my/bug-diagnosis`, `/my/prototype`, `/my/session-handoff`, `/my/session-retro`, `/my/small-improvement`, `/my/test-driven-development`, and `/my/writing-for-agents`. The shared workflow content stays in `skills/`.

To opt in, link the individual command files into `~/.config/opencode/commands/my/` and `agents/reviewer-readonly.md` into `~/.config/opencode/agents/`. OpenCode derives the `/my/` prefix from the installed subdirectory; skill IDs stay unchanged. Use absolute source paths to this clone. Inspect existing destinations first: do not overwrite same-name local files without deliberately choosing to replace them. Nothing in this repository performs that installation.

`reviewer-readonly` is a reviewer profile, not an additional review workflow. Code review stays in the primary session and may delegate lenses to it. Direct edits and nested delegation are denied. Shell commands require approval, with checkout, switch, reset, and stash explicitly denied. This is a permission guardrail, not an operating-system sandbox: approved shell commands and external tools must still obey the read-only instructions. Shell approval can interrupt review in unattended runs.

`/my/clarify-before-build` loads an explicit-only skill: it is registered but not advertised for automatic invocation. It clarifies the request without editing files or starting implementation.

`/my/architecture-review` loads the adapted `architecture-review` skill, including `codebase-design`, `grilling`, and `domain-modeling`. Unlike code review, it delegates work and generates an offline HTML report using inline CSS and static SVG. Shared skills require approval before opening the report or using browser tools, and authorization before editing domain docs. These rules also apply when skills are loaded directly. `grilling` is explicit-only and loaded by architecture review; use `/my/clarify-before-build` for focused implementation clarification. The other supporting skills retain upstream discovery behavior. See the [adaptation notes](../../skills/architecture-review/README.md).

`/my/prototype` loads the adapted logic/UI workflow. The shared skill requires approval before opening prototypes or using browser tools, and ends with findings and a recommendation. Production implementation, commits, pushes, and issue updates require explicit approval. `/my/writing-for-agents` applies the adapted writing/review procedure to the requested document. Both skills allow automatic discovery; neither is added to the global `instructions` array.

`/my/session-retro` is also explicit-only. It reviews the selected session and recommends improvements without editing files or applying them.

`/my/session-handoff` is explicit-only. It writes a continuation document outside the repository by default, without moving source changes or transferring workspace ownership.

`/my/test-driven-development` is explicit-only. It implements agreed behavior one red–green–refactor cycle at a time, rather than reviewing existing test coverage.

`/my/small-improvement` defaults to `local` for one maintenance task in the session's isolated worktree. Use `/my/small-improvement scout` for read-only discovery. Either mode accepts a target area or maintenance priority. Neither commits or publishes; the former `pr` mode and size budgets are not supported. Project-specific migration and naming policies belong in the target repository, not in this adapter.

## Third-party skills

For browser diagnosis, prefer `agent-browser` when available, with `dev-browser` as an agreed alternative. This is an OpenCode adapter preference, not a requirement of the reusable diagnosis skill. Obtain approval for the proposed tool and sequence before loading browser skills or operating the browser; do not install tooling implicitly.

Keep unmodified tool skills upstream-managed rather than copying them into this repository. The executable and its skill are separate installations. For example, to opt into agent-browser globally:

```sh
npm install -g agent-browser
agent-browser install
npx skills@latest add vercel-labs/agent-browser --skill agent-browser -a opencode -g
```

These commands change the machine setup; nothing here runs them. The skills installer currently requires Node.js 22.20 or later. agent-browser's discovery skill loads version-matched instructions with `agent-browser skills get core`. Check skill updates with `npx skills@latest check`; review changes before updating selected skills.

OpenCode discovers global skills from `~/.config/opencode/skills/` and compatibility paths such as `~/.agents/skills/`. Once installed, request one with `@agent-browser` or ask the agent to load it; a slash command requires a separate command wrapper. Configure `ask` permissions for browser skill loading and direct browser shell commands if approval should be enforced beyond the debugging workflow. Skill permission alone does not gate direct CLI use.

## Worktree lifecycle

Apply the shared session-worktree rules using OpenCode's worktree tools where available, then move the session to the resulting directory. OpenCode's `worktree.directory` config controls placement, not whether to create a worktree. Cleanup is manual; no lifecycle hook is configured here.

## Verification

After opting in, confirm that the thirteen repository skills load by ID, all ten `/my/` commands are listed without flat-name duplicates, and the reviewer agent is available. Explicit-only skills should not be advertised for automatic invocation. Exercise each workflow on a representative task, including no-findings, already-clear, and blocked-evidence cases where relevant. For architecture review, verify all three dependencies load, the report renders offline, and report opening waits for approval. Test direct skill loading as well as command invocation: prototype should stop before production implementation or publication, and domain-modeling should propose wording rather than edit without authorization. Check that prototype loads its logic/UI references and waits for browser approval, and writing-for-agents loads its mechanics reference when writing skills. For handoff, verify the output path, source-workspace status, and redaction. For TDD, confirm an observed behavior failure, a passing implementation, and green tests after refactoring.

The discovery and loading model described here agrees with the official V2 skill documentation checked on 2026-11-03. This is a documentation check, not evidence of workflow behavior. Validate the installed build and record its version and observed results when testing; full workflow behavior remains untested.

References:

- [Instructions](https://opencode.ai/v2/docs/instructions)
- [Skills and source precedence](https://opencode.ai/v2/docs/skills)
- [Commands](https://opencode.ai/v2/docs/commands)
- [Agents](https://opencode.ai/v2/docs/agents)
- [Permissions](https://opencode.ai/v2/docs/permissions)
- [Worktree placement](https://opencode.ai/v2/docs/config#worktrees)
- [agent-browser skill loading](https://agent-browser.dev/skills)
