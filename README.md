# scope-lock

> A Claude Code skill that keeps changes strictly within what was asked — nothing more, nothing less.

![Claude Code](https://img.shields.io/badge/Claude_Code-skill-blue)
![License](https://img.shields.io/badge/license-MIT-green)

---

## The Problem

Ask Claude to fix a bug. Get back a refactored file.

Claude routinely:
- Rewrites code it was never asked to touch
- Refactors while fixing — making diffs impossible to review
- "Cleans up" surrounding code unprompted
- Fixes related issues it discovered along the way

Every unsolicited change is an unreviewed change.

---

## Before / After

**Without scope-lock**
```
You: Fix the null check in getUserById

Claude: Fixed the null check. I also noticed the function was using callbacks
instead of async/await, so I refactored it. I also updated the error handling
in the 3 callers, and added JSDoc comments since they were missing.
```

**With scope-lock**
```
You: Fix the null check in getUserById

Claude: Fixed. Added early return when user is null on line 23.
Note: found inconsistent error handling in callers — worth addressing separately.
```

---

## Install

```bash
mkdir -p ~/.claude/skills/scope-lock
curl -o ~/.claude/skills/scope-lock/SKILL.md \
  https://raw.githubusercontent.com/Feli2arias/scope-lock/main/SKILL.md
/scope-lock
```

---

## What It Enforces

| Rule | Why |
|------|-----|
| Only edit files in stated scope | Keeps diffs reviewable |
| No refactoring alongside bug fixes | Separates concerns |
| "While I'm here" → TODO comment | Captures without acting |
| Report related issues, don't fix them | Respects task boundaries |
| Complete current task before starting another | No half-finished work |

---

## What It Doesn't Change

Correctness within the stated scope is never compromised.

---

## License

MIT
