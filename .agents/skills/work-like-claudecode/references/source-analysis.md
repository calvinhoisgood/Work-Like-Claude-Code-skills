# Source Analysis Snapshot

Date collected: 2026-03-04

## 1) GitHub: Yuyz0112/claude-code-reverse

- Repository: `https://github.com/Yuyz0112/claude-code-reverse`
- Local commit analyzed: `c0d99ea1ab7168c12ba74838cfea355ce10f6c56`
- Primary files reviewed:
  - `README.md`
  - `results/prompts/system-workflow.prompt.md`
  - `results/prompts/system-reminder-start.prompt.md`
  - `results/prompts/system-reminder-end.prompt.md`
  - `results/prompts/system-output-style-learning.prompt.md`
  - `results/prompts/system-output-style-explanatory.prompt.md`
  - `results/tools/TodoWrite.tool.yaml`
  - `results/tools/Task.tool.yaml`
  - `results/tools/Bash.tool.yaml`

### Extracted behaviors used in this skill

- Strong concise-output policy with low tolerance for preamble/postamble.
- Tool-first workflow with explicit guidance to search/read before edit.
- Frequent todo/task tracking behavior and immediate state updates.
- Sub-agent/task delegation pattern for broad exploration work.
- Reminder-driven operational discipline using `<system-reminder>` injections.

## 2) GitHub: Piebald-AI/claude-code-system-prompts

- Repository: `https://github.com/Piebald-AI/claude-code-system-prompts`
- Local commit analyzed: `430ed422567ec78a9b42cf57afff3cdcbcf40a1e`
- Primary files reviewed:
  - `README.md`
  - `system-prompts/agent-prompt-explore.md`
  - `system-prompts/agent-prompt-plan-mode-enhanced.md`
  - `system-prompts/agent-prompt-task-tool.md`
  - `system-prompts/agent-prompt-task-tool-extra-notes.md`
  - `system-prompts/system-prompt-tone-and-style-concise-output-short.md`
  - `system-prompts/system-prompt-tone-and-style-concise-output-detailed.md`
  - `system-prompts/system-prompt-tool-usage-task-management.md`
  - `system-prompts/system-reminder-todowrite-reminder.md`
  - `system-prompts/system-reminder-task-tools-reminder.md`
  - `system-prompts/system-reminder-plan-mode-is-active-5-phase.md`

### Extracted behaviors used in this skill

- Read-only Explore and Plan agents with strict no-modification constraints.
- Explicit phased workflow in plan mode, including context gathering and finalization.
- Direct concise style mandates and no inner-monologue exposure.
- XML-style structures used throughout prompts and reminders (`<analysis>`, `<summary>`, `<system-reminder>`, `<example>`, `<reasoning>`, `<env>`).
- Task tracking reminders and status-transition discipline.

## 3) Official Agent Skills Standard / skills-create documentation

### Standards and docs reviewed

- Agent Skills Open Standard specification:
  - `https://agentskills.io/specification`
- OpenAI Codex skill docs:
  - `https://developers.openai.com/codex/skills`
  - `https://developers.openai.com/codex/skills/create-skill`
- OpenAI skills repository:
  - `https://github.com/openai/skills`
  - Local commit analyzed: `8d04dc2f7ea6dd83d7639cd2f22a1d0b4f586573`
- OpenAI system skill-creator scripts:
  - `skills/.system/skill-creator/scripts/init_skill.py`
  - `skills/.system/skill-creator/scripts/generate_openai_yaml.py`
  - `skills/.system/skill-creator/scripts/quick_validate.py`
  - `skills/.system/skill-creator/references/openai_yaml.md`

### Extracted structural requirements used in this package

- Required baseline: folder with `SKILL.md`.
- `SKILL.md` frontmatter must include at least `name` and `description`.
- Optional UI metadata in `agents/openai.yaml` (`interface.display_name`, `interface.short_description`, and optional UI fields).
- Keep core instructions in `SKILL.md`, push detailed references into `references/` for progressive disclosure.
- Validate package shape with `quick_validate.py`.

## Resulting skill design decisions

- Enforce strict terse-output and tool-first behavior through `references/core-system-prompt.xml.md`.
- Encode Explore -> Plan -> Task -> Verify as structured schemas in `references/tool-action-schemas.yaml`.
- Provide explicit trigger and permission metadata in `references/manifest.yaml`.
- Keep installation and runtime integration instructions in `references/implementation.md`.
