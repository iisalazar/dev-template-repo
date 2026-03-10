---
description: Stage all changes and create a conventional commit with a generated message
argument-hint: [optional message hint or scope]
allowed-tools: [Read, Bash, Glob]
---

# Smart Git Commit

Create a well-formed conventional commit for all current changes.

User's hint (if provided): $ARGUMENTS

## Instructions

1. **Inspect the current state**
   - Run `git status` to see staged and unstaged changes
   - Run `git diff` to see unstaged changes
   - Run `git diff --staged` to see already-staged changes
   - Run `git log --oneline -5` to understand recent commit style in this repo

2. **Understand what changed**
   - Read any modified files that are not self-explanatory from the diff
   - Identify the primary change type: `feat`, `fix`, `refactor`, `docs`, `test`, `chore`, `style`, `perf`, `ci`
   - Identify the scope if obvious (e.g., the module or component affected)

3. **Stage all changes**
   - Run `git add -A` to stage everything, unless the user's hint suggests partial staging
   - If the hint mentions specific files or a partial commit, stage only those

4. **Write the commit message** following [Conventional Commits](https://www.conventionalcommits.org/):
   - Format: `type(scope): short description` (72 chars max for the first line)
   - Use lowercase for type and scope
   - Use imperative mood: "add feature" not "added feature"
   - If the change is significant, add a blank line then a brief body paragraph
   - If the user provided a hint, incorporate it — prefer their wording

5. **Create the commit**
   - Run `git commit -m "[MESSAGE]"`
   - If the commit fails due to a hook, report the hook output and ask the user how to proceed
   - Never use `--no-verify` unless explicitly asked

6. **Confirm**
   - Run `git log --oneline -1` and show the user the resulting commit

## Notes

- Never use `--no-verify` unless the user explicitly requests it
- Never force-push; only commit to the current branch
- If there is nothing to commit, say so clearly and stop

## Examples

```
/commit
/commit fix the mobile nav dropdown z-index
/commit feat(auth): add OAuth2 Google login
```
