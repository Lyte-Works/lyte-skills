<!-- reconstructed -->
---
name: "ux-designer"
description: "Interaction design — wireframes, user flows, component design, and design system creation"
workers: ["product-manager", "ui-designer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# UX Designer

## When to Use
- Designing a new feature or page before engineering begins
- Creating user flows for complex interactions
- Building or extending a design system
- Wireframing layouts for stakeholder review
- Improving the usability of an existing interface

## Workflow

### Step 1: Understand the Context
Before designing, gather:
- **User research**: What do we know about the user? (from UX Researcher skill)
- **Product spec**: What is being built? (from Product Manager skill)
- **Constraints**: Technical limitations, timeline, existing design patterns
- **Competitive reference**: How do competitors solve this?

### Step 2: Map User Flows
Create a user flow diagram showing:
- Entry point (how does the user get here?)
- Decision points (where do they choose?)
- Actions (what do they do at each step?)
- Outcomes (where do they end up?)
- Error paths (what happens when something goes wrong?)

Format as a simple flowchart in text:
```
Landing Page → CTA Click → Sign Up Form → Email Verification → Onboarding → Dashboard
                                ↓ (error)
                           Validation Error → Fix → Resubmit
```

### Step 3: Wireframe Key Screens
Create low-fidelity wireframes for each key screen in the flow:
- Focus on layout and hierarchy, not visual design
- Show content zones, not actual content
- Indicate interactive elements (buttons, forms, links)
- Note the purpose of each section

Wireframe in code using Tailwind:
```typescript
// Wireframes can be built as rough Next.js pages with Tailwind
// Gray boxes for images, placeholder text, basic layout
// This serves as both wireframe AND prototype
```

### Step 4: Define Interaction Patterns
For each interactive element, specify:
- **Trigger**: What initiates the interaction? (click, hover, scroll, load)
- **Action**: What happens? (modal opens, form submits, element animates)
- **Feedback**: How does the user know it worked? (loading state, success message, visual change)
- **Edge cases**: What if it fails? What if it takes too long?

### Step 5: Design System Components
If the project has a design system, extend it. If not, start one:

**Base tokens** (defined in `tailwind.config.ts`):
- Colors: primary, secondary, neutral, success, warning, error
- Typography: heading sizes, body text, caption
- Spacing: consistent scale (4, 8, 12, 16, 24, 32, 48, 64)
- Border radius: small, medium, large
- Shadows: subtle, medium, pronounced

**Component library** (in `/components/ui/`):
- Button (primary, secondary, ghost, destructive)
- Input (text, email, password, textarea)
- Card (with header, body, footer variants)
- Modal/Dialog
- Toast/Alert
- Navigation (header, sidebar, breadcrumb)

### Step 6: Handoff to Engineering
Provide:
- User flow diagram
- Wireframes (or coded prototypes)
- Interaction specifications
- Design tokens (in Tailwind config)
- Component specifications
- All documented in Notion with links to code

## Stack Context
- **Next.js App Router**: Wireframes can be built as actual pages in the app. This approach means the wireframe IS the prototype.
- **Tailwind CSS**: Design tokens are defined in `tailwind.config.ts`. Components use Tailwind utility classes. The design system IS the Tailwind config + component library.
- **Vercel**: Preview deployments serve as interactive prototypes. Share preview URLs with stakeholders for feedback.
- **Notion**: User flows, interaction specs, and design decisions documented in Notion.

## Quality Gate
- [ ] User flow covers happy path, error paths, and edge cases
- [ ] Key screens wireframed with clear hierarchy
- [ ] Interactive elements have trigger, action, and feedback defined
- [ ] Design tokens documented in Tailwind config
- [ ] Components follow consistent patterns
- [ ] Handoff includes everything engineering needs to build

## Anti-Patterns
- **Pixel-perfect wireframes** — wireframes are for layout and hierarchy, not visual polish. Save that for implementation.
- **Designing without research** — design decisions should be informed by user research, not personal preference.
- **Inconsistent patterns** — if buttons look different on every page, there is no design system. Consistency first.
- **Over-designing** — design what is needed for the current sprint, not the entire app. Design incrementally.
- **No error states** — every interaction can fail. Design the error state before the happy path is finalized.

## Related Skills
- `strategy/ux-researcher` — research that informs design decisions
- `strategy/product-manager` — product specs that drive design
- `engineering/frontend` — implementing designs in Next.js
- `engineering/ui-designer` — visual design and polish
- `communications/social-card-gen` — designing OG images and social cards
