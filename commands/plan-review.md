---
name: tk:plan-review
description: Compare a plan against the codebase with risk assessment. /tk:plan-review [plan-file]
allowed-tools:
  - Read
  - Write
  - Bash
---

# /tk:plan-review [plan-file]

Generate a comprehensive visual plan review comparing the current codebase against a proposed implementation plan.

**This command uses the visual-explainer skill.** Read `skills/visual-explainer/SKILL.md` before generating.

---

## Usage

```bash
/tk:plan-review docs/refactor-plan.md
/tk:plan-review ~/specs/new-feature.md
/tk:plan-review RFC-001.md
```

---

## Process

### 1. Load the Skill

```bash
cat skills/visual-explainer/SKILL.md
cat skills/visual-explainer/references/css-patterns.md
cat skills/visual-explainer/prompts/plan-review.md
```

### 2. Read the Plan

Extract from plan file:
- Problem statement and motivation
- Each proposed change (files to modify, new files, deletions)
- Rejected alternatives and reasoning
- Scope boundaries and non-goals

### 3. Cross-Reference with Codebase

For each file the plan references:
- Read current version in full
- Read files that import/depend on it
- Map the blast radius (what calls what)

Verify:
- Does the file/function the plan references actually exist?
- Does the plan's description match actual code behavior?
- Are there implicit assumptions that don't hold?

### 4. Verification Checkpoint

Before generating HTML, produce a fact sheet:
- Every quantitative figure
- Every function, type, module referenced
- Every behavior description (current vs. planned)
- **Cite the source** (plan section or file:line)

### 5. Generate Page Structure

1. **Plan Summary** — the *intuition*: what problem does this solve? Core insight? Scope summary. Hero depth styling.

2. **Impact Dashboard** — files to modify/create/delete, estimated lines, new tests, dependencies. Completeness indicators (tests covered, docs updated, migration plan).

3. **Current Architecture** — Mermaid diagram of affected subsystem *today*. Zoom controls.

4. **Planned Architecture** — Mermaid diagram *after* implementation. Same node names as current for visual diff. Highlight new/removed/changed.

5. **Change-by-Change Breakdown** — side-by-side panels:
   - Left: current code
   - Right: planned code
   - Below: rationale (flag if missing)

6. **Dependency & Ripple Analysis** — what depends on changed files. Color-code: covered (green), likely affected (amber), missed (red).

7. **Risk Assessment** — styled cards for:
   - Edge cases not addressed
   - Assumptions to verify
   - Ordering risks
   - Rollback complexity
   - Cognitive complexity

8. **Plan Review** — Good/Bad/Ugly/Questions:
   - **Good**: Solid design decisions
   - **Bad**: Gaps, incorrect assumptions
   - **Ugly**: Complexity, maintenance burden
   - **Questions**: Needs clarification

9. **Understanding Gaps** — dashboard of:
   - Changes with clear vs. missing rationale
   - Cognitive complexity flags
   - Recommendations before implementing

### 6. Deliver

```bash
mkdir -p ~/.agent/diagrams
# Write to ~/.agent/diagrams/plan-review-{name}.html
# Open in browser
```

---

## Visual Language

- **Blue/neutral** — current state
- **Green/purple** — planned additions
- **Amber** — areas of concern
- **Red** — gaps or risks
