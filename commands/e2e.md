---
name: tk:e2e
description: "Generate and run end-to-end tests with Playwright. /tk:e2e mode <user journey>"
allowed-tools:
  - Read
  - Write
  - Bash
  - SubAgent
  - AskUserQuestion
---

$import(commands/tk/_shared.md)

# TK v2.0.0 | /tk:e2e [mode]

Generate and execute end-to-end tests using Playwright for $MESSAGE.

## Process

### Phase 1: Analyze User Journey
**Goal:** Identify test scenarios for the flow

**ALL MODES:**
1. Break down user journey into steps
2. Identify critical assertions
3. Plan test data requirements

### Phase 2: Generate Page Objects
**Goal:** Create maintainable selectors

```typescript
// pages/ExamplePage.ts
export class ExamplePage {
  constructor(private page: Page) {}
  
  async goto() {
    await this.page.goto('/example')
  }
  
  get submitButton() {
    return this.page.locator('[data-testid="submit-btn"]')
  }
}
```

### Phase 3: Generate Test Cases
**Goal:** Create Playwright tests

**LIGHT:** 2 SubAgents in parallel:
```
SubAgent E2E-1: "Generate happy path test for [journey]"
SubAgent E2E-2: "Generate error/edge case tests for [journey]"
```

**MEDIUM:** 4 SubAgents:
```
SubAgent E2E-1-2: Same as LIGHT
SubAgent E2E-3: "Generate mobile responsive tests"
SubAgent E2E-4: "Generate cross-browser compatibility tests"
```

**HEAVY:** 6 SubAgents + validator:
```
SubAgent E2E-1-4: Same as MEDIUM
SubAgent E2E-5: "Generate accessibility tests"
SubAgent E2E-6: "Generate performance tests"
SubAgent Validator: "Review all tests for flakiness risks"
```

### Phase 4: Run Tests

```bash
# Run generated tests
npx playwright test tests/e2e/[journey].spec.ts

# View report
npx playwright show-report
```

### Phase 5: Capture Artifacts

**On All Tests:**
- HTML Report
- JUnit XML for CI

**On Failure:**
- Screenshot
- Video recording
- Trace file

## Test Artifacts

```bash
# View trace for debugging
npx playwright show-trace artifacts/trace.zip

# Run in debug mode
npx playwright test --debug
```

## Browser Coverage

Tests run on:
- ✅ Chromium (Desktop Chrome)
- ✅ Firefox
- ✅ WebKit (Safari)
- ✅ Mobile Chrome (optional)

## Selector Best Practices

**DO:**
```typescript
page.locator('[data-testid="submit"]')
page.getByRole('button', { name: 'Submit' })
page.getByText('Welcome')
```

**DON'T:**
```typescript
page.locator('.btn-primary')  // Class might change
page.locator('#submit-12345') // ID might be dynamic
```

## CI/CD Integration

```yaml
# .github/workflows/e2e.yml
- name: Run E2E tests
  run: npx playwright test
  
- name: Upload artifacts
  if: always()
  uses: actions/upload-artifact@v3
  with:
    name: playwright-report
    path: playwright-report/
```

## Flaky Test Detection

If test fails intermittently:
1. Add explicit waits
2. Increase timeouts
3. Check for race conditions
4. Mark as `test.fixme()` until fixed

## Quick Commands

```bash
npx playwright test                    # Run all
npx playwright test --headed           # See browser
npx playwright test --debug            # Debug mode
npx playwright codegen localhost:3000  # Record test
```
