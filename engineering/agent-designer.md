<!-- reconstructed -->
---
name: "agent-designer"
description: "Design AI agent architectures — tool use, planning, memory, and multi-agent coordination"
workers: ["backend-developer", "systems-architect"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Agent Designer

## When to Use
- Building AI-powered automation that requires multiple steps
- Creating systems where AI needs to use tools (search, database, APIs)
- Designing multi-agent workflows
- Client wants "intelligent automation" beyond simple chat

## Workflow

### Step 1: Define the Agent's Purpose
Answer:
- What task does the agent automate?
- What inputs does it receive?
- What outputs does it produce?
- What tools does it need access to?
- What are the boundaries of its authority? (what it can and cannot do)

### Step 2: Choose the Architecture
| Pattern | Best For | Complexity |
|---------|---------|-----------|
| Single agent + tools | One task with tool access | Low |
| Chain (sequential) | Multi-step workflow with defined order | Medium |
| Router | Task classification + delegation | Medium |
| Multi-agent | Complex workflows with specialized sub-tasks | High |

### Step 3: Define Tools
Each tool the agent can use must have:
- **Name**: Clear, descriptive
- **Description**: When and why to use this tool
- **Input schema**: What parameters it accepts
- **Output schema**: What it returns
- **Side effects**: Does it modify state? (read-only vs. write)

```typescript
// Example tool definition
const tools = [
  {
    name: 'search_knowledge_base',
    description: 'Search the knowledge base for relevant documents',
    parameters: {
      type: 'object',
      properties: {
        query: { type: 'string', description: 'Search query' },
        limit: { type: 'number', description: 'Max results', default: 5 },
      },
      required: ['query'],
    },
  },
  {
    name: 'send_email',
    description: 'Send an email via Resend. Use only when explicitly asked.',
    parameters: {
      type: 'object',
      properties: {
        to: { type: 'string' },
        subject: { type: 'string' },
        body: { type: 'string' },
      },
      required: ['to', 'subject', 'body'],
    },
  },
];
```

### Step 4: Design the Control Loop
```
Input → Plan → Execute Tool → Observe Result → Plan Next Step → ... → Final Output
```

Key decisions:
- **Max iterations**: Set a limit to prevent infinite loops (typically 5-10)
- **Error handling**: What happens when a tool call fails?
- **Human-in-the-loop**: When should the agent ask for human confirmation?
- **Memory**: Does the agent need to remember previous interactions?

### Step 5: Implement Guardrails
- **Input validation**: Validate all user inputs before passing to the agent
- **Output validation**: Check agent outputs before executing actions
- **Rate limiting**: Limit tool calls per session
- **Approval gates**: Require human approval for high-impact actions (sending emails, modifying data)
- **Audit logging**: Log all agent actions for review

### Step 6: Build and Test
```typescript
// app/api/agent/route.ts
import { NextRequest, NextResponse } from 'next/server';
import Anthropic from '@anthropic-ai/sdk';

const client = new Anthropic();

export async function POST(request: NextRequest) {
  const { message } = await request.json();

  const response = await client.messages.create({
    model: 'claude-sonnet-4-20250514',
    max_tokens: 4096,
    tools: tools,
    messages: [{ role: 'user', content: message }],
  });

  // Handle tool use in a loop
  // ... (tool execution logic)

  return NextResponse.json({ response });
}
```

## Stack Context
- **Next.js**: API routes host the agent endpoint. Server Actions for simpler agent interactions.
- **Supabase**: Store conversation history, agent logs, and tool results for audit and memory.
- **Vercel**: Serverless functions for agent endpoints. Be mindful of 10s default timeout — complex agent loops may need longer.
- **Resend**: Common tool for agents that need to send emails.
- **TypeScript**: Type all tool inputs/outputs and agent state.

## Quality Gate
- [ ] Agent purpose and boundaries clearly defined
- [ ] All tools have input/output schemas and descriptions
- [ ] Max iteration limit set to prevent infinite loops
- [ ] Error handling for tool failures
- [ ] Human-in-the-loop for high-impact actions
- [ ] Audit logging for all agent actions
- [ ] Tested with adversarial inputs (edge cases, malicious prompts)

## Anti-Patterns
- **No boundaries** — an agent that can "do anything" is dangerous. Define what it can and cannot do.
- **No iteration limit** — agents without max iterations can loop forever, burning API credits.
- **Trusting agent output blindly** — validate outputs before executing actions, especially for writes.
- **Over-engineering** — if a simple prompt + single tool call solves the problem, do not build a multi-agent system.
- **No audit trail** — if you cannot review what the agent did, you cannot debug or improve it.

## Related Skills
- `engineering/rag-architect` — retrieval systems that agents often use
- `engineering/mcp-server-builder` — building tool servers for agents
- `engineering/backend` — API patterns for hosting agents
- `engineering/security-engineer` — securing agent endpoints
