# Create Your First Project

Here's the full breakdown with exact commands and prompts for building a personal portfolio website.

---

## Step 1: Set up Cursor & Claude Code

You need two tools: Claude Code and Cursor.

### Install Claude Code

- On Mac, open Terminal and run: `npm install -g @anthropic-ai/claude-code`
- If you don't have npm, install Node.js first from https://nodejs.org/
- On Windows, use the native installer from Anthropic's website
- After installation, verify it works by typing: `claude`

### Install Cursor

Download from https://cursor.com and install like any normal app.

**How they connect:**

Cursor has a built-in terminal where you can run Claude Code — so you see your files, code, and AI assistant in one window.

To open the terminal in Cursor: View → Terminal or Cmd+J.

---

## Step 2: Cursor and Claude Code overview

Key commands you'll use in the terminal:

```
claude                    # Start Claude Code
cd  # Navigate into a folder
cd ..                     # Go back one folder
ls                        # List files (Mac)
dir                       # List files (Windows)
```

**Cursor Interface:**

- Left panel: File tree
- Center: Code editor
- Bottom: Terminal (for Claude Code)
- Right: Optional panels (ignore for now)

---

## Step 3: Build your first project

### Create a project folder

In Cursor, go to File → Open Folder and create a new empty folder (e.g., my-portfolio). Open the terminal and start Claude Code.

### The Planning Phase (Critical)

Use this prompt:

```
I want to build a personal portfolio website with:
- A hero section with my name and tagline
- A projects section showing 4 recent works
- An about section with my bio
- A contact section with links to Twitter and LinkedIn

Research the best way to build this and create a plan.md file with:
1. Recommended tech stack
2. File structure
3. Design considerations
4. Step-by-step implementation plan
```

Review plan.md. Adjust if needed, e.g.:

`In the plan, change the tech stack to use vanilla HTML/CSS instead of React. Keep it simple.`

### Implement

`How do I preview this in my browser? Open in localhost`

Or run:

```
npx serve
```

Then visit http://localhost:3000

### Iterate

Give feedback like:

- Make the hero section full-height (100vh). Center the text vertically.
- The projects section looks cramped. Add more padding between cards — at least 32px.
- Add a subtle hover effect on the project cards. Scale up slightly and add a shadow.
- Change the font to Inter from Google Fonts.
- Make it responsive. On mobile, stack the project cards vertically.

Refresh the browser after each change.

---

## Step 4: Save your work with GitHub

### Create a GitHub repository

Sign up at https://github.com and create a new repo (e.g., my-portfolio), and copy the URL.

### Connect and push

In Claude Code:

`Initialize git in this project and connect it to my GitHub repository: https://github.com/yourusername/my-portfolio.git`

### Commit and push

`Commit all files with the message "Initial commit - portfolio site" and push to GitHub.`

---

## Step 5: Deploy and go live

### Create a Vercel account

Sign up at https://vercel.com with GitHub.

### Deploy

Import your repo in the Vercel dashboard and click Deploy, or in Claude Code:

`Deploy this project to Vercel.`

Vercel provides a live URL. Future pushes auto-deploy.

---

## Step 6: Add a Custom Domain

Buy a domain (e.g., via Vercel or Namecheap).

Connect in Vercel: Go to Settings → Domains, add your domain, and follow DNS instructions (e.g., A record to 76.76.21.21, CNAME for www).

Wait for propagation, then your site loads on the custom domain.

This completes the hands-on workflow for your first portfolio site!
