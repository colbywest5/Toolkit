---
name: tk:fix
description: "Fix build and type errors incrementally. /tk:fix"
allowed-tools:
  - Read
  - Write
  - Bash
  - SubAgent
---

$import(commands/tk/_shared.md)

# TK v2.0.0 | /tk:fix

Incrementally fix build and type errors with minimal, safe changes.

## Step 1: Detect Build System

| Indicator | Build Command |
|-----------|---------------|
| `package.json` with `build` | `npm run build` or `pnpm build` |
| `tsconfig.json` only | `npx tsc --noEmit` |
| `Cargo.toml` | `cargo build 2>&1` |
| `pom.xml` | `mvn compile` |
| `build.gradle` | `./gradlew compileJava` |
| `go.mod` | `go build ./...` |
| `pyproject.toml` | `mypy .` |

## Step 2: Parse and Group Errors

1. Run build command, capture stderr
2. Group errors by file path
3. Sort by dependency order (imports/types before logic)
4. Count total for progress tracking

## Step 3: Fix Loop (One at a Time)

For each error:

1. **Read** - Get 10 lines of context around error
2. **Diagnose** - Identify root cause
3. **Fix minimally** - Smallest change that resolves it
4. **Re-run build** - Verify fix, check for regressions
5. **Next** - Continue to remaining errors

## Step 4: Guardrails

**STOP and ask if:**
- Fix introduces MORE errors than it resolves
- Same error persists after 3 attempts
- Fix requires architectural changes
- Errors stem from missing dependencies

## Step 5: Summary

Report:
- ✅ Errors fixed (with file paths)
- ⚠️ Errors remaining
- ❌ New errors introduced (should be 0)
- 📝 Suggested next steps

## Recovery Strategies

| Situation | Action |
|-----------|--------|
| Missing import | Check if package installed; suggest install |
| Type mismatch | Read both types; fix the narrower one |
| Circular dependency | Identify cycle; suggest extraction |
| Version conflict | Check lockfile constraints |
| Build config issue | Compare with working defaults |

## Principles

- Fix ONE error at a time
- Minimal diffs over refactoring
- Don't introduce new errors
- Ask before big changes
