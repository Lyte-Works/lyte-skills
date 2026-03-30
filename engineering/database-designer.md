<!-- reconstructed -->
---
name: "database-designer"
description: "Database schema design for Supabase — tables, relationships, Row Level Security, migrations, and query optimization"
workers: ["backend-developer"]
stack: "aligned"
source: "alirezarezvani/claude-skills"
---

# Database Designer

## When to Use
- Designing a new database schema for a feature or project
- Adding tables or relationships to an existing Supabase database
- Implementing Row Level Security (RLS) policies
- Optimizing slow queries
- Planning database migrations

## Workflow

### Step 1: Requirements to Schema
Translate business requirements into database entities:
- Identify nouns in the requirements (these become tables)
- Identify relationships (one-to-many, many-to-many)
- Identify attributes (these become columns)
- Identify constraints (required fields, unique fields, valid values)

### Step 2: Design Tables
```sql
-- Example: SaaS application with users, organizations, and projects
CREATE TABLE organizations (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  name TEXT NOT NULL,
  slug TEXT UNIQUE NOT NULL,
  created_at TIMESTAMPTZ DEFAULT now() NOT NULL
);

CREATE TABLE users (
  id UUID REFERENCES auth.users(id) PRIMARY KEY,
  email TEXT UNIQUE NOT NULL,
  full_name TEXT,
  organization_id UUID REFERENCES organizations(id),
  role TEXT DEFAULT 'member' CHECK (role IN ('owner', 'admin', 'member')),
  created_at TIMESTAMPTZ DEFAULT now() NOT NULL
);

CREATE TABLE projects (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  organization_id UUID REFERENCES organizations(id) NOT NULL,
  name TEXT NOT NULL,
  status TEXT DEFAULT 'active' CHECK (status IN ('active', 'archived')),
  created_at TIMESTAMPTZ DEFAULT now() NOT NULL,
  updated_at TIMESTAMPTZ DEFAULT now() NOT NULL
);
```

### Step 3: Row Level Security
Every table with user data MUST have RLS enabled:
```sql
-- Enable RLS
ALTER TABLE projects ENABLE ROW LEVEL SECURITY;

-- Users can only see projects in their organization
CREATE POLICY "Users can view their org projects"
  ON projects FOR SELECT
  USING (
    organization_id IN (
      SELECT organization_id FROM users WHERE id = auth.uid()
    )
  );

-- Only admins and owners can create projects
CREATE POLICY "Admins can create projects"
  ON projects FOR INSERT
  WITH CHECK (
    organization_id IN (
      SELECT organization_id FROM users
      WHERE id = auth.uid() AND role IN ('owner', 'admin')
    )
  );
```

### Step 4: Indexes
Add indexes for columns used in WHERE clauses, JOINs, and ORDER BY:
```sql
CREATE INDEX idx_projects_org ON projects(organization_id);
CREATE INDEX idx_users_org ON users(organization_id);
CREATE INDEX idx_projects_status ON projects(status) WHERE status = 'active';
```

### Step 5: Type Generation
Generate TypeScript types from the schema:
```bash
npx supabase gen types typescript --project-id <project-id> > types/supabase.ts
```

Use generated types in the application:
```typescript
import type { Database } from '@/types/supabase';
type Project = Database['public']['Tables']['projects']['Row'];
```

### Step 6: Migrations
```sql
-- supabase/migrations/001_initial_schema.sql
-- Keep migrations small and focused
-- One migration per logical change
-- Always test migrations on a branch database first
```

## Stack Context
- **Supabase**: PostgreSQL database with built-in auth, RLS, and realtime. Use the Supabase CLI for migrations.
- **Next.js**: Query the database from Server Components (direct async queries) and Server Actions (mutations).
- **TypeScript**: Generate types from the schema to ensure type safety across the application.
- **Vercel**: Supabase connection string set as environment variable in Vercel.

## Quality Gate
- [ ] Every table with user data has RLS enabled
- [ ] RLS policies tested for all CRUD operations
- [ ] Foreign keys defined for all relationships
- [ ] Indexes added for frequently queried columns
- [ ] TypeScript types generated from schema
- [ ] Migrations are reversible and tested on a branch database
- [ ] No raw SQL in application code (use Supabase client)

## Anti-Patterns
- **No RLS** — disabling RLS "to make it work" is a security disaster. Fix the policies.
- **Service role key in client code** — the service role key bypasses RLS. Never expose it to the browser.
- **Over-indexing** — indexes speed up reads but slow down writes. Only index columns that appear in WHERE/JOIN/ORDER BY.
- **No migrations** — schema changes without migration files are unreproducible. Always use migrations.
- **UUID as business identifier** — use UUIDs as primary keys but add human-readable slugs or IDs for URLs and display.

## Related Skills
- `engineering/backend` — server-side patterns that use the database
- `engineering/fullstack` — full-stack data flow
- `engineering/security-engineer` — security beyond RLS
- `engineering/senior-architect` — system-level architecture decisions
