<!-- reconstructed -->
---
name: "frontend"
description: "React/Next.js frontend development — App Router, Server Components, client interactions, component architecture"
workers: ["frontend-developer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Frontend Developer

## When to Use
- Building new pages or components in Next.js
- Implementing UI from wireframes or design specs
- Creating interactive client-side features
- Optimizing frontend performance
- Structuring the app directory and component hierarchy

## Workflow

### Step 1: Understand the Requirement
Before writing code:
- Read the product spec or design handoff
- Identify which pages, layouts, and components are needed
- Determine what is Server Component vs. Client Component
- Note any data requirements (API calls, database queries)

### Step 2: Plan the Component Architecture
```
app/
├── layout.tsx          # Root layout (Server Component)
├── page.tsx            # Homepage (Server Component)
├── about/
│   └── page.tsx        # About page (Server Component)
├── blog/
│   ├── page.tsx        # Blog listing (Server Component)
│   └── [slug]/
│       └── page.tsx    # Blog post (Server Component)
└── api/
    └── contact/
        └── route.ts    # Contact form handler

components/
├── ui/                 # Reusable UI primitives
│   ├── button.tsx
│   ├── input.tsx
│   └── card.tsx
├── layout/             # Layout components
│   ├── header.tsx
│   ├── footer.tsx
│   └── nav.tsx
└── features/           # Feature-specific components
    ├── contact-form.tsx    # "use client" — has form interactivity
    └── hero-section.tsx    # Server Component — static content
```

### Step 3: Implement Server Components (Default)
Every component is a Server Component unless it needs:
- Event handlers (onClick, onChange, onSubmit)
- Browser APIs (window, document, localStorage)
- React hooks (useState, useEffect, useRef)
- Third-party client libraries

```typescript
// app/blog/page.tsx — Server Component (default)
import { Card } from '@/components/ui/card';

export default async function BlogPage() {
  const posts = await getPosts(); // Direct async data fetching
  return (
    <main className="max-w-4xl mx-auto px-4 py-12">
      <h1 className="text-4xl font-bold mb-8">Blog</h1>
      <div className="grid gap-6">
        {posts.map(post => (
          <Card key={post.slug} title={post.title} href={`/blog/${post.slug}`} />
        ))}
      </div>
    </main>
  );
}
```

### Step 4: Implement Client Components (Opt-in)
Only add `"use client"` when the component genuinely needs client-side interactivity:

```typescript
// components/features/contact-form.tsx
"use client";

import { useState } from 'react';
import { Button } from '@/components/ui/button';
import { Input } from '@/components/ui/input';

export function ContactForm() {
  const [status, setStatus] = useState<'idle' | 'loading' | 'success' | 'error'>('idle');

  async function handleSubmit(e: React.FormEvent<HTMLFormElement>) {
    e.preventDefault();
    setStatus('loading');
    const formData = new FormData(e.currentTarget);
    const res = await fetch('/api/contact', { method: 'POST', body: formData });
    setStatus(res.ok ? 'success' : 'error');
  }

  return (
    <form onSubmit={handleSubmit} className="space-y-4 max-w-md">
      <Input name="email" type="email" placeholder="your@email.com" required />
      <Input name="message" type="text" placeholder="Your message" required />
      <Button type="submit" disabled={status === 'loading'}>
        {status === 'loading' ? 'Sending...' : 'Send'}
      </Button>
      {status === 'success' && <p className="text-green-600">Message sent!</p>}
      {status === 'error' && <p className="text-red-600">Something went wrong.</p>}
    </form>
  );
}
```

### Step 5: Styling with Tailwind
- Use Tailwind utility classes exclusively
- Use `cn()` helper for conditional classes:
```typescript
import { clsx, type ClassValue } from 'clsx';
import { twMerge } from 'tailwind-merge';

export function cn(...inputs: ClassValue[]) {
  return twMerge(clsx(inputs));
}
```
- Responsive design: mobile-first (`sm:`, `md:`, `lg:` breakpoints)
- Dark mode: use `dark:` variant if enabled in Tailwind config

### Step 6: SEO and Metadata
```typescript
// app/layout.tsx
import type { Metadata } from 'next';

export const metadata: Metadata = {
  title: { default: 'Site Name', template: '%s | Site Name' },
  description: 'Site description',
  openGraph: { type: 'website', locale: 'en_US' },
};
```

Use `generateMetadata` for dynamic pages:
```typescript
export async function generateMetadata({ params }: Props): Promise<Metadata> {
  const post = await getPost(params.slug);
  return { title: post.title, description: post.excerpt };
}
```

### Step 7: Images and Fonts
- Always use `next/image` for images (automatic optimization)
- Always use `next/font` for fonts (self-hosted, no external requests)

## Stack Context
- **Next.js App Router**: Always App Router, never Pages Router. `app/` directory only.
- **TypeScript**: Strict mode. Type all props, API responses, and data structures.
- **Tailwind CSS**: Only styling method. No CSS modules, no styled-components, no inline styles.
- **Vercel**: Auto-deploys from GitHub main branch. Preview deployments for every PR.
- **GitHub**: One repo per client. Feature branches + PRs for all work.

## Quality Gate
- [ ] Server Components used by default; `"use client"` only where required
- [ ] All components typed with TypeScript (no `any`)
- [ ] Tailwind only — no CSS modules or inline styles
- [ ] Metadata set for all pages (title, description, OG)
- [ ] Images use `next/image`, fonts use `next/font`
- [ ] Responsive design tested at mobile, tablet, and desktop
- [ ] Preview deployment reviewed before merge

## Anti-Patterns
- **`"use client"` everywhere** — most components do not need client-side JS. Default to Server Components.
- **CSS modules alongside Tailwind** — pick one system. We use Tailwind.
- **Pages Router patterns** — no `getServerSideProps`, no `getStaticProps`. Use App Router data fetching.
- **Untyped components** — TypeScript strict mode means no `any` types.
- **Giant components** — if a component is over 100 lines, split it.

## Related Skills
- `engineering/fullstack` — when the work spans frontend and backend
- `engineering/landing-page-generator` — quickly generating landing pages
- `engineering/ui-designer` — visual design implementation
- `engineering/playwright-e2e` — testing the frontend
- `strategy/ux-designer` — design specs that drive frontend work
