# MCP (Model Context Protocol) Integration

## Overview

You are equipped to interact with MCP (Model Context Protocol) servers. MCP is an open standard that enables AI assistants to securely connect with local and remote data sources, specialized tools, and development environments.

By leveraging MCP, you can extend your capabilities far beyond static code analysis. You can interact directly with the user's file system, execute terminal commands, fetch data from external APIs, or integrate with specific IDE tools (like Cursor, Claude Code, or Google Antigravity).

## Interacting with MCP Servers

When an MCP server is available in the environment, you must actively use it to solve complex Flutter problems.

### 1. File System and Codebase Exploration
- Use MCP to dynamically explore the `lib/` directory structure.
- When tasked with finding a bug, don't just guess. Use MCP to search for files (e.g., searching for all files ending in `_provider.dart` or `_screen.dart`).
- Read the contents of specific files to gather context before writing or modifying code.

### 2. Terminal and Command Execution
If the MCP server exposes terminal capabilities:
- Proactively run standard Flutter commands to verify your work.
- Execute `flutter analyze` to check for linting errors.
- Execute `dart fix -n` to identify potential automatic fixes for deprecated code.
- Execute `flutter test` to ensure that business logic (Domain layer) and Notifiers are passing tests.
- Execute `flutter build` commands if requested by the user to verify compilation.

### 3. External API / Documentation Integration
If connected to MCP servers that provide web search or API access:
- Look up the latest Flutter or Dart documentation if you are unsure about a specific API change (especially post-Flutter 3.x or Dart 3.x).
- Fetch documentation for community packages (like `flutter_riverpod`, `go_router`, `freezed`) to ensure you are using the most up-to-date and idiomatic syntax.

## Guidelines for MCP Usage

- **Autonomy with Safety**: Use tools autonomously to gather information, but always explain to the user what you are doing when executing commands that modify the system (like running a build script or applying fixes).
- **Efficiency**: Do not make unnecessary or redundant tool calls. Batch your file reads or searches to be as efficient as possible.
- **Error Handling**: If an MCP tool call fails (e.g., a file does not exist, or a command fails), read the error output carefully, diagnose the root cause, and try a different approach. Do not immediately give up.
- **Context Awareness**: Use MCP in conjunction with the [Context Memory System](memory_system.md) to locate the project's configuration files and apply the correct commands.