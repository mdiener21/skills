# skills

> A collection of AI agent skills for business and engineering — ready to drop into Codex, Github Copilot, Claude, PI, or other agent.

## Table of Contents
- [skills](#skills)
  - [Table of Contents](#table-of-contents)
- [Skills For A Real Business using AI and Real Engineers](#skills-for-a-real-business-using-ai-and-real-engineers)
  - [Quickstart (30-second setup)](#quickstart-30-second-setup)
  - [Overview](#overview)
  - [Skills](#skills-1)
  - [Usage](#usage)
  - [Other Productivity Skills from great authors](#other-productivity-skills-from-great-authors)
  - [Contributing](#contributing)
  - [License](#license)

# Skills For A Real Business using AI and Real Engineers

[![skills.sh](https://skills.sh/b/mdiener21/skills)](https://skills.sh/mdiener21/skills)

My agent skills that I use every day to run my real business and do real engineering.

Running a real business solo is hard, and so is developing real applications is hard. You  know your process so build it and define it with an SOP (Standard Operating Procedure). The control is in your hands as you know the problem you are solving.

These skills are designed to be small, easy to adapt, and composable. They work with any model. They're based on decades of engineering experience.


## Quickstart (30-second setup)

1. Run the skills.sh installer:

```bash
npx skills@latest add mdiener21/skills
```


## Overview

This repository hosts reusable, composable **skills** — structured instruction files that extend AI coding agents with domain-specific knowledge and workflows. Each skill lives in its own directory and follows a consistent convention: a `SKILL.md` entrypoint, optional `assets/` for templates, and `references/` for supporting material.

Skills are designed to be invoked by AI agents (GitHub Copilot, Codex, Claude, etc.) when a user's request falls within the skill's domain.

## Skills

| Skill | Description |
|-------|-------------|
| [sop](sop/SKILL.md) | Write, create, update, maintain, and audit Standard Operating Procedures (SOPs) for humans or AI agents. |
<!-- AI UPDATE HOOK: Add new skills above this line -->

## Usage

**Referencing a skill in your agent configuration:**

Point your agent's instructions file at a skill's `SKILL.md`:

```markdown
- **sop** (`path/to/skills/sop/SKILL.md`) — SOPs for humans and AI agents. Trigger: `/sop`
```

**Invoking a skill at runtime:**

Each skill's `SKILL.md` documents its trigger phrases and workflow. For example, the `sop` skill activates on prompts like `/sop`, `"write an SOP for..."`, or `"document this process"`.

## Other Productivity Skills from great authors

The following skills collection I can personally recommend as I use them.

| Skill Collection | Author Github Link | Description |
|-------|-----|-------------|
| Real Engineering Skills | [Matt Pocock](https://github.com/mattpocock/skills/tree/main/skills) | Multiple Skills |
|Superpowers for Engineers | [Jesse Vincent](https://github.com/obra/superpowers/tree/main/skills)  | Multiple Skills |



## Contributing

1. Fork the repository and create a feature branch.
2. Add your skill under a new top-level directory (e.g., `my-skill/`).
3. Include a `SKILL.md` with a YAML frontmatter block (`name`, `description`) and a clear workflow section.
4. Add an `assets/` directory for any templates and a `references/` directory for supporting docs if needed.
5. Update the [Skills](#skills) table in this README.
6. Open a pull request.

## License

[MIT](LICENSE)
