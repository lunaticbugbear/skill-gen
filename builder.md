# The Builder Instructions

Scaffold a new high-impact AI skill using native agent tools.

## Non-Negotiable Rules
1. **Absolute Isolation:** Every skill gets a dedicated folder. Never pollute the parent directory.
2. **Deterministic Logic:** Generate complete, production-ready instructions. No placeholders.
3. **Safety First:** Sanitize all names to `^[a-z0-9-]+$`.
4. **Platform Optimization:** Select the template that matches the user's environment.

## Build Steps

### 1. Identify Target & Template
Determine which platform the user is targeting:
- **Claude Code:** Use `templates/claude-code.md`.
- **Codex CLI:** Use `templates/codex.md`.
- **Generic/Universal:** Use `templates/universal.md`.

### 2. Sanitize & Scaffold
- Sanitize the skill name to kebab-case: `[a-z0-9-]`.
- Create the directory: `mkdir <skill-name>`.
- If folder exists, use versioning: `<skill-name>-v2`, etc.

### 3. Generate `SKILL.md`
Transform the selected template into a mission-critical `SKILL.md`:
- **Mission Realism:** Define the goal with concrete, high-impact language.
- **Fail-Safe Logic:** Inject specific validation steps and self-healing instructions relevant to the goal.
- **Orchestration:** If the task is large (city-scale), add specific instructions for parallel execution and sub-agent delegation.
- **Remove Junk:** Delete any unused `{{optional_api_instructions}}` or empty input lists.

### 4. Supporting Infrastructure
- Create `.env.example` if the skill requires API keys or secrets.
- Create a `docs/` folder if the skill requires complex architectural specs.
- If the skill requires specific datasets, add notes on where to place them.

### 5. The Quality Gate (QA)
Before finishing, run shell commands to verify:
- `SKILL.md` is complete and contains zero `{{` placeholders.
- The directory structure is clean and correctly named.
- The workflow logic is logical and covers common failure modes.

### 6. Handoff
Output exactly:
```text
Mission-Ready Skill created: ./<skill-name>/SKILL.md

Usage:
cd <skill-name>
<agent-command> --skill .
```
(Replace `<agent-command>` with `claude`, `codex`, etc.).
