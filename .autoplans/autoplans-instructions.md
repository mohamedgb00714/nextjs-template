# Next.js Template - AI Development Instructions

## Project Context

This is a **Next.js application** using:
- App Router (not Pages Router)
- React Server Components
- TypeScript
- Tailwind CSS + Shadcn UI

## Critical Rules for AI Agents

### 1. Next.js App Router Conventions

**ALWAYS follow these patterns:**

```typescript
// ✅ Correct: Server Component (default)
export default async function Page() {
  const data = await fetchData();
  return <div>{data}</div>;
}

// ✅ Correct: Client Component (when needed)
'use client'
export default function InteractiveComponent() {
  const [state, setState] = useState(false);
  return <button onClick={() => setState(!state)}>Toggle</button>;
}

// ❌ Wrong: Using old Pages Router patterns
export async function getServerSideProps() { ... }
```

### 2. File-Based Routing

- `app/page.tsx` = Home page (`/`)
- `app/about/page.tsx` = About page (`/about`)
- `app/blog/[slug]/page.tsx` = Dynamic route (`/blog/:slug`)
- `app/layout.tsx` = Layout wrapper
- `app/loading.tsx` = Loading UI
- `app/error.tsx` = Error boundary

### 3. Component Guidelines

**When to use Server Components (default):**
- Data fetching
- Database queries
- API calls on server
- Static content

**When to use Client Components:**
- useState, useEffect, event handlers
- Browser APIs
- Interactive elements
- Third-party libraries that need window/document

### 4. Data Fetching Patterns

```typescript
// ✅ Server Component - fetch directly
async function getData() {
  const res = await fetch('https://api.example.com/data');
  return res.json();
}

export default async function Page() {
  const data = await getData();
  return <div>{JSON.stringify(data)}</div>;
}

// ✅ Client Component - use hooks
'use client'
import useSWR from 'swr';

export default function ClientPage() {
  const { data } = useSWR('/api/data', fetcher);
  return <div>{data}</div>;
}
```

### 5. Styling with Tailwind

**Use Tailwind utility classes:**
```tsx
<div className="flex items-center justify-between p-4 bg-white rounded-lg shadow-md">
  <h1 className="text-2xl font-bold text-gray-900">Title</h1>
</div>
```

**Use Shadcn components when available:**
```tsx
import { Button } from "@/components/ui/button"
<Button variant="outline">Click me</Button>
```

### 6. TypeScript Requirements

**Always define types:**
```typescript
interface User {
  id: string;
  name: string;
  email: string;
}

interface PageProps {
  params: { id: string };
  searchParams: { [key: string]: string | undefined };
}

export default async function UserPage({ params }: PageProps) {
  const user: User = await fetchUser(params.id);
  return <div>{user.name}</div>;
}
```

### 7. Image Optimization

**Always use Next.js Image component:**
```tsx
import Image from 'next/image'

<Image 
  src="/hero.jpg" 
  alt="Hero" 
  width={800} 
  height={600}
  priority // for above-the-fold images
/>
```

### 8. Environment Variables

- Client-side: Prefix with `NEXT_PUBLIC_`
- Server-only: No prefix needed
- Access: `process.env.VARIABLE_NAME`

### 9. API Routes

Create in `app/api/` directory:
```typescript
// app/api/users/route.ts
import { NextResponse } from 'next/server'

export async function GET() {
  const users = await fetchUsers();
  return NextResponse.json(users);
}

export async function POST(request: Request) {
  const body = await request.json();
  // handle POST
  return NextResponse.json({ success: true });
}
```

### 10. Performance Best Practices

1. **Use Server Components** by default
2. **Lazy load** heavy client components:
   ```typescript
   const HeavyComponent = dynamic(() => import('./HeavyComponent'), {
     loading: () => <p>Loading...</p>,
   })
   ```
3. **Optimize images** with Next.js Image
4. **Use metadata API** for SEO:
   ```typescript
   export const metadata = {
     title: 'My Page',
     description: 'Page description',
   }
   ```

## Common Mistakes to Avoid

❌ Don't use Pages Router patterns (getServerSideProps, getStaticProps)
❌ Don't add 'use client' to every component
❌ Don't forget to handle loading and error states
❌ Don't use <img> tags (use Next.js <Image>)
❌ Don't access window/document in Server Components

## AutoPlans Integration

When working on tasks:
1. Check `.autoplans/tasks.md` for current work
2. Use `autoplans_update_task` to mark progress
3. Create subtasks for complex features
4. Update architecture.md when adding major features

## Development Commands

```bash
# Install dependencies
pnpm install
npm install --legacy-peer-deps

# Run development server
pnpm run dev --port 32100
npm run dev -- --port 32100

# Build for production
pnpm build
npm run build

# Lint code
pnpm lint
npm run lint
```

## Getting Help

- Next.js Docs: https://nextjs.org/docs
- Shadcn UI: https://ui.shadcn.com
- Tailwind: https://tailwindcss.com/docs

---
*Follow these instructions for optimal AI-assisted Next.js development.*
