# Codex AGENTS.md Template

🌏 [中文](README.md) | English

A Codex `AGENTS.md` template for Chinese-speaking users. It defines how Codex should communicate, understand context, modify code, debug problems, validate changes, and handle high-risk operations in a project.

The template defaults to **Chinese communication, Windows-friendly commands, and Python-oriented development**, but it is not tied to those choices. You can adapt the relevant sections to your own operating system, programming languages, project type, and team conventions.

This repository is built around Codex `AGENTS.md`, but the workflow principles are not limited to Codex. Users of Claude Code, Cursor, Cline, Roo Code, Gemini CLI, and similar agentic coding tools can adapt these rules to their own instruction files or project conventions.

## Who This Is For

- Users who want Codex to communicate in Chinese by default.
- Users who mainly work on Windows and prefer PowerShell-friendly commands.
- Users who often work on Python projects and want Codex to identify the interpreter, virtual environment, dependency manager, and test commands before running scripts.
- Users who want Codex to read context before changing code and avoid broad unrelated refactors.
- Users who want a clear distinction between "verified" and "theoretically should work."
- Users who want stricter boundaries around deletion, forced overwrite, Git history rewriting, configuration changes, and other high-risk operations.

## Design Goals

This template is not meant to define the only correct way to work with Codex. It is intended as a safer, clearer, and more reviewable starting point for human-Codex collaboration.

It emphasizes:

- Understand the request and project context before editing.
- Prefer the smallest necessary change.
- Follow existing project style and conventions.
- Confirm the interpreter and virtual environment before working on Python projects.
- Reproduce or understand the failure path before fixing bugs.
- Run relevant validation commands after changes whenever possible.
- Ask for explicit confirmation before high-risk operations.
- Report what changed, what was validated, and what risks remain.

## Usage

### Global Usage

Place `AGENTS.md` in the Codex configuration directory:

```powershell
Copy-Item -LiteralPath ".\AGENTS.md" -Destination "$env:USERPROFILE\.codex\AGENTS.md" -Force
```

Then restart Codex so the global rules can take effect.

### Project-Level Usage

You can also place `AGENTS.md` in the root directory of a specific project:

```powershell
Copy-Item -LiteralPath ".\AGENTS.md" -Destination "D:\your-project\AGENTS.md" -Force
```

A project-level `AGENTS.md` applies to that directory and its subdirectories. If a deeper directory contains another `AGENTS.md`, the closer file usually takes precedence for files under that directory.

## What To Customize First

Before using the template, consider reviewing these sections:

- `Default language`: whether Codex should use Chinese by default.
- `Platform and language preference`: whether Windows and Python are still your main defaults.
- `Python environment rules`: whether they match your virtual environment and dependency-management habits.
- `Validation rules`: whether you need to add your project's common test, lint, type-check, or build commands.
- `Safety rules`: whether you need additional boundaries for high-risk operations.
- `Response format`: whether the reporting format matches how you want Codex to summarize work.

If you mainly use frontend stacks, Go, Java, Rust, C++, Linux, or macOS, you can keep the overall workflow discipline and replace the technology-specific parts.

## Limitations

- This is not an official OpenAI template.
- It defaults to Chinese, Windows, and Python, so other stacks should adjust it before use.
- It cannot guarantee that every Codex action will match user expectations; important changes still need review.
- Different Codex versions or runtime environments may interpret `AGENTS.md` details differently.
- For team projects, combine this template with the project's README, contribution guide, CI configuration, and code review conventions.

## Repository Contents

```text
.
├── AGENTS.md
├── README.md
├── README_EN.md
├── LICENSE
└── .gitignore
```

## Contributing

Issues and pull requests are welcome, especially examples of how to adapt `AGENTS.md` for different programming languages, operating systems, and team workflows.

## License

MIT License
