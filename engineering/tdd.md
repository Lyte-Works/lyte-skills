<!-- reconstructed -->
---
name: "tdd"
description: "Test-driven development — write tests first, then implement, using Vitest and React Testing Library"
workers: ["code-reviewer", "frontend-developer", "backend-developer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Test-Driven Development

## When to Use
- Building new features where requirements are clear
- Fixing bugs (write a test that reproduces the bug first)
- Refactoring code (tests ensure behavior is preserved)
- Critical business logic that must be correct

## Workflow

### Step 1: Red — Write the Test First
Before writing any implementation code, write a test that describes the expected behavior:

```typescript
// __tests__/lib/pricing.test.ts
import { describe, it, expect } from 'vitest';
import { calculatePrice } from '@/lib/pricing';

describe('calculatePrice', () => {
  it('returns base price for standard tier', () => {
    expect(calculatePrice('standard', 1)).toBe(29);
  });

  it('applies quantity discount for 10+ seats', () => {
    expect(calculatePrice('standard', 10)).toBe(261); // 10% discount
  });

  it('throws for invalid tier', () => {
    expect(() => calculatePrice('invalid', 1)).toThrow('Invalid tier');
  });

  it('throws for zero or negative quantity', () => {
    expect(() => calculatePrice('standard', 0)).toThrow('Quantity must be positive');
  });
});
```

Run the test — it should FAIL (red).

### Step 2: Green — Write Minimal Implementation
Write the simplest code that makes the test pass:

```typescript
// lib/pricing.ts
const PRICES = { standard: 29, pro: 79, enterprise: 199 } as const;

export function calculatePrice(tier: string, quantity: number): number {
  if (quantity <= 0) throw new Error('Quantity must be positive');
  if (!(tier in PRICES)) throw new Error('Invalid tier');

  const base = PRICES[tier as keyof typeof PRICES] * quantity;
  const discount = quantity >= 10 ? 0.1 : 0;
  return Math.round(base * (1 - discount));
}
```

Run the test — it should PASS (green).

### Step 3: Refactor
Improve the code while keeping tests green:
- Extract constants
- Improve types
- Remove duplication
- Rename for clarity

### Step 4: Testing Strategy by Layer

**Unit tests** (Vitest):
- Pure functions (pricing, formatting, validation)
- Utility functions
- Data transformations

**Component tests** (Vitest + React Testing Library):
```typescript
// __tests__/components/contact-form.test.tsx
import { render, screen, fireEvent } from '@testing-library/react';
import { ContactForm } from '@/components/features/contact-form';

describe('ContactForm', () => {
  it('shows validation error for empty email', async () => {
    render(<ContactForm />);
    fireEvent.click(screen.getByRole('button', { name: /send/i }));
    expect(await screen.findByText(/email is required/i)).toBeInTheDocument();
  });

  it('disables button while submitting', async () => {
    render(<ContactForm />);
    fireEvent.change(screen.getByPlaceholderText('your@email.com'), {
      target: { value: 'test@example.com' },
    });
    fireEvent.click(screen.getByRole('button', { name: /send/i }));
    expect(screen.getByRole('button')).toBeDisabled();
  });
});
```

**Integration tests** (Vitest):
- Server Actions with mocked dependencies
- API routes with mocked database

**E2E tests** (Playwright):
- Critical user flows
- See `engineering/playwright-e2e`

### Step 5: Test Configuration
```typescript
// vitest.config.ts
import { defineConfig } from 'vitest/config';
import react from '@vitejs/plugin-react';
import path from 'path';

export default defineConfig({
  plugins: [react()],
  test: {
    environment: 'jsdom',
    globals: true,
    setupFiles: ['./test/setup.ts'],
  },
  resolve: {
    alias: { '@': path.resolve(__dirname, './') },
  },
});
```

## Stack Context
- **Vitest**: Test runner (fast, compatible with Vite and Next.js).
- **React Testing Library**: Component testing — test behavior, not implementation.
- **Next.js**: Server Components are tested via integration tests. Client Components via React Testing Library.
- **GitHub Actions**: Tests run in CI on every PR.
- **TypeScript**: Tests are typed. Use proper types for mocks and assertions.

## Quality Gate
- [ ] Tests written before implementation (red-green-refactor cycle followed)
- [ ] Critical business logic has unit tests
- [ ] Components with interactivity have component tests
- [ ] Tests are independent (no shared state)
- [ ] Tests pass in CI
- [ ] No `any` types in tests

## Anti-Patterns
- **Tests after code** — writing tests after implementation means tests confirm the code, not the spec. Test first.
- **Testing implementation** — testing that a component uses `useState` is fragile. Test behavior (what the user sees and does).
- **100% coverage obsession** — coverage is a tool, not a goal. Test critical paths, not getters and setters.
- **Slow tests** — unit tests should run in milliseconds. If tests are slow, they are not unit tests.
- **Mocking everything** — over-mocking tests nothing. Only mock external dependencies (APIs, databases).

## Related Skills
- `engineering/playwright-e2e` — E2E testing
- `engineering/code-review` — reviewing tests in PRs
- `engineering/qa-engineer` — broader QA strategy
- `engineering/cicd-pipeline` — running tests in CI
