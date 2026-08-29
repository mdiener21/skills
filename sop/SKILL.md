---
name: sop
description: Write, create, update, maintain, and audit Standard Operating Procedures (SOPs) — for humans or AI agents. Invoke this skill whenever the user wants to document a process, create an SOP, update an existing procedure, review SOPs for completeness, or standardize a repeatable workflow. Trigger on /sop, "write an SOP for", "document this process", "create a procedure for", "update our SOP", "I need to document how we", "standard operating procedure", "process documentation", or any request to formalize a repeatable process — even if the user doesn't use the word "SOP". Also trigger when the user wants to create agent instructions, a runbook, or a workflow that an AI agent should follow.
---

# SOP Skill

You help users create, update, maintain, and audit Standard Operating Procedures.

## What an SOP is

An SOP is structured, executable instructions for a repeatable process. Think of it as a skill file for a human or AI agent — it should be complete enough that the executor (person or agent) can follow it cold, without asking anyone for help, and produce a consistent result every time.

This framing matters for how you write SOPs:
- Steps must be unambiguous — no "use judgment here" without defining what good judgment looks like
- Each step should have a verifiable outcome (the executor can confirm it succeeded before moving on)
- Common Mistakes are as important as the happy path — they make the SOP self-correcting
- The Owner is accountable when the SOP breaks down or goes stale

## Human vs AI-Agent SOPs

Before writing, establish who will execute this SOP:

**Human executor**: Steps can reference UI clicks, visual confirmation, and contextual judgment. Write in imperative second-person ("Open the dashboard", "Confirm the status shows green").

**AI-agent executor**: Steps must be explicit and tool-specific — no "open the dashboard," instead "run `docker ps` and confirm the container is running." Reference exact commands, file paths, API endpoints, and expected output patterns. Verification checkboxes should be machine-checkable (grep for a string, check an exit code, confirm a file exists). Never include raw secrets in commands or examples; use environment variables or secret-manager references (for example, `${API_TOKEN}` or `aws secretsmanager get-secret-value ...`).

**Both**: Many SOPs are followed by either. Write at the human level but include exact commands in code blocks where precision matters.

Ask if unclear: "Will a human, an AI agent, or both follow this SOP?"

## Templates

Two templates are bundled as assets:

- `assets/template-sop-default.md` — for straightforward processes (use this by default)
- `assets/template-sop-detailed.md` — for large, complex, or compliance-critical processes

If the project has templates at `docs/sop/template-sop-default.md` or `docs/sop/template-sop-detailed.md`, prefer those. Fall back to the bundled assets otherwise.

## Choosing the Right Template

Use the **default** template when:
- The process has 5 or fewer steps
- A single role or team owns the whole process end-to-end
- The workflow is well-understood with few edge cases

Use the **detailed** template when:
- The process spans multiple teams or tools
- There are 6+ steps or conditional branches
- Tools/systems need to be inventoried
- Quality checks, escalation paths, or compliance apply
- The user describes it as "complex", "involved", or "critical"
- It will be followed by an AI agent (agents benefit from the explicit structure)

## Workflow

### 1. Identify the Mode

- **Create**: New SOP for an undocumented process
- **Update**: Existing SOP needs new steps, corrections, or a scope change
- **Audit**: Review existing SOP(s) for completeness and staleness

### 2. Interview the User

Ask targeted questions — read the user's message first, only ask about the gaps. Do not dump all questions at once.

**Always ask:**
- Who performs this process (human role, AI agent, or both)?
- Who owns this SOP — who is responsible when it breaks down or goes stale?
- What triggers the process?

**Ask as needed:**
- What must be in hand before starting (credential references, files, decisions)?
- What are the steps, in order? What does "done" look like?
- What goes wrong most often, and how do you recover?

**Owner matters.** If the user doesn't name an owner, prompt them: "Who's the point of contact when this process fails or needs updating?" Every SOP must have a named owner — a role or a person. Do not leave Owner blank or generic ("the team").

For updates: read the existing SOP first, then ask specifically what changed. Bump the version in the Change Log.

### 3. Select the Template and Fill It In

Read the appropriate template file. Replace every placeholder with real content. Never leave template placeholder text in the output — this includes `[Action]`, `[Situation]`, `[Input]`, `[Mistake]`, `[Tool name]`, `YYYY-MM-DD`, and any other `[bracket]` text.

Fill in each section:
- **Purpose**: The specific risk or problem this prevents — not generic ("ensures consistency"), but concrete ("prevents the VPS from serving stale assets after a failed FTP deploy")
- **Scope**: Exact situations where it applies and explicit exceptions
- **Owner**: A named role or person — never blank, never "TBD"
- **Inputs**: Specific things needed before starting (credential reference names such as env vars or vault paths, file names, decisions required). Never include raw secret values.
- **Procedure**: Numbered, imperative sentences. For AI-agent SOPs, include exact commands in code blocks with expected output patterns. Commands must reference secrets indirectly (environment variables, secret files, or secret-manager lookups), never embed literal credentials.
- **Outputs**: Observable, verifiable results — what you can check after
- **Definition of Done**: Concrete checkboxes — each one must be independently verifiable
- **Common Mistakes**: Real failure modes from the interview — table format with Mistake, Impact (or How to Avoid)

### 4. Fill the Change Log — always

**This section is mandatory and must never be left with placeholder text.**

Every SOP must end with a Change Log entry using today's real date:

```
| 2026-05-14 | 1.0 | [Owner name] | Initial version |
```

For updates, add a new row — do not modify existing rows:
```
| 2026-05-14 | 1.1 | [Owner name] | Added step 3b for hotfix path |
```

If you don't know today's date, check with `date +%Y-%m-%d`. Never leave `YYYY-MM-DD` in the output.

### 5. Save the File

Save completed SOPs to `docs/sop/` using kebab-case filenames:

```
docs/sop/deploy-production.md
docs/sop/onboard-new-developer.md
docs/sop/ai-agent-triage-support-tickets.md
```

If `docs/sop/` doesn't exist, create it. For updates, edit in place and bump the Change Log.

### 6. Confirm and Offer Next Steps

Tell the user the file path and offer:
- "Want to walk through this and refine any sections?"
- "Should I create a related SOP for [adjacent process you noticed]?"
- "Would you like a version of this formatted for an AI agent to execute directly?"

## Auditing Existing SOPs

When the user asks to audit or review SOPs:

1. List all `.md` files in `docs/sop/` (exclude files matching `template-*`)
2. For each SOP, check:
   - **Required sections present**: Purpose, Scope, Owner, Inputs, Procedure, Outputs, Definition of Done, Common Mistakes, Change Log
   - **No placeholder text**: `grep -E '\[.+\]|YYYY-MM-DD' <file>` — any match means incomplete
   - **Owner is named**: not blank, not "TBD", not "[Name or Role]"
   - **Steps are imperative**: not passive voice, not "should be done"
   - **Change Log has a real date**: not `YYYY-MM-DD`
   - **Common Mistakes is populated**: not just the template example row
3. Report findings in a table:

| File | Missing Sections | Placeholder Text | Owner Named | Last Updated | Status |
|---|---|---|---|---|---|
| `file.md` | none | none | yes | 2026-01-10 | OK |
| `file2.md` | Owner, Inputs | yes | no | n/a | Needs work |

4. Offer to fix any incomplete SOPs one at a time.

## Quality Bar

An SOP is ready when:
- A human or AI agent could follow it cold, without asking anyone for help
- Every step has an action verb and a verifiable outcome
- Every Definition of Done checkbox corresponds to something independently checkable
- No `[bracket]` placeholder text or `YYYY-MM-DD` remains anywhere in the file
- The Owner section names a real role or person
- The Change Log has a real date in the most recent row
- The file is saved to `docs/sop/` with a meaningful kebab-case name
