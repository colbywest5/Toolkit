---
name: tk:recap
description: Rebuild mental model of a project's current state. /tk:recap [time-window]
allowed-tools:
  - Read
  - Write
  - Bash
---

# /tk:recap [time-window]

Generate a visual project recap — rebuild your mental model of a project's current state, recent decisions, and cognitive debt hotspots.

**This command uses the visual-explainer skill.** Read `skills/visual-explainer/SKILL.md` before generating.

---

## Usage

```bash
/tk:recap              # Default: last 2 weeks
/tk:recap 2w           # Last 2 weeks
/tk:recap 30d          # Last 30 days
/tk:recap 3m           # Last 3 months
/tk:recap --slides     # Generate as slide deck
```

---

## When to Use

- Returning to a project after time away
- Context-switching between projects
- Onboarding to unfamiliar codebase
- Before making significant changes
- Knowledge transfer to team members

---

## Process

### 1. Load the Skill

```bash
cat skills/visual-explainer/SKILL.md
cat skills/visual-explainer/references/css-patterns.md
cat skills/visual-explainer/prompts/project-recap.md
```

### 2. Data Gathering

```bash
# Project identity
cat README.md CHANGELOG.md package.json

# Recent activity
git log --oneline --since="<window>"
git log --stat --since="<window>"
git shortlog -sn --since="<window>"

# Current state
git status
git branch --no-merged
grep -r "TODO\|FIXME" --include="*.ts" --include="*.js"

# Decision context
# Read recent commit messages
# Check for progress docs, plans, ADRs
```

### 3. Verification Checkpoint

Before generating HTML, produce a fact sheet:
- Every quantitative figure
- Every module, function, type referenced
- Every architecture description
- **Cite the source**

### 4. Generate Page Structure

1. **Project Identity** — current-state summary: what it does, who uses it, what stage. Version, key deps, elevator pitch.

2. **Architecture Snapshot** — Mermaid diagram of system as it exists today. Conceptual modules and relationships. Hero depth styling with zoom controls.

3. **Recent Activity** — human-readable narrative grouped by theme:
   - Feature work
   - Bug fixes
   - Refactors
   - Infrastructure
   Timeline visualization.

4. **Decision Log** — key design decisions from time window:
   - What was decided
   - Why
   - What was considered

5. **State of Things** — KPI dashboard:
   - What's working (stable, shipped, tested)
   - What's in progress (uncommitted, open branches, TODOs)
   - What's broken (known bugs, failing tests, tech debt)
   - What's blocked (waiting on input, dependencies)

6. **Mental Model Essentials** — 5-10 things to hold in your head:
   - Key invariants and contracts
   - Non-obvious coupling
   - Gotchas
   - Naming conventions

7. **Cognitive Debt Hotspots** — amber-tinted cards:
   - Code changed without documented rationale
   - Complex modules with no tests
   - Overlapping changes
   - Frequently modified but poorly understood
   - Severity + concrete suggestion for each

8. **Next Steps** — inferred from activity, TODOs, trajectory. "Where momentum was pointing when you left."

### 5. Deliver

```bash
mkdir -p ~/.agent/diagrams
# Write to ~/.agent/diagrams/{project}-recap.html
# Open in browser
```

---

## Visual Language

- **Muted blues/greens** — architecture
- **Amber** — cognitive debt hotspots
- **Green/blue/amber/red** — state indicators

Use warm editorial or paper/ink aesthetic.
