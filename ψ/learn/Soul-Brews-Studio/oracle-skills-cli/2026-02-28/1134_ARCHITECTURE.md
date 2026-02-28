# Oracle Skills CLI Architecture

**Repository**: Soul-Brews-Studio/oracle-skills-cli

## Directory Structure
- `src/cli/`: Contains the core CLI logic.
  - `index.ts`: The main entry point parsing commander args.
  - `installer.ts`: Logic to copy/symlink skills to agent directories.
  - `agents.ts`: Definitions of supported AI agents and their configuration paths.
  - `fs-utils.ts`: File system utilities (supporting Bun shell execution or standard Node.js `fs`).
- `src/commands/`: Pre-defined shell command patterns for `.claude/commands`.
- `src/skills/`: The actual Oracle skills (markdown instructions and subagent prompts).
- `install.sh`: The one-liner bash script for Unix environments.

## Entry Points
- The tool acts as a CLI invoked via `bunx oracle-skills`.
- The entry file specifies `#!/usr/bin/env bun` ensuring execution through Bun.

## Core Abstractions
1. **Agents Dictionary**: `agents.ts` holds a map of supported AI editors/agents (e.g. `claude-code`, `opencode`, `gemini`, `antigravity`) with logic on how to detect if they are installed and where to place their skills.
2. **Skill Profiles**: Allows installing subset of skills (e.g., `seed`, `minimal`, `standard`, `full`).
3. **Shell Mode vs FS Mode**: The installer gracefully handles `Bun.$` for shell-based OS operations or falls back to native Node.js `fs` module, critical for cross-platform compatibility like Windows vs macOS.

## Dependencies
- `@clack/prompts`: For interactive CLI UI.
- `commander`: For argument parsing.
- Built-in Bun utilities.
