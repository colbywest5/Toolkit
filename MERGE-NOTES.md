# Merge Notes: Toolkit + Everything Claude Code

**Date:** March 2026  
**Master:** Toolkit (colbywest5/Toolkit)  
**Merged:** everything-claude-code (affaan-m/everything-claude-code) + ui-design-brain

---

## Summary

This merge preserves Toolkit's architecture and `/tk:` namespace while incorporating the best components from Everything Claude Code (ECC). The result is a unified toolkit with:

- **21+ commands** (original 18 + 4 new from ECC)
- **22 skills** (15 from ECC + 7 original)
- **12 agents** (5 original + 7 from ECC)
- **29 rules** organized by language (from ECC)

---

## What Was Kept

### From Toolkit (Master)

| Component | Reason |
|-----------|--------|
| `/tk:` namespace | Core identity, stays as-is |
| 7-phase build workflow | Superior structured approach |
| Mode system (light/medium/heavy) | Excellent scaling pattern |
| SubAgent documentation pattern | `.tk/agents/{id}.md` logging |
| Install methods (npx, scripts, plugin) | User-friendly installation |
| `.tk/` directory structure | Clean state management |
| Original commands (18) | All preserved |
| Original agents (5) | All preserved |

### From Everything Claude Code

| Component | Files | Reason |
|-----------|-------|--------|
| **Language Rules** | 29 | Comprehensive coding standards |
| `rules/common/` | 9 files | Universal principles |
| `rules/typescript/` | 5 files | TS/JS patterns |
| `rules/python/` | 5 files | Python patterns |
| `rules/golang/` | 5 files | Go patterns |
| **Core Skills** | 15 | Deep knowledge bases |
| `tdd-workflow` | | TDD methodology |
| `security-review` | | Security checklist |
| `coding-standards` | | Universal standards |
| `backend-patterns` | | API/DB/caching patterns |
| `frontend-patterns` | | React/Next.js patterns |
| `api-design` | | REST API design |
| `database-migrations` | | Prisma/Drizzle/Django |
| `deployment-patterns` | | CI/CD, Docker, rollbacks |
| `e2e-testing` | | Playwright patterns |
| `verification-loop` | | Continuous verification |
| `continuous-learning-v2` | | Instinct-based learning |
| `iterative-retrieval` | | Progressive context |
| `eval-harness` | | Eval-driven development |
| `strategic-compact` | | Context management |
| `search-first` | | Research-before-coding |
| **Language Skills** | 6 | Framework-specific |
| `golang-patterns` | | Go idioms |
| `golang-testing` | | Go testing patterns |
| `python-patterns` | | Python idioms |
| `python-testing` | | pytest patterns |
| `docker-patterns` | | Container patterns |
| `postgres-patterns` | | PostgreSQL optimization |
| **Specialized Agents** | 7 | |
| `tdd-guide` | | TDD enforcement |
| `e2e-runner` | | Playwright E2E |
| `database-reviewer` | | DB/Supabase review |
| `python-reviewer` | | Python code review |
| `go-reviewer` | | Go code review |
| `build-error-resolver` | | Build fix specialist |
| `refactor-cleaner` | | Dead code removal |

### From ui-design-brain

| Component | Files | Reason |
|-----------|-------|--------|
| `ui-design-brain` skill | 4 files | UI component knowledge |
| `components.md` | 45KB | Comprehensive UI reference |
| `SKILL.md` | | Usage instructions |

---

## What Was Added (New Commands)

| Command | Purpose | Based On |
|---------|---------|----------|
| `/tk:tdd` | Test-driven development | ECC /tdd |
| `/tk:e2e` | End-to-end testing | ECC /e2e |
| `/tk:fix` | Build error fixing | ECC /build-fix |
| `/tk:instinct` | Continuous learning | ECC instinct-* commands |

---

## What Was Skipped

### From ECC (and why)

| Component | Files | Reason |
|-----------|-------|--------|
| `/plan` command | 1 | Overlaps with `/tk:build` Phase 1-4 |
| `/orchestrate` command | 1 | Overlaps with SubAgent pattern |
| `/multi-*` commands | 5 | PM2-specific, not universal |
| `/pm2` command | 1 | Too niche |
| `/sessions` command | 1 | Low value for most users |
| `/skill-create` command | 1 | Requires external service |
| `/promote`, `/projects` | 2 | Internal ECC tooling |
| `planner.md` agent | 1 | Overlaps with Toolkit flow |
| `architect.md` agent | 1 | Overlaps with code-architect |
| `chief-of-staff.md` | 1 | Overlaps with Toolkit patterns |
| `doc-updater.md` | 1 | Overlaps with docs-agent |
| Cross-platform configs | ~200 | `.cursor/`, `.opencode/`, `.codex/` |
| Translation files | ~100 | zh-CN, zh-TW, ja-JP READMEs |
| Test files | ~500 | Internal test suite |
| Example configs | ~50 | `examples/` directory |
| Docs directory | ~30 | `docs/` (guides are external) |
| Node modules | ~2000 | Dependencies |
| MCP configs | 14 | Project-specific servers |
| Niche skills | ~30 | Django, Spring Boot, Swift, etc. |

### Reasoning

1. **Overlap with Toolkit's 7-phase workflow:** ECC's `/plan` command essentially does Phases 1-4 of `/tk:build`. Keeping both would confuse users.

2. **PM2/Multi-agent commands:** These are specific to PM2 service management. Most projects don't need them.

3. **Cross-platform adapters:** `.cursor/`, `.opencode/`, `.codex/` configs add complexity. Users who need them can reference ECC directly.

4. **Niche framework skills:** Django, Spring Boot, Swift patterns are valuable but add bulk. Added the most universal ones (Python, Go basics).

5. **Test files & examples:** Internal to ECC development, not needed in production toolkit.

---

## File Count Comparison

| Source | Original | Merged |
|--------|----------|--------|
| Toolkit | ~50 | (base) |
| ECC | 3,264 | ~100 selected |
| ui-design-brain | 4 | 4 |
| **Total** | 3,318 | ~154 |

**Reduction:** ~95% file reduction while keeping ~80% of useful functionality.

---

## Directory Structure (After Merge)

```
Toolkit-merged/
├── .claude-plugin/       # Plugin manifest
├── .github/              # Workflows
├── agents/               # 12 agents (5 original + 7 ECC)
│   ├── code-architect.md
│   ├── code-explorer.md
│   ├── code-reviewer.md
│   ├── docs-agent.md
│   ├── security-auditor.md
│   ├── tdd-guide.md      # NEW from ECC
│   ├── e2e-runner.md     # NEW from ECC
│   ├── database-reviewer.md  # NEW
│   ├── python-reviewer.md    # NEW
│   ├── go-reviewer.md        # NEW
│   ├── build-error-resolver.md  # NEW
│   └── refactor-cleaner.md      # NEW
├── assets/               # SVG assets
├── bin/                  # CLI entry point
├── commands/             # 22 commands
│   ├── _shared.md
│   ├── build.md
│   ├── clean.md
│   ├── debug.md
│   ├── deploy.md
│   ├── design.md
│   ├── doc.md
│   ├── help.md
│   ├── init.md
│   ├── learn.md
│   ├── map.md
│   ├── opinion.md
│   ├── qa.md
│   ├── resume.md
│   ├── review.md
│   ├── rules.md
│   ├── status.md
│   ├── sync.md
│   ├── tokens.md
│   ├── update.md
│   ├── version.md
│   ├── workflow.md
│   ├── tdd.md            # NEW from ECC
│   ├── e2e.md            # NEW from ECC
│   ├── fix.md            # NEW from ECC
│   └── instinct.md       # NEW from ECC
├── hooks/                # Event hooks
├── mcp/                  # MCP integration
├── rules/                # NEW: Language rules from ECC
│   ├── README.md
│   ├── common/           # 9 universal rules
│   ├── typescript/       # 5 TS rules
│   ├── python/           # 5 Python rules
│   └── golang/           # 5 Go rules
├── scripts/              # Install scripts
├── skills/               # 22 skills (7 original + 15 ECC)
│   ├── api-design/
│   ├── backend-patterns/
│   ├── coding-standards/
│   ├── continuous-learning-v2/
│   ├── database-migrations/
│   ├── deployment-patterns/
│   ├── docker-patterns/
│   ├── e2e-testing/
│   ├── eval-harness/
│   ├── frontend-patterns/
│   ├── golang-patterns/
│   ├── golang-testing/
│   ├── iterative-retrieval/
│   ├── postgres-patterns/
│   ├── python-patterns/
│   ├── python-testing/
│   ├── search-first/
│   ├── security-review/
│   ├── strategic-compact/
│   ├── tdd-workflow/
│   ├── ui-design-brain/  # From separate repo
│   └── verification-loop/
├── tk.md                 # Main router
├── README.md
├── MERGE-NOTES.md        # This file
├── CHANGELOG.md
├── CONTRIBUTING.md
├── LICENSE
└── package.json
```

---

## Migration Guide

### For Toolkit Users

Nothing changes. All your existing commands work. New commands available:
- `/tk:tdd` - Test-driven development
- `/tk:e2e` - Playwright E2E testing
- `/tk:fix` - Build error fixing
- `/tk:instinct` - Continuous learning

### For ECC Users

| ECC Command | Toolkit Equivalent |
|-------------|-------------------|
| `/plan` | `/tk:build` (Phases 1-4) |
| `/tdd` | `/tk:tdd` |
| `/e2e` | `/tk:e2e` |
| `/build-fix` | `/tk:fix` |
| `/code-review` | `/tk:review` |
| `/refactor-clean` | `/tk:clean` |
| `/instinct-status` | `/tk:instinct status` |
| `/evolve` | `/tk:instinct evolve` |
| `/learn` | `/tk:learn` |
| `/verify` | `/tk:qa` |

---

## Future Considerations

1. **More Skills:** Add remaining ECC skills as needed (Django, Spring Boot, etc.)
2. **Cross-Platform:** If needed, can add `.cursor/` adapter later
3. **MCP Configs:** Project-specific MCP can be added to `.tk/mcp/`
4. **Swift Rules:** Can add `rules/swift/` from ECC when needed

---

## Credits

- **Toolkit:** [colbywest5/Toolkit](https://github.com/colbywest5/Toolkit)
- **Everything Claude Code:** [affaan-m/everything-claude-code](https://github.com/affaan-m/everything-claude-code)
- **ui-design-brain:** UI component knowledge base

Both projects under MIT license. This merge combines their best features.
