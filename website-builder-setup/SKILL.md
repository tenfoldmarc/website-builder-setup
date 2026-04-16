---
name: website-builder-setup
description: "Install the full AI website builder stack — UI/UX Pro Max, Framer Motion animations, and 21st.dev components. One skill, three tools, zero coding experience needed."
---

# Website Builder Setup

This skill walks you through installing everything you need to build professional, animated websites with Claude Code. No coding experience required.

## What Gets Installed

| Tool | What it does |
|------|-------------|
| **UI/UX Pro Max** | Gives Claude access to 50+ design styles, 161 color palettes, 57 font pairings. Your sites look designed, not generated. |
| **Framer Motion** | Adds smooth animations — page transitions, hover effects, scroll reveals. Makes sites feel alive. |
| **21st.dev Magic** | A library of 100+ polished React components Claude can pull from. Production-quality building blocks. |

## Workflow

When this skill is triggered, walk the user through each step one at a time. Be encouraging and clear — assume they have zero coding experience. If any step fails, don't stop. Acknowledge it, give them the manual command, and keep moving.

---

### Step 1: Check Prerequisites

> Before we start, let me make sure you have what we need.

Run this silently:
```bash
node --version 2>&1 && npm --version 2>&1
```

- If Node.js is installed → say "You're good — Node.js is installed. Let's go."
- If NOT installed → say:

> You need Node.js first. Go to https://nodejs.org and download the LTS version. Install it, restart your terminal, then come back and run `/website-builder-setup` again. Takes 2 minutes.

Stop here if Node is missing.

---

### Step 2: Install UI/UX Pro Max

> **Step 1 of 3: UI/UX Pro Max**
>
> This gives me a massive design library — 50+ styles, 161 color palettes, 57 font pairings. When you ask me to build a website, I'm pulling from a real design system instead of guessing. This is why the output won't look like generic AI slop.
>
> Installing now...

Run:
```bash
npm install -g uipro-cli 2>&1
```

Then:
```bash
uipro init --ai claude 2>&1
```

- On success → "UI/UX Pro Max is installed. Your design stack is ready."
- On failure → "Hit a snag. You can try manually later: `npm install -g uipro-cli && uipro init --ai claude`. Let's keep going."

---

### Step 3: Install Framer Motion

> **Step 2 of 3: Framer Motion**
>
> This teaches me how to add real animations to your websites — smooth page transitions, hover effects, scroll-triggered reveals. The stuff that makes a $500 site look like a $10,000 site.
>
> Installing now...

Run:
```bash
npm install framer-motion 2>&1
```

- On success → "Framer Motion is installed. Your sites will have real animations now."
- On failure → "Hit a snag. You can try manually later: `npm install framer-motion`. Moving on."

---

### Step 4: Set Up 21st.dev Magic

> **Step 3 of 3: 21st.dev Components**
>
> This connects me to a library of 100+ beautifully designed React components. Instead of building everything from scratch, I pull from production-quality building blocks — buttons, navbars, hero sections, cards, footers — all pre-designed and ready to use.
>
> This one needs a free API key. Here's how to get it:
>
> 1. Go to **https://21st.dev/magic/console**
> 2. Sign up or log in (it's free)
> 3. Copy your API key
> 4. Paste it here when I ask for it

Wait for the user to provide their API key.

Once they provide it, add the MCP server to their Claude Code config:

Read `~/.claude.json`, find the `mcpServers` object, and add:

```json
"21st-dev-magic": {
  "command": "npx",
  "args": ["-y", "@21st-dev/magic@latest"],
  "env": {
    "API_KEY": "THEIR_KEY_HERE"
  }
}
```

After writing the config:

> 21st.dev Magic is connected. You'll need to restart Claude Code for this one to kick in — just close and reopen your terminal after we're done.

---

### Step 5: Done

> **You're all set.** Here's what you just installed:
>
> - **UI/UX Pro Max** — 50+ styles, 161 palettes, 57 font pairings
> - **Framer Motion** — smooth, professional animations
> - **21st.dev Magic** — 100+ production-ready components
>
> **To build your first website, just tell me:**
> - What your business does
> - Who it's for
> - What vibe you want (dark, minimal, bold, playful, etc.)
>
> I'll handle the rest. Try something like:
>
> *"Build me a landing page for my consulting business targeting small business owners. Dark theme, modern, with animations."*
>
> **Important:** Restart Claude Code first so 21st.dev loads in. Then let's build something.

## Rules
- Walk through each step ONE AT A TIME
- Never dump all instructions at once
- If any install fails, don't stop — acknowledge, give manual command, keep moving
- Be encouraging and casual throughout
- Assume zero coding experience
- After everything is installed, prompt them to build their first site
