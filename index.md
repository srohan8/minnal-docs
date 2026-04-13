---
layout: default
title: Documentation
description: Minnal MarketingHub documentation — get started with AI-native marketing.
---

# Minnal Documentation

Minnal is an AI-native marketing platform. You plan, create, and publish content across social platforms by talking to Claude.

## Overview {#overview}

Minnal connects to Claude via the Model Context Protocol (MCP), giving Claude the tools to schedule posts, check AI visibility, analyze competitor content, and publish across LinkedIn, Facebook, Instagram, and Reddit — all through natural conversation.

## Setup {#setup}

1. Create an account at [app.minnal.io](https://app.minnal.io)
2. Create a project for your brand
3. Connect your social platforms in Integrations
4. Copy your MCP config from Settings and add it to Claude Desktop

## Claude MCP {#mcp}

Add this to your `claude_desktop_config.json`:

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

Find your API key in the app under **Account → API key**. Fully restart Claude Desktop after saving.

## Claude Project {#claude-project}

A Claude Project gives Claude persistent memory about your brand. Without it, every conversation starts fresh.

1. In Claude Desktop, click **Projects → New Project**
2. Name it after your brand
3. Add project instructions — brand name, what you do, tone of voice, target audience, platforms, subreddits

The more specific your instructions, the more on-brand the output.

## AI Visibility {#ai-visibility}

Queries Claude, ChatGPT, Perplexity, Gemini, and Grok with your brand keywords. Scores each response 0–100 based on how prominently your brand appears.

- **0–30** — not mentioned or very weak
- **31–60** — mentioned but not prominently
- **61–100** — strong, prominent mention

Run checks from the **GEO tab** inside your project.

## Content Signals {#content-signals}

Analyzes competitor URLs you add in project settings and identifies topics they cover that you don't. Click **Analyze** to run a fresh AI-powered analysis. Results include topic gaps and suggested post angles.

## GEO Playbook {#geo-playbook}

Prioritized actions to improve how AI models find and cite your brand — comparison posts, Reddit threads, FAQ pages, Wikipedia presence, and citation outreach. Each tactic includes a ready-to-use Claude prompt in the right column.

## Scheduling {#scheduling}

Ask Claude to schedule or publish posts:

> *"Schedule a LinkedIn post about our new feature for next Tuesday at 9am."*

Claude drafts the content, queues it in Minnal, and confirms the time. Check the **Scheduled tab** to review, edit, or cancel before it publishes.

## Integrations {#integrations}

| Platform | Notes |
|---|---|
| **LinkedIn** | OAuth — posts to your personal profile |
| **Facebook** | OAuth — posts to your Pages |
| **Instagram** | Via Facebook Business — image required |
| **Reddit** | OAuth — requires subreddit per post |

## Blog (GitHub Pages) {#github-pages}

Publish blog posts directly to your GitHub Pages site as markdown files. Supports Jekyll, Hugo, Astro, and custom frontmatter.

1. Create a GitHub Personal Access Token with **repo** scope
2. In project Settings → Integrations → GitHub Pages, enter your PAT, repo (`owner/repo`), branch, posts folder, and site type
3. Ask Claude: *"Write a blog post about [topic] and publish it to our blog"*

Claude commits the markdown file directly to your repo. GitHub Pages builds it automatically.

## Knowledge Sources {#knowledge-sources}

Connect a Notion workspace so Claude can reference your existing documents when writing content. Add via **Settings → Knowledge Sources**.
