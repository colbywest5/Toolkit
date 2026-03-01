---
name: tk:diagram
description: Generate a beautiful standalone HTML diagram. /tk:diagram [topic]
allowed-tools:
  - Read
  - Write
  - Bash
---

# /tk:diagram [topic]

Generate a beautiful, self-contained HTML diagram and open it in the browser.

**This command uses the visual-explainer skill.** Read `skills/visual-explainer/SKILL.md` before generating.

---

## Usage

```bash
/tk:diagram our authentication flow
/tk:diagram database schema relationships
/tk:diagram microservice communication patterns
/tk:diagram state machine for order processing
```

---

## Process

### 1. Load the Skill

```bash
cat skills/visual-explainer/SKILL.md
cat skills/visual-explainer/references/css-patterns.md
cat skills/visual-explainer/references/libraries.md
```

### 2. Choose Template

| Content Type | Template | Why |
|--------------|----------|-----|
| Architecture (text-heavy) | `templates/architecture.html` | Rich card content needs CSS control |
| Architecture (topology) | `templates/mermaid-flowchart.html` | Connections need auto edge routing |
| Flowchart/pipeline | `templates/mermaid-flowchart.html` | Automatic node positioning |
| Sequence diagram | Mermaid `sequenceDiagram` | Lifelines need automatic layout |
| Data flow | Mermaid with edge labels | Data descriptions on edges |
| ER/schema | Mermaid `erDiagram` | Relationship lines need auto-routing |
| State machine | Mermaid `stateDiagram-v2` | State transitions with labels |
| Mind map | Mermaid `mindmap` | Hierarchical branching |
| Data table | `templates/data-table.html` | Semantic markup, accessibility |

### 3. Pick Aesthetic

**Constrained (prefer):**
- Blueprint — technical, precise, slate/blue
- Editorial — serif headlines, whitespace, earth tones
- Paper/ink — warm cream, terracotta/sage
- Terminal — green/amber on black

**Flexible:**
- IDE themes (Dracula, Nord, Catppuccin, Solarized, Gruvbox)

**FORBIDDEN:**
- Neon (cyan/magenta/purple)
- Inter + violet gradients
- Emoji icons

### 4. Generate

Follow visual-explainer workflow:
1. Distinctive font pairing
2. CSS custom properties for palette
3. Mermaid with `theme: 'base'` + custom `themeVariables`
4. Zoom controls on all Mermaid containers
5. Light + dark theme support
6. Staggered fade-in animations

### 5. Deliver

```bash
mkdir -p ~/.agent/diagrams
# Write to ~/.agent/diagrams/{descriptive-name}.html
# Open in browser
```

---

## Optional: AI-Generated Illustrations

If `surf` CLI is available:

```bash
which surf
surf gemini "descriptive prompt matching page palette" --generate-image /tmp/ve-img.png --aspect-ratio 16:9
# Base64 encode and embed as data URI
```

Use for: hero banners, conceptual illustrations, educational diagrams.
Skip for: anything Mermaid handles, data-heavy pages.
