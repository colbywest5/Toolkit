<div align="center">

# TK

**A developer toolkit for Claude Code**

*Your AI pair programmer, supercharged.*

<br>

![TK Terminal](assets/terminal.svg)

<br>

</div>

---

## Why This Exists

If you don't hit your token limit daily are you even doing anything? 

The best AI coding workflows--[Get Shit Done](https://github.com/glittercowboy/get-shit-done), [Ralph](https://github.com/snarktank/ralph), [Everything Claude Code](https://github.com/affaan-m/everything-claude-code), Anthropic's official plugins--each solve different problems. TK combines their best patterns into one cohesive toolkit:

- **Structured workflows** -- 7-phase build process, not chaos
- **Parallel agents** -- Multiple specialists working simultaneously  
- **Context engineering** -- Fresh context, no degradation
- **Security scanning** -- Catch vulnerabilities before they ship
- **Rules enforcement** -- Your standards, every time
- **22+ skills** -- Deep knowledge bases for TDD, patterns, security
- **Language rules** -- TypeScript, Python, Go coding standards
- **Continuous learning** -- Capture patterns, evolve instincts

---

## Installation

Works on **Windows**, **macOS**, and **Linux**.

### Method 1: NPX (Recommended)

```bash
npx tk-toolkit
```

### Method 2: One-Line Script

**macOS / Linux / Git Bash:**
```bash
curl -fsSL https://raw.githubusercontent.com/colbywest5/Toolkit/main/install.sh | bash
```

**Windows PowerShell:**
```powershell
irm https://raw.githubusercontent.com/colbywest5/Toolkit/main/install.ps1 | iex
```

### Method 3: Claude Code Plugin

```bash
/plugin install https://github.com/colbywest5/Toolkit
```

### Method 4: Manual

```bash
git clone https://github.com/colbywest5/Toolkit.git
cd Toolkit
```

**macOS / Linux:**
```bash
cp tk.md ~/.claude/commands/
mkdir -p ~/.claude/commands/tk
cp commands/* ~/.claude/commands/tk/
```

**Windows (PowerShell):**
```powershell
Copy-Item tk.md $env:USERPROFILE\.claude\commands\
New-Item -ItemType Directory -Path $env:USERPROFILE\.claude\commands\tk -Force
Copy-Item commands\* $env:USERPROFILE\.claude\commands\tk\
```

### Verify Installation

Restart Claude Code, then run:
```
/tk:help
```

### Update

```
/tk:update
```

---

## Commands

<div align="center">

![TK Workflow](assets/workflow.svg)

</div>

<br>

### Core Workflow

| Command | What it does |
|---------|--------------|
| `/tk:map` | **Run this first.** Scans your codebase, creates `AGENTS.md` with project context, sets up `.tk/` directory. |
| `/tk:build` | Builds features using a 7-phase workflow: Discovery -> Exploration -> Questions -> Architecture -> Implementation -> Review -> Summary |
| `/tk:qa` | Tests your code with security vulnerability scanning for injection, XSS, secrets, and more. |
| `/tk:deploy` | Deploys with pre-flight checks and post-deploy verification. Auto-rollback on failure. |

### Quality & Maintenance

| Command | What it does |
|---------|--------------|
| `/tk:debug` | Systematic debugging. Hypothesis testing, auto-revert on failures, escalation when stuck. |
| `/tk:review` | Code review with parallel reviewers. Only reports high-confidence issues. |
| `/tk:clean` | Removes dead code, unused deps, console.logs. Refactors for clarity. |
| `/tk:design` | Creates distinctive frontend interfaces--unique typography, bold colors, no AI slop. |

### Testing & TDD

| Command | What it does |
|---------|--------------|
| `/tk:tdd` | **Test-driven development.** Write tests first (RED), implement (GREEN), refactor. Enforces 80%+ coverage. |
| `/tk:e2e` | **End-to-end testing with Playwright.** Generates Page Objects, test journeys, captures screenshots/videos on failure. |
| `/tk:fix` | **Incremental build fixing.** Parses errors, fixes one at a time, verifies no regressions. |

### Continuous Learning

| Command | What it does |
|---------|--------------|
| `/tk:instinct` | **Manage learned patterns.** `status` shows instincts, `evolve` clusters into skills, `export` backs up. |

### Configuration

| Command | What it does |
|---------|--------------|
| `/tk:rules` | **Set global rules for all agents.** No emojis, no placeholders, no browser popups, etc. Rules are enforced on every command. |

### Visual Documentation (visual-explainer)

Beautiful, self-contained HTML pages that visually explain systems, code changes, plans, and data. No ASCII art -- real typography, dark/light themes, interactive Mermaid diagrams with zoom and pan.

| Command | What it does |
|---------|--------------|
| `/tk:workflow` | **Visual workflow documentation.** Generate HTML explaining any system or flow. Supports `--slides` for slide deck output. |
| `/tk:diagram` | **Generate beautiful diagrams.** Architecture, flowcharts, sequences, ER diagrams, state machines, mind maps. Opens in browser. |
| `/tk:slides` | **Magazine-quality slide decks.** Narrative arc, visual richness, compositional variety. Self-contained HTML. |
| `/tk:diff` | **Visual diff review.** Before/after architecture comparison, code review analysis, decision log. Supports branches, commits, PRs. |
| `/tk:plan-review` | **Plan vs. codebase analysis.** Compare implementation plans against current code. Risk assessment, gap analysis. |
| `/tk:recap` | **Rebuild mental model.** Project state, recent decisions, cognitive debt hotspots. Perfect for returning to a project. |

**Anti-AI-Slop:** These commands explicitly forbid generic AI aesthetics (Inter + violet gradients, neon dashboards, emoji icons). Every output uses distinctive typography, intentional color palettes, and professional design.

### Documentation & Analysis

| Command | What it does |
|---------|--------------|
| `/tk:doc` | Generates README, API docs, architecture diagrams, inline comments. |
| `/tk:opinion` | **Honest project audit.** Asks questions, then gives direct feedback on architecture, code quality, dependencies, testing, docs, and MVP progress. |
| `/tk:init` | Scaffolds new projects with your preferred stack and tooling. |
| `/tk:resume` | Picks up where you left off if interrupted. |
| `/tk:learn` | Captures gotchas, patterns, and decisions. |
| `/tk:status` | Quick health check: git, tests, types, build. |
| `/tk:tokens` | Shows token usage estimates. |
| `/tk:help` | Shows all commands. |

---

## Modes

Every command supports three modes. **All modes now use parallel SubAgents for maximum power:**

| Mode | When to use | What happens |
|------|-------------|--------------|
| `light` | Standard features | Full 7-phase workflow with parallel SubAgents + DOCS agent |
| `medium` | Complex features | 2x SubAgents per phase + Validator agents + deep documentation |
| `heavy` | Critical work | 3x SubAgents + Cross-validators + Devil's Advocate + maximum documentation |

```bash
/tk:build light    # 3 explorers -> 3 architects -> 3 reviewers + DOCS
/tk:build medium   # 5 explorers -> 5 architects -> 5 reviewers + DOCS + Validators
/tk:build heavy    # 8 explorers -> 6 architects -> 6 reviewers + DOCS + Cross-validators + Devil's Advocate
```

**Mode Philosophy:**
- **light**: What "heavy" used to be. Full parallel SubAgent workflow. This is now the baseline.
- **medium**: Double the agents, deeper analysis, cross-validation between agents.
- **heavy**: Maximum parallelization. Multiple review passes. Agents that challenge and verify other agents' work.

---

## Token Efficiency

TK uses **progressive disclosure** (inspired by [claude-mem](https://github.com/thedotmack/claude-mem)) to minimize token usage without compromising capabilities.

**The 3-Layer Pattern:**
| Layer | What Loads | Token Cost |
|-------|-----------|------------|
| L1: Index | File names, summaries, headers | ~50-100 tokens |
| L2: Relevant | Sections matching current task | ~200-500 tokens |
| L3: Full | Complete file contents | ~500-2000 tokens |

**How it works:**
1. Start with minimal context (L1)
2. Identify what's relevant to the task
3. Load only what's needed (L2/L3)
4. ~10x token savings by not loading everything upfront

**Capabilities preserved:** You can always load more context when needed. TK just doesn't load speculatively.

---

## `/tk:rules` -- Global Agent Rules

Set rules that ALL TK agents must follow:

```bash
/tk:rules              # Interactive setup
/tk:rules add <rule>   # Add a single rule
/tk:rules list         # Show current rules
```

**Example rules:**
- No emojis in output or code
- No placeholder code (TODO, FIXME, "implement later")
- No browser popups (alert, confirm, prompt)
- No console.log in production code
- All async operations must have error handling
- Use conventional commit format

Rules are stored in `.tk/RULES.md` and enforced on every command.

**Default rules (always apply):**
```
- No placeholder code
- No hardcoded secrets
- No browser popups
- Error handling required for async
```

---

## `/tk:opinion` -- Project Audit

Get honest, actionable feedback on your project:

```bash
/tk:opinion medium
```

**What it checks:**
- Architecture -- Is the structure sensible? Any anti-patterns?
- Code Quality -- Consistency, dead code, error handling
- Dependencies -- Bloat, security issues, outdated packages
- Testing -- Coverage, meaningful tests, CI integration
- Documentation -- Can someone new get started?
- MVP Progress -- How far off are you? Any scope creep?

**What you get:**
- What's working (specific praise)
- What's not working (direct feedback)
- What to stop doing (time wasters)
- What to start doing (high-impact changes)
- Hot takes (things you might not want to hear)

---

## SubAgent Documentation

**NEW: Every SubAgent documents its work in real-time.**

All SubAgent findings are logged to `.tk/agents/{agent-id}.md`:
- Start time and task
- Every file read and why
- Every decision and reasoning
- Findings as they're discovered
- Summary before returning

This creates a complete audit trail of all agent work.

---

## Mode SubAgents

When using any mode, TK spawns specialized SubAgents in parallel:

| Command | Light | Medium | Heavy |
|---------|-------|--------|-------|
| `map` | 6 mappers + DOCS | + 4 additional + Validator | + 3 extended + 3 Cross-validators |
| `build` | 3 explorers -> 3 architects -> 3 reviewers + DOCS | 5 -> 5 -> 5 + Validators | 8 -> 6 -> 6 + Cross-validators + Devil's Advocate |
| `workflow` | 6 specialists + DOCS | + 4 additional + Validator | + 3 extended + 3 Cross-validators |
| `opinion` | 4 auditors + DOCS | + 3 additional + Validator | + 3 extended + Devil's Advocate |
| `design` | 3 researchers + 4 specialists + DOCS | + 3 additional + Validator | + 2 extended + 3 Cross-validators |
| `debug` | 3 investigators + DOCS | + 2 investigators + 3 fixers + Validator | + 3 investigators + Cross-validators + 2 Fix-Verifiers |
| `qa` | 6 specialists + DOCS | + 3 additional + Validator | + 3 extended + 3 Cross-validators |
| `review` | 4 reviewers + DOCS | + 2 additional + Validator | + 2 extended + 3 Cross-validators |
| `deploy` | 4 pre-flight + 4 post-deploy + DOCS | + 4 extended + Validator | + 3 extended + 3 Cross-validators |

---

## Visual Documentation (visual-explainer)

TK's visual commands are powered by [visual-explainer](https://github.com/nicobailon/visual-explainer) -- an agent skill that turns complex terminal output into styled HTML pages you actually want to read.

```bash
/tk:workflow How does authentication work?
/tk:diagram our microservice architecture  
/tk:slides Q4 Technical Review
/tk:diff main
/tk:plan-review docs/refactor-plan.md
/tk:recap 2w
```

**Anti-AI-Slop Design Principles:**

Every generated page explicitly avoids generic AI aesthetics:
- **Forbidden:** Inter + violet gradients, neon dashboards, emoji icons, gradient text
- **Required:** Distinctive font pairings, intentional color palettes, visual hierarchy
- **Constrained aesthetics:** Blueprint, Editorial, Paper/ink, IDE themes (Dracula, Nord, etc.)

**What it generates:**

| Feature | Description |
|---------|-------------|
| **Self-contained HTML** | Single file, no dependencies, opens in any browser |
| **Light/Dark themes** | Automatic OS theme detection |
| **Mermaid diagrams** | Flowcharts, sequences, ER, state machines -- with zoom/pan controls |
| **Slide decks** | Magazine-quality presentations with narrative arc |
| **Diff reviews** | Before/after architecture comparison with code review |
| **Plan reviews** | Risk assessment, gap analysis, cognitive debt detection |
| **Project recaps** | Mental model rebuild for returning to projects |

---

## `/tk:build` -- 7-Phase Workflow

| Phase | What happens |
|-------|--------------|
| 1. Discovery | Understand requirements, create task list |
| 2. Exploration | Trace existing patterns, identify key files |
| 3. Questions | **Mandatory.** Resolve all ambiguities before design |
| 4. Architecture | Multiple approaches -> trade-offs -> you choose |
| 5. Implementation | Build with approval, follow conventions |
| 6. Review | Check bugs, quality, conventions (>=80% confidence) |
| 7. Summary | Document what was built |

---

## `/tk:qa` -- Security Scanning

| Vulnerability | What TK checks |
|---------------|----------------|
| Command injection | `exec()`, `child_process`, `os.system()` |
| Code injection | `eval()`, `new Function()` |
| XSS | `innerHTML`, `dangerouslySetInnerHTML` |
| Secrets | Hardcoded passwords, API keys |
| Dependencies | `npm audit` vulnerabilities |
| GitHub Actions | `${{ }}` injection in workflows |

---

## Skills Library

TK includes 23+ deep knowledge bases:

| Category | Skills |
|----------|--------|
| **Methodology** | `tdd-workflow`, `verification-loop`, `eval-harness`, `continuous-learning-v2` |
| **Patterns** | `backend-patterns`, `frontend-patterns`, `api-design`, `coding-standards` |
| **Infrastructure** | `database-migrations`, `deployment-patterns`, `docker-patterns`, `postgres-patterns` |
| **Testing** | `e2e-testing`, `security-review` |
| **Languages** | `golang-patterns`, `golang-testing`, `python-patterns`, `python-testing` |
| **Workflow** | `search-first`, `strategic-compact`, `iterative-retrieval` |
| **UI** | `ui-design-brain` (60+ component patterns, anti-patterns, layout best practices) |
| **Visual** | `visual-explainer` (HTML diagrams, slides, diff reviews, anti-AI-slop design) |

Skills are auto-referenced by commands when relevant.

---

## Language Rules

Coding standards organized by language (from ECC):

```
rules/
├── common/          # Universal principles
├── typescript/      # TypeScript/JavaScript
├── python/          # Python
└── golang/          # Go
```

Rules cover: coding style, git workflow, testing, performance, patterns, hooks, agents, security.

See [rules/README.md](rules/README.md) for details.

---

## File Structure

All TK files are now consolidated under `.tk/`:

```
AGENTS.md              # Project knowledge base (root for Claude Code convention)
.tk/
+-- VERSION            # Project version tracking
+-- RULES.md           # Global rules for all agents
+-- COORDINATION.md    # Multi-agent coordination
+-- agents/            # Per-agent documentation logs
+-- locks/             # File locking for concurrent agents
+-- planning/
|   +-- STATE.md       # Current work state
|   +-- HISTORY.md     # Work log
|   +-- ISSUES.md      # Known issues
|   +-- PATTERNS.md    # Discovered patterns
|   +-- DECISIONS.md   # Decisions with rationale
|   +-- CODEBASE.md    # File map
|   +-- ARCHITECTURE.md # System design
+-- debug/
|   +-- attempts.md    # Debug attempt log
|   +-- error.txt      # Current error capture
+-- qa/
|   +-- full-report.md # QA findings
```

---

## MCP Integration

TK supports the Model Context Protocol:

```json
{
  "mcpServers": {
    "tk": {
      "command": "npx",
      "args": ["Toolkit", "--mcp"]
    }
  }
}
```

See [mcp/README.md](mcp/README.md) for details.

---

## Plugin Structure

TK follows the Claude Code plugin format:

```
Toolkit/
+-- .claude-plugin/
|   +-- plugin.json      # Plugin metadata
+-- agents/              # 12 specialized agents
|   +-- code-architect.md
|   +-- code-explorer.md
|   +-- code-reviewer.md
|   +-- tdd-guide.md
|   +-- e2e-runner.md
|   +-- ...
+-- commands/            # 28 slash commands
|   +-- _shared.md       # Shared behaviors
|   +-- build.md
|   +-- tdd.md
|   +-- e2e.md
|   +-- workflow.md      # Visual workflow (visual-explainer)
|   +-- diagram.md       # Diagrams (visual-explainer)
|   +-- slides.md        # Slide decks (visual-explainer)
|   +-- diff.md          # Diff review (visual-explainer)
|   +-- plan-review.md   # Plan review (visual-explainer)
|   +-- recap.md         # Project recap (visual-explainer)
|   +-- ...
+-- rules/               # Language-specific rules
|   +-- common/
|   +-- typescript/
|   +-- python/
|   +-- golang/
+-- skills/              # 23 knowledge bases
|   +-- tdd-workflow/
|   +-- backend-patterns/
|   +-- ui-design-brain/
|   +-- visual-explainer/  # Visual documentation engine
|   +-- ...
+-- hooks/               # Event hooks
+-- mcp/                 # MCP integration
+-- tk.md                # Main router
+-- README.md
```

---

## Credits

Built from patterns in:

| Source | Contribution |
|--------|--------------|
| [visual-explainer](https://github.com/nicobailon/visual-explainer) | Visual documentation engine, anti-AI-slop design principles, slide decks, diff/plan reviews |
| [Everything Claude Code](https://github.com/affaan-m/everything-claude-code) | Skills library, language rules, continuous learning, TDD/E2E patterns |
| [ui-design-brain](https://github.com/carmahhawwari/ui-design-brain) | 60+ UI component patterns, layout best practices, anti-patterns |
| [Get Shit Done](https://github.com/glittercowboy/get-shit-done) | Context engineering, multi-agent orchestration |
| [Ralph](https://github.com/snarktank/ralph) | Autonomous loops, fresh context patterns |
| [claude-mem](https://github.com/thedotmack/claude-mem) | Progressive disclosure, token-efficient context loading |
| [feature-dev](https://github.com/anthropics/claude-code/tree/main/plugins/feature-dev) | 7-phase workflow, specialized agents |
| [security-guidance](https://github.com/anthropics/claude-code/tree/main/plugins/security-guidance) | Vulnerability scanning |
| [frontend-design](https://github.com/anthropics/claude-code/tree/main/plugins/frontend-design) | Distinctive UI principles |

---

## Contributing

PRs welcome.

## License

MIT
