---
name: "multi-dimensional-thinking"
description: "Meta-cognitive skill for analyzing problems across multiple dimensions — prevents tunnel vision, surfaces blind spots, maps intersections"
workers: ["ALL"]
stack: "aligned"
source: "Lyte-Works/lyte-skills (original)"
---

# Multi-Dimensional Thinking

## When to Use
- A problem has more than one axis of concern (technical + business + user + timing)
- The worker suspects tunnel vision — deep in one dimension, blind to others
- A decision will have second-order effects across domains
- The task requires cross-functional reasoning (not just domain expertise)
- Someone asks: "what are we missing?", "think about this holistically", "what are the blind spots?"
- A recommendation feels too clean — real problems have tension between dimensions

## Workflow

### Step 1: Dimension Mapping
Before solving, decompose the problem into its constituent dimensions. Do not jump to solutions.

**Core dimensions** (scan all, use what applies):

| Dimension | What it asks |
|-----------|-------------|
| **Functional** | Does it work? Does it do what it needs to do? |
| **Structural** | How does it fit into what already exists? What does it depend on? What depends on it? |
| **Temporal** | What is the timing? What happens in week 1 vs month 6 vs year 2? What decays? |
| **Economic** | What does it cost? What does it save? What is the ROI curve? |
| **Human** | Who uses this? Who is affected? What is the cognitive load? What is the emotional response? |
| **Strategic** | Does this move us toward or away from where we want to be? Does it open or close future options? |
| **Risk** | What can go wrong? What is the blast radius? What is the recovery path? |
| **Competitive** | How does this compare to alternatives? What do others do here? What advantage does this create? |

Not every dimension applies to every problem. Select the 3-6 most relevant. If fewer than 3 apply, this skill is probably overkill — proceed with normal domain reasoning.

### Step 2: Independent Analysis
Analyze each selected dimension **on its own terms**. Do not let one dimension's logic leak into another yet.

For each dimension:
1. **State the question** this dimension asks about the problem
2. **Analyze** — what does this dimension reveal?
3. **Surface the non-obvious** — what does this dimension show that the others might hide?

The goal is honest, isolated analysis. A solution that is structurally elegant but economically ruinous needs both truths stated separately before synthesis.

### Step 3: Intersection Mapping
Now cross the dimensions. For each pair of selected dimensions, ask:

- **Tension**: Where do these dimensions pull in opposite directions?
- **Synergy**: Where does serving one dimension automatically serve the other?
- **Dependency**: Does one dimension gate the other? (Can't solve X until Y is addressed)
- **Hidden constraint**: Does the intersection reveal something neither dimension shows alone?

Document only the meaningful intersections. Not every pair will have tension or synergy.

### Step 4: Second-Order Effects
For the top recommendation emerging from the analysis:

1. **First-order**: What happens immediately?
2. **Second-order**: What does that cause? (The effects of the effects)
3. **Adaptation**: How will people/systems/markets adapt to the change? Does the adaptation undermine the original intent?

Most mistakes live in second-order effects. A pricing change (economic) that drives away power users (human) that kills word-of-mouth (competitive) that stalls growth (strategic) — that chain is invisible if you only analyze pricing.

### Step 5: Synthesis
Produce a unified recommendation that:

1. **Names the dimensions considered** and why they were selected
2. **States the recommendation** clearly in 1-2 sentences
3. **Acknowledges the trade-offs** — which dimensions are being prioritized and which are being deprioritized
4. **Flags the risks** — what could invalidate this recommendation
5. **Defines the review trigger** — what signal would tell us to revisit this decision

Format:

```
## Multi-Dimensional Analysis: [Problem]

**Dimensions analyzed**: [list]

**Recommendation**: [1-2 sentences]

**Trade-offs**:
- Prioritizing [dimension]: [what we gain]
- Deprioritizing [dimension]: [what we accept]

**Risks**:
- [Risk + what would trigger it]

**Revisit when**: [signal or condition]
```

## Stack Context
This is a pure thinking methodology — no tech stack dependency. It works identically whether the worker is writing code, planning strategy, designing UI, or drafting copy. The output format is markdown, which fits Notion (strategy docs), GitHub (ADRs, PR descriptions), and direct conversation.

## Quality Gate
- [ ] At least 3 dimensions identified and analyzed independently
- [ ] Intersections mapped — tensions and synergies documented
- [ ] Second-order effects considered for the recommendation
- [ ] Trade-offs are explicit — no "best of all worlds" claims
- [ ] Recommendation is actionable, not just analytical
- [ ] The analysis added value — it surfaced something the worker would have missed with single-dimension thinking

## Anti-Patterns
- **Dimension soup** — analyzing 8 dimensions when 3 matter. More dimensions ≠ better analysis. Select ruthlessly.
- **False balance** — treating all dimensions as equally important. Some dimensions are load-bearing for a given problem; others are context. Prioritize.
- **Analysis paralysis** — using multi-dimensional thinking as an excuse to delay action. The goal is better decisions, not exhaustive analysis. Time-box if needed.
- **Dimension contamination** — letting economic reasoning shape the human analysis, or letting structural constraints limit strategic thinking before synthesis. Keep them independent until Step 3.
- **Missing the obvious** — this skill is for complex problems with real tension. If the answer is obvious, just do it. Not every task needs multi-dimensional analysis.
- **Synthetic harmony** — forcing a recommendation that "serves all dimensions." Real recommendations have trade-offs. If yours doesn't, you are lying to yourself.

## Related Skills
- `core/decision-logger` — log the output of multi-dimensional analysis as a decision record
- `strategy/positioning` — strategic dimension often dominates positioning problems
- `engineering/senior-architect` — structural dimension often dominates architecture problems
- `advisory/ceo-advisor` — CEO-level decisions almost always require multi-dimensional analysis
