---
name: grilling
description: Stress-test a plan, decision, or idea with focused questions and recommendations. Use when the user wants to stress-test their thinking, or uses any 'grill' trigger phrases.
disable-model-invocation: true
---

Stress-test the selected plan, decision, or idea until consequential decisions within the agreed scope are clear. Map these as a **design tree**: each decision can branch into decisions that depend on it. Keep hypothetical future work outside the tree unless the user requests it.

Work the tree in **small rounds**. The **frontier** is every in-scope decision whose prerequisites are already settled: the questions you can ask _now_ without guessing at answers you haven't heard yet. Ask a manageable set of the highest-impact independent questions from the frontier: number each question and give your recommended answer. Then wait for the user's answers before the next round.

Format a round like so:

```
❓ **Q1** - **<question title>**: <question body, might be multiple paragraphs, including multiple choices>

➡️ <your recommended answer>

---

❓ **Q2** - **<question title>**: <question body, might be multiple paragraphs, including multiple choices>

➡️ <your recommended answer>
```

Word each question so "yes" accepts your recommended answer.

Each round the user answers reshapes the tree: settled decisions push the frontier outward and unblock questions that depended on them. Recompute the frontier and ask the next round. A question whose answer depends on another question still open in this round belongs to a _later_ round, not this one.

Finding _facts_ is your job, never the user's. When a frontier question needs a fact from the environment (filesystem, tools, etc.), dispatch a sub-agent with a fresh context window to find it; don't ask the user for anything you could look up yourself. Don't block on it: a running exploration is an unsettled prerequisite, so only the questions downstream of it wait for the sub-agent to report; ask the rest of the frontier now. The _decisions_ are the user's: put each to them and wait.

Finish when consequential decisions for the agreed scope are resolved or explicitly deferred by the user. Summarize the decisions, assumptions, and deferred questions; distinguish deferred blockers from optional follow-up work. Do not keep branching merely because more questions are possible. Exhaustive exploration is an option only when the user requests it. Do not act on the plan until the user confirms the shared understanding and authorizes the next action.
