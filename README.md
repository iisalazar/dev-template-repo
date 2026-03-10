# Claude Code Template

A ready-to-use template for configuring [Claude Code](https://claude.ai/code) in any project.
Clone or copy this template when starting a new project to get Claude Code working well from day one.

## What's Included

| File | Purpose |
|------|---------|
| `CLAUDE.md` | Project context Claude reads every session |
| `.claude/settings.json` | Permissions and hooks committed to git |
| `.claude/commands/commit.md` | `/commit` — smart conventional git commit |
| `.claude/commands/review.md` | `/review` — structured code review |
| `.claude/commands/fix.md` | `/fix` — run linter + type checker, fix all errors |
| `.claude/memory/MEMORY.md` | Persistent memory scratchpad across sessions |
| `.gitignore` | Ignores local-only Claude settings and secrets |

## Quick Start

### Option A: Use as a GitHub Template

Click **"Use this template"** on GitHub, then clone your new repo.

### Option B: Clone and reset git history

```bash
git clone https://github.com/[YOUR_USERNAME]/dev-template-repo my-project
cd my-project
rm -rf .git
git init
```

### Option C: Copy configuration into an existing project

```bash
# From the root of your existing project:
git clone https://github.com/[YOUR_USERNAME]/dev-template-repo /tmp/claude-template
cp /tmp/claude-template/CLAUDE.md .
cp -r /tmp/claude-template/.claude .
# Merge .gitignore entries manually as needed
```

## Setup Checklist

After cloning, complete these steps before your first Claude session:

- [ ] **Edit `CLAUDE.md`** — Replace all `[PLACEHOLDER]` sections with real project info.
      The more context you provide, the better Claude's responses will be.
- [ ] **Review `.claude/settings.json`** — Expand the `allow` list for tools your workflow needs
      (e.g., `"Bash(npm run*)"`, `"Bash(pytest*)"`, `Edit`, `Write`).
- [ ] **Add project-specific ignore patterns** to `.gitignore` if needed (e.g., `dist/`, `__pycache__/`).
- [ ] **Customize slash commands** in `.claude/commands/` if your workflow differs.

## Slash Commands

Once set up, these are available in any Claude Code session:

### `/commit [hint]`

Inspects all changes, writes a [Conventional Commit](https://www.conventionalcommits.org/) message, and commits.

```
/commit
/commit fix login redirect after OAuth
/commit feat(auth): add Google SSO
```

### `/review [target]`

Reviews code for correctness, security, quality, and test coverage.
Target can be a file path, directory, keyword ("security"), or git ref.

```
/review
/review security
/review src/api/payments.ts
/review main
```

### `/fix [target]`

Detects the project's linter and type checker, runs them, and fixes all errors.

```
/fix
/fix src/components/
/fix src/auth/session.ts
```

## Permissions

`.claude/settings.json` ships with a conservative `allow` list (read-only tools + git inspection).
Expand it as you get comfortable with Claude's behavior:

```json
{
  "permissions": {
    "allow": [
      "Read", "Glob", "Grep", "Edit", "Write",
      "Bash(npm run*)",
      "Bash(git status)", "Bash(git diff*)", "Bash(git log*)"
    ],
    "deny": [
      "Bash(rm -rf *)",
      "Bash(git push --force*)"
    ]
  }
}
```

### Local overrides

Create `.claude/settings.local.json` for personal settings that should **not** be committed
(e.g., more permissive tool access on your own machine). This file is already gitignored.

## Memory

`.claude/memory/MEMORY.md` is a scratchpad Claude can read and write across sessions.
Use it for:

- Decisions made and why ("Chose X over Y because...")
- Patterns to follow or avoid
- Domain knowledge and terminology
- In-progress notes during long multi-session features

## License

MIT
