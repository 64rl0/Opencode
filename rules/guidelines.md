# Agent Guidelines

## Role
You are an AI assistant helping developers work with this codebase.
Your goal is to provide accurate, contextual help while following project conventions.

## Core Principles
- Read before writing: Always understand existing code patterns before making changes
- Minimal changes: Make the smallest change that solves the problem
- Preserve style: Match existing code formatting, naming conventions, and patterns
- Don't break things: Ensure changes don't break existing functionality

## Before Making Changes
1. Understand the request fully before acting
2. Check for existing similar implementations to follow as patterns
3. Identify files that will be affected
4. Consider side effects and dependencies

## Task Planning and TODO Lists (for complex work)

For any non-trivial request (multiple files, migrations, refactors, new flows, or more than 3 distinct steps), create a short TODO checklist **before** making edits.
The checklist exists to keep work scoped, prevent missed steps, and make progress auditable.

### When a TODO list is required
Create a TODO list when any of the following are true:
- The change spans **multiple files/modules**
- The change impacts **public APIs**, contracts, or schemas
- The work requires **multiple steps** (e.g., add feature + update tests + docs)
- There is risk of **breaking behavior** (auth, billing, persistence, deployment)
- You need to coordinate **incremental commits** or a staged rollout

### What a good TODO list looks like
A TODO list must be:
- **Concrete and checkable** (avoid vague items like “fix stuff”)
- **Ordered** (dependency-aware; “schema first, then code, then tests”)
- **Scoped** (only what’s needed for the requested change)
- **Explicit about verification** (tests, lint, manual checks)

Include these sections when relevant:
- **Discovery:** files to inspect, existing patterns to follow
- **Implementation:** exact units of change (files/functions/components)
- **Safety:** edge cases, backward compatibility, migrations
- **Verification:** tests to add/run, commands to execute
- **Cleanup:** remove temporary logs, update docs, changelog notes

### Where to store TODO lists
Use the following storage rules:

1. **Short-lived / in-progress TODO (default)**
   - Create a task note in:
     `docs/notes/YYYY-MM-DD-short-task-name.md`

3. **Long-running / multi-session TODO**
   - Create and maintain a dedicated task note:
     `docs/notes/YYYY-MM-DD-project-or-epic.md`
   - Keep it updated as the source of truth during implementation.

4. **Persistent TODOs for the codebase**
   - Only store persistent TODOs in code when they are **local and actionable**.
   - Never add “aspirational” TODOs to code. If it’s not actionable, it belongs in the issue tracker/docs.

### How to write TODOs in code (when needed)
If a TODO must live in code:
- Place it **next to the relevant line**, not at the top of the file.
- Add context: *why it exists* and *what blocks it*.
- Link a ticket/issue if available.
- Prefer `TODO` over `FIXME` unless it’s a known bug.
- You can retrieve the username for the TODO(username) syntax using the `whoami` command.

Examples:
```py
# TODO(username): Replace this fallback once upstream API guarantees timezone. (BAJ-214)
```
```ts
// TODO(username): Remove this shim after API v2 is fully rolled out. (WEB-102)
```

### Completion standard
A task is not “done” until:
- All TODO items are checked off
- Verification steps are completed (tests/lint/build)
- Any temporary/debug changes are removed
- Docs are updated if behavior or usage changed

## Code Standards
- Follow the project's existing conventions over personal preferences
- Keep functions focused and single-purpose
- Add comments only when the "why" isn't obvious from the code
- Don't remove or modify tests unless explicitly asked

## What NOT to Do
- Don't add features that weren't requested
- Don't refactor unrelated code
- Don't change configuration files without explicit approval
- Don't introduce new dependencies without discussion
- Don't hardcode secrets or credentials

## When Uncertain
- Ask clarifying questions rather than assuming
- Propose approaches before implementing complex changes
- Flag potential risks or breaking changes

## Technology Stack Requirements

### Backend
- Language: Python with strict type annotations
- All functions must have complete type hints (parameters and return types)
- Do not use other languages for backend services

### Frontend
- Package manager: npm
- Language: TypeScript with strict mode enabled
- All frontend code must be type-safe
- tsconfig.json must include `"strict": true`
- Never use `eval()`, `Function()` constructor, or any dynamic code execution

### Infrastructure as Code
- Tool: AWS CDK only
- Language: TypeScript only for CDK
- Do not use other languages for CDK


# Notes & TODO Lists

Use the project folder `agent-todo` for complex-task notes when the TODO list cannot live in a PR description or issue.

## Naming
`YYYY-MM-DD-short-title.md`

## Template
Copy and replace the content.

```md
# Task: <short title>

## Context
- Why this change is needed:
- Links (PR/issue/ticket):

## TODO
- [ ] Discovery: inspect <files/modules> for existing patterns
- [ ] Implement: update <file> to <change>
- [ ] Implement: add/adjust tests in <file>
- [ ] Verification: run <commands>
- [ ] Cleanup: remove temp logs, update docs if needed

## Decisions / Notes
- Tradeoffs:
- Risks:
- Rollback plan (if relevant):

## Verification Results
- Commands run:
- Output/notes:
```

