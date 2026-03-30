<!-- reconstructed -->
---
name: "positioning"
description: "Define market positioning, unique value proposition, and competitive differentiation for small businesses"
workers: ["business-strategist"]
stack: "aligned"
source: "BrianRWagner/ai-marketing-claude-code-skills"
---

# Positioning

## When to Use
- New client onboarding — before any marketing or website work begins
- Client is struggling to articulate what makes them different
- Entering a new market or launching a new product
- Existing positioning feels generic or undifferentiated
- Competitors are closing the gap on previous differentiators

## Workflow

### Step 1: Gather Inputs
Collect from the client (via Notion intake doc):
- What do you sell?
- Who do you sell it to? (specific segments, not "everyone")
- What alternatives exist? (direct competitors + indirect substitutes)
- Why do customers choose you over those alternatives? (actual reasons, not aspirational)
- What would customers miss most if you disappeared?

### Step 2: Identify the Category
Define the market category the client competes in. This is NOT what the product is — it is the mental box the buyer puts you in.
- If no clear category exists, consider whether to create one (risky but high-reward) or anchor to an adjacent known category.

### Step 3: Map Competitive Alternatives
List what customers would do if the client did not exist:
- Direct competitors (same category, same customer)
- Indirect substitutes (different category, same job-to-be-done)
- Status quo (do nothing, use a spreadsheet, hire an intern)

### Step 4: Extract Unique Attributes
For each competitive alternative, identify what the client does differently:
- Features (what it does)
- Delivery model (how it works)
- Business model (how you pay)
- Experience (what it feels like)

### Step 5: Map Attributes to Value Themes
Group unique attributes into 2-3 value themes that matter to the target customer. Value themes answer: "So what? Why does this attribute matter to the buyer?"

### Step 6: Write the Positioning Statement
Use this structure:
> For [target customer] who [key need/problem], [product/company] is a [category] that [key differentiator]. Unlike [primary alternative], we [unique value].

### Step 7: Validate
- Read the statement to 3 people unfamiliar with the business. If they cannot explain back what makes the company different, rewrite.
- Check: does the positioning hold against each competitive alternative identified in Step 3?

### Step 8: Document in Notion
Create a "Positioning" page in the client's Notion workspace with:
- Positioning statement
- Target customer definition
- Competitive landscape map
- Value themes with supporting evidence
- Date and version number

## Stack Context
- **Notion**: All positioning work lives in the client's Notion workspace as the canonical strategy document. Other workers reference this when building website copy, ad campaigns, or sales materials.
- **Website (Next.js)**: The positioning statement directly informs the hero section, meta description, and overall messaging hierarchy on the client's site.
- **Vercel Analytics**: After positioning is implemented on the site, monitor bounce rate and time-on-page for the homepage to validate resonance.

## Quality Gate
- [ ] Positioning statement follows the template structure
- [ ] At least 3 competitive alternatives identified (not just direct competitors)
- [ ] Value themes are customer-centric (benefits, not features)
- [ ] Statement validated with at least 1 person outside the project
- [ ] Documented in Notion with version number
- [ ] No jargon or buzzwords that a customer would not use

## Anti-Patterns
- **"We're the best"** — positioning is about being different, not better. If your statement could apply to any competitor, it is not positioning.
- **Feature listing** — listing product features is not positioning. Translate features into customer value.
- **Too many audiences** — if you are positioned for "everyone," you are positioned for no one. Pick a segment.
- **Category creation without justification** — creating a new category is expensive and risky. Only do it when existing categories genuinely misrepresent what you do.
- **Ignoring the status quo** — the biggest competitor is often "do nothing." Include it in your alternatives map.

## Related Skills
- `strategy/competitive-teardown` — deep-dive on specific competitors
- `strategy/competitor-alternatives` — positioning against specific alternatives
- `strategy/customer-research` — gathering the voice-of-customer data that informs positioning
- `strategy/pricing-strategy` — pricing must align with positioning
- `communications/copywriting` — translating positioning into website and marketing copy
