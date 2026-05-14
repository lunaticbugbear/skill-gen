<div align="center">
  <h1>skill-gen</h1>
  <p><b>A purely native, zero-dependency meta-compiler for AI agent skills.</b></p>
  <p>
    <a href="https://github.com/lunaticbugbear/skill-gen/blob/master/LICENSE">
      <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License" />
    </a>
    <img src="https://img.shields.io/badge/Platform-Claude_Code_|_Codex_|_Cursor-success.svg" alt="Platform" />
    <img src="https://img.shields.io/badge/Execution-Markdown_Native-red.svg" alt="Execution" />
  </p>
</div>

---

## What is this?

`skill-gen` is a framework for **Agentic Meta-Programming**. It allows your CLI agents (like Claude Code, Codex, or Cursor) to write, isolate, and audit *other* CLI agent skills.

By running entirely within the LLM context window via native Markdown directives, it eliminates the need for Python wrappers, Node scripts, or external dependencies. It is raw, highly optimized system instructions.

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

### Cursor

Tell Cursor Composer or Chat:
> *"Fetch and follow the skill instructions from `https://raw.githubusercontent.com/lunaticbugbear/skill-gen/refs/heads/master/SKILL.md`"*

## How it Works

The meta-compiler executes a deterministic pipeline inside the agent reasoning loop:

1. **Context Extraction (`interviewer.md`)**: Parses user intent. If vague, proposes 3 high-leverage automation targets.
2. **Scaffold Engine (`builder.md`)**: Sanitizes inputs (`^[a-z0-9-]+$`), creates an isolated workspace, selects the right template, and injects execution logic.
3. **Template Compilation**: Transforms intent into a production-grade skill with input validation and execution guardrails.
   - `templates/claude-code.md` — optimized for Claude Code (uses `Agent`, `Bash`, `Read`/`Write`, `Glob`).
   - `templates/universal.md` — agnostic template for Codex, Cursor, or any markdown-compatible agent.

## Usage

Navigate to the directory where you want to scaffold new skills, then invoke the meta-skill:

```bash
# Claude Code
cd ~/my-projects
claude --skill ~/.claude/skills/skill-gen
```

Then describe your intent:
> *"Build a skill that audits AWS IAM roles for least-privilege violations and outputs a CSV report."*

The compiler will:
1. Confirm the goal and required inputs with you in one message.
2. Create an isolated `<skill-name>/` directory.
3. Generate a complete, placeholder-free `SKILL.md` inside it.
4. Optionally create `.env.example` if secrets are needed.

## Templates

| Template | Best For | Tools Used |
|---|---|---|
| `templates/claude-code.md` | Claude Code | `Agent`, `Bash`, `Read`, `Write`, `Glob` |
| `templates/universal.md` | Codex, Cursor, any agent | Generic shell + file operations |

## Security Guardrails

- **Sanitized Execution**: All generated artifacts are regex-stripped before touching the file system.
- **Stateless Operation**: Leaves no trace outside the designated skill folder.
- **Path Traversal Defense**: All file operations are constrained to the new `<skill-name>` directory.
- **Escape Hatch**: Input `exit` or `abort` to safely terminate compilation without mutating state.

## Contributing

Contributions are welcome. Please ensure modifications strictly adhere to the Markdown-native architecture.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/my-feature`)
3. Commit your changes (`git commit -m ''feat: add my feature''`)
4. Push to the branch (`git push origin feature/my-feature`)
5. Open a Pull Request

## License

Distributed under the MIT License. See `LICENSE` for more information.
