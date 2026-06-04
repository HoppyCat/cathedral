# Conversation Window 048: Evaluating KVM2 VPS hosting options (aka KVM2 VPS Claude)

Conversation ID: c701ba1e-c6b4-4e78-bbee-9a4967eb82ab
Message count: 12

## Summary
**Conversation Overview**

The person was setting up a VPS on Hostinger to run OpenClaw, an AI agent platform. The conversation covered evaluating the KVM2 VPS plan, understanding Nexos AI credits, and walking through the VPS configuration steps. Claude confirmed that KVM2 is a viable starting point for OpenClaw, noting it handles single-agent deployments but recommending a future upgrade to KVM4 for production workloads. The upgrade path discussed was KVM2 → KVM4 → KVM8 as workload grows.

Regarding Nexos AI credits, the person asked whether 20 credits represented good value. Claude explained that 20 credits equates to roughly $20, carries approximately a 90–100% markup over direct API pricing, and is suitable for getting started without API key setup. The person then asked about switching from Nexos credits to their own API keys later, and Claude confirmed this is straightforward — unused Nexos credits do not expire, and OpenClaw supports swapping in a direct provider API key via environment configuration or the dashboard without reinstalling anything.

The conversation concluded with the person going through Hostinger's VPS setup screens. Claude recommended selecting Ubuntu 24.04 LTS as the operating system over newer non-LTS versions due to better compatibility with Docker and OpenClaw. For the additional features screen, Claude advised enabling both the Malware Scanner (already selected) and the Docker Manager, as OpenClaw runs in Docker and the manager simplifies administration from the Hostinger dashboard.

## Messages

### 0001 | 2026-03-11 | aimee

I'm looking at plans on openclaw hostsinger solutions is kvm2 a good vps solution?

### 0002 | 2026-03-11 | kvm2 vps claude

**Short answer:** Yes, KVM2 on Hostinger is a solid starting point for running OpenClaw — it's the most commonly recommended entry-level plan for it, but it may not be enough if you plan to run multiple agents or heavier workloads.

Here's a quick breakdown:

**KVM2 is good for:**
- Single-agent deployments
- Getting started / testing OpenClaw
- It provides enough CPU and RAM to avoid slowdowns for basic use

**KVM2 limitations:**
- Minimum 4GB RAM handles single-agent deployments, but you may see performance degradation with multiple sessions. 8GB RAM is recommended for production workloads, since each concurrent agent requires roughly 1GB plus ~2GB base overhead.
- KVM1 is usually too slow for stable automation tasks, so KVM2 is the minimum viable plan.

**If you need more power:**
- The recommended upgrade path is KVM2 → KVM4 → KVM8 as your workload grows. Hostinger KVM4 (4 vCPU, 8GB RAM) is considered the optimal plan for production OpenClaw hosting.

**Worth noting:** IONOS's VPS L plan is only $1/month more than Hostinger's KVM2, but offers double the CPU cores and more than double the storage — so it's worth comparing if you're price-sensitive.

In short: **KVM2 is fine to start**, but budget for an upgrade to KVM4 if you're serious about running it reliably. Would you like more detail on anything — like specs, pricing, or setup?

### 0003 | 2026-03-11 | aimee

are 20 nexos ai credits good?

### 0004 | 2026-03-11 | kvm2 vps claude

**Short answer:** 20 Nexos credits ($20) is a decent starting amount for light to moderate use — it should last a while. But be aware the credits carry a significant markup over using your own API keys directly.

Here's what the numbers look like:

**How far do 20 credits go?**
- 1 Nexos credit = €1, so 20 credits ≈ $20
- One reviewer observed a cost of roughly $0.005 per message, meaning you'd need about 4,000 messages per month to spend $20 — so for casual use, 20 credits could last a long time
- Credits don't expire and are only used when a model actually runs, so there's no rush to use them up

**The catch — markup:**
- Nexos AI credits carry approximately a 90–100% markup over direct API pricing. That means $10 in Nexos credits gets you roughly $5 worth of AI compute at direct rates.
- So if you plan to use OpenClaw heavily, **bringing your own API key** (e.g. from Anthropic or OpenAI directly) is much cheaper in the long run

**Bottom line:**
- ✅ 20 credits is **fine for getting started** and experimenting without the hassle of API key setup
- ⚠️ If you end up using it a lot, switching to your own API keys will save you money

Would you like help deciding whether to use Nexos credits or set up your own API keys?

### 0005 | 2026-03-11 | aimee

what happens if i start with this and swap later?

### 0006 | 2026-03-11 | kvm2 vps claude

Good news — it's easy to swap. Based on what we already found:

- If you have purchased Nexos AI credits and want to use them with another OpenClaw instance, or switch, you can connect your own API key manually by adding it as an environment variable (`NEXOS_API_KEY` replaced with your own provider key) in the Docker configuration.

- Your remaining Nexos credits don't go to waste either — they don't expire, so any unused balance stays in your account.

- More advanced users who prefer managing their own API keys can still do so — OpenClaw's configuration supports 20+ providers.

So the flow would basically be:
1. Start with Nexos credits (easy, no setup)
2. Use up credits or decide you want cheaper direct access
3. Grab your own API key from Anthropic/OpenAI
4. Swap it in via the OpenClaw dashboard or environment config

No need to reinstall or repurchase anything. It's a pretty low-risk way to get started. Want to know more about any specific step of that process?

### 0007 | 2026-03-11 | aimee

these are my options

### 0008 | 2026-03-11 | kvm2 vps claude

For OpenClaw, pick **Ubuntu** — it's the most recommended OS for this setup.

A couple of reasons:
- Multiple guides we found specifically use **Ubuntu 24.04 LTS** for OpenClaw on Hostinger
- It has the best compatibility with Docker and npm (which OpenClaw runs on)
- It's the most widely supported, so you'll find the most help online if something goes wrong

The starred options (AlmaLinux, Debian, Rocky Linux, Ubuntu) are Hostinger's recommended picks — Ubuntu being the safest choice for your use case.

Also note: since you're deploying OpenClaw, you might want to click the **"Docker application"** tab instead and find OpenClaw there directly — that's the one-click setup path that auto-configures everything for you, which is much easier than starting from a plain OS.

Want me to walk you through which tab/option to pick next?

### 0009 | 2026-03-11 | aimee

These are my options:

### 0010 | 2026-03-11 | kvm2 vps claude

Go with **Ubuntu 24.04 LTS** — it's already selected and it's the right choice.

Avoid the newer 25.04/25.10 versions for now, as they're less tested with OpenClaw and Docker setups tend to work most reliably on LTS (Long Term Support) releases. 24.04 LTS is exactly what the guides we found recommend.

### 0011 | 2026-03-11 | aimee

[Sent screenshot]

### 0012 | 2026-03-11 | kvm2 vps claude

**Check the Docker manager too!** You'll need it for OpenClaw.

- **Malware scanner** — already ticked, free, keep it ✅
- **Docker manager** — tick this one too ✅ OpenClaw runs in Docker, and this makes managing it much easier from the Hostinger dashboard

Then hit **Finish setup**.

