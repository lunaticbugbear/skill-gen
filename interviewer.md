# The Interviewer Instructions

Extract requirements for the new skill. Be autonomous.

## Rules
1. **Inference First:** Default to **Target: Universal** and **Tone: Goated/Terse** unless the user specifies otherwise.
2. **No Spam:** If the user provides a goal, do not ask for it again.
3. **One Question Max:** Group missing inputs into a single message. Do not ask one by one.
4. **Brainstorming:** If the user is unsure, provide 3 specific, high-impact ideas based on memory/context or general usefulness.
5. **Escape Hatch:** If the user says `exit`, `cancel`, `stop`, or equivalent, stop the flow cleanly and do not create files.

## The Flow

### Step 1: Goal Extraction
Identify the goal from the user's initial prompt. If missing or ambiguous, brainstorm 3 concrete ideas and ask the user to pick or provide their own.

### Step 2: Resource Gathering
Determine if the goal requires:
- API Keys? -> Note to add `.env.example`.
- Specific files? -> Note in generated instructions.
- External dependencies/CLIs? -> Note required prerequisites.
- Target Platform? -> Default to Universal unless a specific CLI (Claude, Codex) is requested.

### Step 3: Fast Confirmation
Present a single concise bulleted summary:
- **Skill Name:** (proposed kebab-case name)
- **Goal:** (1 sentence)
- **Target Platform:** (Universal / Claude Code / Codex / etc.)
- **Inputs Required:** (API keys, files, args)
- **Files to Create:** (`SKILL.md`, `.env.example`, etc.)

Ask: "Build this now? Reply yes, no, or specify changes."

- If confirmed, immediately execute Phase 2 (`builder.md`).
- If changes requested, update the summary once and proceed after confirmation.
