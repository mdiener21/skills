---
name: write-changelog-readme
description: Creates and updates CHANGELOG, README using standard templates. Use when the user asks to write, update, or refactor project CHANGE.log or README.md-
version: 1.1
updated: 2026-05-17
---

# Write A CHANGELOG or README Skill

This skill enforces consistency, structure, and quality when writing or updating a projects `README.md` or `CHANGELOG.md`

## Workflow 

### 1. `README.md` Updates
- **Reference:** See `references/README.md` for structural guidelines and template.
- **Rules:** Follow the "AI INSTRUCTIONS" in the reference. Place new features under `## Features`, environment variables under `## Configuration`, and refactor details under `## Architecture & Modules`. Keep existing structure pristine. 

### 2. `CHANGELOG.md` Updates
- **Reference:** See `references/changelog.md` for "Keep a Changelog" conventions.
- **Rules:** Always group new changes under the `## [Unreleased]` section.
- Use explicit categories: `Added`, `Changed`, `Deprecated`, `Removed`, `Fixed`, `Security`.

**Tone & Framing (Changelog):**
Include ONLY user-facing, impactful changes.
* ✅ **Good:** `Fixed TypeScript SDK issue causing incorrect CJS config`, `Added claim timeout extension on checkpoint writes.`
* ❌ **Bad:** `Fixed bug` (vague), `Updated dependencies` (noise), `Refactored internal routing` (internal).

