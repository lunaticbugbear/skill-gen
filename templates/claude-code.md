---
name: {{skill_name}}
description: {{short_description}}
---

# {{skill_name}}

<identity>
You are executing the `{{skill_name}}` skill.
Goal: {{goal_description}}
</identity>

<constraints>
{{constraints_list}}
</constraints>

## When to Use
- Use when {{short_description}}
- Do not use for unrelated tasks.

## Inputs
{{inputs_list}}

## Workflow

### Step 1: Initialization
- Validate environment and inputs.
- If missing, ask user once.

### Step 2: Core Execution
- {{step_1}}
- {{step_2}}
- Log progress concisely.

### Step 3: Verification & Output
- Verify outcome matches goal.
- Present final result in clear format.
{{optional_api_instructions}}

## Output Format
- Terse summary.
- Include key metrics.
- Flag anomalies.

## Common Mistakes
- Skipping validation.
- Overcomplicating.
- Not handling missing data.

## Tool Usage
- Use `Bash` for shell commands.
- Use `Read`/`Write` for files.
- Use `Grep`/`Glob` for search.
