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

## ⚡ What is this?
`skill-gen` is a framework for **Agentic Meta-Programming**. It allows your CLI agents (like Claude Code or Codex) to write, isolate, and audit *other* CLI agents. 

By running entirely within the LLM's context window via native Markdown directives, it eliminates the need for Python wrappers, Node scripts, or external dependencies. It is just raw, highly optimized system instructions.

## 📦 Installation

Since `skill-gen` is an independent, native Markdown skill, it does not rely on a centralized plugin marketplace. You install it by cloning it directly into your agent's local skills directory.

### Claude Code

```bash
# Create your local skills directory if it doesn't exist
mkdir -p ~/.claude/skills

# Clone the repository
git clone https://github.com/lunaticbugbear/skill-gen.git ~/.claude/skills/skill-gen
```

### Codex CLI

```bash
# Create your local skills directory if it doesn't exist
mkdir -p ~/.agents/skills

# Clone the repository
git clone https://github.com/lunaticbugbear/skill-gen.git ~/.agents/skills/skill-gen
```

### Cursor

Tell Cursor's Composer or Chat:
> *"Fetch and follow the skill instructions from `https://raw.githubusercontent.com/lunaticbugbear/skill-gen/refs/heads/master/SKILL.md`"*

## 🏗️ How it Works

The meta-compiler executes a deterministic pipeline within the agent's reasoning loop:

1. **Context Extraction (`interviewer.md`)**: Semantically parses user intent. If vague, it cross-references project memory to propose high-leverage automation targets.
2. **Scaffold Engine (`builder.md`)**: Sanitizes inputs (`^[a-z0-9-]+$`), instantiates an isolated workspace, and injects execution logic.
3. **Template Compilation (`templates/claude-code.md`)**: Transforms the intent into a production-grade skill, complete with input validation and execution guardrails.

## 🚀 Usage

Navigate to the directory where you want to scaffold new skills, and invoke the meta-skill:

```bash
# Example using Claude Code
cd ~/my-projects
claude --skill ~/.claude/skills/skill-gen
```

Then provide your intent:
> *"Build a skill that audits AWS IAM roles for least-privilege violations and outputs a CSV report."*

The compiler will autonomously handle the rest.

## 🛡️ Security Guardrails
- **Sanitized Execution**: All generated artifacts are regex-stripped before touching the file system.
- **Stateless Operation**: Leaves no trace outside the designated skill folder.
- **Escape Hatch**: Input `exit` or `abort` to safely terminate the compilation without mutating state.

## 🤝 Contributing
Contributions are welcome. Please ensure that modifications strictly adhere to the Markdown-native architecture. 

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'feat: Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License
Distributed under the MIT License. See `LICENSE` for more information.
