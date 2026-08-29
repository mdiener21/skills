# Skills For A Real Business using AI and Real Engineers

> A collection of composable AI agent skills for business and engineering — ready to drop into Claude, GitHub Copilot, Codex, Gemini, or any agent that reads instruction files.

[![skills.sh](https://skills.sh/b/mdiener21/skills)](https://skills.sh/mdiener21/skills)
![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-lightgrey)

My agent skills that I use every day to run my real business and do real engineering.

Running a solo business and developing real applications is hard. You know your process — so define it with an SOP and let your agent follow it. These skills are small, easy to adapt, and composable. They work with any model and are grounded in decades of engineering experience.

## Table of Contents
- [Overview](#overview)
- [Skills](#skills)
- [Architecture & Modules](#architecture--modules)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Deployment](#deployment)
- [Other Skill Collections](#other-skill-collections)
- [Contributing](#contributing)
- [License](#license)

## Overview

This repository hosts reusable, composable **skills** — structured instruction files that extend AI coding agents with domain-specific knowledge and workflows. Each skill follows a consistent convention and is invoked automatically when a user's request falls within its domain.

## Skills

| Skill | Description |
|-------|-------------|
| [sop](sop/SKILL.md) | Write, create, update, maintain, and audit Standard Operating Procedures (SOPs) for humans or AI agents. |
| [write-changelog-readme](write-changelog-readme/SKILL.md) | Creates and updates CHANGELOG and README using standard Keep-a-Changelog and readme templates. |
<!-- AI UPDATE HOOK: Add new skills above this line -->

## Architecture & Modules

Each skill lives in its own top-level directory and follows this structure:

```
my-skill/
├── SKILL.md          # Entrypoint: trigger phrases, workflow, and instructions for the agent
├── assets/           # Templates, boilerplate, or static files the skill uses
└── references/       # Supporting documentation or format guides
```

Skills are registered in `.claude-plugin/plugin.json` for Claude Code discovery and listed in `AGENTS.md` / `GEMINI.md` for cross-agent compatibility.

## Installation

Install via the skills.sh CLI — takes about 30 seconds:

```bash
npx skills@latest add mdiener21/skills
```

Or clone manually and point your agent's instructions file at the skill's `SKILL.md`.

## Configuration

No environment variables or system configuration required. Skills are plain instruction files — no build step, no runtime dependencies.

## Usage

**Referencing a skill in your agent configuration:**

```markdown
- **sop** (`path/to/skills/sop/SKILL.md`) — SOPs for humans and AI agents. Trigger: `/sop`
```

**Invoking a skill at runtime:**

Each skill's `SKILL.md` documents its trigger phrases and workflow. For example:

- `sop` activates on `/sop`, `"write an SOP for..."`, or `"document this process"`
- `write-changelog-readme` activates on requests to write, update, or refactor `CHANGELOG.md` or `README.md`

## Deployment

Skills are distributed via [skills.sh](https://skills.sh). Push to `main` and the installer picks up the latest version automatically — no build or publish step needed.

## Other Skill Collections

The following collections I personally recommend and use:

| Skill Collection | Author | Description |
|------------------|--------|-------------|
| Real Engineering Skills | [Matt Pocock](https://github.com/mattpocock/skills/tree/main/skills) | Multiple skills for TypeScript and engineering workflows |
| Superpowers for Engineers | [Jesse Vincent](https://github.com/obra/superpowers/tree/main/skills) | Multiple skills for developer productivity |

## Contributing

1. Fork the repository and create a feature branch.
2. Add your skill under a new top-level directory (e.g., `my-skill/`).
3. Include a `SKILL.md` with a YAML frontmatter block (`name`, `description`) and a clear workflow section.
4. Add an `assets/` directory for templates and a `references/` directory for supporting docs if needed.
5. Register the skill in `.claude-plugin/plugin.json` and update the [Skills](#skills) table above.
6. Open a pull request.

## License

[MIT](LICENSE)
