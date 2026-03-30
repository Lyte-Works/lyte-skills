<!-- reconstructed -->
---
name: "playwright-e2e"
description: "End-to-end testing with Playwright — test setup, page objects, user flow testing, and CI integration"
workers: ["frontend-developer", "qa-engineer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Playwright E2E Testing

## When to Use
- Setting up E2E tests for a Next.js application
- Testing critical user flows (signup, checkout, onboarding)
- Regression testing before releases
- Validating cross-browser compatibility
- CI/CD pipeline needs automated testing

## Workflow

### Step 1: Setup
```bash
npm init playwright@latest
```

Configuration:
```typescript
// playwright.config.ts
import { defineConfig, devices } from '@playwright/test';

export default defineConfig({
  testDir: './e2e',
  fullyParallel: true,
  forbidOnly: !!process.env.CI,
  retries: process.env.CI ? 2 : 0,
  workers: process.env.CI ? 1 : undefined,
  reporter: 'html',
  use: {
    baseURL: 'http://localhost:3000',
    trace: 'on-first-retry',
  },
  projects: [
    { name: 'chromium', use: { ...devices['Desktop Chrome'] } },
    { name: 'mobile', use: { ...devices['iPhone 13'] } },
  ],
  webServer: {
    command: 'npm run dev',
    url: 'http://localhost:3000',
    reuseExistingServer: !process.env.CI,
  },
});
```

### Step 2: Page Object Pattern
```typescript
// e2e/pages/home.page.ts
import { type Page, type Locator } from '@playwright/test';

export class HomePage {
  readonly page: Page;
  readonly heroHeadline: Locator;
  readonly ctaButton: Locator;
  readonly emailInput: Locator;

  constructor(page: Page) {
    this.page = page;
    this.heroHeadline = page.getByRole('heading', { level: 1 });
    this.ctaButton = page.getByRole('button', { name: /get started/i });
    this.emailInput = page.getByPlaceholder('your@email.com');
  }

  async goto() {
    await this.page.goto('/');
  }

  async submitEmail(email: string) {
    await this.emailInput.fill(email);
    await this.ctaButton.click();
  }
}
```

### Step 3: Write Tests
```typescript
// e2e/homepage.spec.ts
import { test, expect } from '@playwright/test';
import { HomePage } from './pages/home.page';

test.describe('Homepage', () => {
  test('displays hero headline', async ({ page }) => {
    const homePage = new HomePage(page);
    await homePage.goto();
    await expect(homePage.heroHeadline).toBeVisible();
  });

  test('email signup works', async ({ page }) => {
    const homePage = new HomePage(page);
    await homePage.goto();
    await homePage.submitEmail('test@example.com');
    await expect(page.getByText('Thanks for signing up')).toBeVisible();
  });

  test('is responsive on mobile', async ({ page }) => {
    const homePage = new HomePage(page);
    await homePage.goto();
    await expect(homePage.heroHeadline).toBeVisible();
    await expect(homePage.ctaButton).toBeVisible();
  });
});
```

### Step 4: Test Critical Flows
Prioritize testing:
1. **Signup/registration flow** — the most important conversion path
2. **Contact/lead forms** — revenue-generating interactions
3. **Navigation** — all pages accessible, no broken links
4. **Checkout flow** — if payments are active
5. **Authentication** — login, logout, protected routes

### Step 5: CI Integration
```yaml
# .github/workflows/e2e.yml
name: E2E Tests
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm ci
      - run: npx playwright install --with-deps
      - run: npx playwright test
      - uses: actions/upload-artifact@v4
        if: always()
        with:
          name: playwright-report
          path: playwright-report/
```

## Stack Context
- **Next.js**: Playwright's `webServer` config starts the Next.js dev server automatically.
- **Vercel**: Run E2E tests against Vercel preview deployments in CI by setting `baseURL` to the preview URL.
- **GitHub Actions**: E2E tests run on every PR. Artifacts include the HTML report.
- **Supabase**: For tests that need database state, use Supabase's test project or seed data.

## Quality Gate
- [ ] Page object pattern used (no raw selectors in tests)
- [ ] Critical user flows covered (signup, contact, navigation)
- [ ] Tests pass on CI
- [ ] Mobile viewport tested
- [ ] Tests are independent (no shared state between tests)
- [ ] Test report accessible as CI artifact

## Anti-Patterns
- **Testing implementation details** — test user-visible behavior, not CSS classes or DOM structure.
- **Fragile selectors** — use `getByRole`, `getByText`, `getByPlaceholder` instead of CSS selectors.
- **Shared state** — tests that depend on other tests running first are brittle. Each test should set up its own state.
- **Testing everything E2E** — E2E tests are slow. Test critical paths E2E, test components with unit tests.
- **No CI integration** — E2E tests that only run locally are not reliable. Run them in CI on every PR.

## Related Skills
- `engineering/tdd` — test-driven development approach
- `engineering/qa-engineer` — broader QA strategy
- `engineering/frontend` — the application being tested
- `engineering/cicd-pipeline` — CI/CD pipeline that runs tests
