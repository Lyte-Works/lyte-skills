<!-- reconstructed -->
---
name: "social-card-gen"
description: "Generate OG images and social sharing cards — dynamic image generation for blog posts, pages, and campaigns"
workers: ["ui-designer", "frontend-developer"]
stack: "aligned"
source: "BrianRWagner/ai-marketing-claude-code-skills"
---

# Social Card Generator

## When to Use
- Pages need OG images for social sharing (LinkedIn, Twitter/X, Slack)
- Creating dynamic OG images for blog posts
- Building a consistent visual identity for social shares
- Campaign-specific social card assets

## Workflow

### Step 1: Design the Card Template
Standard OG image size: 1200x630 pixels

Elements to include:
- Brand logo or name
- Page title (large, readable)
- Optional: subtitle or description
- Optional: author photo
- Brand colors and fonts

### Step 2: Dynamic OG Image with Next.js
```typescript
// app/api/og/route.tsx
import { ImageResponse } from 'next/og';

export const runtime = 'edge';

export async function GET(request: Request) {
  const { searchParams } = new URL(request.url);
  const title = searchParams.get('title') || 'Default Title';
  const subtitle = searchParams.get('subtitle') || '';

  return new ImageResponse(
    (
      <div style={{
        width: '100%',
        height: '100%',
        display: 'flex',
        flexDirection: 'column',
        justifyContent: 'center',
        padding: '60px',
        backgroundColor: '#0c4a6e',
        color: 'white',
        fontFamily: 'system-ui',
      }}>
        <div style={{ fontSize: 60, fontWeight: 'bold', lineHeight: 1.2 }}>
          {title}
        </div>
        {subtitle && (
          <div style={{ fontSize: 28, marginTop: 20, opacity: 0.8 }}>
            {subtitle}
          </div>
        )}
        <div style={{ fontSize: 24, marginTop: 40, opacity: 0.6 }}>
          yourdomain.com
        </div>
      </div>
    ),
    { width: 1200, height: 630 }
  );
}
```

### Step 3: Use in Metadata
```typescript
// app/blog/[slug]/page.tsx
export async function generateMetadata({ params }: Props): Promise<Metadata> {
  const post = await getPost(params.slug);
  return {
    title: post.title,
    description: post.excerpt,
    openGraph: {
      title: post.title,
      description: post.excerpt,
      images: [{
        url: `/api/og?title=${encodeURIComponent(post.title)}&subtitle=${encodeURIComponent(post.excerpt)}`,
        width: 1200,
        height: 630,
      }],
    },
    twitter: {
      card: 'summary_large_image',
    },
  };
}
```

### Step 4: Validate
Test with:
- Twitter Card Validator
- LinkedIn Post Inspector
- Facebook Sharing Debugger
- Check in Slack (paste the URL)

### Step 5: Static Cards for Campaigns
For campaign-specific cards, generate static images:
- Create a `/public/og/` directory for static OG images
- Reference in metadata for campaign pages

## Stack Context
- **Next.js**: `ImageResponse` from `next/og` for dynamic generation. Edge runtime for fast generation.
- **Vercel**: Edge function deployment for OG image generation.
- **Tailwind**: Design tokens guide the visual style (colors, fonts), but OG images use inline styles (JSX, not Tailwind).

## Quality Gate
- [ ] OG image displays correctly on LinkedIn, Twitter, and Slack
- [ ] Text is readable at small preview sizes
- [ ] Brand colors and logo included
- [ ] Dynamic generation works for all page types
- [ ] Validated with social platform debug tools

## Anti-Patterns
- **No OG image** — shared links without images get significantly less engagement.
- **Generic image for all pages** — dynamic OG images are worth the effort.
- **Text too small** — social previews are small. Use large, bold text.
- **Not testing** — each platform renders OG images differently. Test on all.

## Related Skills
- `communications/social-content` — social posts that use these cards
- `communications/linkedin-authority` — LinkedIn sharing optimization
- `engineering/frontend` — metadata implementation
- `engineering/ui-designer` — visual design consistency
