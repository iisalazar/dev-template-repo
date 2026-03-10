# Project: [PROJECT_NAME]

<!-- TODO: Replace [PROJECT_NAME] with your actual project name -->

## Project Overview

<!-- TODO: 2-4 sentences describing what this project does, who uses it, and its primary purpose -->

[PROJECT_NAME] is a [TYPE_OF_APPLICATION] that [PRIMARY_PURPOSE].

Primary users: [WHO_USES_IT]

## Repository Structure

<!-- TODO: Describe the top-level directory layout. Example below — replace it. -->

```
src/          # Application source code
tests/        # Test suite
docs/         # Documentation
scripts/      # Build and utility scripts
```

## Tech Stack

<!-- TODO: List the languages, frameworks, databases, and key dependencies -->

- **Language**: [e.g., TypeScript 5.x, Python 3.12, Go 1.22]
- **Framework**: [e.g., Next.js 14, FastAPI, Gin]
- **Database**: [e.g., PostgreSQL 16, SQLite, MongoDB]
- **Key dependencies**: [List 3-5 most important libraries]

## Development Setup

<!-- TODO: Exact commands to get the project running locally -->

```bash
# Install dependencies
[INSTALL_COMMAND]   # e.g., npm install / pip install -e ".[dev]" / go mod tidy

# Run development server
[DEV_COMMAND]       # e.g., npm run dev / uvicorn main:app --reload / go run .

# Run tests
[TEST_COMMAND]      # e.g., npm test / pytest / go test ./...

# Run linter/formatter
[LINT_COMMAND]      # e.g., npm run lint / ruff check . / golangci-lint run
```

## Architecture & Key Concepts

<!-- TODO: Explain any non-obvious architectural decisions, patterns, or concepts Claude should know -->

<!--
Examples of what to put here:
- "We use event sourcing — never mutate state directly, always emit events"
- "All API responses follow the JSend spec: {status, data, message}"
- "Business logic lives exclusively in the service layer, not controllers"
- "Database migrations are code-first using [TOOL]"
-->

[ARCHITECTURE_NOTES]

## Coding Conventions

<!-- TODO: Project-specific style rules that go beyond the linter -->

<!--
Examples:
- "Use named exports only — no default exports"
- "All async functions must handle errors with try/catch, not .catch()"
- "Write tests before implementation (TDD)"
- "Commit messages follow Conventional Commits: feat/fix/chore/docs/refactor"
-->

[CODING_CONVENTIONS]

## Testing Approach

<!-- TODO: Describe testing strategy, what to test, what not to test, where tests live -->

- Test framework: [e.g., Jest, pytest, Go testing]
- Test location: [e.g., co-located `*.test.ts` files / `tests/` directory]
- Coverage target: [e.g., 80% on business logic]

[TESTING_NOTES]

## Environment & Configuration

<!-- TODO: List required environment variables (names only, not values) -->

Key environment variables:
- `[VAR_NAME]` — [what it's for]
- `[VAR_NAME]` — [what it's for]

Config file: [e.g., `.env` (gitignored), `config/settings.yaml`]

## Important Files & Entry Points

<!-- TODO: List the most important files Claude should know about -->

- `[PATH]` — [e.g., "Application entry point"]
- `[PATH]` — [e.g., "Database schema definition"]
- `[PATH]` — [e.g., "Core business logic"]
- `[PATH]` — [e.g., "API route definitions"]

## Current Focus / Active Work

<!-- TODO: Update this section regularly — what is being actively worked on? -->
<!-- This helps Claude give relevant, context-aware help. -->

[CURRENT_SPRINT_OR_FOCUS]

## Off-Limits / Do Not Touch

<!-- TODO: List files, directories, or patterns Claude should never modify -->

- [e.g., `generated/` — auto-generated, do not edit manually]
- [e.g., `legacy/` — deprecated code, do not refactor without discussion]

## External Resources

<!-- TODO: Add links to docs, design files, issue tracker, etc. -->

- Docs: [URL]
- Issue tracker: [URL]
- Design / Figma: [URL]
