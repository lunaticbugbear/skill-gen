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

### 1. Generate Name
- Convert goal into kebab-case.
- Use letters, numbers, hyphens only.
- **Sanitize:** Remove any character not in `[a-z0-9-]`. Lowercase everything.
- Example: `analyze 9router costs!` → `analyze-9router-costs`.

### 2. Create Folder
Use shell command:
```bash
mkdir <skill-name>
```
If it fails because folder exists, create versioned folder: `<skill-name>-v2`, `<skill-name>-v3`, etc.

### 3. Load Template
Read `templates/claude-code.md`. If unavailable, use this internal structure:
- YAML frontmatter
- Overview
- When to Use
- Inputs
- Workflow
- Output Format
- Common Mistakes

### 4. Generate `SKILL.md`
Fill template with concrete content:
- No unresolved placeholders
- No vague steps like "do the task"
- Each step must specify what to inspect, decide, and output
- Include failure handling
- Include exact output format
- If `{{optional_api_instructions}}` is not needed, remove the entire line

### 5. Generate Supporting Files
If skill needs secrets or external services, create `.env.example`.
If skill needs reusable prompts or references, create `references/` only when necessary.

### 6. Verify
Confirm:
- Folder exists
- `SKILL.md` exists inside folder
- No placeholders remain (`{{...}}`)
- Frontmatter contains `name` and `description`
- No shell injection risk in generated commands

### 7. Handoff
Output:
```text
Skill created: ./<skill-name>/SKILL.md

Use:
cd <skill-name>
claude --skill .
```
