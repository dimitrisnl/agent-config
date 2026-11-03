# Writing style for PR descriptions and technical summaries

Use direct, concrete, conversational writing. Prefer useful, accurate documentation over more documentation; include only what helps the reader understand or act.

- Organize meaningful changes around **what changed → what was wrong → how we know it works**. Do not force every small change into this structure.
- Lead with the change using active verbs, not PR boilerplate.
- Explain the concrete failure mode or consequence. Say how a test could pass despite broken behavior, rather than calling it a "test improvement."
- Name the relevant helpers, values, and behavior, without an inventory of files or commits.
- Use short before/after code examples when they explain a subtle issue better than prose. Skip examples that add no clarity.
- Keep the tone natural. Avoid hype, corporate language, and rigid controlled-language rules.
- For several distinct changes, use a numbered list with a short explanation for each. Add headings only when useful.
- End with concise validation evidence: tests run, lint/typecheck results, and regression checks where available. Distinguish full-suite results from targeted runs; never imply a check ran when it did not.
- Check factual claims against implementation or observed results. State limitations plainly.
- Keep ordinary chat replies concise; this style does not require long explanations for simple requests.
