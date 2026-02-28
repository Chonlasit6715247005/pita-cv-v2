# Lesson Learned: Shell Agnostic Execution on Windows & Git Repo Nesting

**Date**: 2026-02-28
**Source**: Session Retrospective (CV V2 & SEFER Awakening)

## Pattern Discovered
When executing commands from pre-defined workflows (like Oracle Skill bash scripts) on a Windows environment utilizing PowerShell, there are significant compatibility frictions. Commands like `mkdir -p`, variable setting (`HOME=/path`), or Unix-specific string parsing (`date +%Y`) will crash and require retry cycles.

Additionally, running `/learn` which clones external repositories via `ghq` or `git clone` inside an already-initialized Git repository (`$ROOT/.git/`) causes git to register "embedded git repositories," leading to tracking and staging warnings.

## Solution / Recommended Behavior
1. **Always default to PowerShell Cmdlets explicitly** when possible on Windows hosts. (e.g. `New-Item -ItemType Directory -Force ...` instead of `mkdir -p`).
2. **For Date Parsing**: Use `$(Get-Date -Format '...')` instead of Unix `date`.
3. **For Git Nested Tracking**: To prevent "embedded git repository" warnings, ensure paths acting as cache or study areas (e.g. `ψ/learn/*`) are immediately added to `.gitignore` strictly BEFORE the first major `git add .` or commit action.

## Status
Active - Pattern ingrained into SEFER core logic.
