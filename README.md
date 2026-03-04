# Work-Like-Claude-Code Skill

A Codex skill package that enforces a Claude Code-style execution pattern:

- minimal user-facing text
- tool-first implementation
- defensive codebase exploration before edits
- explicit task tracking for non-trivial work
- autonomous verify-and-repair loops (lint/test/typecheck)
![Uploading image.png…]()

## What This Repository Contains

Primary skill package:

- `.agents/skills/work-like-claudecode/SKILL.md`
- `.agents/skills/work-like-claudecode/agents/openai.yaml`
- `.agents/skills/work-like-claudecode/references/core-system-prompt.xml.md`
- `.agents/skills/work-like-claudecode/references/tool-action-schemas.yaml`
- `.agents/skills/work-like-claudecode/references/manifest.yaml`
- `.agents/skills/work-like-claudecode/references/implementation.md`
- `.agents/skills/work-like-claudecode/references/source-analysis.md`

## Install (Codex)

Copy the skill folder to your Codex skills directory:

```powershell
Copy-Item -Path ".agents\skills\work-like-claudecode" -Destination "$env:USERPROFILE\.codex\skills\work-like-claudecode" -Recurse -Force
```

Restart Codex, then invoke with:

```text
$work-like-claudecode <your task>
```

## Behavior Summary

When invoked, the skill pushes the agent toward:

1. Explore: read project configs and existing patterns before editing.
2. Plan: maintain a clear task list for complex requests.
3. Task: apply direct file edits with tools instead of long markdown code dumps.
4. Verify: run quality gates and auto-fix until passing or blocked.

## References Used

The skill behavior and structure were derived from the following sources:

1. Claude Code reverse-engineering repository  
   https://github.com/Yuyz0112/claude-code-reverse
2. Claude Code system prompts repository  
   https://github.com/Piebald-AI/claude-code-system-prompts
3. Agent Skills Open Standard  
   https://agentskills.io/specification
4. OpenAI Codex Skills documentation  
   https://developers.openai.com/codex/skills  
   https://developers.openai.com/codex/skills/create-skill
5. OpenAI skills repository and skill-creator scripts  
   https://github.com/openai/skills

## Notes

- This is a skill-level behavior layer. It cannot override higher-priority runtime system/developer instructions.
- Source extraction details are tracked in:
  - `.agents/skills/work-like-claudecode/references/source-analysis.md`
