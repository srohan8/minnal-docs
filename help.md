---
layout: default
title: User Guide
description: Full user guide for Minnal MarketingHub — setup, workflows, example prompts, and troubleshooting.
---

# Minnal MarketingHub — User Guide

> **MarketingHub — Built for the Future of Search**
> Minnal is an AI-native marketing platform. You plan, create, and publish content across social platforms by talking to Claude — not clicking through a dashboard.

---

## Table of Contents

1. [What is Minnal?](#what-is-minnal)
2. [Before You Start — Prerequisites](#before-you-start)
3. [Step 1 — Install Node.js](#step-1--install-nodejs)
4. [Step 2 — Configure Claude Desktop (MCP)](#step-2--configure-claude-desktop)
5. [Step 3 — Set Up a Claude Project ⭐ Most Important](#step-3--set-up-a-claude-project)
6. [Step 4 — Create Your First Brand Project](#step-4--create-your-first-brand-project)
7. [Step 5 — Connect Your Social Platforms](#step-5--connect-your-social-platforms)
8. [Step 6 — Connect Your Blog (GitHub Pages)](#step-6--connect-your-blog-github-pages)
9. [Step 7 — Schedule Your First Post](#step-7--schedule-your-first-post)
10. [AI Visibility](#ai-visibility)
11. [Content Signals](#content-signals)
12. [GEO Playbook](#geo-playbook)
13. [Knowledge Sources](#knowledge-sources)
14. [Using Claude Effectively — Dos & Don'ts](#using-claude-effectively)
15. [Example Prompts That Work](#example-prompts-that-work)
16. [Example Workflows](#example-workflows)
17. [Pro Tips](#pro-tips)
18. [Troubleshooting & FAQ](#troubleshooting--faq)

---

## What is Minnal?

Minnal connects Claude Desktop to your social media accounts and blog via the **Model Context Protocol (MCP)**. Instead of logging into a dashboard to write and schedule posts, you simply tell Claude what you want — and it handles the rest.

**How it works:**

```
You (in Claude Desktop)
       ↓  conversation
   Claude AI
       ↓  MCP tools
  Minnal Server
       ↓  API calls
Reddit · LinkedIn · Facebook · Instagram · GitHub Pages Blog
```

**What you can do:**
- Ask Claude to plan a week of social content for your brand
- Schedule posts across multiple platforms in one conversation
- Publish blog posts directly to your GitHub Pages site
- Check how AI models mention your brand (AI Visibility)
- Identify content gaps vs your competitors (Content Signals)
- Get a prioritized GEO Playbook with ready-to-use Claude prompts
- Review and approve posts before they go live
- Check engagement analytics without leaving Claude

**What Minnal is NOT:**
- A traditional social media dashboard with a post editor
- An auto-pilot that posts without your approval
- A tool that works without Claude Desktop

---

## Before You Start

You need three things before Minnal works:

| Requirement | Why |
|---|---|
| **Node.js** (v18+) | Runs the `npx minnal-mcp@latest` client on your machine |
| **Claude Desktop** | The AI interface you talk to; Minnal runs as an MCP server inside it |
| **Minnal account** | Your API key + the server that stores credentials and schedules posts |

---

## Step 1 — Install Node.js

1. Go to **https://nodejs.org**
2. Download the **LTS** version (recommended)
3. Run the installer — default options are fine
4. Verify it worked: open a terminal and run:

```bash
node --version
# Should print something like: v20.11.0

npx --version
# Should print a version number
```

> If `npx` is not found after installing Node.js, restart your terminal or computer.

---

## Step 2 — Configure Claude Desktop

This is what connects Claude's brain to your Minnal account.

### Get your config from Minnal

1. Log into your Minnal dashboard at [app.minnal.io](https://app.minnal.io)
2. Go to **Settings**
3. Find the **MCP Configuration** card
4. Click **Copy Configuration** — you'll get a JSON block like this:

```json
{
  "mcpServers": {
    "minnal": {
      "command": "npx",
      "args": ["minnal-mcp@latest"],
      "env": {
        "MINNAL_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

### Paste it into Claude Desktop

Open the Claude Desktop config file for your platform:

**macOS:**
```
~/Library/Application Support/Claude/claude_desktop_config.json
```

**Windows:**
```
%APPDATA%\Claude\claude_desktop_config.json
```

> **Tip:** If the file doesn't exist yet, create it. If it already has content (other MCP servers), merge the `"minnal"` block inside the existing `"mcpServers"` object — don't replace the whole file.

### Restart Claude Desktop

After saving the config file, **fully quit and reopen Claude Desktop**. You should now see Minnal tools available (look for the 🔧 tools icon in a new conversation).

---

## Step 3 — Set Up a Claude Project

> ⭐ **This is the single most important step. Most users skip it and wonder why Claude writes generic content.**

A **Claude Project** gives Claude persistent memory about your brand. Without it, every conversation starts fresh and Claude has no idea who you are, what your tone is, or who your audience is.

### How to create a Claude Project

1. In Claude Desktop, click **Projects** in the sidebar
2. Click **New Project**
3. Name it after your brand (e.g. "Flow Marketing", "Acme Content")
4. Click **Add project instructions** (or "Set instructions")

### What to put in your project instructions

Paste something like this — fill in your own details:

```
Brand: [Your brand name]

What we do: [2-3 sentences about your product/service]

Target audience:
- Primary: [Who is the main person you're talking to? Age, job, pain points]
- Secondary: [Any other audience segments]

Tone of voice:
- [e.g. Conversational and honest, never corporate]
- [e.g. Personal, vulnerable, shares real struggles]
- [e.g. Technical but accessible, assumes smart readers]

What we post about:
- [Topic 1, e.g. productivity for ADHD entrepreneurs]
- [Topic 2, e.g. building in public / startup journey]
- [Topic 3, e.g. mental health in business]

What to avoid:
- [e.g. Buzzwords like "synergy", "leverage", "game-changer"]
- [e.g. Overly salesy language]
- [e.g. Making claims we can't back up]

Platforms we post on: [LinkedIn, Reddit, Facebook, Instagram]

Reddit subreddits: [e.g. r/ADHD, r/productivity, r/entrepreneur]
```

> The more specific you are here, the better Claude performs. Revisit this every few weeks as your brand voice evolves.

---

## Step 4 — Create Your First Brand Project

A **Minnal project** (separate from a Claude Project) stores your social platform credentials, audience settings, competitor URLs, and post history.

1. Log into Minnal dashboard
2. Click **Projects** → **New Project**
3. Fill in:
   - **Name** — your brand name
   - **Description** — what the brand does (Claude uses this for content context)
   - **Target audiences** — describe who you're writing for (be specific)
   - **Platforms** — select which platforms you'll post to
   - **Competitor URLs** — add competitor websites for Content Signals analysis
4. Click **Save**

> **Important:** The description and audience fields are passed to Claude when it generates content. Treat them like mini brand briefs — the more detail, the better the output.

---

## Step 5 — Connect Your Social Platforms

Go to **Integrations** in the Minnal dashboard. Connect each platform you want to post to.

### Facebook & Instagram

1. Click **Connect Facebook**
2. Log in with your Facebook account
3. Select the **Facebook Page** you want to post from
4. Instagram is automatically connected if your Instagram Business account is linked to that Facebook Page

> You need a **Facebook Page** (not a personal profile) and an **Instagram Business account** (not a personal account). Instagram posts require an image.

### LinkedIn

1. Click **Connect LinkedIn**
2. Authorize with your LinkedIn account
3. Posts go to your personal LinkedIn profile

> Company page support is on the roadmap — currently posts to personal profiles only.

### Reddit

1. Click **Connect Reddit**
2. Authorize with your Reddit account
3. Every Reddit post requires a **subreddit** — specify it when asking Claude to schedule (e.g. `r/productivity`)
4. Make sure your account has enough karma to post in your target subreddits (most require at least 5–10 karma)

---

## Step 6 — Connect Your Blog (GitHub Pages)

Minnal can publish blog posts directly to your GitHub Pages site as markdown files. Supports Jekyll, Hugo, Astro, and custom frontmatter.

### Setup

1. Create a [GitHub Personal Access Token](https://github.com/settings/tokens) with **repo** scope
2. In your Minnal project, go to **Settings → Integrations → GitHub Pages**
3. Enter:
   - **GitHub PAT** — your personal access token
   - **Repo** — in `owner/repo` format (e.g. `yourname/yourname.github.io`)
   - **Branch** — default is `main`
   - **Posts folder** — default is `_posts` (Jekyll standard)
   - **Site type** — Jekyll, Hugo, Astro, or Custom
4. Click **Connect**

### Publishing via Claude

Once connected, ask Claude:

```
Write a blog post about [topic] and publish it to our GitHub Pages blog.
```

Claude will draft the post, add the correct frontmatter for your site type, and commit it directly to your repo. GitHub Pages picks it up automatically.

---

## Step 7 — Schedule Your First Post

Once everything is connected, open Claude Desktop (make sure you're inside your Claude Project) and try:

```
Schedule a LinkedIn post for [your brand name] for tomorrow at 9am.
Topic: [what you want to write about]
Tone: [brief, story-style, educational, etc.]
```

Claude will:
1. Write the post using your brand voice from the Claude Project
2. Call the `schedule_post` tool to queue it in Minnal
3. Confirm the scheduled time and let you review or edit

Check the **Scheduled** tab in your Minnal dashboard to see and manage the queue. You can edit the content, change the time, or cancel any post before it publishes.

### Reddit posts

Reddit requires a subreddit for every post:

```
Schedule a Reddit post for r/entrepreneur tomorrow at 10am about [topic].
```

---

## AI Visibility

AI Visibility tracks how prominently your brand is mentioned when the 5 major AI models are asked about your category.

**Models checked:** Claude, ChatGPT, Perplexity, Gemini, Grok

**How it works:**
- Each model is queried with your brand keywords and audience-based questions
- Responses are scored 0–100 based on whether your brand and keywords appear
- Results show per-model scores so you can see where you're visible and where you're not

**How to run a check:**
1. Go to the **GEO** tab in your project
2. Click **Run AI Visibility Check**
3. Results appear as score cards — one per model per keyword

**Understanding the scores:**
- **0–30** — not mentioned or very weak presence
- **31–60** — mentioned but not prominently
- **61–100** — strong, prominent mention

> Retrieval-based models (Perplexity) respond quickly to new content. Training-based models (ChatGPT, Claude, Gemini, Grok) reflect longer-term brand authority.

---

## Content Signals

Content Signals analyzes competitor websites you add to your project and identifies topics they cover that you don't — so you can close the gap.

**How to use it:**
1. Add competitor URLs in your project settings (Settings → Competitors)
2. Go to the **GEO** tab → **Content Signals**
3. Click **Analyze** to run a fresh analysis
4. Review the topic gaps and suggested post ideas

**What you get:**
- A list of topics your competitors cover that you don't
- Suggested post angles for each gap
- Ready-to-use prompts to give Claude

> Analysis is powered by AI and may take 30–60 seconds. Run it monthly or after major competitor updates.

---

## GEO Playbook

The GEO Playbook gives you a prioritized list of actions to improve how AI models find and cite your brand — tailored to your visibility scores.

**Tactics included:**
- **Comparison posts** — "Your Brand vs Competitor" content gets cited heavily by Perplexity
- **Reddit threads** — authentic community discussions get indexed by retrieval models
- **FAQ pages** — comprehensive structured answers get picked up by all models
- **Wikipedia presence** — strongest training-data signal for ChatGPT, Claude, and Gemini
- **Citation outreach** — press mentions and authoritative blog citations influence future training

Each tactic includes a **ready-to-use Claude prompt** in the right column. Copy it and paste it into Claude to fast-track the content creation.

---

## Knowledge Sources

Knowledge Sources let you connect external content — like a Notion workspace — so Claude can reference your existing documents when writing content.

**Currently supported:** Notion

**How to connect:**
1. Go to **Settings → Knowledge Sources** in the dashboard
2. Add your Notion workspace ID and access token
3. Claude can now reference your Notion pages when generating content

**In Claude:**
```
List my connected knowledge sources.
```

---

## Using Claude Effectively

### ✅ Do This

**Be specific about platform, brand, timing, and tone**
> "Schedule 3 LinkedIn posts for [Brand] next week targeting ADHD founders. Keep the tone personal and a bit vulnerable — share real struggles, not polished advice."

**Ask for a weekly plan first, then approve post by post**
> "Plan this week's content for [Brand]. Give me a list of post ideas across LinkedIn and Reddit before scheduling anything."

**Set up and maintain your Claude Project instructions** (see Step 3)
> Without this, every post will sound like generic marketing copy.

**Tell Claude what performed well**
> "The story-format post last Tuesday got 3× more engagement than usual. Write more content in that style."

**Review before it goes live**
> Use the Scheduled tab to read every post before it publishes.

**Use Claude to analyse GEO context before writing**
> "Get the GEO context for [Brand] before you write anything — use the visibility scores to pick the right tactic."

---

### ❌ Don't Do This

**Don't give vague instructions**
> ❌ "Do my marketing"
> ❌ "Make some posts"
> ✅ "Schedule 2 Reddit posts for r/productivity this week about how [Brand] helps with focus"

**Don't skip the Claude Project setup**
Every conversation without project context produces generic, off-brand content. It takes 10 minutes to set up and makes everything dramatically better.

**Don't schedule without connecting a platform first**
If LinkedIn isn't connected in Integrations, scheduled LinkedIn posts will fail silently.

**Don't forget to add competitor URLs**
Content Signals needs competitor URLs in your project settings to find gaps.

**Don't use Minnal without Claude Desktop configured**
The `npx minnal-mcp@latest` MCP bridge must be running. If Claude doesn't show Minnal tools, re-check your `claude_desktop_config.json` and restart Claude Desktop.

---

## Example Prompts That Work

### Weekly planning
```
I'm planning content for [Brand] this week. We focus on [topic].
Give me 5 post ideas: 2 for LinkedIn, 2 for Reddit (r/[subreddit]), 1 for Instagram.
Don't schedule anything yet — just ideas with a one-line rationale for each.
```

### Batch scheduling
```
Schedule these 3 posts for [Brand]:
1. LinkedIn — Monday 8am — [topic/angle]
2. Reddit r/entrepreneur — Wednesday 12pm — [topic/angle]
3. LinkedIn — Friday 9am — [topic/angle]
Write each one based on our brand voice.
```

### GEO-informed post
```
Get the GEO context for [Brand], then write a post that targets our weakest AI model.
Use the content gap suggestions to pick the topic.
Schedule it for tomorrow at 9am on LinkedIn.
```

### Blog post to GitHub Pages
```
Write a blog post about [topic] for [Brand].
Make it SEO-friendly, around 600 words, with clear headings.
Publish it to our GitHub Pages blog.
```

### Performance review
```
Pull the analytics for [Brand] for the last 30 days.
Which posts got the most engagement? What patterns do you see?
What should we focus on next month based on this data?
```

### Reactive post
```
We just shipped [feature/milestone]. Write a LinkedIn post announcing it.
Tone: excited but grounded, not hype. Include what problem it solves and who it's for.
Schedule it for today at 2pm.
```

### Reddit post (community-first)
```
Write a Reddit post for r/[subreddit] about [topic].
It should feel like a genuine community contribution — no promotion, no brand mention.
Just a useful or interesting perspective that our audience would find valuable.
Schedule for tomorrow morning.
```

---

## Example Workflows

### Weekly Content Workflow (30 minutes)

1. **Monday morning:** Open Claude Desktop (in your brand's Project)
2. **GEO check:** *"Get the GEO context for [Brand] — what's our weakest model and top content gap?"*
3. **Plan:** *"Suggest this week's content for [Brand] — 5 posts across LinkedIn and Reddit targeting the gaps. Just ideas, don't schedule yet."*
4. **Review:** Go through each idea, ask Claude to adjust any that feel off
5. **Approve & schedule:** *"Great, schedule posts 1, 3, and 5. Skip 2 and 4."*
6. **Confirm:** Check the Scheduled tab in Minnal to review the queue
7. **Friday:** *"How did this week's posts perform so far? Anything to learn for next week?"*

---

### Blog Publishing Workflow

1. *"Get the GEO context for [Brand] — what topic should we write about to improve AI visibility?"*
2. *"Write a 700-word blog post on that topic. Include a clear intro, 3–4 sections with headers, and a CTA to try [Brand]."*
3. Review the draft
4. *"Publish it to our GitHub Pages blog"*
5. Share the post URL on LinkedIn and Reddit to amplify reach

---

### Monthly Performance Review

1. *"Pull analytics for [Brand] for the past month"*
2. *"What content themes got the most engagement?"*
3. *"Run a Content Signals analysis and tell me what competitor topics we're missing"*
4. *"Run an AI visibility check across all models and tell me where we're weakest"*
5. Update your Claude Project instructions if the data reveals something new about what resonates

---

## Pro Tips

**Start with one project, one platform**
Get the full loop working (Claude → schedule → publish → analytics) for one brand on one platform before expanding.

**Keep your Claude Project instructions updated**
Every time something changes about your brand — new product, new audience, new tone — update the Claude Project instructions.

**Batch your scheduling session**
Do a 30-minute session once or twice a week and schedule everything at once. Claude remembers the context across the whole conversation.

**Use the queue as your editorial calendar**
The Scheduled tab is your editorial calendar. Before approving a week's worth of posts, read them in sequence — check for repetition, tonal consistency, and timing.

**Tell Claude about your competitors**
Add to your Claude Project instructions: *"We don't want to sound like [Competitor]. Their tone is [X]. We differentiate by being [Y]."*

**Use GEO context before every content session**
Ask Claude to `get_geo_context` before writing anything. It will automatically pick the right tactic (comparison post, Reddit thread, FAQ) based on your current visibility scores.

**Publish blog posts to boost training-model visibility**
Blog posts committed to GitHub Pages get indexed over time. Authoritative, well-structured posts on your category topics are one of the strongest signals for ChatGPT, Claude, and Gemini.

---

## Troubleshooting & FAQ

### Claude doesn't show any Minnal tools

**Cause:** Claude Desktop hasn't picked up the MCP config.

**Fix:**
1. Open your `claude_desktop_config.json` and confirm the JSON is valid (no trailing commas, correct brackets)
2. Fully quit Claude Desktop (not just close the window — quit from the menu bar / taskbar)
3. Reopen Claude Desktop
4. Start a new conversation and look for the 🔧 tools icon

---

### `npx: command not found`

**Cause:** Node.js isn't installed or isn't in your PATH.

**Fix:**
1. Install Node.js from https://nodejs.org (LTS version)
2. Restart your terminal or computer
3. Run `node --version` to confirm it's installed

---

### Post failed / status shows "failed" in the Scheduled tab

**Cause:** Usually a disconnected or expired platform credential.

**Fix:**
1. Go to **Integrations** in the Minnal dashboard
2. Reconnect the affected platform (the OAuth token may have expired)
3. Re-queue the post via Claude: *"The post scheduled for [time] failed. Please reschedule it."*

---

### Claude is writing generic, off-brand content

**Cause:** Your Claude Project instructions are missing or too vague.

**Fix:**
1. Go to your Claude Project in Claude Desktop
2. Open the project instructions and add more detail — specific tone guidance, audience description, what to avoid, example phrases
3. The more specific the instructions, the more on-brand the output

---

### I connected Facebook but Instagram isn't showing

**Cause:** Your Instagram account isn't linked to the Facebook Page as a Business account.

**Fix:**
1. Go to Facebook → Settings → Linked Accounts
2. Connect your Instagram Business account to your Facebook Page
3. Reconnect via Minnal's Integrations tab

---

### GitHub Pages blog publish failed

**Cause:** PAT expired, wrong repo name, or insufficient token permissions.

**Fix:**
1. Go to [github.com/settings/tokens](https://github.com/settings/tokens) and check your token is still valid and has **repo** scope
2. In Minnal Settings → Integrations → GitHub, verify the repo is in `owner/repo` format
3. Disconnect and reconnect GitHub in the Integrations tab with a fresh token

---

### Reddit post failed — invalid subreddit or karma too low

**Cause:** The subreddit doesn't exist, is private, or your account doesn't have enough karma to post there.

**Fix:**
1. Verify the subreddit name is correct (no typos, correct capitalisation)
2. Check the subreddit rules — some require minimum karma or account age
3. Try a more open subreddit first to build karma

---

### Content Signals shows empty results

**Cause:** No competitor URLs added, or the analysis provider hit a quota limit.

**Fix:**
1. Go to project Settings → add at least one competitor URL
2. Click **Analyze** again — the system tries multiple AI providers automatically
3. If it still fails, wait a few minutes and try again

---

### AI Visibility scores seem low across all models

This is normal when you're starting out. The GEO Playbook gives you a prioritized action list. Focus on:
1. Publishing a comparison post ("Your Brand vs [Competitor]")
2. Seeding a Reddit thread in a relevant community
3. Writing a comprehensive FAQ page for your category

Run another visibility check after 1–2 weeks of content publishing to track progress.

---

## Need More Help?

- **Dashboard:** Your Minnal dashboard has context-sensitive tips throughout
- **Email:** [hello@minnal.io](mailto:hello@minnal.io)
- **Blog:** [blog.minnal.io](https://blog.minnal.io) — guides on GEO, AI visibility, and content strategy

---

*Minnal MarketingHub — Built for the Future of Search*
