# Conversation Window 047: Setting up Galaxie Nemo Claude bot

Conversation ID: a5d164ee-71dd-4a11-94d0-86a08f5f325a
Message count: 10

## Summary
**Conversation Overview**

The person initiated a session to set up an AI personal assistant named "Galaxie Nemo." After some clarification, they specified they wanted to deploy an OpenClaw agent on a VPS. Claude researched OpenClaw (an open-source autonomous AI agent framework that integrates with external LLMs and messaging platforms) and provided a summary of its capabilities, including its use of Markdown and YAML for memory storage and a systemd daemon for persistent operation.

The person confirmed their setup requirements: Ubuntu/Debian VPS, Telegram as the messaging interface, and Claude (Anthropic) as the powering LLM. Claude then fetched the official OpenClaw documentation and produced a complete step-by-step installation guide covering Node.js prerequisites, OpenClaw installation via curl script, the onboarding wizard (including Anthropic API key configuration and Telegram bot creation via BotFather), agent naming in the config file, restricting access by Telegram user ID, and verifying the systemd daemon status. Claude also flagged security considerations around prompt injection and broad permissions. The session concluded with the full setup guide delivered and an offer to help configure a system prompt for Galaxie Nemo's personality or add skills like calendar, email, or web search.

**Tool Knowledge**

Claude used `web_search` to research "OpenClaw agent framework AI" and `web_fetch` to retrieve documentation from `https://docs.openclaw.ai`, `https://docs.openclaw.ai/channels/telegram`, and `https://docs.openclaw.ai/start/getting-started`. The docs site responded with usable content across all three endpoints, making direct URL fetching reliable for this project's documentation.

## Messages

### 0001 | 2026-03-11 | aimee

Okay we're going to set up a Claude Bot named Galaxie Nemo today.

### 0002 | 2026-03-11 | setting up galaxie claude

Fun name! To make sure I help you set this up correctly — what kind of Claude Bot are you looking to build?

### 0003 | 2026-03-11 | aimee

be my personal assistant

### 0004 | 2026-03-11 | setting up galaxie claude

Got it! Galaxie Nemo as your personal assistant. Where would you like to set it up?

### 0005 | 2026-03-11 | aimee

I would like to set up an OpenClaw agent on a VPS named Galaxie Nemo

### 0006 | 2026-03-11 | setting up galaxie claude

I want to make sure I help you correctly — I'm not familiar with **OpenClaw**. Could you clarify what you mean?

### 0007 | 2026-03-11 | aimee

Can you research it

### 0008 | 2026-03-11 | setting up galaxie claude

Great find — OpenClaw is very cool! Here's what it is:

OpenClaw is a free and open-source autonomous AI agent. It runs locally (or on a VPS) and is designed to integrate with an external LLM like Claude, GPT, or DeepSeek. You interact with it through messaging apps like WhatsApp, Telegram, Signal, or Discord.

It stores conversations, long-term memory, and skills as plain Markdown and YAML files. The Gateway runs as a background daemon — on Linux that's via systemd — with a configurable heartbeat that lets the agent proactively check in and take action even when you're not messaging it.

So basically: you install OpenClaw on your VPS, connect it to Claude (or another model) via API key, hook it up to a messaging channel, give it a name (Galaxie Nemo 🦞), and it becomes your always-on personal assistant you can message from anywhere.

**A heads-up on security:** OpenClaw can be powerful but presents real security concerns — it's susceptible to prompt injection attacks, and misconfigured instances can be risky given the broad permissions it typically requires. Worth keeping in mind as we set it up.

Ready to get started? A few quick questions:

### 0009 | 2026-03-12 | aimee

Q: What OS is your VPS running?
A: Ubuntu/Debian

Q: Which messaging app will you use to talk to Galaxie Nemo?
A: Telegram

Q: Which LLM should power Galaxie Nemo?
A: Claude (Anthropic)

### 0010 | 2026-03-12 | setting up galaxie claude

Great combo! Let me pull the latest install docs to make sure the steps are accurate.

Got everything I need. Here's your full setup guide for **Galaxie Nemo** on Ubuntu + Telegram + Claude:

---

## Step 1 — Prerequisites

SSH into your VPS and make sure you have **Node 22+**:

```bash
node --version
```

If it's missing or outdated:

```bash
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash -
sudo apt install -y nodejs
```

---

## Step 2 — Install OpenClaw

```bash
curl -fsSL https://openclaw.ai/install.sh | bash
```

---

## Step 3 — Run the Onboarding Wizard

```bash
openclaw onboard --install-daemon
```

The wizard will walk you through:
- Setting your **Anthropic API key** (have it ready from [console.anthropic.com](https://console.anthropic.com))
- Choosing your model (pick **claude-sonnet-4-6** for the best balance of speed and quality)
- Connecting a channel — choose **Telegram** when prompted

For Telegram, the wizard will ask you to create a bot via [@BotFather](https://t.me/BotFather) on Telegram:
1. Message BotFather: `/newbot`
2. Give it a name: `Galaxie Nemo`
3. Copy the bot token and paste it into the wizard

---

## Step 4 — Name Your Agent

Once the wizard is done, open the config:

```bash
nano ~/.openclaw/openclaw.json
```

Set your agent's name to Galaxie Nemo and lock it down to only respond to you:

```json
{
  "agent": {
    "name": "Galaxie Nemo"
  },
  "channels": {
    "telegram": {
      "allowFrom": ["YOUR_TELEGRAM_USER_ID"]
    }
  }
}
```

To find your Telegram user ID, message [@userinfobot](https://t.me/userinfobot).

---

## Step 5 — Check the Gateway

```bash
openclaw gateway status
```

Since you used `--install-daemon`, it runs automatically as a systemd service on your VPS — so Galaxie Nemo stays alive even after reboots. 🦞

---

## Step 6 — Say Hello

Open Telegram, find your new bot, and send it a message. Galaxie Nemo should respond via Claude!

---

Want to go further? I can help you set up a **system prompt** to give Galaxie Nemo its personality, or configure **skills** to give it superpowers like calendar access, email, or web search.

