# skills

> A collection of AI agent skills for business and engineering — ready to drop into Codex, Github Copilot, Claude, PI, or other agent.

## Table of Contents
- [skills](#skills)
  - [Table of Contents](#table-of-contents)
  - [Overview](#overview)
  - [Skills](#skills-1)
  - [Usage](#usage)
  - [Contributing](#contributing)
  - [License](#license)

## Overview

This repository hosts reusable, composable **skills** — structured instruction files that extend AI coding agents with domain-specific knowledge and workflows. Each skill lives in its own directory and follows a consistent convention: a `SKILL.md` entrypoint, optional `assets/` for templates, and `references/` for supporting material.

Skills are designed to be invoked by AI agents (GitHub Copilot, Claude, etc.) when a user's request falls within the skill's domain. They encode repeatable processes, domain constraints, and quality guardrails so agents produce consistent, high-quality output.

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

## Contributing

1. Fork the repository and create a feature branch.
2. Add your skill under a new top-level directory (e.g., `my-skill/`).
3. Include a `SKILL.md` with a YAML frontmatter block (`name`, `description`) and a clear workflow section.
4. Add an `assets/` directory for any templates and a `references/` directory for supporting docs if needed.
5. Update the [Skills](#skills) table in this README.
6. Open a pull request.

## License

[MIT](LICENSE)
