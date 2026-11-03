# Skill mechanics

Use alongside [writing-for-agents](SKILL.md) when creating or changing a skill.

## Choose how it is reached

- **Automatically discoverable:** use when the agent should recognize the task without the user naming a skill. Describe its purpose and distinct trigger conditions clearly.
- **Explicitly requested:** use when the workflow should start only at the user's request. State that expectation in the instructions and use the target tool's discovery controls where supported.
- **Shared reference:** keep supporting material in a referenced file when it has no independent trigger. A separate skill is useful only when independent discovery or reuse justifies it.

Discovery, loading, and permission are different concerns. Hiding a skill from automatic discovery does not universally prevent an agent or another workflow from loading it explicitly. Consult the target tool's current documentation; keep its configuration syntax in the adapter rather than assuming one invocation model works everywhere.

## Keep packaging proportional

Keep the skill name, purpose, and entry instructions clear. Link supporting references with conditions for reading them. Split skills when they represent independently useful tasks, not merely to shorten a file. Add a router only when choosing among existing skills is an observed problem, and verify how the target tool permits it to recommend or invoke them.
