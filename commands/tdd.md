---
name: tk:tdd
description: "Test-driven development workflow. /tk:tdd mode <what to build>"
allowed-tools:
  - Read
  - Write
  - Bash
  - SubAgent
  - AskUserQuestion
---

$import(commands/tk/_shared.md)

# TK v2.0.0 | /tk:tdd [mode]

Enforce test-driven development methodology for $MESSAGE.

## TDD Cycle

```
RED → GREEN → REFACTOR → REPEAT

RED:      Write a failing test
GREEN:    Write minimal code to pass
REFACTOR: Improve code, keep tests passing
REPEAT:   Next feature/scenario
```

## Process

### Phase 1: Scaffold Interfaces
**Goal:** Define types/interfaces before implementation

**ALL MODES:** Read existing patterns, create interface definitions

```typescript
// Define input/output types FIRST
export interface InputType {
  // ...
}
export function featureName(input: InputType): OutputType {
  throw new Error('Not implemented')
}
```

### Phase 2: Write Failing Tests (RED)
**Goal:** Tests must fail because code doesn't exist yet

**LIGHT:** 3-5 test cases (happy path + edge cases)
**MEDIUM:** 6-10 test cases (+ error scenarios)
**HEAVY:** 10+ test cases (comprehensive coverage)

```bash
# Verify tests FAIL before implementing
npm test -- path/to/file.test.ts
```

### Phase 3: Implement (GREEN)
**Goal:** Write MINIMAL code to make tests pass

- Don't over-engineer
- Just make tests pass
- Ugly code is fine at this stage

```bash
# Verify tests PASS
npm test -- path/to/file.test.ts
```

### Phase 4: Refactor
**Goal:** Improve code while keeping tests green

- Extract constants
- Improve naming
- Add helper functions
- Remove duplication

```bash
# Verify tests STILL PASS
npm test -- path/to/file.test.ts
```

### Phase 5: Verify Coverage
**Goal:** Ensure 80%+ coverage (100% for critical code)

```bash
npm test -- --coverage path/to/file.test.ts
```

**CRITICAL CODE requiring 100% coverage:**
- Financial calculations
- Authentication logic
- Security-critical code
- Core business logic

## Mode Scaling

| Mode | Test Cases | Coverage Target | SubAgents |
|------|-----------|-----------------|-----------|
| light | 3-5 | 80% | 1 test generator |
| medium | 6-10 | 90% | 2 generators + validator |
| heavy | 10+ | 100% | 3 generators + cross-validator |

## Best Practices

**DO:**
- ✅ Write test FIRST, before implementation
- ✅ Run tests after each change
- ✅ Write minimal code to pass
- ✅ Refactor only after green
- ✅ Test behavior, not implementation

**DON'T:**
- ❌ Write implementation before tests
- ❌ Skip running tests
- ❌ Over-engineer during GREEN phase
- ❌ Test private methods
- ❌ Mock everything

## Integration

After TDD:
- `/tk:review` - Code quality check
- `/tk:qa` - Full test suite + security scan
