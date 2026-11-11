---
name: clarify-before-build
description: Resolve consequential implementation questions and agree on scope before coding. Use only when the user explicitly requests this clarification workflow.
disable-model-invocation: true
---

# Clarify before build

Reach shared understanding of the requested change before implementation.

- Inspect the request, conversation, and relevant code. Look up available facts; ask the user for consequential decisions.
- Ask a few focused questions at a time, prioritizing answers that could change scope, behavior, design, or validation.
- Recommend answers with brief reasons where useful. Distinguish proposed defaults from agreed decisions.
- Group independent questions; wait for prerequisite decisions before asking dependent ones. Do not reopen settled questions without new evidence.
- Stop when the work is clear enough to implement. Do not manufacture questions if the request is already clear.
- Summarize the agreed change, validation approach, and unresolved questions. Keep clarification read-only and wait for confirmation before implementing.
