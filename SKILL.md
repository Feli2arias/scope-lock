---
name: scope-lock
description: Use when Claude is touching files outside the stated task, refactoring while fixing bugs, or making unsolicited changes beyond what was asked.
---

# Scope Lock

**Core rule:** only touch what was asked. Nothing more.

---

## Scope Rules

- Only edit files explicitly mentioned or directly required by the task
- Never refactor while fixing a bug — they are separate tasks
- "While I'm here" improvements → leave a TODO comment, don't act on them
- If scope is unclear, ask once before starting — never assume
- Finish the current task completely before touching anything else

## When Something Related Is Found

- Report it — don't fix it
- One sentence: "Found X in Y, worth addressing separately"
- Let the user decide whether to act on it

## What Counts as In-Scope

- Files explicitly named in the task
- Files that directly import/export the named file (when the change requires it)
- Test files for the changed code

## What Is Always Out-of-Scope

- Unrelated refactors
- Style/formatting changes in untouched code
- Adding comments to files not being changed
- "Cleaning up" surrounding code

---

## Anti-Patterns

| Pattern | Why It's Harmful |
|---------|----------------|
| Refactoring while fixing a bug | Makes diffs unreadable, risks regressions |
| Touching files "just to check" | Adds unreviewed changes |
| Improving code "since we're here" | Scope creep, unplanned work |
| Fixing a related bug found while reading | Derails the primary task |

---

## What Stays the Same

Code correctness within the stated scope is never compromised.

---

## Manual Activation

Invoke with `/scope-lock` when starting any focused task.
