---
name: tk:slides
description: Generate a magazine-quality slide deck as self-contained HTML. /tk:slides [topic]
allowed-tools:
  - Read
  - Write
  - Bash
---

# /tk:slides [topic]

Generate a stunning magazine-quality slide deck as a self-contained HTML page.

**This command uses the visual-explainer skill.** Read `skills/visual-explainer/SKILL.md` and `skills/visual-explainer/references/slide-patterns.md` before generating.

---

## Usage

```bash
/tk:slides Introduction to our API
/tk:slides Q4 Technical Review
/tk:slides Architecture Overview for New Engineers
/tk:slides Product Demo for Investors
```

---

## Process

### 1. Load the Skill

```bash
cat skills/visual-explainer/SKILL.md
cat skills/visual-explainer/references/slide-patterns.md
cat skills/visual-explainer/templates/slide-deck.html
cat skills/visual-explainer/references/css-patterns.md
cat skills/visual-explainer/references/libraries.md
```

### 2. Pick Preset

**Slide-specific presets:**
- **Midnight Editorial** — dark, sophisticated, serif headlines
- **Warm Signal** — cream backgrounds, terracotta accents
- **Terminal Mono** — green/amber on black, monospace
- **Swiss Clean** — minimal, grid-based, sans-serif

Or adapt the 8 general aesthetics for slides.

### 3. Plan Narrative Arc

Slides have temporal dimension — compose a story, not a list:

1. **Impact** — Title slide (what + why it matters)
2. **Context** — Overview (set the stage)
3. **Deep dive** — Content, diagrams, data
4. **Resolution** — Summary, next steps, call to action

### 4. Slide Types (10)

| Type | Use For |
|------|---------|
| Title | Opening slide with hero visual |
| Section Divider | Major topic transitions |
| Content | Text + bullets + optional image |
| Split | Two-column comparison |
| Diagram | Mermaid flowcharts, architecture |
| Dashboard | KPIs, metrics, charts |
| Table | Data comparison, feature matrix |
| Code | Code snippets with syntax highlighting |
| Quote | Key insight, testimonial |
| Full-Bleed | Hero image background |

### 5. Compositional Variety

**CRITICAL:** Consecutive slides MUST vary spatial approach:
- Centered
- Left-heavy
- Right-heavy
- Split
- Edge-aligned
- Full-bleed

Three centered slides in a row = push one off-axis.

### 6. Visual Richness

**Proactively reach for visuals:**
- AI-generated images via `surf` (if available)
- SVG decorative accents
- Inline sparklines
- Mini-charts (Chart.js)
- Small Mermaid diagrams

Visual-first, text-second.

### 7. Deliver

```bash
mkdir -p ~/.agent/diagrams
# Write to ~/.agent/diagrams/{topic}-slides.html
# Open in browser
```

---

## Content Completeness

**Changing medium does NOT mean dropping content.**

- Inventory the source material
- Map every item to slides
- Verify coverage
- Add more slides rather than cutting content

A 22-slide deck that covers everything beats a 13-slide deck missing 40%.

---

## Forbidden

- Neon color schemes
- Inter + violet gradients
- Emoji icons
- Generic dark theme
- Scrolling within slides (each slide = 100dvh)
