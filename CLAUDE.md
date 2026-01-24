# Claude Code Guide

A beginner-focused learning resource for Claude Code.

## Content Guidelines

1. Focus exclusively on Claude Code (the CLI agent tool)
2. Avoid generic AI/prompting advice that could apply to any chatbot (Exception: `reference/prompts.md` provides general prompting context for beginners)
3. Use practical, actionable examples
4. Write for beginners who are learning
5. Reference official Claude Code documentation when possible

## File Organization

- `home/` — Landing page and learning path
- `getting-started/` — Installation and effective communication with Claude Code
- `advanced/` — Advanced techniques, CLAUDE.md guide, skills, and autonomous loops
- `reference/` — Glossary, resources, and people to follow
- `examples/` — Project showcases

## Writing Style

- Be concise and scannable
- Use headers to break up content
- Provide code examples where relevant
- Link to official docs rather than duplicating content

## Git Workflow

- When the user says "commit [description]", immediately commit and push all changes using their description
- Do NOT look at git status, git diff, or read any files first - just execute directly
- Use this command: `git add . && git commit -m "[user's description]\n\nCo-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>" && git push`
- Example: User says "commit style change to text xyz in home page" → immediately execute the command with that exact description

## Important Notes

- Focus on Claude Code specific content only
- Do not add generic AI/prompting advice (except in `reference/prompts.md`)
- Keep navigation order: Getting Started → Advanced → Reference
- Use h2 headers (##) for main topics with dividers (---) between sections
- Add external link icons to all http/https links
- Maintain consistent formatting across all pages
- Update README.md and this CLAUDE.md when structure changes
