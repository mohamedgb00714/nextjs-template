# AutoPlans Project

This project is managed with [autoplans.dev](https://autoplans.dev) for AI-assisted development.

## Project Type

**Next.js Application** - Modern React framework with server-side rendering and static site generation.

## Getting Started

1. Install dependencies: `pnpm install` or `npm install --legacy-peer-deps`
2. Start development server: `pnpm run dev --port 32100` or `npm run dev -- --port 32100`
3. Build for production: `pnpm build` or `npm run build`

## Tech Stack

- **Framework**: Next.js (App Router)
- **UI Library**: React.js
- **Styling**: Tailwind CSS + Shadcn UI
- **Language**: TypeScript
- **Build Tool**: Next.js built-in bundler

## AI Development Workflow

When working with AI agents on this project:

1. **Read Context**: Always check `.autoplans/tasks.md` for current work
2. **Follow Architecture**: Review `.autoplans/architecture.md` for system design
3. **Update Tasks**: Use AutoPlans tools to track progress
4. **Sync Changes**: Run `autoplans_sync_project_to_repo` after major updates

## Available AutoPlans Tools

- `autoplans_list_tasks` - View all tasks
- `autoplans_create_task` - Add new tasks
- `autoplans_update_task` - Update task status/details
- `autoplans_bulk_update_tasks` - Update multiple tasks at once
- `autoplans_sync_project_to_repo` - Sync project files to repository

---
*This project uses AutoPlans.dev for AI-powered project management.*
