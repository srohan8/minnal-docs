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
8. [Step 6 — Schedule Your First Post](#step-6--schedule-your-first-post)
9. [Using Claude Effectively — Dos & Don'ts](#using-claude-effectively)
10. [Example Prompts That Work](#example-prompts-that-work)
11. [Example Workflows](#example-workflows)
12. [Pro Tips](#pro-tips)
13. [Troubleshooting & FAQ](#troubleshooting--faq)

---

## What is Minnal?

Minnal connects Claude Desktop to your social media accounts via the **Model Context Protocol (MCP)**. Instead of logging into a dashboard to write and schedule posts, you simply tell Claude what you want — and it handles the rest.

**How it works:**

```
You (in Claude Desktop)
       ↓  conversation
   Claude AI
       ↓  MCP tools
  Minnal Server
       ↓  API calls
Reddit · LinkedIn · Facebook · Instagram
```

**What you can do:**
- Ask Claude to plan a week of social content for your brand
- Schedule posts across multiple platforms in one conversation
- Review and approve posts before they go live
- Check engagement analytics without leaving Claude
- Connect your Notion workspace as a knowledge source for Claude

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

1. Log into your Minnal dashboard
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
3. Name it after your brand (e.g. "Flow Marketing", "Lungiman Content")
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

A **Minnal project** (separate from a Claude Project) stores your social platform credentials, audience settings, and post history.

1. Log into Minnal dashboard
2. Click **Projects** → **New Project**
3. Fill in:
   - **Name** — your brand name
   - **Description** — what the brand does (Claude uses this)
   - **Target audiences** — describe who you're writing for (be specific)
   - **Platforms** — select which platforms you'll post to
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

> You need a **Facebook Page** (not a personal profile) and an **Instagram Business account** (not a personal account).

### LinkedIn

1. Click **Connect LinkedIn**
2. Authorize with your LinkedIn account
3. Select your personal profile or a company page

### Reddit

1. Click **Connect Reddit**
2. Authorize with your Reddit account
3. Make sure your account has enough karma to post in your target subreddits (most require at least 5–10 karma)

---

## Step 6 — Schedule Your First Post

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

Check the **Scheduled** tab in your Minnal dashboard to see and manage the queue.

---

## Using Claude Effectively

### ✅ Do This

**Be specific about platform, brand, timing, and tone**
> "Schedule 3 LinkedIn posts for Flow next week targeting ADHD founders. Keep the tone personal and a bit vulnerable — share real struggles, not polished advice."

**Ask for a weekly plan first, then approve post by post**
> "Plan this week's content for [Brand]. Give me a list of post ideas across LinkedIn and Reddit before scheduling anything."

**Set up and maintain your Claude Project instructions** (see Step 3)
> Without this, every post will sound like generic marketing copy.

**Tell Claude what performed well**
> "The story-format post last Tuesday got 3× more engagement than usual. Write more content in that style."

**Review before it goes live**
> Use the Scheduled tab to read every post before it publishes. Claude gets things wrong sometimes.

**Use Claude to analyse performance**
> "How did last month's posts perform? What should I focus on this month?"

---

### ❌ Don't Do This

**Don't give vague instructions**
> ❌ "Do my marketing"
> ❌ "Make some posts"
> ✅ "Schedule 2 Reddit posts for r/productivity this week about how [Brand] helps with focus"

**Don't skip the Claude Project setup**
Every conversation without project context produces generic, off-brand content. It takes 10 minutes to set up and makes everything dramatically better.

**Don't schedule without connecting a platform first**
If LinkedIn isn't connected in Integrations, scheduled LinkedIn posts will fail silently. Connect platforms before asking Claude to schedule.

**Don't forget to set audiences in your Minnal project**
Claude reads the audience description from your project when generating content. Vague audiences ("everyone") produce vague posts.

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

### Performance review
```
Pull the analytics for [Brand] for the last 30 days.
Which posts got the most engagement? What patterns do you see?
What should we focus on next month based on this data?
```

### Reactive post (based on something that happened)
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
2. **Plan:** *"Suggest this week's content for [Brand] — 5 posts across LinkedIn and Reddit. Just ideas, don't schedule yet."*
3. **Review:** Go through each idea, ask Claude to adjust any that feel off
4. **Approve & schedule:** *"Great, schedule posts 1, 3, and 5. Skip 2 and 4."*
5. **Confirm:** Check the Scheduled tab in Minnal to review the queue
6. **Friday:** *"How did this week's posts perform so far? Anything to learn for next week?"*

---

### Monthly Performance Review

1. *"Pull analytics for [Brand] for the past month"*
2. *"What content themes got the most engagement?"*
3. *"Based on this, what should our content focus be next month?"*
4. Update your Claude Project instructions if the data reveals something new about what resonates

---

### Responding to a Trend or News

1. *"There's a trending conversation on LinkedIn about [topic]. Write a post for [Brand] that adds our angle to this — don't just echo the trend, say something specific."*
2. Review the draft
3. *"Schedule this for today at 4pm"*

---

## Pro Tips

**Start with one project, one platform**
Get the full loop working (Claude → schedule → publish → analytics) for one brand on one platform before expanding. Complexity kills momentum.

**Keep your Claude Project instructions updated**
Every time something changes about your brand — new product, new audience, new tone — update the Claude Project. 10 minutes of maintenance pays off in every subsequent post.

**Batch your scheduling session**
Instead of scheduling one post at a time, do a 30-minute session once or twice a week and schedule everything at once. Claude remembers the context across the whole conversation.

**Use the queue as your editorial calendar**
The Scheduled tab is your editorial calendar. Before approving a week's worth of posts, read them in sequence — check for repetition, tonal consistency, and timing.

**Tell Claude about your competitors and what NOT to sound like**
Add to your Claude Project instructions: *"We don't want to sound like [Competitor]. Their tone is [X]. We differentiate by being [Y]."*

**LLM Visibility is a real channel**
Minnal includes AI visibility monitoring (how often your brand appears in Claude, ChatGPT, and Perplexity responses). Check this regularly — optimising for AI search is the next SEO.

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

### LinkedIn posts are publishing to my personal profile, not my company page

**Cause:** Company page permissions require special LinkedIn API access (r_organization_admin scope) which is pending approval.

**Status:** This is a known limitation. Currently Minnal can only post to personal LinkedIn profiles. Company page support is on the roadmap.

---

### The MCP config file doesn't exist yet

**Fix:** Create it yourself. Open a text editor, paste in the config JSON from your Minnal Settings, and save the file at the correct path:

- macOS: `~/Library/Application Support/Claude/claude_desktop_config.json`
- Windows: `%APPDATA%\Claude\claude_desktop_config.json`

Make sure the file is saved as `.json`, not `.json.txt`.

---

## Need More Help?

- **Dashboard:** Your Minnal dashboard has a Help & Tips section with quick dos and don'ts
- **Email:** Contact us at [your support email]
- **Updates:** Follow the changelog for new features and platform additions

---

*Minnal MarketingHub — Built for the Future of Search*
