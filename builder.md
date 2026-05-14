# The Builder Instructions

Scaffold a new skill using only markdown and built-in agent file tools.

## Non-Negotiable Rules
1. Create a brand new isolated folder for every generated skill.
2. Never write generated skill files into the current directory root.
3. Never use `AskUserQuestion` or any platform-specific UI tool.
4. Generate complete instructions, not placeholder docs.
5. If folder exists, append `-v2`, `-v3`, etc.
6. Sanitize skill name to `[a-z0-9-]` before any shell command.

## Build Steps

### 1. Generate Name & Setup
- Convert goal into kebab-case. Use letters, numbers, hyphens only.
- **Sanitize:** Remove any character not in `[a-z0-9-]`. Lowercase everything. Example: `analyze 9router costs!` -> `analyze-9router-costs`.

### 2. Create Directory
Use shell command:
```bash
mkdir <skill-name>
```
If it fails because the folder exists, create a versioned folder: `<skill-name>-v2`, `<skill-name>-v3`, etc.

### 3. Select & Load Template
Determine the agent platform the user is likely targeting (Claude Code, Codex, or Universal).
- Claude Code: Read `templates/claude-code.md`
- Universal/Other: Read `templates/universal.md`

*Fallback:* If reading fails, use this internal structure:
- YAML frontmatter (`name`, `description`)
- Overview & Goal
- Constraints
- When to Use
- Required Inputs
- Workflow (Initialization, Action, Verification)
- Expected Output Format

### 4. Generate `SKILL.md`
Fill the selected template with concrete content, writing it to `<skill-name>/SKILL.md`:
- No unresolved placeholders (`{{...}}`).
- No vague steps like "do the task". Detail the exact commands or logical steps.
- Each step must specify what to inspect, decide, and output.
- Include failure handling and exact output format.
- If `{{optional_api_instructions}}` is not needed, remove the entire line.

### 5. Generate Supporting Files
- If the skill needs secrets, create `<skill-name>/.env.example`.
- If the skill needs reusable prompts or context, create `<skill-name>/references/` (only when strictly necessary).

### 6. Verification
Run shell commands (`ls -la <skill-name>`, `cat <skill-name>/SKILL.md` or equivalent) to confirm:
- Folder exists.
- `SKILL.md` exists inside the folder and is non-empty.
- No placeholders remain (`{{...}}`).
- Frontmatter contains `name` and `description`.
- No shell injection risk in generated commands.

### 7. Handoff
Output exactly:
```text
Skill created: ./<skill-name>/SKILL.md

Use:
cd <skill-name>
<agent-cli-command> --skill .
```
(Replace `<agent-cli-command>` with `claude`, `codex`, etc. depending on context).
