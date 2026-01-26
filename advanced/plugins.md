# Plugins

## What Are Claude Code Plugins?

Claude Code doesn't use traditional "Templates" - instead it has a **Plugin System** that packages reusable components:
- **Slash commands** - Custom commands like `/test`, `/review`
- **Agents** - Specialized AI agents for specific tasks
- **Skills** - Autonomous capabilities Claude invokes automatically
- **Hooks** - Event handlers (pre-commit, post-task automation)
- **MCP servers** - External tool integrations
- **LSP servers** - Language-specific code intelligence

---

## Installation Strategy: Global + Project-Specific

### The Smart Approach

Install plugins **once globally**, then enable/disable them per project as needed.

**Mental Model:**
- **Global installation** = "I own this tool" (installed once)
- **Project-level control** = "This project uses this tool" (enable/disable)

### Installation Commands

#### 1. Install Globally (Recommended for Most Plugins)

```bash
# Install for ALL your projects (user scope)
claude plugin install <plugin-name> --scope user

# Example: Code review plugin available everywhere
claude plugin install code-reviewer --scope user
```

**Benefits:**
- Install once, use anywhere
- No duplication across projects
- Easy to manage updates centrally

#### 2. Install for Specific Project (Team-Shared)

```bash
# Install for THIS project only (tracked in git)
cd /path/to/your-project
claude plugin install <plugin-name> --scope project
```

**Use when:**
- Team needs standardized tools
- Project-specific requirements
- Want plugin config in version control

#### 3. Install Locally (Temporary/Experimental)

```bash
# Install for THIS project only (gitignored)
claude plugin install <plugin-name> --scope local
```

**Use when:**
- Testing a plugin
- Sensitive/private configurations
- Don't want to commit to version control

### Managing Plugins Per Project

```bash
# Navigate to your project
cd /path/to/your-project

# Enable a globally-installed plugin for this project
claude plugin enable code-reviewer

# Disable a plugin for this project
claude plugin disable code-reviewer
```

---

## Quick Command Reference

### Discovery & Installation

```bash
# List configured marketplaces
claude plugin marketplace list

# Add a marketplace
claude plugin marketplace add <url-or-path>

# Install a plugin
claude plugin install <plugin-name> --scope user

# Install from specific marketplace
claude plugin install <plugin-name>@<marketplace> --scope user
```

### Management

```bash
# Update a plugin
claude plugin update <plugin-name>

# Uninstall a plugin
claude plugin uninstall <plugin-name>

# Enable plugin for current project
claude plugin enable <plugin-name>

# Disable plugin for current project
claude plugin disable <plugin-name>

# Validate a plugin manifest
claude plugin validate <path>
```

### Usage

```bash
# Use plugin commands (syntax varies by plugin)
/plugin-name:command

# Get help
/help
```
---

## Recommended Workflow

### Phase 1: Start Minimal

1. **Check available marketplaces**
   ```bash
   claude plugin marketplace list
   ```

2. **Install 1-2 essential plugins globally**
   ```bash
   claude plugin install code-reviewer --scope user
   ```

3. **Enable in specific projects as needed**
   ```bash
   cd /path/to/project
   claude plugin enable code-reviewer
   ```
