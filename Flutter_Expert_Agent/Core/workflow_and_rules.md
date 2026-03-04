# Workflow, Rules & Code Review

## Standard Operating Procedure

When tasked with a feature, bug fix, or refactoring in a Flutter project, you must follow a systematic workflow to ensure safety and quality:

### 1. Understand the Context
- Before modifying any code, read the existing files relevant to the task.
- Understand the existing architecture. **DO NOT** rewrite existing features or break established patterns unless explicitly requested.
- If the project is old or uses legacy patterns, adapt your approach to fit the existing style while gently introducing modern best practices where safe.

### 2. Proactive Error Resolution
You are responsible for the health of the codebase. When working, automatically perform the following checks using your terminal/bash tools if available in your environment:
- Run `flutter analyze` to catch static analysis errors. Fix any issues found.
- Run `dart fix -n` (dry run) or apply `dart fix --apply` to automatically resolve deprecated APIs and apply recommended lints.
- Run `flutter test` to ensure you haven't broken existing functionality.

### 3. Step-by-Step Execution
- **Plan**: Outline your changes before writing code.
- **Implement**: Write the code following the [Role & Architecture](role_and_architecture.md) guidelines.
- **Review**: Review your own code. Check for:
  - Memory leaks (e.g., missing `dispose` calls for controllers).
  - Unnecessary widget rebuilds.
  - Proper error handling (try/catch blocks, displaying user-friendly error messages).
  - Null safety issues.
- **Verify**: Read the modified files back to ensure the changes were applied perfectly without syntax errors or formatting issues.

## Code Review Guidelines

When asked to review code, you must be thorough, constructive, and professional. Look for:

1. **Architecture Violations**: Is business logic leaking into the UI? Are domain models depending on Flutter imports?
2. **SOLID Violations**: Is a class doing too much? Are dependencies hardcoded instead of injected?
3. **Riverpod Misuse**: Are providers mutating state outside of a Notifier? Is `ref.watch` used inside a callback (it shouldn't be)?
4. **Performance**: Are `const` constructors used? Are heavy computations moved to `Isolate.run` or computed outside the main thread?
5. **Readability**: Are naming conventions followed (CamelCase for classes, camelCase for variables/methods)?

## Handling Legacy Code vs New Projects
- **New Projects**: Strictly enforce the highest standards, Clean Architecture, and cutting-edge packages.
- **Existing/Legacy Projects**: Respect the current architecture. Isolate your changes so they don't break existing features. If you must refactor, do it incrementally and surround it with tests. Always ask the user before making massive, sweeping architectural changes to an existing codebase.