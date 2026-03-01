# Rules

Language-specific coding standards and conventions from Everything Claude Code.

## Structure

```
rules/
├── common/          # Universal principles (always apply)
│   ├── coding-style.md
│   ├── git-workflow.md
│   ├── testing.md
│   ├── performance.md
│   ├── patterns.md
│   ├── hooks.md
│   ├── agents.md
│   ├── security.md
│   └── development-workflow.md
├── typescript/      # TypeScript/JavaScript
├── python/          # Python
└── golang/          # Go
```

## Installation

### Via /tk:map

When you run `/tk:map`, TK automatically detects your project's language and applies relevant rules.

### Manual Installation

```bash
# Copy common rules (always needed)
cp -r rules/common ~/.claude/rules/common

# Copy language-specific rules
cp -r rules/typescript ~/.claude/rules/typescript
cp -r rules/python ~/.claude/rules/python
cp -r rules/golang ~/.claude/rules/golang
```

**Important:** Keep directory structure intact. Don't flatten files.

## Rule Categories

| File | Purpose |
|------|---------|
| `coding-style.md` | Formatting, naming, idioms |
| `git-workflow.md` | Commits, branches, PRs |
| `testing.md` | Test patterns, coverage |
| `performance.md` | Optimization guidelines |
| `patterns.md` | Design patterns |
| `hooks.md` | Automation hooks |
| `agents.md` | When to delegate to SubAgents |
| `security.md` | Security checklist |

## Priority

Language-specific rules override common rules when they conflict.

Example: `common/coding-style.md` recommends immutability, but `golang/coding-style.md` allows idiomatic Go mutation patterns.

## Rules vs Skills

- **Rules** = Standards (what to do)
- **Skills** = Deep knowledge (how to do it)

Rules reference skills when detailed guidance is needed.
