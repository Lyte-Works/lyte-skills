<!-- reconstructed -->
---
name: "signup-flow-cro"
description: "Signup and registration funnel optimization — reduce friction, improve completion rates"
workers: ["performance-marketer"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Signup Flow CRO

## When to Use
- Signup form has high abandonment
- Optimizing free trial or account creation flow
- Reducing signup-to-activation drop-off
- Adding or removing signup steps

## Workflow

### Step 1: Map the Current Flow
```
Landing → Signup Form → Email Verify → Onboarding → First Action
```
Measure conversion at each step.

### Step 2: Reduce Friction
| Friction Point | Fix |
|---------------|-----|
| Too many fields | Ask only what is essential (email + password minimum) |
| Password requirements visible only after error | Show requirements upfront |
| No social signup | Add Google/GitHub OAuth if audience uses them |
| Email verification blocks access | Allow access immediately, verify later |
| Unclear value | Show what they get after signup |
| Slow form | Optimize form component (no unnecessary re-renders) |

### Step 3: Implementation
```typescript
// components/signup-form.tsx
"use client";
import { signIn } from 'next-auth/react';

export function SignupForm() {
  return (
    <div className="space-y-4 max-w-sm mx-auto">
      {/* Social signup first (lowest friction) */}
      <button onClick={() => signIn('google')} className="w-full border rounded py-2">
        Continue with Google
      </button>

      <div className="text-center text-sm text-neutral-400">or</div>

      {/* Email signup (minimal fields) */}
      <form action={signup} className="space-y-3">
        <input name="email" type="email" placeholder="Email" required className="w-full border rounded px-3 py-2" />
        <input name="password" type="password" placeholder="Password (8+ characters)" required minLength={8} className="w-full border rounded px-3 py-2" />
        <button type="submit" className="w-full bg-brand-600 text-white rounded py-2">Create account</button>
      </form>

      <p className="text-xs text-neutral-400 text-center">
        By signing up, you agree to our <a href="/terms" className="underline">Terms</a> and <a href="/privacy" className="underline">Privacy Policy</a>.
      </p>
    </div>
  );
}
```

### Step 4: Optimize Post-Signup
After signup, immediately:
1. Show progress (step indicator)
2. Ask the minimum needed to personalize
3. Get them to their first valuable action ASAP
4. Send a welcome email (Resend)

### Step 5: Measure
Track with custom events:
- `signup_started` — form viewed
- `signup_completed` — account created
- `email_verified` — email confirmed
- `onboarding_completed` — first valuable action

Calculate conversion between each step.

## Stack Context
- **NextAuth.js**: OAuth providers (Google, GitHub) for social signup.
- **Next.js**: Signup form as Client Component with Server Action.
- **Supabase**: User storage with auth integration.
- **Resend**: Welcome email triggered by signup.
- **Vercel Analytics**: Funnel tracking with custom events.

## Quality Gate
- [ ] Signup form requires minimum fields only
- [ ] Social signup option available
- [ ] Conversion tracked at each funnel step
- [ ] Post-signup flow gets user to first value quickly
- [ ] Welcome email sent automatically
- [ ] Form tested on mobile

## Anti-Patterns
- **Asking for everything upfront** — name, company, phone, job title before they even know if they want the product.
- **Blocking on email verification** — let them in immediately, verify later.
- **No progress indicator** — multi-step forms without progress feel endless.
- **Redirecting to homepage** — after signup, take them to the next logical step, not the homepage.

## Related Skills
- `communications/page-cro` — landing page optimization
- `communications/onboarding-cro` — post-signup onboarding
- `communications/form-cro` — form optimization
- `engineering/frontend` — signup form implementation
