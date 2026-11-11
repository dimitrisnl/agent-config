# Working on agent-config

- Keep shared instructions and skills tool-neutral; put agent-tool configuration and loading syntax in `adapters/`.
- Maintain each workflow in one place. Adapters should reference it, not duplicate it.
- Keep private details and live machine configuration outside this repository. Check changes for sensitive content before committing or publishing.
- Remove source-project assumptions from imported workflows; discover conventions from the target repository instead.
- Check adapter configuration against the tool's current documentation.
