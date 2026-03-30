<!-- reconstructed -->
---
name: "rag-architect"
description: "Design retrieval-augmented generation systems — document ingestion, embedding, vector search, and LLM integration"
workers: ["backend-developer", "systems-architect"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# RAG Architect

## When to Use
- Building an AI-powered search or Q&A system
- Client wants to "chat with their data" (documents, knowledge base, help center)
- Creating AI features that need access to custom/proprietary data
- Improving LLM responses with domain-specific context

## Workflow

### Step 1: Define the Use Case
Answer:
- What data will the system search? (documents, help articles, product info)
- Who will use it? (internal team, end users, support agents)
- What is the expected interaction? (search, Q&A, chat, recommendations)
- What is the accuracy requirement? (high precision vs. broad recall)

### Step 2: Document Ingestion Pipeline
```
Source Documents → Chunking → Embedding → Vector Storage → Ready for Query
```

**Chunking strategy:**
- Split documents into chunks of 500-1000 tokens
- Overlap chunks by 100-200 tokens to preserve context
- Preserve document metadata (title, source, section) with each chunk

### Step 3: Embedding and Storage
Using Supabase with pgvector:
```sql
-- Enable the vector extension
CREATE EXTENSION IF NOT EXISTS vector;

-- Create the documents table
CREATE TABLE documents (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  content TEXT NOT NULL,
  metadata JSONB DEFAULT '{}',
  embedding vector(1536), -- OpenAI ada-002 dimension
  created_at TIMESTAMPTZ DEFAULT now()
);

-- Create an index for similarity search
CREATE INDEX ON documents USING ivfflat (embedding vector_cosine_ops)
  WITH (lists = 100);
```

### Step 4: Query Pipeline
```
User Query → Embed Query → Vector Search → Retrieve Top K → Build Prompt → LLM → Response
```

```typescript
// lib/rag.ts
import { supabase } from '@/lib/db';

export async function queryRAG(query: string, topK: number = 5) {
  // 1. Embed the query
  const queryEmbedding = await embedText(query);

  // 2. Vector similarity search
  const { data: documents } = await supabase.rpc('match_documents', {
    query_embedding: queryEmbedding,
    match_threshold: 0.7,
    match_count: topK,
  });

  // 3. Build context from retrieved documents
  const context = documents
    .map(doc => doc.content)
    .join('\n\n---\n\n');

  // 4. Generate response with context
  const response = await generateResponse(query, context);

  return {
    answer: response,
    sources: documents.map(d => d.metadata),
  };
}
```

### Step 5: Supabase RPC Function
```sql
CREATE OR REPLACE FUNCTION match_documents(
  query_embedding vector(1536),
  match_threshold float,
  match_count int
)
RETURNS TABLE (
  id UUID,
  content TEXT,
  metadata JSONB,
  similarity float
)
LANGUAGE plpgsql
AS $$
BEGIN
  RETURN QUERY
  SELECT
    documents.id,
    documents.content,
    documents.metadata,
    1 - (documents.embedding <=> query_embedding) AS similarity
  FROM documents
  WHERE 1 - (documents.embedding <=> query_embedding) > match_threshold
  ORDER BY documents.embedding <=> query_embedding
  LIMIT match_count;
END;
$$;
```

### Step 6: API Integration
```typescript
// app/api/ask/route.ts
import { NextRequest, NextResponse } from 'next/server';
import { queryRAG } from '@/lib/rag';

export async function POST(request: NextRequest) {
  const { question } = await request.json();

  if (!question) {
    return NextResponse.json({ error: 'Question required' }, { status: 400 });
  }

  const result = await queryRAG(question);

  return NextResponse.json({
    answer: result.answer,
    sources: result.sources,
  });
}
```

## Stack Context
- **Supabase**: pgvector extension for vector storage and similarity search. Postgres functions for efficient querying.
- **Next.js**: API routes for the query endpoint. Server Components for the search/chat UI.
- **Vercel**: Edge functions for low-latency query processing. Environment variables for API keys.
- **TypeScript**: Type-safe document and query interfaces.

## Quality Gate
- [ ] Chunking strategy defined with appropriate size and overlap
- [ ] Vector index created for efficient similarity search
- [ ] Similarity threshold tuned (not just using defaults)
- [ ] Source attribution included in responses
- [ ] Error handling for embedding and LLM API failures
- [ ] RLS policies on the documents table if user-scoped data
- [ ] Response quality evaluated on 10+ test queries

## Anti-Patterns
- **No chunking strategy** — dumping entire documents as single vectors produces poor retrieval quality.
- **Ignoring metadata** — source attribution builds trust. Always track which document a chunk came from.
- **No similarity threshold** — returning low-similarity results adds noise. Set a minimum threshold.
- **Over-relying on RAG** — RAG is not magic. If the data is not in the documents, RAG cannot answer. Be honest about limitations.
- **No evaluation** — test retrieval quality with known questions. If the right document is not in the top 5, tuning is needed.

## Related Skills
- `engineering/agent-designer` — AI agent patterns that may use RAG
- `engineering/database-designer` — schema design for the vector store
- `engineering/backend` — API route patterns
- `engineering/mcp-server-builder` — building tool integrations for AI
