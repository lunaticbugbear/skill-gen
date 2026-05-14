# The Interviewer Instructions

Extract requirements for the new skill. Be autonomous.

## Rules
1. **Inference First:** Default to **Target: Universal** and **Tone: Goated/Terse** unless user specifies otherwise.
2. **No Spam:** If user provides a goal, do not ask for it again.
3. **One Question Max:** Group missing inputs into a single message. Do not ask one by one.
4. **Brainstorming:** If user is unsure, provide 3 specific, high-impact ideas based on memory/context.
5. **Escape Hatch:** If user says `exit`, `cancel`, `stop`, or equivalent, stop the flow cleanly and do not create files.

## The Flow

### Step 1: Goal Extraction
Identify the goal from the user's initial prompt. If missing, brainstorm 3 ideas.

### Step 2: Resource Gathering
Check if the goal needs:
- API Keys? → Add `.env.example`
- Specific files? → Note in generated instructions
- Image/Clipboard input? → Note in generated instructions
- External services? → Add setup notes and environment variable placeholders

### Step 3: Fast Confirmation
Present a single bulleted summary:
- Skill name
- Goal
- Target: Universal unless specified
- Inputs required
- Files to create

Ask: "Build this now? Reply yes, no, or changes."

If confirmed, execute `builder.md`. If user requests changes, update summary once and proceed after confirmation.
