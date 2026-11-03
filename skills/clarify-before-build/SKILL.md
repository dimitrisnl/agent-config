---
name: clarify-before-build
description: Resolve implementation-relevant questions before coding, with focused questions and recommended answers. Use only when the user explicitly requests this clarification workflow.
disable-model-invocation: true
---

# Clarify before build

Reach enough shared understanding to implement the requested change without guessing at consequential decisions. Clarification is not permission to start implementation.

## Establish what is known

Read the request, existing conversation, repository instructions, and relevant code or docs. Inspect facts you can establish yourself; ask the user for decisions, not information already available in the repository. If a necessary fact is inaccessible, explain what is missing rather than inventing it.

Keep exploration read-only. Do not edit code, create planning files or domain docs, or operate a browser merely to clarify a request. Ask separately when additional access or an interactive investigation is needed. Use direct inspection for routine lookups; delegate only when authorized and useful.

## Ask focused questions

Ask only questions whose answers could change scope, observable behavior, implementation design, constraints, or validation. Resolve high-impact uncertainty first. Skip preferences already established by repository conventions and do not turn hypothetical future needs into requirements.

Use small rounds of short numbered questions. For each question, give a recommended answer and a brief reason; include alternatives or trade-offs when meaningful. Clearly distinguish a proposed default from an agreed decision.

Ask independent questions together. If an answer depends on an unresolved decision, wait for that decision before asking downstream questions. Wait for the user's response between rounds, incorporate their answers, and do not ask settled questions again unless new evidence changes the premise.

## Stop when ready

Stop when the requested scope, expected behavior, relevant constraints, and validation approach are clear enough to implement. Do not exhaust every conceivable branch. If the request is already clear, say so without manufacturing an interview.

Summarize the agreed change, consequential decisions, how success will be checked, and any remaining assumptions or blockers in the conversation. Keep the summary proportional to the task; do not save it to a file unless asked.

Ask the user to confirm or correct that understanding before implementation. A blocker requiring a product or design decision stays open until resolved or explicitly deferred; do not silently choose for the user. Begin coding only when the user authorizes it.
