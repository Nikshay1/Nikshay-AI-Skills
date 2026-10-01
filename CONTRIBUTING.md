# Contributing

Add instructions that help an agent complete a specific, repeatable task. Explain when the skill applies and preserve the user's task scope.

## Add a skill

Create `skills/<category>/<skill-name>/SKILL.md` with this structure:

```markdown
---
name: skill-name
description: Explain what this skill does and when to use it.
---

# Skill title

Describe the relevant workflow, decision criteria, and required context.
```

Choose an existing category when it fits. Names must use lowercase letters, digits, and hyphens, be at most 64 characters, match their folder, and be unique across the repository.

Keep each folder portable. Place substantial examples or conditional procedures in `references/` and link them from `SKILL.md`. Add scripts or assets only when the workflow needs them.

Add the skill to `catalog.json` and the README table. Every catalog entry uses `name`, `category`, `description`, `path`, `keywords`, and `source_files`; use an empty `source_files` array for skills authored directly in this repository. Add `references` when there are supporting documents. Store repository-relative paths in the catalog.

Before submitting a change, verify the YAML frontmatter, catalog entries, local links, and portability of any machine-specific commands. Run `git diff --check` and test executable helpers if you add them.
