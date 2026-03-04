# Implementation Instructions

## Package Layout

This skill package uses the following structure:

- `SKILL.md` (required runtime instructions)
- `agents/openai.yaml` (UI metadata for skill pickers/chips)
- `references/core-system-prompt.xml.md` (strict behavior contract)
- `references/tool-action-schemas.yaml` (Explore/Plan/Task/Verify action schemas)
- `references/manifest.yaml` (explicit triggers and permission model)
- `references/source-analysis.md` (evidence and extraction notes)

## Build/Init

Initialize a new copy using the official initializer:

```bash
python "<CODEX_HOME>/skills/.system/skill-creator/scripts/init_skill.py" work-like-claudecode --path "<target-dir>" --resources references
```

Regenerate `agents/openai.yaml` interface values if needed:

```bash
python "<CODEX_HOME>/skills/.system/skill-creator/scripts/generate_openai_yaml.py" "<target-dir>/work-like-claudecode" --interface display_name="Work Like Claude Code" --interface short_description="Strict Claude Code-style engineering execution"
```

Validate the skill:

```bash
python "<CODEX_HOME>/skills/.system/skill-creator/scripts/quick_validate.py" "<target-dir>/work-like-claudecode"
```

## Install

Install by placing the folder under:

- `%USERPROFILE%\.codex\skills\work-like-claudecode` (Codex local install), or
- any host-specific skills directory that supports Agent Skills Open Standard folders.

Restart the host agent runtime to pick up new skills.

## Runtime Invocation

Use explicit invocation for deterministic behavior:

- `$work-like-claudecode fix this failing test suite`
- `$work-like-claudecode implement this feature with strict verify loops`
