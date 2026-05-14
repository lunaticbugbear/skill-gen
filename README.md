<div align="center">
  <img src="https://raw.githubusercontent.com/lunaticbugbear/skill-gen/master/assets/logo.png" alt="skill-gen logo" width="120" />
  <h1>skill-gen</h1>
  <p><b>A purely native, zero-dependency meta-compiler for AI agent skills.</b></p>
  <p>
    <a href="https://github.com/lunaticbugbear/skill-gen/blob/master/LICENSE">
      <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License" />
    </a>
    <img src="https://img.shields.io/badge/Platform-Claude_Code_|_Codex_|_OpenCode_|_Cursor-success.svg" alt="Platform" />
    <img src="https://img.shields.io/badge/Execution-Markdown_Native-red.svg" alt="Execution" />
  </p>
</div>

---

## ⚡ What is this?
`skill-gen` is a framework for **Agentic Meta-Programming**. It allows your CLI agents (like Claude Code, Codex, or Cursor) to write, isolate, and audit *other* CLI agents. 

By running entirely within the LLM's context window via native Markdown directives, it eliminates the need for Python wrappers, Node scripts, or external dependencies. It is just raw, highly optimized system instructions.

## 📦 Installation

Installation differs by harness. If you use more than one, install `skill-gen` separately for each one.

### Claude Code

Available via the official Claude plugin marketplace.

```bash
/plugin install skill-gen@claude-plugins-official
```

### Codex CLI

```bash
# Open the plugin search interface
/plugins

# Search for skill-gen
skill-gen

# Select Install Plugin
```

### Gemini CLI

```bash
gemini extensions install https://github.com/lunaticbugbear/skill-gen

# Update later:
gemini extensions update skill-gen
```

### OpenCode

OpenCode uses its own plugin install; install `skill-gen` separately even if you already use it in another harness.

Tell OpenCode:
```text
Fetch and follow instructions from https://raw.githubusercontent.com/lunaticbugbear/skill-gen/refs/heads/main/README.md
```

### Cursor

In Cursor Agent chat, install from marketplace:
```bash
/add-plugin skill-gen
```

Or search for "skill-gen" in the plugin marketplace.

### GitHub Copilot CLI

```bash
copilot plugin marketplace add lunaticbugbear/skill-gen-marketplace
copilot plugin install skill-gen@skill-gen-marketplace
```

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
claude --skill skill-gen
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
