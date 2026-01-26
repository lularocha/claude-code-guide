# Advanced Techniques

## Create Slash Commands

Slash commands automate repetitive tasks and save significant time. Ask Claude to help you create them:

- "What are some useful slash commands that can save me time?"
- "Make me a slash command that commits and pushes all code to GitHub"

Commands can be global or project-specific depending on your needs.

_Note: Slash Commands have been merged with Skills. [Check Thariq's post on X](https://x.com/trq212/status/2014836841846132761?s=46&t=xXOubYP77x-93VPw93nVnA)._

---

## Use Git Workflows

Beyond basic commits, leverage full Git workflows: feature branches for isolation, pull requests for code review, and meaningful commit messages for history. Claude can help manage these workflows conversationally, making version control more accessible.

*Note: If you deploy your project with platforms like Vercel, pushing changes to your repository will automatically trigger a new deployment, making your updates live without any manual steps.*

---

## Use MCP Servers

Model Context Protocol (MCP) servers connect Claude to external tools and data sources. This extends Claude's capabilities to interact with databases, APIs, file systems, and other services beyond the local codebase.

---

## Use Skills

**[Skills](./skills.md)** are specialized instruction sets that extend Claude's capabilities for specific tasks. They provide domain expertise and workflows that go beyond general coding assistance, such as PR reviews, documentation generation, or framework-specific patterns.

---

## Multi-Claude Workflows

Run parallel Claude instances for complex work. Use one instance for planning, another for implementation, or split work across different parts of a codebase. This approach helps maintain focus and can speed up larger projects.

---

## Use Headless Mode

Run Claude in CI pipelines or scripts using the `-p` flag for non-interactive execution. This enables automated code generation, testing, and other tasks without manual intervention—useful for scheduled tasks or integration into existing workflows.

---

## Customize with Hooks

Extend Claude's behavior with custom scripts that run at specific points in the workflow. Hooks let you add validation, formatting, notifications, or any custom logic that integrates Claude into your development process.

---

## References

- [Claude Code: Best practices for agentic coding](https://www.anthropic.com/engineering/claude-code-best-practices) - Anthropic Engineering
