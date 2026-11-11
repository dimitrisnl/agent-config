# Agent config

Personal instructions and skills for coding agents.

- `instructions/` for shared preferences
- `skills/` for specific workflows
- `adapters/` for tool-specific configuration

## OpenCode setup

- In `~/.config/opencode/opencode.jsonc`, add this clone's absolute `instructions/*.md` glob to `instructions` and its absolute `skills/` directory to `skills`. Keep any local instruction entries.
- Optionally link the files in `adapters/opencode/commands/` into `~/.config/opencode/commands/my/` for `/my/` commands.
- Optionally link `adapters/opencode/agents/reviewer-readonly.md` into `~/.config/opencode/agents/` for delegated reviews.

[MIT License](LICENSE)
