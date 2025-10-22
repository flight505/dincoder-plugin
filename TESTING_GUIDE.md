# DinCoder Plugin Testing Guide

This guide will help you test the DinCoder plugin installation and functionality in Claude Code.

## Prerequisites Check

Before installing, verify you have all requirements:

```bash
# Check Claude Code version (must be >= 2.0.13)
claude --version

# Check Node.js version (must be >= 18)
node --version

# Check npm is installed
npm --version
```

**Expected output:**
- Claude Code: `2.0.13` or higher
- Node.js: `v18.0.0` or higher
- npm: Any recent version (e.g., `10.x.x`)

---

## Installation Testing

### Test 1: Marketplace Addition

**Command:**
```bash
/plugin marketplace add flight505/dincoder-plugin
```

**Expected Result:**
- ✅ Success message: "Marketplace 'dincoder-marketplace' added successfully"
- ✅ No errors in Developer Console

**If it fails:**
- Check GitHub repository exists: https://github.com/flight505/dincoder-plugin
- Verify `.claude-plugin/marketplace.json` is present in the repo
- Check Developer Console for detailed error messages

---

### Test 2: Plugin Installation

**Command:**
```bash
/plugin install dincoder
```

**Expected Result:**
- ✅ Success message: "Plugin 'dincoder' installed successfully"
- ✅ MCP server auto-installation triggered (npm install mcp-dincoder@latest)
- ✅ Files copied to Claude Code plugins directory

**If it fails:**
- Verify npm is working: `npm --version`
- Check network connection (npm needs to download mcp-dincoder)
- Check write permissions in Claude Code plugins directory
- Try: `/plugin list` to see installed plugins

---

### Test 3: Restart Claude Code

**Steps:**
1. **macOS/Linux:** Press `Cmd+Q` to quit, then reopen Claude Code
2. **Windows:** Press `Alt+F4` to quit, then reopen Claude Code
3. **Alternative:** Press `Cmd/Ctrl+Shift+P` → Type "Developer: Reload Window"

**Wait for:** Claude Code to fully reload (5-10 seconds)

---

## Functionality Testing

### Test 4: Slash Commands Availability

**Action:** Type `/` in Claude Code chat

**Expected Result:**
You should see these commands in the autocomplete list:
- ✅ `/spec` - Create or refine project specification
- ✅ `/plan` - Generate technical implementation plan
- ✅ `/tasks` - Break down into actionable tasks
- ✅ `/progress` - View progress report with analytics
- ✅ `/validate` - Check specification quality
- ✅ `/next` - Show next actionable tasks

**If commands don't appear:**
1. Completely quit and restart Claude Code (not just reload)
2. Check: `/plugin list` - verify "dincoder" is listed as "Active"
3. Check Developer Console (Help → Toggle Developer Tools) for errors
4. Try reinstalling: `/plugin uninstall dincoder` then `/plugin install dincoder`

---

### Test 5: Specialized Agents Availability

**Action:** Type `@` in Claude Code chat

**Expected Result:**
You should see these agents in the autocomplete list:
- ✅ `@spec-writer` - Expert at creating validated specifications
- ✅ `@plan-architect` - Expert at designing technical implementation plans
- ✅ `@task-manager` - Expert at managing tasks and tracking progress

**If agents don't appear:**
1. Same troubleshooting steps as Test 4
2. Verify agent files exist in plugin directory:
   - `agents/spec-writer.md`
   - `agents/plan-architect.md`
   - `agents/task-manager.md`

---

### Test 6: MCP Server Activation

**Action:**
1. Open Claude Code Settings
2. Navigate to: Extensions → MCP Servers
3. Look for "dincoder" in the list

**Expected Result:**
- ✅ "dincoder" server listed
- ✅ Status: "Active" or "Running"
- ✅ Command shown: `npx -y mcp-dincoder@latest`

**If server not active:**
1. Check npm can run: `npx -y mcp-dincoder@latest --help`
2. Check MCP configuration in plugin:
   - Verify `.mcp.json` exists in plugin directory
   - Content should reference `mcp-dincoder@latest`
3. Try manually starting: Settings → MCP Servers → Click "Restart" on dincoder

---

## End-to-End Workflow Testing

### Test 7: Create a Specification

**Command:**
```bash
/spec
```

**Expected Behavior:**
1. ✅ Claude asks clarifying questions about:
   - What problem you're solving
   - Who the users are
   - Success criteria
   - Constraints
   - Out of scope items

2. ✅ After providing answers, Claude creates `.dincoder/spec.md`

3. ✅ Spec includes sections:
   - Goals
   - Requirements
   - Acceptance Criteria
   - Edge Cases
   - Out of Scope

4. ✅ Claude runs `spec_validate` automatically

**Test Input Example:**
> "Build a simple todo list application for personal task management"

**Expected Output File:**
- Location: `.dincoder/spec.md`
- Contains structured specification with all required sections

---

### Test 8: Generate Implementation Plan

**Prerequisites:** Must have completed Test 7 (spec.md exists)

**Command:**
```bash
/plan
```

**Expected Behavior:**
1. ✅ Claude asks about technical preferences:
   - Technology stack
   - Architecture patterns
   - Performance requirements

2. ✅ Claude creates `.dincoder/plan.md`

3. ✅ Plan includes:
   - Milestones
   - Technical decisions
   - Implementation phases
   - Dependencies

4. ✅ Claude runs `artifacts_analyze` to verify spec-plan alignment

**Test Input Example:**
> "Use React with TypeScript, localStorage for persistence, Tailwind CSS"

---

### Test 9: Generate Tasks

**Prerequisites:** Must have completed Test 8 (plan.md exists)

**Command:**
```bash
/tasks
```

**Expected Behavior:**
1. ✅ Claude analyzes the plan
2. ✅ Creates `.dincoder/tasks.md` with numbered tasks
3. ✅ Tasks include:
   - Task IDs (T001, T002, etc.)
   - Dependencies (depends: T001)
   - Metadata (phase, type, priority, effort)
4. ✅ Claude shows dependency visualization
5. ✅ Claude shows task statistics

---

### Test 10: Progress Tracking

**Prerequisites:** Must have tasks.md with some completed tasks

**Command:**
```bash
/progress
```

**Expected Behavior:**
1. ✅ Shows overall completion percentage
2. ✅ Displays phase distribution
3. ✅ Lists next actionable tasks
4. ✅ Shows blockers (if any)
5. ✅ Provides recommendations
6. ✅ Includes ASCII progress charts

---

### Test 11: Validation

**Prerequisites:** Must have spec.md

**Command:**
```bash
/validate
```

**Expected Behavior:**
1. ✅ Runs comprehensive quality checks
2. ✅ Reports on:
   - Completeness (all sections present)
   - Acceptance criteria (testable when/then)
   - Clarifications (no unresolved [NEEDS CLARIFICATION])
   - Implementation leakage (no HOW in WHAT)
3. ✅ Shows validation results with ✅ or ❌
4. ✅ Suggests fixes if validation fails

---

### Test 12: Next Tasks

**Prerequisites:** Must have tasks.md

**Command:**
```bash
/next
```

**Expected Behavior:**
1. ✅ Shows top 5 actionable tasks (unblocked, pending)
2. ✅ Sorted by priority
3. ✅ Includes task metadata
4. ✅ Explains why each task is actionable
5. ✅ Recommends which to start first

---

## Agent Testing

### Test 13: Spec Writer Agent

**Command:**
```
@spec-writer
> Help me create a specification for a weather dashboard app
```

**Expected Behavior:**
1. ✅ Agent asks targeted discovery questions
2. ✅ Uses `specify_start` if needed
3. ✅ Uses `specify_describe` to create spec
4. ✅ Runs `spec_validate` automatically
5. ✅ Uses `spec_refine` if validation fails
6. ✅ Uses `clarify_add` for ambiguities
7. ✅ Continues until spec passes all quality gates

---

### Test 14: Plan Architect Agent

**Prerequisites:** Must have spec.md

**Command:**
```
@plan-architect
> Design an implementation plan for this spec
```

**Expected Behavior:**
1. ✅ Agent asks about technical preferences
2. ✅ Uses `plan_create` to generate plan
3. ✅ Uses `artifacts_analyze` to verify alignment
4. ✅ Uses `research_append` to log key decisions
5. ✅ Presents plan structure clearly
6. ✅ Suggests next steps (running /tasks)

---

### Test 15: Task Manager Agent

**Prerequisites:** Must have tasks.md

**Command:**
```
@task-manager
> Show me what I should work on next
```

**Expected Behavior:**
1. ✅ Uses `tasks_filter` with preset "next"
2. ✅ Uses `tasks_stats` to show overall progress
3. ✅ Uses `tasks_visualize` for dependency graph
4. ✅ Recommends specific tasks based on priority
5. ✅ Explains why recommended tasks are good choices

---

## Troubleshooting Guide

### Issue: Commands don't appear

**Solutions:**
1. Completely quit and restart Claude Code
2. Check `/plugin list` - verify "dincoder" is Active
3. Check Developer Console for errors
4. Reinstall: `/plugin uninstall dincoder` then `/plugin install dincoder`

---

### Issue: MCP server not working

**Solutions:**
1. Check npm is installed: `npm --version`
2. Manually test server: `npx -y mcp-dincoder@latest`
3. Check MCP server logs in Developer Console
4. Verify `.mcp.json` configuration
5. Restart MCP server in Settings → Extensions → MCP Servers

---

### Issue: Files not being created

**Solutions:**
1. Check current working directory in Claude Code
2. Verify write permissions
3. Check Developer Console for file system errors
4. Manually create `.dincoder/` directory
5. Try running tools directly (not via slash commands)

---

### Issue: Agent not responding correctly

**Solutions:**
1. Check agent markdown files exist in plugin directory
2. Verify agent files have proper frontmatter (`---` header)
3. Check Developer Console for parsing errors
4. Try slash commands instead of agents
5. Report issue with logs to GitHub

---

## Success Criteria

✅ **Installation Complete:**
- Marketplace added successfully
- Plugin installed without errors
- Restart completed

✅ **Functionality Working:**
- All 6 slash commands appear in autocomplete
- All 3 agents appear in autocomplete
- MCP server shows as Active in settings

✅ **Workflow Tested:**
- Can create spec with `/spec`
- Can generate plan with `/plan`
- Can create tasks with `/tasks`
- Can track progress with `/progress`
- Can validate with `/validate`
- Can see next tasks with `/next`

✅ **Agents Tested:**
- `@spec-writer` creates validated specs
- `@plan-architect` designs technical plans
- `@task-manager` manages tasks efficiently

---

## Reporting Issues

If you encounter problems:

1. **Collect information:**
   - Claude Code version
   - Node.js version
   - npm version
   - Error messages from Developer Console
   - Steps to reproduce

2. **Check existing issues:**
   - https://github.com/flight505/dincoder-plugin/issues

3. **Create new issue:**
   - Use clear title: "[Bug] Commands don't appear after installation"
   - Include all collected information
   - Attach screenshots if applicable

---

## Next Steps After Testing

Once testing is complete:

1. **Document your workflow:**
   - Save successful test cases
   - Note any customizations made
   - Share feedback with team

2. **Explore advanced features:**
   - Try `tasks_visualize` for dependency graphs
   - Use `tasks_filter` for complex queries
   - Experiment with `clarify_add/resolve` workflow

3. **Integrate into projects:**
   - Use on real projects
   - Customize templates if needed
   - Share learnings with community

---

**Happy Testing! 🚀**
