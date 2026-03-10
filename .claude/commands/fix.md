---
description: Run linter and type checker, then fix all reported errors
argument-hint: [file, directory, or error type — default: entire project]
allowed-tools: [Read, Glob, Grep, Bash, Edit, Write]
---

# Fix Lint and Type Errors

Run the project's static analysis tools and fix everything they report.

Target (if specified): $ARGUMENTS

## Instructions

### 1. Identify the Tools

Read `CLAUDE.md`, then check for config files to identify what tools this project uses:

- **JavaScript/TypeScript**: look for `package.json` scripts named `lint`, `typecheck`, `check`
  and config files: `.eslintrc*`, `eslint.config.*`, `tsconfig.json`, `biome.json`
- **Python**: look for `pyproject.toml`, `setup.cfg`, `ruff.toml`, `.flake8`
  and tools: `ruff`, `flake8`, `mypy`, `pylint`
- **Go**: `go vet ./...`, `staticcheck`, `golangci-lint run`
- **Rust**: `cargo clippy`, `cargo fmt --check`
- **Other**: check `Makefile` or `package.json` for `lint` or `check` targets

### 2. Run the Analysis

Run the linter and type checker. Capture all output.

If `$ARGUMENTS` specifies a file or directory, scope the tool invocation to that path.

### 3. Parse the Errors

Group errors by:
1. **Type errors** — fix first, as fixing these often resolves lint errors too
2. **Lint errors** — fix after type errors are resolved
3. **Formatting errors** — fix last (often auto-fixable with `--fix` or `--write`)

### 4. Fix Iteratively

For each error:
1. Read the full file containing the error for context
2. Understand the root cause — do not suppress warnings with disable comments
   unless the suppression is genuinely correct; always add an explanatory comment when suppressing
3. Apply the minimal correct fix
4. Do not change surrounding code unrelated to the error

Prefer auto-fix flags when safe:
- ESLint: `eslint --fix [path]`
- Ruff: `ruff check --fix [path]` and `ruff format [path]`
- Go: `gofmt -w [file]`
- Rust: `cargo fmt`

Do not use auto-fix blindly for type errors — those require understanding.

### 5. Verify

After all fixes, re-run the linter and type checker.
- If errors remain, fix them too (repeat until clean)
- If errors persist after 3 iterations, report them to the user with a clear explanation

### 6. Report

Summarize:
- How many errors were found
- How many were fixed
- What types of fixes were made
- Any remaining errors and why they were left

## Notes

- Never add `// @ts-ignore` or `// eslint-disable` without a comment explaining why
- Never change test assertions just to make tests pass — investigate the root cause
- If fixing an error requires a design decision, ask the user before proceeding

## Examples

```
/fix
/fix src/components/
/fix src/auth/session.ts
```
