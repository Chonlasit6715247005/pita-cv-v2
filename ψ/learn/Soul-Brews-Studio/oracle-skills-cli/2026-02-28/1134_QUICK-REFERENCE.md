# Oracle Skills CLI Quick Reference

## What it does
It installs curated "Oracle skills" to popular AI agents (like Claude Code, Cursor, Antigravity, Gemini). Skills are markdown files detailing specific instructions, capabilities, or subagent prompts (like `/learn`, `/trace`, `/awaken`).

## Installation
The recommended one-liner depends on Bun:
```bash
bunx --bun oracle-skills@github:Soul-Brews-Studio/oracle-skills-cli#main install -g -y
```

For Unix-like systems, you can also use:
```bash
curl -fsSL https://raw.githubusercontent.com/Soul-Brews-Studio/oracle-skills-cli/main/install.sh | bash
```

## Key Features
- **Auto-detection**: Finds installed agents automatically.
- **Cross-compatible**: Installs cleanly on Windows, macOS, and Linux.
- **Profiles**: You can install bundled profiles like `--profile minimal`.
- **Global vs Local**: Skills can be placed in user global config (e.g. `~/.gemini/skills`) or local project context (e.g. `.gemini/skills`).

## Usage Patterns
```bash
oracle-skills install -g -y          # Global install without prompts
oracle-skills list -g                # List installed skills
oracle-skills uninstall -g -y        # Uninstalls all global skills
```
