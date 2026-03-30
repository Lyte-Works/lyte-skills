<!-- reconstructed -->
---
name: "ui-designer"
description: "Visual UI design implementation — design tokens, component styling, animations, and visual polish with Tailwind CSS"
workers: ["ui-designer", "frontend-developer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# UI Designer

## When to Use
- Implementing visual design from mockups or wireframes
- Creating or extending a Tailwind design system
- Adding animations and micro-interactions
- Visual polish and refinement pass
- Building reusable UI component library

## Workflow

### Step 1: Design Tokens in Tailwind
```typescript
// tailwind.config.ts
import type { Config } from 'tailwindcss';

const config: Config = {
  content: ['./app/**/*.{ts,tsx}', './components/**/*.{ts,tsx}'],
  theme: {
    extend: {
      colors: {
        brand: {
          50: '#f0f9ff',
          100: '#e0f2fe',
          500: '#0ea5e9',
          600: '#0284c7',
          700: '#0369a1',
          900: '#0c4a6e',
        },
        neutral: {
          50: '#fafafa',
          100: '#f5f5f5',
          200: '#e5e5e5',
          700: '#404040',
          900: '#171717',
        },
      },
      fontFamily: {
        sans: ['var(--font-inter)', 'system-ui', 'sans-serif'],
        mono: ['var(--font-jetbrains)', 'monospace'],
      },
      borderRadius: {
        DEFAULT: '0.5rem',
        lg: '0.75rem',
        xl: '1rem',
      },
    },
  },
  plugins: [],
};

export default config;
```

### Step 2: Typography System
```typescript
// Consistent typography scale
// Use Tailwind's built-in scale, extend only when needed

// Headings
<h1 className="text-4xl font-bold tracking-tight">  // Page title
<h2 className="text-2xl font-semibold">              // Section title
<h3 className="text-xl font-medium">                 // Subsection
<h4 className="text-lg font-medium">                 // Card title

// Body
<p className="text-base text-neutral-700">            // Body text
<p className="text-sm text-neutral-500">              // Supporting text
<span className="text-xs text-neutral-400">           // Caption
```

### Step 3: Component Library
Build reusable components in `/components/ui/`:

```typescript
// components/ui/button.tsx
import { cn } from '@/lib/utils';

interface ButtonProps extends React.ButtonHTMLAttributes<HTMLButtonElement> {
  variant?: 'primary' | 'secondary' | 'ghost' | 'destructive';
  size?: 'sm' | 'md' | 'lg';
}

export function Button({ variant = 'primary', size = 'md', className, ...props }: ButtonProps) {
  return (
    <button
      className={cn(
        'inline-flex items-center justify-center rounded font-medium transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-brand-500 disabled:opacity-50',
        {
          'bg-brand-600 text-white hover:bg-brand-700': variant === 'primary',
          'border border-neutral-200 bg-white hover:bg-neutral-50': variant === 'secondary',
          'hover:bg-neutral-100': variant === 'ghost',
          'bg-red-600 text-white hover:bg-red-700': variant === 'destructive',
        },
        {
          'h-8 px-3 text-sm': size === 'sm',
          'h-10 px-4 text-sm': size === 'md',
          'h-12 px-6 text-base': size === 'lg',
        },
        className
      )}
      {...props}
    />
  );
}
```

### Step 4: Animations
```typescript
// Subtle, purposeful animations only
// Use Tailwind's built-in transitions

// Hover effects
<button className="transition-colors hover:bg-brand-700">

// Entrance animations (use sparingly)
<div className="animate-in fade-in slide-in-from-bottom-4 duration-500">

// Loading states
<div className="animate-pulse bg-neutral-200 rounded h-4 w-32" />
```

### Step 5: Responsive Design
Mobile-first approach:
```typescript
// Mobile first, then scale up
<div className="px-4 md:px-8 lg:px-16">
<div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
<h1 className="text-2xl md:text-3xl lg:text-4xl">
```

### Step 6: Dark Mode (optional)
```typescript
// tailwind.config.ts
{ darkMode: 'class' }

// Usage
<div className="bg-white dark:bg-neutral-900 text-neutral-900 dark:text-neutral-100">
```

## Stack Context
- **Tailwind CSS**: The only styling system. Design tokens in config. Utilities in components.
- **Next.js**: Server Components for static UI. Client Components only for interactive elements.
- **`next/font`**: Self-hosted fonts via `next/font/google` or `next/font/local`.
- **`next/image`**: All images optimized automatically.

## Quality Gate
- [ ] Design tokens defined in Tailwind config (not hardcoded values)
- [ ] Component library with consistent API (variant, size props)
- [ ] Typography scale consistent across all pages
- [ ] Responsive design tested at mobile, tablet, desktop
- [ ] Focus states visible for keyboard navigation
- [ ] Animations are subtle and purposeful (not decorative)

## Anti-Patterns
- **Hardcoded colors** — use design tokens from Tailwind config, not hex values in components.
- **Inconsistent spacing** — use Tailwind's spacing scale. No arbitrary `px-[37px]` values.
- **Heavy animations** — animations that delay content are harmful. Keep them subtle and fast.
- **No focus states** — keyboard users need visible focus indicators.
- **Desktop-first design** — always start mobile-first. Desktop is the enhancement.

## Related Skills
- `engineering/frontend` — component implementation
- `strategy/ux-designer` — wireframes and interaction design
- `communications/social-card-gen` — OG image design
- `engineering/performance-profiler` — visual design affects performance
