# Glossary

## Claude Code

The command-line tool from Anthropic that brings Claude into your terminal. It can read your files, run commands, and make changes to your codebase through natural conversation.

---

## CLAUDE.md

A markdown file that Claude automatically reads at the start of each session. Place it in your project root to provide persistent instructions—code style, architecture notes, commands to use—without repeating them every time.

---

## SKILL.md

A markdown file that defines a specialized skill for Claude Code. Skills extend Claude's capabilities for specific tasks like PR reviews, documentation generation, or framework-specific workflows.

---

## Plan Mode

A mode where Claude plans before acting. Start with `/plan` or `shift+tab`. Claude will outline an approach and ask clarifying questions before writing code. Useful for complex tasks.

---

## Act Mode

The default mode where Claude can read, write, and execute. In act mode, Claude actively makes changes to your codebase rather than just planning.

---

## Session

A single Claude Code conversation from start to `/clear` or exit. Claude remembers context within a session but starts fresh after clearing or restarting.

---

## Context Window

The amount of conversation Claude can "see" at once. As sessions get long, older parts may fall out of context. Use `/clear` between unrelated tasks to keep context focused.

---

## Slash Commands

Commands starting with `/` that trigger specific actions:
- `/help` — Show available commands
- `/clear` — Reset conversation context
- `/compact` — Summarize and compress context
- `/cost` — Show token usage and cost
- `/plan` — Enter plan mode

You can also create custom slash commands for repetitive tasks.

---

## Skills

Pre-packaged instruction sets that extend Claude for specific tasks. Skills provide domain expertise and workflows—like reviewing PRs, generating docs, or working with specific frameworks.

---

## MCP (Model Context Protocol)

A protocol that connects Claude to external tools and data sources. MCP servers let Claude interact with databases, APIs, and services beyond your local codebase.

---

## Hooks

Custom scripts that run at specific points in Claude's workflow. Hooks let you add validation, formatting, or notifications that integrate Claude into your development process.

---

## Headless Mode

Running Claude non-interactively using the `-p` flag. Useful for CI pipelines, scripts, and automated workflows where no human is present.

Example: `claude -p "Run all tests and report failures"`

---

## Agentic Coding

A development approach where AI acts as an agent—reading code, making decisions, executing commands, and iterating—rather than just responding to prompts. Claude Code is an agentic coding tool.

---

## Ralph Wiggum Loop

A technique for running Claude autonomously in a loop until a task is complete. Uses a bash script to repeatedly call Claude with instructions, letting it iterate until done.

---

## Token

A unit of text that Claude processes. Roughly 4 characters or 0.75 words. Token usage affects cost and context window limits.

---

## References

- [Claude Code Documentation](https://code.claude.com/docs/en/overview)
- [Advanced Techniques](../advanced/advanced-techniques.md)
