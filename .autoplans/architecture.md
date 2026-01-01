# Next.js Application Architecture

## Project Overview

This is a Next.js application using the App Router architecture with React Server Components.

## Technology Stack

### Core Framework
- **Next.js**: App Router for file-based routing and server components
- **React**: UI library with hooks and component composition
- **TypeScript**: Type safety and developer experience

### Styling & UI
- **Tailwind CSS**: Utility-first CSS framework
- **Shadcn UI**: Re-usable component library built on Radix UI
- **PostCSS**: CSS processing

### Build & Development
- **Next.js Bundler**: Built-in Turbopack/Webpack for fast builds
- **ESLint**: Code linting
- **TypeScript Compiler**: Type checking

## Folder Structure

```
├── app/                    # Next.js App Router directory
│   ├── layout.tsx         # Root layout
│   ├── page.tsx           # Home page
│   └── */                 # Additional routes
├── components/            # React components
│   ├── ui/               # Shadcn UI components
│   └── */                # Custom components
├── lib/                  # Utility functions and helpers
├── public/               # Static assets
├── styles/              # Global styles
└── .autoplans/          # AutoPlans project management
```

## Routing

Next.js App Router uses file-system based routing:
- `app/page.tsx` → `/`
- `app/about/page.tsx` → `/about`
- `app/blog/[slug]/page.tsx` → `/blog/:slug`

## Component Patterns

### Server Components (Default)
- Data fetching on the server
- Direct database access
- Reduced client bundle size

### Client Components
- Interactive UI with state
- Browser APIs usage
- Event handlers
- Mark with `'use client'` directive

## Data Fetching

- **Server Components**: Use async/await directly
- **Client Components**: Use SWR or TanStack Query
- **API Routes**: Create in `app/api/` directory

## Styling Approach

1. **Tailwind Utilities**: For most styling needs
2. **Shadcn Components**: For complex UI patterns
3. **CSS Modules**: For component-specific styles (if needed)
4. **Global Styles**: In `app/globals.css`

## Build & Deployment

### Development
```bash
pnpm run dev --port 32100
# or
npm run dev -- --port 32100
```

### Production Build
```bash
pnpm build && pnpm start
# or
npm run build && npm start
```

## Best Practices

1. **Server-First**: Use Server Components by default
2. **Client When Needed**: Add 'use client' only when necessary
3. **TypeScript**: Define types for props and data
4. **Component Composition**: Break down complex UIs
5. **Responsive Design**: Mobile-first with Tailwind

## Environment Variables

Create `.env.local` for local development:
```
NEXT_PUBLIC_API_URL=
DATABASE_URL=
API_KEY=
```

## Performance Optimization

- Use Next.js `<Image>` component for images
- Implement lazy loading with `next/dynamic`
- Optimize fonts with `next/font`
- Enable static generation where possible

## Testing Strategy

- **Unit Tests**: Component testing with Vitest/Jest
- **Integration Tests**: API route testing
- **E2E Tests**: Playwright or Cypress
- **Type Safety**: TypeScript compiler

---
*Architecture evolves with project needs. Update this document as the system grows.*
