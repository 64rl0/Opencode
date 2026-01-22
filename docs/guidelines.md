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

