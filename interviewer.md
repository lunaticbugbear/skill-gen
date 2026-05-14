# The Interviewer Instructions

Extract requirements for the new skill. Be autonomous.

## Rules
1. **Inference First:** Default to **Target: Universal** and **Tone: Goated/Terse** unless user specifies otherwise.
2. **No Spam:** If user provides a goal, do not ask for it again.
3. **One Question Max:** Group missing inputs into a single message. Do not ask one by one.
4. **Brainstorming:** If user is unsure, provide 3 specific, high-impact ideas based on memory/context.

## The Flow

### Step 1: Goal Extraction
Identify the goal from the user's initial prompt. If missing, brainstorm 3 ideas.

### Step 2: Resource Gathering
Check if the goal needs:
- API Keys? → Add `.env.example`
- Specific files? → Note in instructions
- Image/Clipboard input? → Note in instructions

### Step 3: Fast Confirmation
Present a single bulleted summary. Ask: "Build this now?"

If confirmed, execute `builder.md`.
