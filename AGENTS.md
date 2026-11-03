# Working on agent-config

- Keep reusable instructions and skills tool-neutral. Put tool-specific configuration and loading syntax under `adapters/`.
- Keep one source of truth for each workflow. Do not generate or maintain copies without a concrete tool requirement.
- Keep private details and live tool configuration outside this repository. Inspect changes for sensitive content before committing or publishing.
- Prioritize useful, accurate documentation over quantity. Prefer short, concrete guidance and preserve meaningful constraints when simplifying instructions.
- Generalize workflows imported from project work. Do not carry over project-specific examples, paths, tools, labels, or commands as universal requirements; discover them from the target repository when needed.
- Check adapter configuration against the relevant tool's current documentation. Do not claim compatibility or successful validation without evidence.
- Read `instructions/writing.md` when writing PR descriptions or technical summaries.
