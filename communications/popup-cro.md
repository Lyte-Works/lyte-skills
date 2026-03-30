<!-- reconstructed -->
---
name: "popup-cro"
description: "Popup optimization — timing, design, targeting, and conversion for email capture and promotional popups"
workers: ["performance-marketer"]
stack: "aligned"
source: "coreyhaines31/marketingskills"
---

# Popup CRO

## When to Use
- Adding email capture popups to a site
- Existing popups are annoying users without converting
- Exit-intent popup strategy
- Popup A/B testing

## Workflow

### Step 1: Define the Popup Goal
One popup, one goal: email capture, promo announcement, or feature highlight.

### Step 2: Trigger Strategy
| Trigger | When | Best For |
|---------|------|---------|
| Exit intent | Mouse moves toward close/back | Last-chance email capture |
| Time delay | After 30-60 seconds | Engaged visitors |
| Scroll depth | After 50% scroll | Content readers |
| Page-specific | On pricing or checkout pages | Conversion nudge |

**Never**: Popup on page load (immediately annoying).

### Step 3: Design Rules
- Clear close button (X) — visible and easy to click
- Mobile-friendly (not full-screen blocking on mobile)
- One field (email only for capture)
- Clear value proposition (what do they get for their email?)
- Dismissible and remembers dismissal (cookie/localStorage)

### Step 4: Implementation
```typescript
// components/exit-popup.tsx
"use client";
import { useState, useEffect } from 'react';

export function ExitPopup() {
  const [show, setShow] = useState(false);
  const [dismissed, setDismissed] = useState(false);

  useEffect(() => {
    if (localStorage.getItem('popup-dismissed')) return;

    const handler = (e: MouseEvent) => {
      if (e.clientY < 10 && !dismissed) setShow(true);
    };
    document.addEventListener('mousemove', handler);
    return () => document.removeEventListener('mousemove', handler);
  }, [dismissed]);

  function dismiss() {
    setShow(false);
    setDismissed(true);
    localStorage.setItem('popup-dismissed', 'true');
  }

  if (!show) return null;

  return (
    <div className="fixed inset-0 bg-black/50 z-50 flex items-center justify-center p-4">
      <div className="bg-white rounded-lg p-6 max-w-sm relative">
        <button onClick={dismiss} className="absolute top-2 right-2 text-neutral-400">X</button>
        <h3 className="text-xl font-bold mb-2">Before you go...</h3>
        <p className="text-sm text-neutral-600 mb-4">Get our free guide to [topic]. No spam.</p>
        <form action={captureEmail} className="space-y-2">
          <input name="email" type="email" placeholder="Your email" required className="w-full border rounded px-3 py-2" />
          <button type="submit" className="w-full bg-brand-600 text-white rounded py-2">Send me the guide</button>
        </form>
      </div>
    </div>
  );
}
```

### Step 5: Measure
- Popup impressions (how many see it)
- Popup conversion rate (how many submit)
- Popup dismissal rate
- Impact on bounce rate (ensure popups are not increasing bounces)

## Stack Context
- **Next.js**: Popup as Client Component (requires browser events).
- **Tailwind**: Overlay and modal styling.
- **Supabase**: Store captured emails.
- **Resend**: Send the promised content.
- **Vercel Analytics**: Track popup performance.

## Quality Gate
- [ ] Popup has a clear, single goal
- [ ] Trigger is not on page load
- [ ] Close button is visible and accessible
- [ ] Popup remembers dismissal
- [ ] Mobile-friendly
- [ ] Conversion tracked

## Anti-Patterns
- **Immediate popups** — appearing before the user has read anything.
- **Uncloseable** — making the close button hard to find.
- **Multiple popups** — one popup per visit max.
- **No value exchange** — asking for email without offering something in return.
- **Ignoring mobile** — full-screen popups on mobile violate Google guidelines.

## Related Skills
- `communications/form-cro` — form within popup
- `communications/page-cro` — page-level conversion
- `communications/email-sequences` — follow-up after capture
