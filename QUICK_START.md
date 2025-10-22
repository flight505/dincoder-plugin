# DinCoder Plugin - Quick Start Guide

Get started with spec-driven development in 5 minutes!

## Installation (2 minutes)

```bash
# Step 1: Add marketplace
/plugin marketplace add flight505/dincoder-plugin

# Step 2: Install plugin
/plugin install dincoder

# Step 3: Restart Claude Code
# macOS/Linux: Cmd+Q then reopen
# Windows: Alt+F4 then reopen
```

## First Project (3 minutes)

### 1. Create Specification

```bash
/spec
```

Tell Claude what you want to build:
> "Build a simple todo list app for personal task management"

Claude will ask clarifying questions, then generate `spec.md`.

### 2. Generate Plan

```bash
/plan
```

Tell Claude your tech preferences:
> "Use React with TypeScript and localStorage"

Claude will generate `plan.md` with implementation details.

### 3. Create Tasks

```bash
/tasks
```

Claude will generate `tasks.md` with numbered, ordered tasks ready to execute.

## Available Commands

| Command | What It Does |
|---------|-------------|
| `/spec` | Create detailed specification |
| `/plan` | Generate implementation plan |
| `/tasks` | Break down into actionable tasks |
| `/progress` | View analytics and next steps |
| `/validate` | Check specification quality |
| `/next` | Show what to work on next |

## Available Agents

| Agent | Expertise |
|-------|-----------|
| `@spec-writer` | Creating validated specifications |
| `@plan-architect` | Designing technical plans |
| `@task-manager` | Managing tasks and progress |

**Usage:**
```
@spec-writer
> Help me create a spec for a weather app
```

## File Structure

The plugin creates:
```
.dincoder/
├── spec.md          # WHAT to build
├── plan.md          # HOW to build it
├── tasks.md         # Task list
├── research.md      # Technical decisions
└── constitution.md  # Project principles
```

## Tips

1. **Start with `/spec`** - Define WHAT before HOW
2. **Use agents** - They guide you through best practices
3. **Run `/validate`** - Check quality before moving forward
4. **Track with `/progress`** - Stay on top of your work
5. **Use `/next`** - Always know what to work on

## Help

- **Full Guide:** See [TESTING_GUIDE.md](./TESTING_GUIDE.md)
- **Issues:** https://github.com/flight505/dincoder-plugin/issues
- **Main Repo:** https://github.com/flight505/mcp-dincoder

---

**Ready to build better software!** 🚀
