# DinCoder Plugin for Claude Code

Transform your development workflow with spec-driven methodology. This plugin integrates the [DinCoder MCP server](https://github.com/dincoder/mcp-server) with Claude Code, providing slash commands, specialized agents, and workflow automation.

## Features

✨ **Slash Commands** - Quick access to spec-driven workflows
🤖 **Specialized Agents** - Expert assistance for specifications, planning, and task management
📊 **Progress Tracking** - Real-time analytics and dependency visualization
🔧 **MCP Server Integration** - Automatic installation and configuration
📝 **Quality Gates** - Validation to ensure high-quality specifications

## Installation

```bash
# In Claude Code
/plugin install dincoder/claude-plugin
```

After installation, restart Claude Code to activate the plugin.

## Quick Start

### Create a New Project

```bash
/spec
```

Follow the guided workflow to create a detailed specification.

### Generate Implementation Plan

```bash
/plan
```

Transform your specification into a technical implementation plan.

### Break Down Into Tasks

```bash
/tasks
```

Generate an actionable task list with dependencies and metadata.

### Check Progress

```bash
/progress
```

View comprehensive progress report with statistics and charts.

## Commands

| Command | Description |
|---------|-------------|
| `/spec` | Create or refine project specification |
| `/plan` | Generate technical implementation plan |
| `/tasks` | Break down plan into actionable tasks |
| `/progress` | View progress report with analytics |
| `/validate` | Check specification quality |
| `/next` | Show next actionable tasks |

## Agents

Access specialized agents by typing `@`:

| Agent | Expertise |
|-------|-----------|
| `@spec-writer` | Creating validated specifications |
| `@plan-architect` | Designing technical implementation plans |
| `@task-manager` | Managing tasks and tracking progress |

## Workflow

The plugin implements a proven spec-driven methodology:

```
1. Specify → Define WHAT to build
   ├── /spec - Create specification
   └── /validate - Check quality

2. Plan → Design HOW to build it
   └── /plan - Generate implementation plan

3. Execute → Build following tasks
   ├── /tasks - Create task list
   └── /next - Show actionable tasks

4. Track → Monitor progress
   └── /progress - View analytics
```

## File Structure

The plugin creates a `.dincoder/` directory in your project:

```
.dincoder/
├── spec.md          # Project specification (WHAT)
├── plan.md          # Implementation plan (HOW)
├── tasks.md         # Actionable task list
├── research.md      # Technical decisions log
└── constitution.json # Project principles
```

## MCP Tools

The plugin automatically installs and configures the DinCoder MCP server, providing 26 tools:

**Project Setup**: `specify_start`, `prereqs_check`, `constitution_create`
**Specification**: `specify_describe`, `spec_validate`, `spec_refine`, `clarify_add/resolve/list`
**Planning**: `plan_create`, `artifacts_analyze`
**Task Management**: `tasks_generate`, `tasks_visualize`, `tasks_filter`, `tasks_search`, `tasks_stats`, `tasks_tick`, `tasks_tick_range`
**Quality**: `quality_format`, `quality_lint`, `quality_test`
**Research**: `research_append`, `artifacts_read`

## Examples

### Creating a Specification

```bash
# Use the spec command
/spec

# Claude guides you through:
# - Problem definition
# - User requirements
# - Acceptance criteria
# - Edge cases
# - Out of scope items
```

### Using Specialized Agents

```bash
# Get expert help writing specs
@spec-writer
> Help me create a specification for a REST API

# The agent will:
# - Ask targeted questions
# - Draft the specification
# - Run validation checks
# - Iterate until complete
```

### Tracking Progress

```bash
# View comprehensive progress report
/progress

# Shows:
# - Overall completion percentage
# - Phase distribution
# - Next actionable tasks
# - Blockers and dependencies
# - Recommendations
```

## Best Practices

### Specifications
- Focus on **WHAT** to build, not **HOW**
- Include testable acceptance criteria (when/then statements)
- Flag assumptions as clarifications
- Be explicit about out-of-scope items

### Planning
- Document architectural decisions with rationale
- Include trade-off analysis
- Phase work for iterative delivery
- Log key decisions to research.md

### Tasks
- Keep tasks atomic (completable in one session)
- Add metadata: `(phase: setup, type: backend, priority: high, effort: 3)`
- Use dependencies to enforce order
- Update status regularly

### Progress Tracking
- Run `/progress` daily or before standups
- Focus on unblocked tasks
- Visualize dependencies before starting work
- Celebrate completed milestones

## Quality Gates

The plugin enforces quality at each phase:

✅ **Spec Validation** - Before moving to planning
- All required sections present
- Acceptance criteria are testable
- No unresolved clarifications
- No implementation details in spec

✅ **Plan-Spec Alignment** - Before generating tasks
- All requirements addressed
- No missing features
- Technically feasible

✅ **Dependency Check** - Before starting tasks
- No circular dependencies
- Clear critical path
- Parallelization opportunities identified

## Support

- **Main Repo**: [github.com/dincoder/mcp-server](https://github.com/dincoder/mcp-server)
- **npm Package**: [npmjs.com/package/mcp-dincoder](https://www.npmjs.com/package/mcp-dincoder)
- **Issues**: [github.com/dincoder/mcp-server/issues](https://github.com/dincoder/mcp-server/issues)
- **Documentation**: See [CLAUDE.md](./CLAUDE.md) for detailed usage

## Version

Current version: 0.5.0
- Compatible with Claude Code 2.0.13+
- Requires npm for MCP server installation

## License

MIT License - see [LICENSE](./LICENSE)
