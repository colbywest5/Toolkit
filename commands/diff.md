---
name: tk:diff
description: Generate a visual HTML diff review with architecture comparison. /tk:diff [ref] [--slides]
allowed-tools:
  - Read
  - Write
  - Bash
---

# /tk:diff [ref] [--slides]

Generate a comprehensive visual diff review as a self-contained HTML page. Before/after architecture comparison with code review analysis.

**This command uses the visual-explainer skill.** Read `skills/visual-explainer/SKILL.md` before generating.

---

## Usage

```bash
/tk:diff                    # Diff against main
/tk:diff main               # Diff against main branch
/tk:diff HEAD               # Uncommitted changes only
/tk:diff abc123             # Specific commit
/tk:diff abc123..def456     # Range between commits
/tk:diff #42                # PR number (uses gh pr diff)
/tk:diff --slides           # Generate as slide deck
```

---

## Process

### 1. Load the Skill

```bash
cat skills/visual-explainer/SKILL.md
cat skills/visual-explainer/references/css-patterns.md
cat skills/visual-explainer/references/libraries.md
cat skills/visual-explainer/prompts/diff-review.md
```

### 2. Scope Detection

Determine what to diff based on argument:

| Input | Action |
|-------|--------|
| Branch name | `git diff <branch>` |
| Commit hash | `git show <hash>` |
| `HEAD` | `git diff` + `git diff --staged` |
| PR number `#42` | `gh pr diff 42` |
| Range `a..b` | `git diff a..b` |
| No argument | Default to `main` |

### 3. Data Gathering

```bash
# File-level overview
git diff --stat <ref>
git diff --name-status <ref> --

# Line counts comparison
git show <ref>:file | wc -l
wc -l <file>

# New public API surface
# Grep for exported symbols, functions, classes

# Read all changed files in full
# Check CHANGELOG.md for entries
# Check if README/docs need updates
```

### 4. Verification Checkpoint

Before generating HTML, produce a fact sheet:
- Every quantitative figure (line counts, file counts)
- Every function, type, module referenced
- Every behavior description
- **Cite the source** for each claim

If unverified, mark as uncertain.

### 5. Generate Page Structure

1. **Executive Summary** — the *intuition*: why do these changes exist? What problem solved, what insight? Hero depth styling.

2. **KPI Dashboard** — lines added/removed, files changed, new modules, tests. Housekeeping indicators (CHANGELOG updated, docs needed).

3. **Module Architecture** — Mermaid diagram of current state with zoom controls.

4. **Feature Comparisons** — side-by-side before/after panels for significant changes.

5. **Flow Diagrams** — Mermaid for new lifecycle/pipeline/interaction patterns.

6. **File Map** — full tree with color-coded indicators (new/modified/deleted).

7. **Test Coverage** — before/after test file counts.

8. **Code Review** — Good/Bad/Ugly/Questions analysis:
   - **Good**: Solid choices, improvements, clean patterns
   - **Bad**: Bugs, regressions, missing error handling
   - **Ugly**: Tech debt, maintainability concerns
   - **Questions**: Needs clarification

9. **Decision Log** — for each significant choice:
   - Decision, Rationale, Alternatives, Confidence level
   - Green border (high), blue (medium/inferred), amber (low)

10. **Re-entry Context** — note from present-you to future-you:
    - Key invariants
    - Non-obvious coupling
    - Gotchas
    - Follow-up work needed

### 6. Deliver

```bash
mkdir -p ~/.agent/diagrams
# Write to ~/.agent/diagrams/diff-{ref}.html
# Open in browser
```

---

## Visual Language

- **Red** — removed/before
- **Green** — added/after
- **Yellow** — modified
- **Blue** — neutral context

---

## Quality Checks

- [ ] All claims verified against code
- [ ] Zoom controls on Mermaid diagrams
- [ ] Side-by-side panels handle overflow
- [ ] Both themes work
- [ ] No AI slop (Inter + violet gradients)
