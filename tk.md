---
name: tk
description: "Universal work command. Usage: /tk:task mode [message]"
allowed-tools:
  - Read
  - Write
  - Bash
  - SubAgent
  - AskUserQuestion
  - WebSearch
  - WebFetch
---

# /tk:task mode [message]

**Tasks:** map, build, design, debug, qa, review, clean, doc, workflow, diagram, slides, diff, plan-review, recap, deploy, init, resume, learn, status, tdd, e2e, fix, instinct, help
**Modes:** light (fast), medium (balanced), heavy (comprehensive + parallel SubAgents)

## Parse & Route

1. Extract TASK (first word), MODE (second), MESSAGE (rest)
2. If TASK=help → show help below
3. If TASK=status → run status (no mode needed)
4. Otherwise → Read `commands/_shared.md` for core behaviors, then read `commands/{TASK}.md`

## Help Reference

```
/tk:task mode [message]

CORE TASKS:
  map        Map project, create context (RUN FIRST)
  build      Build/create something
  design     Create distinctive frontend interfaces
  debug      Fix a problem  
  qa         Test something
  review     Review code
  clean      Cleanup codebase
  doc        Generate documentation
  deploy     Deploy to production
  init       Initialize new project
  resume     Resume previous work
  learn      Capture a learning
  status     Show project status

VISUAL (visual-explainer):
  workflow   Visual workflow docs (SVG diagrams + analysis)
  diagram    Generate beautiful standalone HTML diagrams
  slides     Generate magazine-quality slide decks
  diff       Visual diff review with architecture comparison
  plan-review Compare a plan against codebase with risk assessment
  recap      Rebuild mental model of project state

TESTING:
  tdd        Test-driven development workflow
  e2e        End-to-end testing with Playwright
  fix        Fix build/type errors incrementally

LEARNING:
  instinct   Continuous learning (status/evolve/export)
  help       This help

MODES:
  light      Fast, minimal interaction
  medium     Balanced, key decisions
  heavy      Comprehensive, parallel SubAgents + DOCS

EXAMPLES:
  /tk:map heavy This is a Next.js e-commerce app
  /tk:build medium Add user authentication
  /tk:design heavy Landing page for a premium fitness app
  /tk:debug light API returns 500 on large requests
  /tk:qa heavy Test everything before launch
  
  VISUAL EXAMPLES:
  /tk:workflow How does authentication work?
  /tk:diagram our microservice architecture
  /tk:slides Q4 Technical Review
  /tk:diff main
  /tk:diff #42
  /tk:plan-review docs/refactor-plan.md
  /tk:recap 2w
  /tk:recap 30d --slides
```
