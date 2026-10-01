# Agent navigation

This repository is a library of reusable skills. Reading the repository does not activate every skill.

## Select a skill

1. Read `catalog.json` for names, descriptions, categories, keywords, and entry-point paths.
2. Choose the skill that matches the user's task.
3. Read that skill's `SKILL.md` before applying its instructions.
4. Follow linked references when the entry point calls for them. Resolve reference paths relative to the skill folder.

| Task | Entry point |
| --- | --- |
| Improve prose and remove AI writing patterns | `skills/writing/unslop/SKILL.md` |
| Find available open-source GitHub issues | `skills/open-source/issue-finder/SKILL.md` |
| Investigate or review Grafana fixes | `skills/grafana/grafana-pr-checklist/SKILL.md` |
| Run Grafana with disk-backed Go temporary files | `skills/grafana/grafana-backend-run/SKILL.md` |

Skills provide task guidance within the user's request. A skill does not itself authorize publishing, assigning issues, posting comments, deleting caches, or changing machine-wide configuration.

## Maintain this repository

- Put skills in `skills/<category>/<skill-name>/SKILL.md`.
- Use lowercase hyphenated skill names; the folder name and YAML `name` must match and be unique across the catalog.
- Give every skill a concise YAML `description` that explains when to use it.
- Keep installation-independent instructions and relative reference links inside each skill folder.
- Update `catalog.json` and the README catalog when adding, moving, or renaming a skill.
- Preserve the provenance of imported Markdown. Label historical examples and machine-specific assumptions.
- Check YAML frontmatter, catalog paths, local Markdown links, and `git diff --check` before committing.

See [CONTRIBUTING.md](CONTRIBUTING.md) for the skill layout.
