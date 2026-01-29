# Create Your First Project

This tutorial is from [**Felix Lee**](https://x.com/felixleezd) post [**The ultimate guide to vibe-coding for designers**](https://x.com/felixleezd/status/2013654252263219406?s=46&t=xXOubYP77x-93VPw93nVnA). 

I strongly recommend reading it (especially the introduction). Felix shares project examples: from easier to more complex. The following instructions are for the first simpler one (Building a Personal Portfolio) that fits the whole purpose of this website—Learn by Doing. 

I did it myself and added some personal notes (in yellow).

---

## The ultimate guide to vibe-coding for designers

Here's the full breakdown with exact commands and prompts for building a **personal portfolio website**. 

## Step 1: Set up Cursor & Claude Code

You need two tools: Claude Code and Cursor.
<div class="personal-note">
Cursor is an IDE (Integrated Development Environment), where you can create and manage your project's files and folders, write and edit code, and use your AI assistant, all in one window.
</div>

### Install Claude Code:

- On Mac, open Terminal and run: `npm install -g @anthropic-ai/claude-code`
- If you don't have npm, install Node.js first from https://nodejs.org/
- On Windows, use the native installer from Anthropic's website
- After installation, verify it works by typing: `claude`

You should see Claude Code launch in your terminal.

### Install Cursor:

Download from https://cursor.com/home and install like any normal app.


**How they connect:**

Cursor has a built-in terminal where you can run Claude Code — so you see your files, code, and AI assistant in one window.

To open the terminal in Cursor: View → Terminal or Cmd+J.

---

## Step 2: Cursor and Claude Code overview

Key commands you'll use in the terminal:

```
claude                    # Start Claude Code
cd                        # Navigate into a folder
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

### Create a project folder:

In Cursor, go to File → Open Folder and create a new empty folder (e.g., my-portfolio). Open the terminal and start Claude Code (by typing: `claude`)

### The Planning Phase (Critical):

Before writing any code, ask for a plan. Here's the sample prompt I use:

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

Claude Code will create a plan.md file in your project. Open it in Cursor and review it.

### Approve or Adjust:

If something looks off, tell Claude:

`In the plan, change the tech stack to use vanilla HTML/CSS instead of React. Keep it simple.`

<div class="personal-note">
In my case, using Opus 4.5, the suggested tech was Astro+Tailwind CSS and I accepted the plan with only one change to the last deployment step - you can <a href="https://github.com/lularocha/felix-portfolio/blob/main/plan.md">check out the plan I got in my repo</a>. Note: I have special instructions for Claude in a project level CLAUDE.md file, which means you'll probably get a different plan - that's ok go ahead with it.
</div>

### Implement:

Once the plan looks good:

Implement this project according to plan.md. Start with the HTML structure, then add CSS styling.

<div class="personal-note">
Tell Claude to: <code>Start building</code> or <code>Implement the plan</code>
</div>

Watch as files appear in your file tree: index.html, styles.css, maybe an images folder.

### Preview Locally:

Ask Claude:

`How do I preview this in my browser? Open in localhost`

It will either open a local server or tell you to simply open index.html in your browser.

For a proper local server, you can run:

`npx serve`

Then open:  `http://localhost:3000`

<div class="personal-note">
You might get a different port if you already have a server running on the 3000 port.
</div>  

### Iterate:

Now the fun part. Look at your site and give feedback:

- Make the hero section full-height (100vh). Center the text vertically.
- The projects section looks cramped. Add more padding between cards — at least 32px.
- Add a subtle hover effect on the project cards. Scale up slightly and add a shadow.
- Change the font to Inter from Google Fonts.
- Make it responsive. On mobile, stack the project cards vertically.

Each prompt → code change → refresh browser. The loop is fast.

---

## Step 4: Save your work with GitHub

Think of GitHub like Google Drive for your code and everything you've done in an IDE (like Cursor).

### Create a GitHub account:

Go to https://github.com and sign up (free).

### Create a new repository:

Click the + icon → New repository

- Name it (e.g., my-portfolio)
- Keep it Public or Private (your choice)
- Don't initialize with README (we'll create our own)
- Click Create repository

Copy the repository URL, it looks like `https://github.com/yourusername/my-portfolio.git`

### Connect your project:

In Claude Code:

`Initialize git in this project and connect it to my GitHub repository: https://github.com/yourusername/my-portfolio.git`

Or manually:

```
git init
git remote add origin https://github.com/yourusername/my-portfolio.git
```

### Create documentation:

Tell Claude to:

`Create a README.md that explains what this project is, what it does, and how to run it locally.`

And also:

`Create a CLAUDE.md file that describes the project architecture, my preferences for code style, and context for future sessions.`

<div class="personal-note">
<a href="../advanced/claude-md-guide.md">Check out more info on CLAUDE.md files</a> (It's a must Best Practice using Claude Code).
</div>

### Commit and push:

`Commit all files with the message "Initial commit - portfolio site" and push to GitHub.`

Or manually:

```
git add 
git commit -m "Initial commit - portfolio site"
git push -u origin main
```

**Your code is now saved online.**

<div class="personal-note">
If you make more changes after the Initical Commit, update your Github repository by asking Claude to <code>commit and push</code>.<br><br>
After your site is live (Step 5), the new pushes will auto deploy and the live site will be automatically updated with your changes.
</div>

---

## Step 5: Deploy and go live

### Create a Vercel account:

Go to https://vercel.com and sign up with your GitHub account.

<div class="personal-note">
Signing up with GitHub automatically connects your GitHub account to Vercel, allowing Vercel to access your repositories for deployment.
</div>

### Deploy:

Option 1: Through Vercel dashboard:

- Click Add New → Project
- Import your GitHub repository
- Click Deploy

Option 2: Through Claude Code:

`Deploy this project to Vercel.`

This one is straightforward, if you connect that repo to Vercel, it just deploys automatically when you commit (after your first time).
It will walk you through authentication and deployment.

**Result:**

Vercel gives you a live URL like my-portfolio-abc123.vercel.app

Your site is now on the internet. Share it with anyone.

Automatic updates:
From now on, every time you push to GitHub, Vercel automatically redeploys. Your live site always matches your latest code.

---

## Step 6: Add a Custom Domain

### Buy a domain:

Options:

- Directly in Vercel (easiest — auto-configures everything)
- From Namecheap, Google Domains, Cloudflare, etc.

### Connect to Vercel:

In your Vercel project dashboard:
1. Go to Settings → Domains
2. Add your domain (e.g., felixlee.dev)
3. Vercel shows you DNS records to add

Update DNS (if you bought elsewhere):

Go to your domain provider's DNS settings and add:
```
Type: A
Name: @
Value: 76.76.21.21

Type: CNAME
Name: www
Value: cname.vercel-dns.com
````

Wait 5-30 minutes for DNS propagation.

ALWAYS Verify: Visit your custom domain. Your site should load.

---
## Going further: Building real web apps

The next step in Felix's tutorial is to add advanced features to the portfolio like user authentication, AI chat, and a comment system. 

[Check the post for more](https://x.com/felixleezd/status/2013654252263219406) starting at Step 7: Pan a Web App.

---

## My Project documentation

You can checkout the whole code I created with this tutorial in my [Felix Portfolio repo](https://github.com/lularocha/felix-portfolio/tree/main)

For more tips and insights take a look at [my-docs folder](https://github.com/lularocha/felix-portfolio/tree/main/my-docs) to see my Initial Prompt and Implementation Notes.