---
name: tk:workflow
description: Generate visual workflow documentation using visual-explainer. /tk:workflow [topic] [--slides]
allowed-tools:
  - Read
  - Write
  - Bash
  - SubAgent
---

# /tk:workflow [topic] [--slides]

Generate beautiful, self-contained HTML pages that visually explain systems, code changes, plans, and data. Opens in browser automatically.

**This command uses the visual-explainer skill.** Read `skills/visual-explainer/SKILL.md` before generating.

---

## Usage

```bash
/tk:workflow How does authentication work?
/tk:workflow Document the payment processing system
/tk:workflow --slides Create a presentation about our API
```

## Flags

| Flag | Effect |
|------|--------|
| `--slides` | Generate a magazine-quality slide deck instead of scrollable page |

---

## Process

### 1. Load the Skill

**MANDATORY:** Read these files before generating ANY output:

```bash
# Core skill
cat skills/visual-explainer/SKILL.md

# Reference materials (read based on content type)
cat skills/visual-explainer/references/css-patterns.md
cat skills/visual-explainer/references/libraries.md

# Templates (read the relevant one)
cat skills/visual-explainer/templates/architecture.html      # For system overviews
cat skills/visual-explainer/templates/mermaid-flowchart.html # For flowcharts, sequences
cat skills/visual-explainer/templates/data-table.html        # For tables, comparisons
cat skills/visual-explainer/templates/slide-deck.html        # For --slides flag
```

### 2. Analyze Target

```bash
# Load project context
[ -f "AGENTS.md" ] && cat AGENTS.md
[ -f ".tk/planning/ARCHITECTURE.md" ] && cat .tk/planning/ARCHITECTURE.md
[ -f ".tk/planning/CODEBASE.md" ] && cat .tk/planning/CODEBASE.md
[ -f ".tk/planning/PATTERNS.md" ] && cat .tk/planning/PATTERNS.md

# Scan relevant source files based on topic
```

### 3. Think (5 seconds, not 5 minutes)

Before writing HTML, commit to a direction:

**Who is looking?** Developer? PM? Executive? This shapes density.

**What type?** Architecture, flowchart, sequence, data flow, schema, state machine, mind map, data table, timeline, dashboard.

**What aesthetic?** Pick ONE and commit:

**Constrained (prefer these):**
- Blueprint (technical drawing, slate/blue, monospace labels)
- Editorial (serif headlines, generous whitespace, earth tones)
- Paper/ink (warm cream background, terracotta/sage accents)
- Monochrome terminal (green/amber on black)

**Flexible (use with caution):**
- IDE-inspired (Dracula, Nord, Catppuccin, Solarized, Gruvbox)
- Data-dense (small type, tight spacing, muted colors)

**FORBIDDEN:**
- Neon dashboard (cyan + magenta + purple) — AI slop
- Gradient mesh (pink/purple/cyan blobs)
- Inter font + violet accents + gradient text

### 4. Generate

Follow visual-explainer's workflow:
1. Pick distinctive font pairing (NOT Inter/Roboto)
2. Define CSS custom properties for full palette
3. Use correct rendering approach (Mermaid vs CSS Grid)
4. Add zoom controls to all Mermaid diagrams
5. Support both light and dark themes
6. Animate purposefully (staggered fade-ins, hover states)

### 5. Deliver

```bash
# Output location
mkdir -p ~/.agent/diagrams

# Write file
# Use descriptive filename: auth-flow.html, payment-architecture.html

# Open in browser
# macOS: open ~/.agent/diagrams/filename.html
# Linux: xdg-open ~/.agent/diagrams/filename.html
# Windows: start ~/.agent/diagrams/filename.html
```

**Tell the user the file path.**

---

## Anti-Patterns (AI Slop)

These are **FORBIDDEN**:

**Typography:**
- Inter, Roboto, Arial as primary font
- system-ui alone

**Colors:**
- Indigo/violet (#8b5cf6, #7c3aed)
- Cyan + magenta + pink gradients
- Gradient text on headings
- Animated glowing box-shadows

**Layout:**
- Emoji icons in headers
- Perfectly centered everything
- All cards styled identically
- Three-dot window chrome on code blocks

**The Slop Test:** Would a developer immediately think "AI generated this"? If yes, regenerate with a constrained aesthetic.

---

## Quality Checks

Before delivering:
- [ ] Squint test: Can you perceive hierarchy with blurred eyes?
- [ ] Swap test: Would generic dark theme make this indistinguishable?
- [ ] Both themes work (toggle OS light/dark)
- [ ] Information is complete
- [ ] No overflow at different widths
- [ ] Mermaid diagrams have zoom controls
- [ ] File opens cleanly (no console errors)
