# Project Tasks

This file tracks all tasks for this Next.js project.

## Task Organization

Tasks are managed through AutoPlans.dev and can be viewed/updated using:
- `autoplans_list_tasks({projectId})` - List all tasks
- `autoplans_create_task({projectId, title, description, priority, type})` - Create new task
- `autoplans_update_task({taskId, status, priority, ...})` - Update existing task

## Initial Setup Tasks

### Not Started
- [ ] Configure environment variables (.env.local)
- [ ] Set up database (if needed)
- [ ] Configure authentication (if needed)
- [ ] Review and customize Tailwind config
- [ ] Add project-specific Shadcn components

### Template Setup Complete
- [x] Next.js application initialized
- [x] Tailwind CSS configured
- [x] TypeScript setup
- [x] Base folder structure created

## Development Guidelines

When creating new tasks:
- Use descriptive titles
- Include acceptance criteria in description
- Set appropriate priority: `low`, `medium`, `high`, or `critical`
- Choose correct type: `coding`, `design`, `documentation`, `testing`, or `other`

## Subtasks

Individual task subtasks are stored in `.autoplans/tasks/{task-id}.md`

---
*Last Updated: Auto-generated on project creation*
