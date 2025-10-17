# DinCoder Plugin

This plugin provides a complete spec-driven development workflow using the DinCoder MCP server.

## Philosophy

**Spec-Driven Development** separates WHAT from HOW:

1. **Specify** - Define what to build (specification)
2. **Plan** - Design how to build it (technical plan)
3. **Execute** - Build following tasks (implementation)
4. **Track** - Monitor progress (analytics)

## Quick Start

### New Project

```
/spec
```

Guides you through creating a detailed specification.

### Existing Project

If you already have `.dincoder/spec.md`:

```
/plan     # Generate implementation plan
/tasks    # Break down into actionable tasks
/next     # Show what to work on now
```

## Available Commands

### Workflow Commands

- `/spec` - Create or refine specification
- `/plan` - Generate implementation plan
- `/tasks` - Generate actionable task list
- `/progress` - View progress report
- `/validate` - Check spec quality
- `/next` - Show next actionable tasks

### Specialized Agents

Type `@` to access agents:

- `@spec-writer` - Expert at creating validated specifications
- `@plan-architect` - Expert at designing technical plans
- `@task-manager` - Expert at managing tasks and progress

## File Structure

```
.dincoder/
├── spec.md          # Project specification (WHAT)
├── plan.md          # Implementation plan (HOW)
├── tasks.md         # Actionable task list
├── research.md      # Technical decisions log
└── constitution.json # Project principles
```

## MCP Tools Available

### Project Setup
- `specify_start` - Initialize .dincoder/ directory
- `prereqs_check` - Verify environment

### Specification
- `specify_describe` - Create spec.md
- `spec_validate` - Quality checks
- `spec_refine` - Update sections
- `clarify_add` / `clarify_resolve` / `clarify_list`

### Planning
- `plan_create` - Generate plan.md
- `artifacts_analyze` - Verify alignment

### Task Management
- `tasks_generate` - Create tasks.md
- `tasks_visualize` - Dependency graphs (Mermaid/Graphviz/ASCII)
- `tasks_filter` - Smart filtering (presets: next, frontend, backend, ready, cleanup)
- `tasks_search` - Fuzzy search
- `tasks_stats` - Progress analytics
- `tasks_tick` - Mark complete
- `tasks_tick_range` - Batch completion (T001-T005)

### Quality
- `quality_format` / `quality_lint` / `quality_test`
- `research_append` - Log decisions

## Workflow Example

```bash
# 1. Create specification
/spec
> I want to build a task management API...

# 2. Generate plan
/plan

# 3. Create tasks
/tasks

# 4. Check what's next
/next

# 5. Work on tasks...
# (Claude helps implement)

# 6. Track progress
/progress

# 7. Repeat
```

## Best Practices

### Specifications
- Focus on WHAT, not HOW
- Every feature needs testable acceptance criteria
- Flag assumptions as clarifications
- Be specific about what's out of scope

### Planning
- Start simple, scale as needed
- Document technical trade-offs
- Phase work for iterative delivery
- Log decisions to research.md

### Tasks
- Keep tasks atomic (1 session)
- Add metadata (phase, type, depends, priority, effort)
- Update status regularly
- Use batch operations for efficiency

### Progress Tracking
- Run `/progress` daily
- Focus on unblocked tasks
- Resolve blockers quickly
- Celebrate completed phases

## Quality Gates

✅ **Spec Validation** - Before planning
✅ **Plan-Spec Alignment** - Before tasks
✅ **Dependency Check** - Before starting tasks
✅ **Progress Review** - Regularly during execution

## Tips

- Use `/next` when you don't know what to work on
- Use `@spec-writer` for help writing specs
- Use `@task-manager` for progress insights
- Use `/validate` before moving to next phase
- Commit .dincoder/ to git for team sharing

## Support

- GitHub: https://github.com/dincoder/mcp-server
- npm: https://www.npmjs.com/package/mcp-dincoder
- Issues: https://github.com/dincoder/mcp-server/issues
