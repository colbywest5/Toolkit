---
name: tk:instinct
description: "Continuous learning: view, manage, and evolve instincts. /tk:instinct [status|evolve|export]"
allowed-tools:
  - Read
  - Write
  - Bash
  - SubAgent
---

$import(commands/tk/_shared.md)

# TK v2.0.0 | /tk:instinct [action]

Manage learned instincts from your coding sessions.

## What Are Instincts?

Instincts are patterns learned from your work:
- Coding preferences (prefer functional style)
- Project conventions (use kebab-case filenames)
- Workflow patterns (always run tests before commit)
- Error handling approaches

## Actions

### /tk:instinct status

Show current instincts with confidence scores:

```
INSTINCTS - 12 total
════════════════════

PROJECT: my-app
  WORKFLOW (3)
    ███████░░░  70%  grep-before-edit
    ████████░░  80%  test-first
    █████████░  90%  commit-often

GLOBAL (applies everywhere)
  SECURITY (2)
    █████████░  85%  validate-input
    ████████░░  80%  escape-output
```

### /tk:instinct evolve

Analyze instincts and suggest evolutions:

```
EVOLVE ANALYSIS
════════════════

SKILL CANDIDATES
  Cluster: "testing workflow"
  Instincts: 3 | Avg confidence: 82%
  → Could become: tdd-workflow skill

COMMAND CANDIDATES
  /add-migration
  From: migration-workflow instincts
  Confidence: 84%

AGENT CANDIDATES
  debugger-agent
  Covers: 4 debugging instincts
  Avg confidence: 88%
```

### /tk:instinct export

Export instincts for backup or sharing:

```bash
# Exports to .tk/instincts-export.json
```

### /tk:instinct import <file>

Import instincts from another source:

```bash
/tk:instinct import path/to/instincts.json
```

## How Instincts Are Learned

1. **Session End Hook** - Extracts patterns from session
2. **Learn Command** - Manual `/tk:learn` captures patterns
3. **Review Feedback** - Adjusts confidence based on outcomes

## Confidence Scoring

| Score | Meaning |
|-------|---------|
| 90%+ | Well-established pattern |
| 70-89% | Emerging pattern |
| 50-69% | Tentative pattern |
| <50% | Needs validation |

## Storage

```
.tk/
├── instincts/
│   ├── project/          # Project-specific
│   │   ├── workflow.md
│   │   └── conventions.md
│   └── global/           # Cross-project
│       ├── security.md
│       └── patterns.md
```

## Evolution Path

Instincts can evolve into higher structures:

```
Instincts → Skills → Commands → Agents
   (observations)  (workflows)  (reusable)  (autonomous)
```

## Integration

- `/tk:learn` - Capture patterns from current session
- `/tk:map` - Includes instincts in project context
- `/tk:build` - Applies relevant instincts during development
