<!-- reconstructed -->
---
name: "form-cro"
description: "Form completion optimization — field reduction, validation UX, and conversion improvement for web forms"
workers: ["performance-marketer"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Form CRO

## When to Use
- Forms have low completion rates
- Contact, signup, or lead capture forms need optimization
- Multi-step forms with high abandonment
- Adding a new form to a page

## Workflow

### Step 1: Audit the Form
| Check | Status |
|-------|--------|
| Number of fields | Too many? Each field reduces completion by ~7% |
| Required vs optional | Are optional fields clearly marked? |
| Field labels | Clear and descriptive? |
| Error messages | Helpful and specific? |
| Mobile usability | Inputs properly sized? Keyboard types correct? |
| CTA button text | Action-oriented? (not "Submit") |
| Progress indicator | Present for multi-step forms? |
| Trust signals | Privacy note near email field? |

### Step 2: Reduce Fields
For every field, ask: "Do we need this to deliver value?"
- Name: Do we need it? (sometimes just email is enough)
- Phone: Almost never needed for a contact form
- Company: Can we look this up from the email domain?
- "How did you hear about us?": Ask this after conversion, not before

### Step 3: Implementation Best Practices
```typescript
// components/lead-form.tsx
"use client";

export function LeadForm() {
  return (
    <form action={submitLead} className="space-y-3 max-w-sm">
      {/* Minimal fields */}
      <div>
        <label htmlFor="email" className="block text-sm font-medium mb-1">
          Work email
        </label>
        <input
          id="email"
          name="email"
          type="email"
          required
          autoComplete="email"
          inputMode="email"
          placeholder="you@company.com"
          className="w-full border rounded px-3 py-2"
        />
      </div>

      {/* Action-oriented CTA */}
      <button type="submit" className="w-full bg-brand-600 text-white rounded py-2 font-medium">
        Get your free report
      </button>

      {/* Trust signal */}
      <p className="text-xs text-neutral-400">
        No spam. Unsubscribe anytime.
      </p>
    </form>
  );
}
```

### Step 4: Error Handling
- Show errors inline next to the field (not at the top)
- Show errors on blur (not only on submit)
- Use specific messages ("Please enter a valid email" not "Invalid input")
- Do not clear the form on error (preserve user input)
- Disable submit button while processing (prevent double submission)

### Step 5: Measure
Track:
- Form views (how many see the form)
- Form starts (how many interact with the first field)
- Form completions (how many submit)
- Errors (which fields cause errors most often)

## Stack Context
- **Next.js**: Forms use Server Actions for submission. Client Components for interactivity.
- **Tailwind**: Consistent form styling, focus states, error states.
- **Zod**: Server-side validation for all form inputs.
- **Supabase**: Store form submissions.
- **Resend**: Send confirmation or notification emails on submission.
- **Vercel Analytics**: Track form views, starts, and completions.

## Quality Gate
- [ ] Minimum fields necessary (each field justified)
- [ ] CTA text is action-oriented (not "Submit")
- [ ] Error messages are inline, specific, and helpful
- [ ] Trust signal near email field
- [ ] Form tested on mobile
- [ ] Form conversion tracked

## Anti-Patterns
- **"Submit" button** — tell users what they get ("Get the report" not "Submit").
- **Too many fields** — every additional field reduces conversion. Be ruthless.
- **Clearing on error** — making users re-enter everything after an error is hostile.
- **No trust signals** — asking for an email without a privacy note feels risky.
- **Desktop-only testing** — most form traffic is mobile. Always test there.

## Related Skills
- `communications/signup-flow-cro` — signup form optimization
- `communications/page-cro` — form within landing page optimization
- `communications/popup-cro` — popup form optimization
- `engineering/frontend` — form implementation
