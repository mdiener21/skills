# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- Agents now automatically review and update CHANGELOG and README after every repository change, enforced via `AGENTS.md` workflow rules.

### Changed
- Enhanced `write-changelog-readme` README reference template with richer structural guidelines and AI instructions for consistent output.
- Strengthened `sop` skill guidance for credential handling by requiring secret references (env vars or secret-manager paths) and prohibiting literal credential values in SOP inputs and command examples.

### Removed
- Removed PRD writing from the `write-changelog-readme` skill scope

## [1.0.0] - 2026-05-17

### Added
- `sop` skill — write, create, update, and audit Standard Operating Procedures for humans or AI agents, with templates and references
- `write-changelog-readme` skill — create and update CHANGELOG and README using standard Keep-a-Changelog and readme templates
- Claude plugin configuration (`.claude-plugin/plugin.json`) for registering skills with Claude Code
- `AGENTS.md` and symlinks so Gemini and other agents can discover skills alongside Claude
- `.gitignore` covering agent code directories, node modules, and IDE files
- README with overview, quickstart installer (`npx skills@latest add`), skills table, usage instructions, and contributing guidelines
- skills.sh badge for install tracking

[Unreleased]: https://github.com/mdiener21/skills/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/mdiener21/skills/releases/tag/v1.0.0
