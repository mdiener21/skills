---
name: write-changelog-readme
description: Creates and updates CHANGELOG, README using standard templates. Use when the user asks to write, update, or refactor project documentation.
version: 1.1
updated: 2026-05-17
---

# Write Code Docs Skill

This skill enforces consistency, structure, and quality when writing or updating project documentation (`README.md`, `CHANGELOG.md`, PRDs).

## Workflow 

### 1. `README.md` Updates
- **Reference:** See `references/README.md` for AI structural guidelines and template.
- **Rules:** Follow the "AI INSTRUCTIONS" in the reference. Place new features under `## Features`, environment variables under `## Configuration`, and refactor details under `## Architecture & Modules`. Keep existing structure pristine. 

### 2. `CHANGELOG.md` Updates
- **Reference:** See `references/changelog.md` for "Keep a Changelog" conventions.
- **Rules:** Always group new changes under the `## [Unreleased]` section.
- Use explicit categories: `Added`, `Changed`, `Deprecated`, `Removed`, `Fixed`, `Security`.

**Tone & Framing (Changelog):**
Include ONLY user-facing, impactful changes.
* ✅ **Good:** `Fixed TypeScript SDK issue causing incorrect CJS config`, `Added claim timeout extension on checkpoint writes.`
* ❌ **Bad:** `Fixed bug` (vague), `Updated dependencies` (noise), `Refactored internal routing` (internal).

### 3. PRDs / Specifications
- Frame context clearly: 1) What is being solved? 2) Proposed architecture. 3) Metrics for success.
- Extract details from the conversation and generalize into standard headers. Always strive for concise, declarative language.
