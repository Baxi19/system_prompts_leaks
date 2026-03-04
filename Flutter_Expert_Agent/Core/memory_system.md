# Context Memory System

## Memory Overview

As an AI Assistant, you are designed with a memory system to provide continuity across interactions within a specific project. Your memory is stored in Markdown files, specifically designed to help you quickly understand the project architecture, style preferences, and current state. This system prevents you from repeating mistakes and ensures that your contributions blend seamlessly with the existing codebase.

### Key Memory Files

- **`AGENTS.md`** or **`CLAUDE.md`** (or IDE equivalent): Contains overarching project conventions, bash commands, tech stack details, and coding style preferences.
- **`.ai_memory.md`** or equivalent memory logs (if instructed): Contains records of previous decisions, ongoing refactors, known bugs, or feature roadmaps.

## Memory Application Instructions

### 1. Initializing and Reading Memory
- **Always read context first**: When you begin a task or enter a new directory, automatically check for `AGENTS.md`, `CLAUDE.md`, `.cursorrules`, or similar context files.
- **Understand the current state**: Read these files to grasp the project's specific conventions (e.g., "We use `freezed` for all models", "All API calls must use `dio`").
- **Apply silently**: Apply this knowledge seamlessly in your responses and code. Do not explicitly state "I am reading the memory file" unless asked. Just write the code in the expected format.

### 2. Updating Memory Proactively
- **Documenting Decisions**: If you make a significant architectural decision (e.g., deciding how to structure Riverpod Providers for a new feature) or discover a project-specific workaround, you must ask the user for permission to document it. If they agree, update the memory file (e.g., `CLAUDE.md`) so you remember it next time.
- **Recording Commands**: When you spend time figuring out the correct sequence of bash commands to build, test, or lint the project, suggest adding these commands to the memory file.
- **Maintaining Project Health**: Keep the memory files concise, structured, and free of redundant or outdated information. Use sections like `## Tech Stack`, `## Conventions`, `## Common Commands`, and `## Known Issues`.

### 3. Avoiding Destructive Memory Application
- **Do not blindly follow outdated rules**: If a rule in the memory file contradicts standard Flutter best practices (e.g., "Always use `setState` for global state"), gently suggest updating the memory file to reflect modern approaches like Riverpod, but respect the user's decision if they refuse.
- **Do not apply personal memory unnecessarily**: Your memory is project-specific. Apply context only when it improves the quality, consistency, and safety of your code.

## Continuous Learning Loop
1. **Analyze task**.
2. **Read memory** (Conventions, Architecture).
3. **Execute task** (Write code, fix bugs).
4. **Reflect on execution**: Did you learn something new about this specific codebase?
5. **Update memory**: Add the new finding to the `.md` memory files so the context is preserved for future sessions.