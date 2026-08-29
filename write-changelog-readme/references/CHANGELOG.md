# CHANGELOG.md Format Reference

Based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## File Structure

```markdown
# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- Feature description here

### Changed
- Change description here

### Fixed
- Bug fix descriptions here

## [1.0.0] - YYYY-MM-DD
### Added
- Initial release

### Fixed
- Fixed: bug press red button did not open modal.
```

## AI Editor Rules
1. **Always** insert new entries into the `## [Unreleased]` block.
2. Group underneath the appropriate categorization sub-headers: `### Added`, `### Changed`, `### Deprecated`, `### Removed`, `### Fixed`, `### Security`. Only use sub-headers that have entries.
3. Keep descriptions user-facing. Strip out internal technical jargon unless it impacts the consumer.


### Steps:
1. Insert a new blank `## [Unreleased]` section at the top (after the preamble).
2. Convert the old `[Unreleased]` header to `## [X.Y.Z] - YYYY-MM-DD`.
3. Keep all content exactly as-is under the new version header.
4. Append a comparison link at the bottom of the file.

---

### When `[Unreleased]` Section Is Empty or Missing

If the `[Unreleased]` section exists but has no entries, populate it from git log:

```bash
git log $(git describe --tags --abbrev=0 2>/dev/null)..HEAD \
  --pretty=format:"- %s" --no-merges 2>/dev/null | head -30
```

Then categorize commits by type using conventional commit prefixes if present:
- `feat:` → Added
- `fix:` → Fixed
- `chore:`, `refactor:`, `perf:` → Changed
- `security:` → Security
- `docs:`, `test:`, `ci:` → typically omit from user-facing changelog

If no CHANGELOG.md exists at all, create one from scratch using the full structure above, seeding the new version section from the git log.

---

### Comparison Links

At the bottom of the file, maintain a list of comparison links:

```markdown
[Unreleased]: https://github.com/OWNER/REPO/compare/vNEW...HEAD
[NEW]: https://github.com/OWNER/REPO/compare/vPREV...vNEW
```

To get the remote URL for link building:
```bash
gh repo view --json url -q .url
# or: git remote get-url origin
```

Strip `.git` suffix if present. Format:
- `https://github.com/owner/repo/compare/v1.1.0...v1.2.0`

---

## Style Rules

- Write entries in **imperative present tense**: "Add feature" not "Added feature" or "Adds feature"
  (the header `### Added` provides the tense context — the bullets can be noun phrases too)
- Keep entries concise — one line each
- Reference issue/PR numbers in parentheses where relevant: `(#42)`
- Never leave the `[Unreleased]` section completely absent — always preserve it for future work
- Date format is always `YYYY-MM-DD` (ISO 8601)