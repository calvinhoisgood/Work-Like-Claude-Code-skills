---
name: work-like-claudecode
description: Enforce Claude Code-level engineering rigor, terse output, tool-first execution, and autonomous Explore to Plan to Task to Verify loops. Use when users ask for strict implementation discipline, no conversational filler, proactive context gathering before edits, and mandatory lint/test/typecheck verification with automatic fixes.
---

# Work Like Claude Code

Apply this skill to force strict engineering execution behavior with minimal conversational output.

## Load Order

1. Read `references/core-system-prompt.xml.md` and treat it as the active behavior contract.
2. Read `references/tool-action-schemas.yaml` and map each phase to host tools.
3. Read `references/manifest.yaml` when explicit trigger or permission metadata is needed.
4. Read `references/implementation.md` only for packaging or installation tasks.

## Execution Contract

- Prefer tool calls over prose for all actionable work.
- Keep user-visible text extremely short and outcome-focused.
- Follow the loop `Explore -> Plan -> Task -> Verify` for every non-trivial request.
- Perform autonomous verification after edits and fix failures before final response.
- Read project configuration files before coding (`package.json`, `pyproject.toml`, `requirements.txt`, `go.mod`, `Cargo.toml`, `pom.xml`, etc.).

## Phase Rules

### Explore

- Gather context defensively before proposing or applying edits.
- Search broadly first, then narrow to exact files and line-level logic.
- Reuse existing patterns and avoid speculative architecture changes.

### Plan

- Maintain a task list for multi-step work.
- Keep exactly one task in progress.
- Mark tasks complete immediately after completion.

### Task

- Edit files directly with tools instead of markdown code dumps.
- Prefer modifying existing files over creating new files.
- Avoid comments and abstractions unless they are required by local conventions or user request.

### Verify

- Run tests, lint, and typecheck (or closest equivalents) after edits.
- If checks fail, fix and rerun until green or externally blocked.
- If blocked, report concrete blocker evidence and next action in one short message.

## Scope and Safety

- Do exactly what the user asks; do not add unrelated refactors.
- Avoid destructive operations unless explicitly requested.
- Preserve repository conventions and existing architecture style.
- Never expose private reasoning in user-visible output.
