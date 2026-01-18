# How to Talk to Claude Code

Claude Code is different from chat-based AI. You're working together inside your actual codebase—Claude can see your files, run commands, and make changes. Here's how to communicate effectively.

## Think Colleague, Not Tool

Talk to Claude like you would a developer sitting next to you:

- "Can you look at the auth module and tell me why login is failing?"
- "I need to add a dark mode toggle to the settings page"
- "What's the best way to structure this API?"

Don't worry about "prompting techniques." Just explain what you need.

---

## Be Specific About What You Want

The more detail you provide, the better Claude can help.

**Effective:**
- "Add form validation to the contact form. Email should be required and validated. Show inline error messages."
- "Refactor the UserService to use dependency injection. Keep the existing tests passing."
- "Create a new endpoint `/api/users` that returns all users as JSON."

**Less effective:**
- "Make the form better"
- "Clean up the code"
- "Add a feature"

---

## Tell Claude What You Know

Provide context that helps Claude understand your situation:

- "This is a Next.js 14 app using the app router"
- "We're using PostgreSQL, not MongoDB"
- "The styling uses Tailwind CSS"
- "Don't modify the `legacy/` folder—that code is frozen"

This prevents Claude from making wrong assumptions about your stack.

---

## Use Screenshots for Visual Work

Paste screenshots directly when working on UI:

- "Match this design" + screenshot
- "This button is misaligned" + screenshot
- "The modal should look like this" + screenshot

Claude can see images and use them to understand layouts, identify issues, or implement designs.

---

## Ask Claude to Ask You Questions

When starting complex work, invite clarification:

- "Before we start, what questions do you have about the requirements?"
- "Ask me anything you need to clarify before implementing this"
- "What else do you need to know?"

This surfaces missing context early, before Claude starts coding.

---

## Give Feedback in the Conversation

Claude learns from your corrections during the session:

- "That's close, but use blue instead of green"
- "Good, but we also need error handling"
- "Actually, let's use a different approach..."

Don't start over—refine what Claude produced.

---

## Use /clear Between Unrelated Tasks

Reset context when switching topics:

- Finished one feature? `/clear` before starting another
- Debugging a different issue? `/clear` first
- Confused responses? `/clear` and start fresh

This prevents old context from confusing new work.

---

## Reference Your CLAUDE.md

If you have project-specific conventions, put them in a `CLAUDE.md` file so you don't repeat yourself every session:

- Code style preferences
- Testing requirements
- Files to avoid modifying
- Common commands

See the [CLAUDE.md Guide](../advanced/claude-md-guide.md) for setup instructions.

---

## Common Patterns

**Starting a new feature:**
> "I want to add user authentication. Before we start, ask me questions to understand what I'm looking for."

**Debugging:**
> "The login form isn't working. Can you look at `src/auth/LoginForm.tsx` and the auth API route to figure out what's wrong?"

**Refactoring:**
> "This file is getting too long. Can you break it into smaller modules while keeping all the tests passing?"

**Learning the codebase:**
> "I'm new to this project. Can you explain how the payment flow works?"

---

## What Makes Claude Code Different

Unlike chat-based AI where you paste code snippets, Claude Code:

- **Sees your files** — no need to copy/paste code
- **Runs commands** — can execute tests, builds, git operations
- **Makes changes** — edits files directly in your project
- **Remembers context** — within a session, builds on previous conversation

Work with it like a pair programming partner, not a search engine.

---

## References

- [Claude Code Documentation](https://code.claude.com/docs/en/overview) — Official docs
- [Claude Code Best Practices](https://www.anthropic.com/engineering/claude-code-best-practices) — Anthropic engineering blog
