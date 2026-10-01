# Nikshay AI Skills

Practical Markdown skills for AI coding agents, organized by the work you need to do. Start with the catalog, choose a skill, and read its `SKILL.md`.

## Find a skill

| Category | Skill | Use it when |
| --- | --- | --- |
| Writing | [Unslop](skills/writing/unslop/SKILL.md) | Editing text to remove formulaic AI language and preserve a natural voice. |
| Open source | [Issue finder](skills/open-source/issue-finder/SKILL.md) | Finding GitHub issues that are available, still relevant, and realistic to contribute to. |
| Grafana | [PR checklist](skills/grafana/grafana-pr-checklist/SKILL.md) | Investigating or reviewing a Grafana fix across state producers, callers, UI modes, and recovery paths. |
| Grafana | [Backend run guide](skills/grafana/grafana-backend-run/SKILL.md) | Running Grafana locally when Go build temporary files may exhaust RAM-backed `/tmp`. |

## Repository layout

```text
.
├── README.md                 Human-readable catalog and setup
├── AGENTS.md                 Agent routing and repository conventions
├── CLAUDE.md                 Claude Code entry point
├── catalog.json              Machine-readable skill index
├── CONTRIBUTING.md           Adding and maintaining skills
└── skills/
    ├── writing/
    │   └── unslop/
    │       └── SKILL.md
    ├── open-source/
    │   └── issue-finder/
    │       └── SKILL.md
    └── grafana/
        ├── grafana-pr-checklist/
        │   ├── SKILL.md
        │   └── references/pr-checklist.md
        └── grafana-backend-run/
            ├── SKILL.md
            └── references/original-run-guide.md
```

Each skill folder is self-contained. YAML `name` and `description` fields support discovery; the body contains instructions. Longer guidance lives in linked references so an agent can load only the detail it needs.

## Use with an AI agent

For direct use, give your agent the skill path:

> Read `skills/open-source/issue-finder/SKILL.md` and use it to find an available GitHub issue in the repository I specify.

Agents exploring this repository should start with [AGENTS.md](AGENTS.md) and [catalog.json](catalog.json). Claude Code imports the same navigation through [CLAUDE.md](CLAUDE.md).

### Install a skill for Codex or Claude Code

Clone this repository, then copy the **whole skill folder**, including references, into your agent's skill directory. Run these commands from the clone:

```bash
git clone https://github.com/Nikshay1/Nikshay-AI-Skills.git
cd Nikshay-AI-Skills
```

For Codex:

```bash
mkdir -p "$HOME/.agents/skills"
cp -R -i skills/writing/unslop "$HOME/.agents/skills/"
```

For Claude Code:

```bash
mkdir -p "$HOME/.claude/skills"
cp -R -i skills/writing/unslop "$HOME/.claude/skills/"
```

Replace `skills/writing/unslop` with another folder from the catalog. To scope a skill to one project, copy it into that project's `.agents/skills/` for Codex or `.claude/skills/` for Claude Code. Start a new session after installation.

The categorized `skills/` tree is a library; cloning it alone does not install every skill in your agent's discovery directory. See the official [Codex skill documentation](https://learn.chatgpt.com/docs/build-skills) and [Claude Code skill documentation](https://code.claude.com/docs/en/skills) for discovery behavior.

## Source notes

This collection began with four Markdown files from Nikshay's local skill library. Their original relative filenames are recorded in `catalog.json`. The writing and issue-finding skills retain their original instructions, with YAML metadata added and trailing heading whitespace cleaned up. The two Grafana documents are preserved in their skill folders as references, with concise entry points added for discovery.

The original Grafana run guide describes Nikshay's workstation. Its `/home/nikshay` paths and SSD/tmpfs assumptions are examples; the entry point explains how to check and adapt them for another machine. The PR checklist's issue number and component names describe a historical case, not a guarantee about Grafana's current source.
