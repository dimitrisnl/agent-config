---
name: review-architecture
description: Review a codebase area for concrete architectural friction and recommend changes with evidence and trade-offs. Use only when the user explicitly requests an architecture review.
disable-model-invocation: true
---

# Review architecture

- Focus on the requested area. If none is given, use recent changes to identify a useful starting point.
- Read relevant code, callers, tests, and recorded design decisions.
- Look for scattered knowledge, tangled responsibilities, unnecessary indirection, and interfaces that make changes or testing difficult.
- For each finding, show concrete evidence and explain its consequence.
- Compare the proposed change with keeping the current design. Include trade-offs and migration cost; do not assume consolidation or additional abstraction is better.
- Recommend the strongest candidates. No findings is a valid outcome.
- Keep the review read-only and report in the conversation. Discuss before implementing. Use diagrams only when they help; delegate exploration only when authorized and useful.
