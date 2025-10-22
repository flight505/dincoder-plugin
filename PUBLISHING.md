# DinCoder Plugin - Publishing to Claude Code Marketplace

This guide explains how to publish the DinCoder plugin to make it available to Claude Code users.

## Current Status

✅ **Repository Setup Complete**
- GitHub repository: `https://github.com/flight505/dincoder-plugin`
- Marketplace config: `.claude-plugin/marketplace.json` ✅
- Plugin manifest: `.claude-plugin/plugin.json` ✅
- All files pushed to GitHub ✅
- Files are publicly accessible ✅

## How Claude Code Plugin Marketplaces Work

Unlike traditional app stores, Claude Code uses a **decentralized marketplace model**:

1. **No central registry** - Anyone can create a marketplace by publishing a `marketplace.json` file
2. **Git-based distribution** - Marketplaces are hosted on GitHub, GitLab, or any Git repository
3. **User-initiated** - Users add marketplaces they trust
4. **Automatic updates** - Claude Code pulls from Git when plugins are installed/updated

### Our Marketplace Structure

```
https://github.com/flight505/dincoder-plugin
└── .claude-plugin/
    ├── marketplace.json    # Catalog of plugins (currently: 1 plugin)
    └── plugin.json         # Plugin metadata
```

## Installation Command for Users

Once published, users install the plugin like this:

```bash
# Step 1: Add our marketplace
/plugin marketplace add flight505/dincoder-plugin

# Step 2: Install the plugin
/plugin install dincoder
```

**That's it!** Claude Code will:
1. Fetch `marketplace.json` from our GitHub repo
2. Find the "dincoder" plugin entry
3. Download plugin files (commands, agents, .mcp.json)
4. Install the MCP server via `npx -y mcp-dincoder@latest`

## Publishing Steps

### 1. ✅ GitHub Repository Setup (DONE)

The repository is already set up correctly:
- [x] Repository is public
- [x] `.claude-plugin/marketplace.json` exists
- [x] `.claude-plugin/plugin.json` exists
- [x] All plugin files (commands, agents) are present
- [x] `.mcp.json` configures MCP server
- [x] README.md has installation instructions

**Verification:**
```bash
curl https://raw.githubusercontent.com/flight505/dincoder-plugin/main/.claude-plugin/marketplace.json
curl https://raw.githubusercontent.com/flight505/dincoder-plugin/main/.claude-plugin/plugin.json
```

Both should return valid JSON.

### 2. Create a GitHub Release (Recommended)

Creating a release helps users track versions:

```bash
# Tag the current version
git tag -a v0.5.0 -m "Release v0.5.0 - Claude Code plugin with marketplace"
git push origin v0.5.0
```

**Then on GitHub:**
1. Go to: https://github.com/flight505/dincoder-plugin/releases
2. Click "Draft a new release"
3. Choose tag: `v0.5.0`
4. Title: `v0.5.0 - Initial Marketplace Release`
5. Description:
   ```markdown
   ## DinCoder Plugin v0.5.0

   First official release of the DinCoder plugin for Claude Code!

   ### Features
   - ✨ 6 slash commands: /spec, /plan, /tasks, /progress, /validate, /next
   - 🤖 3 specialized agents: @spec-writer, @plan-architect, @task-manager
   - 🔧 Auto-installs mcp-dincoder MCP server
   - 📊 26 MCP tools for spec-driven development

   ### Installation
   ```bash
   /plugin marketplace add flight505/dincoder-plugin
   /plugin install dincoder
   ```

   See [README.md](./README.md) for full documentation.
   ```
6. Click "Publish release"

### 3. Test the Installation

**Test in a clean Claude Code environment:**

```bash
# Add the marketplace
/plugin marketplace add flight505/dincoder-plugin
# Expected: "Marketplace 'dincoder-marketplace' added successfully"

# List available plugins
/plugin marketplace list
# Expected: Should show "dincoder" plugin

# Install the plugin
/plugin install dincoder
# Expected: Plugin installation with MCP server setup

# Restart Claude Code (Cmd+Q then reopen)

# Verify installation
# Type / - Should see: /spec, /plan, /tasks, /progress, /validate, /next
# Type @ - Should see: @spec-writer, @plan-architect, @task-manager
```

**Detailed testing:** See [TESTING_GUIDE.md](./TESTING_GUIDE.md) for 15 comprehensive test cases.

### 4. Promote to Community (Optional)

**Official Anthropic Marketplace:**

While there isn't a single centralized Claude Code marketplace yet, you can:

1. **Submit to community catalogs:**
   - Create an issue/PR at: https://github.com/anthropics/claude-code-plugins (if exists)
   - Share on Claude Code community forums

2. **Social promotion:**
   - Tweet/post about the plugin
   - Share on Reddit: r/ClaudeAI, r/LocalLLaMA
   - Share on dev communities: Dev.to, Hacker News

3. **Documentation sites:**
   - Add to awesome-claude-code lists
   - Submit to plugin directories

**Example promotion post:**
```markdown
# DinCoder Plugin for Claude Code 🚀

Transform ideas into implementation with spec-driven development!

✨ Features:
- 6 slash commands (/spec, /plan, /tasks, etc.)
- 3 specialized agents (@spec-writer, @plan-architect, @task-manager)
- 26 MCP tools for systematic development
- Based on GitHub's Spec Kit methodology

🔧 Install:
/plugin marketplace add flight505/dincoder-plugin
/plugin install dincoder

📚 Docs: https://github.com/flight505/dincoder-plugin
```

## Marketplace Management

### Adding More Plugins to Our Marketplace

Our marketplace can host multiple plugins. To add more:

1. **Edit `.claude-plugin/marketplace.json`**:
   ```json
   {
     "name": "dincoder-marketplace",
     "plugins": [
       { /* dincoder plugin */ },
       {
         "name": "new-plugin-name",
         "version": "1.0.0",
         ...
       }
     ]
   }
   ```

2. **Add plugin files**:
   ```
   dincoder-plugin/
   ├── .claude-plugin/
   │   └── marketplace.json
   ├── dincoder/              # Current plugin
   │   ├── commands/
   │   └── agents/
   └── new-plugin/            # New plugin
       ├── commands/
       └── agents/
   ```

### Versioning Strategy

**Plugin versions** (`plugin.json`):
- Bump version when updating plugin features
- Follow semantic versioning: MAJOR.MINOR.PATCH
- Examples:
  - `0.5.1` - Bug fix
  - `0.6.0` - New command added
  - `1.0.0` - Stable release

**Marketplace versions** (`marketplace.json`):
- Bump when adding/removing plugins from marketplace
- Separate from individual plugin versions

## Update Process

When you update the plugin:

1. **Update version** in `plugin.json`:
   ```json
   {
     "version": "0.5.1",
     ...
   }
   ```

2. **Update marketplace** if needed:
   ```json
   {
     "plugins": [
       {
         "name": "dincoder",
         "version": "0.5.1",  // Update version here too
         ...
       }
     ]
   }
   ```

3. **Commit and tag**:
   ```bash
   git add .
   git commit -m "chore: bump version to 0.5.1"
   git tag v0.5.1
   git push origin main --tags
   ```

4. **Users get updates**:
   ```bash
   /plugin update dincoder
   ```

## Troubleshooting

### Issue: Users can't add marketplace

**Possible causes:**
- Repository is private → Make it public
- `marketplace.json` not in `.claude-plugin/` folder
- Invalid JSON in marketplace.json
- GitHub rate limiting

**Solution:**
```bash
# Test manually:
curl https://raw.githubusercontent.com/flight505/dincoder-plugin/main/.claude-plugin/marketplace.json

# Should return valid JSON without errors
```

### Issue: Plugin not found after adding marketplace

**Check:**
1. Plugin `name` in marketplace.json matches install command
2. All required files exist (commands/, agents/, .mcp.json)
3. Plugin version is valid semver

### Issue: MCP server doesn't install

**Check:**
1. `.mcp.json` has correct format:
   ```json
   {
     "mcpServers": {
       "dincoder": {
         "command": "npx",
         "args": ["-y", "mcp-dincoder@latest"]
       }
     }
   }
   ```
2. User has npm installed
3. Network allows npm downloads

## Monitoring

**Track plugin adoption:**
- GitHub repository stars
- GitHub clone statistics
- Issues/discussions created
- Community mentions

**Collect feedback:**
- Enable GitHub Issues
- Monitor community forums
- Create feedback issue template

## Support

**When users have issues:**

1. **Direct to documentation:**
   - [README.md](./README.md) - Installation
   - [TESTING_GUIDE.md](./TESTING_GUIDE.md) - Verification
   - [QUICK_START.md](./QUICK_START.md) - First project

2. **Common issues:**
   - See troubleshooting section in TESTING_GUIDE.md
   - Check Developer Console for errors
   - Verify prerequisites (Claude Code 2.0.13+, Node 18+)

3. **Bug reports:**
   - GitHub Issues: https://github.com/flight505/dincoder-plugin/issues
   - Include: Claude Code version, error messages, steps to reproduce

## Summary

✅ **Your plugin is published!**

**Installation command:**
```bash
/plugin marketplace add flight505/dincoder-plugin
/plugin install dincoder
```

**What happens automatically:**
1. Claude Code fetches marketplace.json from GitHub
2. Finds "dincoder" plugin entry
3. Downloads plugin files
4. Installs MCP server via npm
5. User restarts → Commands and agents available

**No further action needed** - the plugin is live and installable right now!

**Next steps:**
- ✅ Create GitHub release (recommended)
- ✅ Test installation yourself
- ⏳ Promote to community (optional)
- ⏳ Monitor feedback and iterate

---

**Plugin Live Status:** 🟢 **PUBLISHED** (installable now via GitHub)
