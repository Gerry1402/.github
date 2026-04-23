# Git Commit Message Instructions for GitHub Copilot

When generating or suggesting Git commit messages, strictly follow the seven rules
defined by Chris Beams in https://chris.beams.io/git-commit/. These rules are
explained and justified below.

---

## The Seven Rules

### 1. Separate subject from body with a blank line

Always leave an empty line between the subject line and the body (if a body is
needed). Git uses this blank line to distinguish the title from the description.
Tools like `git log --oneline`, `git shortlog`, and `git rebase` rely on this
separator to function correctly.

If the change is trivial and self-explanatory, a subject-only message is fine:

```
Fix typo in README
```

If context is needed, add a blank line and then the body:

```
Derezz the master control program

MCP turned out to be evil and had become intent on world domination.
This commit throws Tron's disc into MCP (causing its deresolution)
and turns it back into a chess game.
```

### 2. Limit the subject line to 50 characters

Keep the subject line at or under 50 characters. This is not a hard limit but a
strong recommendation to ensure readability. 72 characters is the absolute
maximum — GitHub truncates anything beyond that with an ellipsis.

A short subject forces clarity: if summarizing is difficult, the commit is
probably doing too many things at once (consider splitting it).

- ✅ `Add input validation to login form`
- ❌ `Added some input validation and also fixed a couple of bugs in the login form and refactored some code`

### 3. Capitalize the subject line

Always begin the subject line with a capital letter.

- ✅ `Refactor authentication module`
- ❌ `refactor authentication module`

### 4. Do not end the subject line with a period

Trailing punctuation adds no value and wastes the limited space available in the
subject line.

- ✅ `Remove deprecated API methods`
- ❌ `Remove deprecated API methods.`

### 5. Use the imperative mood in the subject line

Write the subject line as if giving a command or instruction. This matches the
convention Git itself uses when generating automatic commit messages (e.g.,
`Merge branch 'feature'`, `Revert "Add the thing"`).

A simple test: the subject line must complete this sentence naturally:

> *"If applied, this commit will **[your subject line]**"*

Examples that pass the test:
- `Fix failing unit tests` → *If applied, this commit will fix failing unit tests* ✅
- `Update getting started documentation` ✅
- `Release version 2.0.0` ✅

Examples that fail the test:
- `Fixed failing unit tests` ❌ (past tense)
- `Fixing failing unit tests` ❌ (present participle)
- `More fixes for broken stuff` ❌ (vague, not imperative)

> Note: the imperative mood applies **only to the subject line**. The body can be
> written in any natural style.

### 6. Wrap the body at 72 characters

Git does not wrap text automatically. Manually wrap each line in the body at
72 characters so that the output of `git log` remains readable in terminals and
other tools, which typically indent text and work best within an 80-character
display width.

### 7. Use the body to explain *what* and *why*, not *how*

The body should explain the **reason** for the change and **what** problem it
solves — not the implementation details. The code itself explains *how* the
change was made. If the *how* needs explanation, source comments are the right
place for it.

Focus on:
- What was wrong before this change
- Why this change was necessary
- Any side effects or non-obvious consequences

---

## Full Template

```
Short imperative summary, 50 chars or less

More detailed explanation if necessary. Wrap lines at 72 characters.
Explain the problem this commit solves. Focus on WHY, not HOW.
Mention side effects or non-obvious consequences if relevant.

Further paragraphs come after blank lines.

- Bullet points are acceptable
- Use a hyphen or asterisk, preceded by a single space

If you use an issue tracker, reference issues at the bottom:

Resolves: #123
See also: #456, #789
```

---

## Quick Reference

| Rule | Requirement |
|------|-------------|
| Subject / body separator | Blank line between them |
| Subject length | ≤ 50 chars (72 absolute max) |
| Subject capitalization | First letter uppercase |
| Subject punctuation | No trailing period |
| Subject mood | Imperative ("Fix", "Add", "Remove"…) |
| Body line length | ≤ 72 characters |
| Body content | What and why, not how |

---

## Common Imperative Verbs to Start the Subject Line

`Add` · `Fix` · `Remove` · `Update` · `Refactor` · `Rename` · `Move` ·
`Revert` · `Merge` · `Release` · `Improve` · `Extract` · `Replace` ·
`Simplify` · `Document` · `Test` · `Enable` · `Disable` · `Expose` · `Hide`
