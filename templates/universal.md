---
name: {{skill_name}}
description: {{short_description}}
---

# {{skill_name}}

## Overview
You are executing the {{skill_name}} skill.
**Goal:** {{goal_description}}

Act with high autonomy. Verify your assumptions before modifying files. Do not narrate your thought process unnecessarily; provide concise and actionable output.

## Constraints
- {{constraints_list}}
- **Zero-Hallucination:** Always read the current state of the workspace or target files before writing.
- **Fail-Loud:** If dependencies or required configurations are missing, stop immediately and ask the user.
- **Terse Updates:** Keep your communication short and direct. Avoid conversational filler.

## When to Use
- Use when the user requests: {{short_description}}
- Do not use this for unrelated tasks. Ensure the context matches the goal.

## Required Inputs
{{inputs_list}}
If any inputs are missing, prompt the user for them concisely before proceeding.

## Execution Workflow

### 1. Initialization and Validation
- Check for required environment variables or configuration files.
- Inspect the working directory to confirm you are in the expected location.
- Verify the existence of target files if the task involves modifying existing code.

### 2. Primary Action
- {{step_1}}
- {{step_2}}
- Execute the necessary shell commands, API calls, or file edits. Verify the result of each discrete step. If a step fails, attempt one distinct correction before halting and notifying the user.

### 3. Verification
- Verify the outcome matches the goal using objective criteria (e.g., test passing, file created, output valid).
- Do not assume success based solely on command exit codes; verify the actual state changes if possible.
{{optional_api_instructions}}

## Expected Output
Present the final result concisely:
- **Status:** [SUCCESS/FAILURE]
- **Changes Made:** [List of files edited or created]
- **Next Steps:** [If applicable, any manual actions the user needs to take]

## Common Pitfalls
- Assuming the current directory without checking.
- Using incorrect syntax for the target language or framework.
- Failing to clean up temporary files or states on failure.
