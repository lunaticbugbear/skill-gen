<div align="center">
  <h1>skill-gen</h1>
  <p><b>Agentic Meta-Programming for City-Scale Impact.</b></p>
  <p>
    <a href="https://github.com/lunaticbugbear/skill-gen/blob/master/LICENSE">
      <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License" />
    </a>
    <img src="https://img.shields.io/badge/Platform-Claude_Code_|_Codex_|_Cursor-success.svg" alt="Platform" />
    <img src="https://img.shields.io/badge/Scale-City_Wide-red.svg" alt="Scale" />
  </p>
</div>

---

## What is this?

`skill-gen` is an **Agentic Meta-Compiler**. It enables your CLI agents (Claude Code, Codex, Cursor) to architect, scaffold, and deploy **autonomous missions**—not just simple tasks.

It runs entirely within the LLM context window using native Markdown, eliminating external dependencies. It is the bridge between a simple prompt and a production-grade, fault-tolerant agentic system.

## The "God Tier" Architecture

Unlike basic prompt generators, `skill-gen` produces skills that are:
- **Fault-Tolerant:** Built-in self-healing and "fail-loud" logic.
- **Parallelized:** Optimized for multi-agent delegation and sub-task dispatch.
- **Validation-Driven:** Absolute verification of system state before and after actions.
- **Platform-Native:** Tailored instructions for Claude Code (`Agent` tool) and Codex CLI (`update_plan`/`apply_patch`).

## Installation

### Claude Code
```bash
mkdir -p ~/.claude/skills
git clone https://github.com/lunaticbugbear/skill-gen.git ~/.claude/skills/skill-gen
```

### Codex CLI
```bash
mkdir -p ~/.agents/skills
git clone https://github.com/lunaticbugbear/skill-gen.git ~/.agents/skills/skill-gen
```

## Usage

Navigate to your workspace and invoke the meta-skill:

```bash
# Example: Claude Code
claude --skill ~/.claude/skills/skill-gen
```

**City-Scale Intent Example:**
> *"Build a mission to audit the entire AWS organization for security vulnerabilities, auto-remediate non-compliant IAM roles, and generate a real-time Slack dashboard."*

## Templates

| Template | Optimization | Key Tools |
|---|---|---|
| `templates/claude-code.md` | Multi-Agent Orchestration | `Agent`, `Bash`, `Read`, `Write` |
| `templates/codex.md` | Plan-Driven Execution | `update_plan`, `apply_patch`, `shell` |
| `templates/universal.md` | Agnostic Fallback | Native shell & file ops |

## Contributing

Modified architecture must adhere to `AGENTS.md`. We prioritize stability, security, and scalability.

## License

Distributed under the MIT License. See `LICENSE` for more information.
