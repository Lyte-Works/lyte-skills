<!-- reconstructed -->
---
name: "mcp-server-builder"
description: "Build Model Context Protocol servers — tool definitions, resource exposure, and Claude integration"
workers: ["backend-developer", "systems-architect"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# MCP Server Builder

## When to Use
- Building custom tools for Claude or other MCP-compatible AI assistants
- Exposing application data or functionality as MCP resources
- Creating integrations between AI assistants and business systems
- Building internal tooling that AI agents can interact with

## Workflow

### Step 1: Define What to Expose
Decide what the MCP server will provide:
- **Tools**: Actions the AI can perform (query database, send email, create record)
- **Resources**: Data the AI can read (documents, configurations, dashboards)
- **Prompts**: Pre-defined prompt templates for common tasks

### Step 2: Server Setup
```typescript
// mcp-server/index.ts
import { McpServer } from '@modelcontextprotocol/sdk/server/mcp.js';
import { StdioServerTransport } from '@modelcontextprotocol/sdk/server/stdio.js';
import { z } from 'zod';

const server = new McpServer({
  name: 'my-mcp-server',
  version: '1.0.0',
});
```

### Step 3: Define Tools
```typescript
// Tool: Search the knowledge base
server.tool(
  'search_docs',
  'Search documentation for relevant information',
  {
    query: z.string().describe('Search query'),
    limit: z.number().optional().default(5).describe('Max results'),
  },
  async ({ query, limit }) => {
    const results = await searchDocuments(query, limit);
    return {
      content: [
        {
          type: 'text',
          text: JSON.stringify(results, null, 2),
        },
      ],
    };
  }
);

// Tool: Create a support ticket
server.tool(
  'create_ticket',
  'Create a new support ticket in the system',
  {
    title: z.string().describe('Ticket title'),
    description: z.string().describe('Ticket description'),
    priority: z.enum(['low', 'medium', 'high']).describe('Ticket priority'),
  },
  async ({ title, description, priority }) => {
    const ticket = await createTicket({ title, description, priority });
    return {
      content: [
        {
          type: 'text',
          text: `Ticket created: ${ticket.id} - ${ticket.title}`,
        },
      ],
    };
  }
);
```

### Step 4: Define Resources
```typescript
// Resource: Project configuration
server.resource(
  'config://project',
  'Current project configuration',
  async () => ({
    contents: [
      {
        uri: 'config://project',
        mimeType: 'application/json',
        text: JSON.stringify(await getProjectConfig()),
      },
    ],
  })
);
```

### Step 5: Connect Transport
```typescript
// Stdio transport for CLI integration
const transport = new StdioServerTransport();
await server.connect(transport);
```

### Step 6: Configure for Claude
Add to Claude Code configuration:
```json
{
  "mcpServers": {
    "my-server": {
      "command": "node",
      "args": ["./mcp-server/dist/index.js"],
      "env": {
        "SUPABASE_URL": "...",
        "SUPABASE_KEY": "..."
      }
    }
  }
}
```

## Stack Context
- **TypeScript**: MCP servers are TypeScript applications using `@modelcontextprotocol/sdk`.
- **Supabase**: Common backend for MCP tools — query data, create records, manage state.
- **Resend**: MCP tools can send emails on behalf of the user.
- **Next.js**: The MCP server can interact with the same database and services as the Next.js application.
- **GitHub**: MCP server code lives in the same repo or a dedicated tools repo.

## Quality Gate
- [ ] Every tool has a clear description and typed parameters
- [ ] Input validation using Zod schemas
- [ ] Error handling returns useful error messages
- [ ] Resources have appropriate access controls
- [ ] Server tested with MCP inspector or Claude Code
- [ ] Documentation for each tool and resource

## Anti-Patterns
- **Overly broad tools** — a tool that "does everything with the database" is not useful. Specific, focused tools are better.
- **No input validation** — even though the AI generates inputs, validate them. AI makes mistakes.
- **Exposing secrets** — MCP server has access to environment variables. Do not expose them through tool responses.
- **No error handling** — a tool that crashes on bad input breaks the AI's workflow.
- **Too many tools** — fewer, well-designed tools work better than dozens of overlapping tools.

## Related Skills
- `engineering/agent-designer` — agents that use MCP tools
- `engineering/backend` — server-side patterns
- `engineering/rag-architect` — search tools for MCP
- `engineering/database-designer` — data access patterns
