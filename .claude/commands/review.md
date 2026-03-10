---
description: Review code changes for bugs, style issues, security, and correctness
argument-hint: [file/directory/focus area — default: recent uncommitted changes]
allowed-tools: [Read, Glob, Grep, Bash]
---

# Code Review

Perform a thorough code review.

Review target (if specified): $ARGUMENTS

## Instructions

### 1. Determine Scope

If `$ARGUMENTS` is provided:
- If it looks like a file path or glob, review those specific files
- If it looks like a keyword ("security", "performance", "types"), use it as a focus lens while reviewing the default scope
- If it looks like a git ref (e.g., `main`, `HEAD~3`), diff against that ref

If no arguments provided, default scope is:
- Uncommitted changes: `git diff HEAD`
- If working tree is clean: the last commit: `git diff HEAD~1 HEAD`

### 2. Gather Context

- Read the full contents of each changed file (not just the diff)
- Scan for related files (e.g., if reviewing `auth.ts`, also check `auth.test.ts`)
- Run `git log --oneline -3 [FILE]` to understand recent history of changed files

### 3. Review Criteria

Evaluate against these categories (skip any that are not applicable):

**Correctness**
- Logic errors, off-by-one errors, incorrect conditionals
- Missing error handling or unhandled promise rejections
- Race conditions or incorrect async/await usage
- Null/undefined access without guards

**Security**
- Input validation and sanitization
- SQL injection, XSS, path traversal vulnerabilities
- Hardcoded secrets, tokens, or credentials
- Overly permissive access controls

**Code Quality**
- Adherence to conventions documented in `CLAUDE.md`
- DRY violations — duplicated logic that should be extracted
- Functions/methods that are too long or do too many things
- Unclear naming that requires mental decoding

**Tests**
- Are new code paths covered by tests?
- Do tests assert meaningful behavior, or just that code runs?
- Are edge cases tested?

**Performance**
- N+1 query patterns, unnecessary re-renders, inefficient loops
- Missing indexes implied by query patterns
- Unneeded computation in hot paths

### 4. Format the Review

Structure output as:

```
## Code Review: [SCOPE DESCRIPTION]

### Summary
One paragraph overview of what the change does and overall assessment.

### Issues

#### Critical (must fix before merge)
- [FILE:LINE] — Description of issue and suggested fix

#### Warning (should fix)
- [FILE:LINE] — Description and suggested fix

#### Suggestion (optional improvement)
- [FILE:LINE] — Description

### Positive Notes
- What was done well
```

Omit severity sections with no issues. If the code is clean, say so clearly.

## Examples

```
/review
/review security
/review src/api/payments.ts
/review main
```
