# IMPORTANT: Before Any Git Commit

**STOP — Read This First**

Before running `git commit` (or asking me to commit), you MUST check for `.claude-plugin/` directory and bump versions in these files if they exist:

- `.claude-plugin/marketplace.json`
- `.claude-plugin/plugin.json`

For each file that exists:
1. If it has a `version` field → increment it (e.g., `1.0.1` → `1.0.2`)
2. If the `version` field is missing → add it with an appropriate version number
3. If both files exist → apply this rule to BOTH files

**This is non-negotiable. No exceptions. No commits without version bumps when these files exist.**

---

# Project Instructions

## Additional project-specific guidance...

@AGENTS.md
