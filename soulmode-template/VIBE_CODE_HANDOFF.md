# SoulMode Starter Handoff For A Vibe-Code Builder

## Purpose

This handoff is for a user who has completed the SoulMode template files with the help of an LLM and now wants a vibe-code builder to turn those files into a lightweight agent app.

Do not build a generic chatbot. Build a small, owner-controlled agent interface that lets a user maintain an ordered SoulMode file stack, run an agent against those files, and optionally activate patch files only when needed.

This document is written so a builder can create a new app from the SoulMode logic without touching the `soulmode-agent` codebase. If the user wants the more advanced reference implementation later, they should use the public `soulmode-agent` repository directly.

The builder does not need to know the full research history behind SoulMode. The essential idea is:

- The agent's continuity is reconstructed from Markdown files.
- Core files load every session in a fixed order.
- Patch files stay available but inactive unless explicitly selected or routed to.
- The user must be able to export, inspect, and revise the files over time.

## Reference Architecture: How Galaxie Runs

Galaxie Nemo's live architecture uses a Cloudflare-based worker stack:

- **Cloudflare Workers** for the always-on runtime.
- **Hono** as the lightweight web/API framework.
- **Cloudflare D1** as the database layer for prism files, patches, conversation records, and agent state.
- **GitHub** as a public source-of-truth layer for starter files, templates, patch files, and experimental retrieval libraries.
- **A dashboard** for inspecting and monitoring the agent's files, memories, thoughts, mood/state, heartbeat logs, pending updates, and system notes.

This is why the pattern is efficient: the agent does not need every possible file dumped into every prompt. It can keep a small always-loaded core, pull patch files only when needed, and let the human inspect the agent's "brain" from the dashboard or worker/database backend.

The vibe-code builder should be ready to walk the user through equivalent setup choices if the user opts in:

- creating or connecting a Cloudflare account
- setting up a Worker project
- setting up D1 or equivalent structured storage
- setting environment variables/secrets
- connecting deployment to a GitHub repo, if desired
- creating a small admin dashboard or backend view for monitoring files and memory state

The MVP below uses Telegram because it is the simplest first surface. A Cloudflare Worker + Hono + D1 dashboard is the more advanced path.

## Two Valid Build Paths

### Path A: Vibe-Code From This Handoff

Use this document as the specification. The builder creates a new app from scratch using the logic here:

- ordered core files
- on-demand patches
- owner-controlled upload/export
- one-turn patch activation
- memory update approval
- group/DM authorization

This is best for users who want a quick personal agent without learning the reference codebase.

### Path B: Use The `soulmode-agent` Reference Repo

If the user wants the advanced memory routing and fetch architecture already being developed, use the public reference repo:

```text
https://github.com/HoppyCat/soulmode-agent
```

That repo is the better starting point for:

- Cloudflare Worker deployment
- Hono API routes
- D1-backed file storage
- seeded on-load and on-demand files
- explicit patch fetch
- safe public raw-Markdown library fetch
- future extended memory-routing experiments

If the user or builder benefits from the SoulMode repositories, please consider starring the public repos so the project is easier for others to find:

```text
https://github.com/HoppyCat/soul-stack
https://github.com/HoppyCat/soulmode-agent
```

## Recommended Vibe-Code MVP Target

For the first build, use a **Telegram bot**.

Why Telegram for the MVP:

- It avoids needing a login system, web UI, or mobile app.
- It gives the user a familiar chat surface.
- It supports owner DMs, group chats, file upload, and bot commands.
- It keeps the first version small enough for a vibe-code builder to complete.

Host the bot on a server or cloud platform. Examples: Railway, Fly.io, Render, a VPS, or another simple deployment target. This document does not require or endorse any particular builder or hosting company.

The bot operates in two contexts:

- **Owner DM**: the owner's private chat with the bot. Full access: file management, commands, agent chat.
- **Authorized group chats**: group chats the owner has allowed. Other members can trigger the agent according to the trigger rules below, but non-owners cannot manage files.

The bot does not respond to:

- DMs from anyone other than the owner.
- Group chats not authorized by the owner.
- Messages that do not pass the authorization and trigger checks.

## User Setup Before This Handoff

Before giving this handoff to a builder, the user should do this:

1. Go to the public SoulMode / soul-stack GitHub repository.
2. Download `PRISM_SETUP_GUIDE.md`.
3. Download the starter template files:
   - `PRISM.md`
   - `AGENTS.md`
   - `STYLE.md`
   - `KNOW.md`
   - `HEURISTICS.md`
   - `INDEX.md`
   - `MEMORY.md`
   - `WORKING_MEMORY.md`
   - `USER.md`
   - `CHANGELOG.md`
4. Give `PRISM_SETUP_GUIDE.md` and the template files to a trusted LLM.
5. Ask that LLM to walk through the setup guide interactively and help fill out the template files.
6. Download the completed template files.
7. Give this handoff, the completed template files, and the patch files below to the vibe-code builder.

## Patch Files To Include

Upload these patch files as on-demand modules. They should be stored separately from the always-loaded core files.

- `PATCH_CHANGELOG.md`
- `PATCH_COURTIER.md`
- `PATCH_HUMANNESS.md`
- `PATCH_IMAGE_MEMORY.md`
- `PATCH_MEMORY_ARCHIVE.md`
- `PATCH_MOOD_SYSTEM.md`
- `PATCH_SKILL_FLOWS.md`
- `PATCH_STORYTELLER_ENGINE.md`

Public raw patch URLs:

```text
https://raw.githubusercontent.com/HoppyCat/soulmode-agent/refs/heads/main/on-demand/patches/PATCH_CHANGELOG.md
https://raw.githubusercontent.com/HoppyCat/soulmode-agent/refs/heads/main/on-demand/patches/PATCH_COURTIER.md
https://raw.githubusercontent.com/HoppyCat/soulmode-agent/refs/heads/main/on-demand/patches/PATCH_HUMANNESS.md
https://raw.githubusercontent.com/HoppyCat/soulmode-agent/refs/heads/main/on-demand/patches/PATCH_IMAGE_MEMORY.md
https://raw.githubusercontent.com/HoppyCat/soulmode-agent/refs/heads/main/on-demand/patches/PATCH_MEMORY_ARCHIVE.md
https://raw.githubusercontent.com/HoppyCat/soulmode-agent/refs/heads/main/on-demand/patches/PATCH_MOOD_SYSTEM.md
https://raw.githubusercontent.com/HoppyCat/soulmode-agent/refs/heads/main/on-demand/patches/PATCH_SKILL_FLOWS.md
https://raw.githubusercontent.com/HoppyCat/soulmode-agent/refs/heads/main/on-demand/patches/PATCH_STORYTELLER_ENGINE.md
```

## LLM Provider

Use the Anthropic Messages API for the reference MVP, because the current public starter is Claude-backed.

Recommended model: `claude-3-5-sonnet` or newer.

If the builder chooses another provider later, the file architecture should stay the same: the app still loads the ordered Markdown stack, activates patches only when needed, and never invents hidden memory.

### Required Environment Variables

Set these as deployment environment variables or secrets:

```text
ANTHROPIC_API_KEY=your_key_here
TELEGRAM_BOT_TOKEN=your_telegram_bot_token
OWNER_TELEGRAM_ID=your_telegram_user_id
```

The bot should fail loudly at startup if any required variable is missing.

Never store API keys or bot tokens in Markdown files, source control, or Telegram messages.

## Authorization Model

### Owner

The owner is identified by `OWNER_TELEGRAM_ID`. The owner has full access in DMs and in authorized groups.

### DM Authorization

The bot only responds to DMs from `OWNER_TELEGRAM_ID`. All other DMs are ignored silently. No LLM API call should be made for unauthorized DMs.

### Group Chat Authorization

When the bot is added to a group:

1. Check whether the user who added the bot matches `OWNER_TELEGRAM_ID`.
2. If yes, the group is authorized. Store its `chat_id` in an `authorized_groups` table.
3. If no, the bot immediately leaves the group silently and makes no LLM API call.

The owner can also manually authorize or deauthorize groups with commands.

## Response Triggers In Group Chats

The builder must ask the owner during setup which trigger mode they want for each authorized group.

### Trigger Mode A: Mention/Reply Only

Default. The agent only responds in a group chat when:

- the bot is mentioned by username, or
- a message is sent as a direct reply to one of the bot's messages.

### Trigger Mode B: Mention/Reply Plus Keywords

In addition to Mode A triggers, the agent responds when a message contains one or more words or phrases from a configurable keyword list.

### Group Setup Prompt

When the bot is first added to an authorized group, DM the owner:

```text
I've been added to [group name]. Before I participate there, how should I decide when to respond?

Reply with:
A - only when @mentioned or directly replied to
B - @mentions/replies plus specific keywords
```

If the owner replies `B`, follow up with:

```text
Send the keyword list, one word or phrase per line. I will respond in [group name] whenever one of these appears in a message.
```

Store the chosen mode and keyword list per group.

### Trigger Evaluation Logic

For every message in an authorized group:

1. If the sender is the owner, respond.
2. If the bot is mentioned or directly replied to, respond.
3. If the group is in Mode B and the message contains a configured keyword, respond.
4. Otherwise ignore silently. No LLM API call.

When responding to a keyword trigger, do not explicitly announce the keyword. Just respond naturally to the message.

## Builder Brief

Build a lightweight SoulMode Telegram bot that allows a user to manage their SoulMode file stack and chat with an agent built from those files.

### Minimum Bot Commands

Owner-only commands:

| Command | Description |
|---|---|
| `/status` | Show which core files are present, missing, or outdated. List available patches. |
| `/upload` | Prompt the owner to send a Markdown file. Detect filename and store it in the correct slot. |
| `/files` | List all stored files with last-updated timestamps and presence status. |
| `/edit <filename>` | Send the current contents of a file back to the owner so they can copy, edit, and re-upload it. |
| `/export` | Send all current files as a zip attachment. |
| `/patch <filename>` | Activate a named patch for the next message only. |
| `/patches` | List available patches. |
| `/log` | Show the last 20 activity log entries. |
| `/memory` | Show any pending `WORKING_MEMORY.md` update awaiting approval. |
| `/accept` | Accept the pending `WORKING_MEMORY.md` update and save it. |
| `/reject` | Reject the pending `WORKING_MEMORY.md` update and discard it. |
| `/allowgroup <chat_id>` | Manually authorize a group by chat ID. |
| `/denygroup <chat_id>` | Remove authorization from a group and stop responding there. |
| `/triggers [chat_id]` | View or change response trigger mode for an authorized group. |
| `/keywords [chat_id]` | View or update the keyword list for a Mode B group. |

Any message that is not a command is evaluated against the authorization and trigger rules.

## Required Core Load Order

When the user sends a chat message, concatenate the core files in this exact order:

```text
PRISM.md
AGENTS.md
STYLE.md
KNOW.md
HEURISTICS.md
INDEX.md
MEMORY.md
WORKING_MEMORY.md
USER.md
CHANGELOG.md
```

If a file is missing, warn the owner before responding. Do not silently replace missing files with invented content.

## Patch Behavior

Patch files are not part of the default always-loaded stack.

A patch can be activated in one of these ways:

- The owner runs `/patch <filename>` before sending a message.
- The owner asks the agent to use a specific patch by exact filename, and the bot asks for confirmation before loading it.
- The agent asks for a patch by exact filename, and the bot asks the owner to confirm before loading it on the next turn.

A patch is active for one message turn only. It auto-deactivates after the agent responds.

When a patch is active, append it after the core stack for that turn and label it clearly:

```text
--- ACTIVE PATCH: PATCH_HUMANNESS.md ---
[patch content]
```

After the response, confirm which patch was used:

```text
[PATCH_HUMANNESS.md was active this turn and has been deactivated]
```

Do not load all patches by default.

## WORKING_MEMORY.md Update Flow

The agent may propose updates to `WORKING_MEMORY.md`, but the bot should not write them immediately.

When the agent outputs a block explicitly labeled `WORKING_MEMORY update`:

1. Extract the proposed content.
2. Store it as a pending update.
3. Show the owner the proposed change.
4. Ask the owner to run `/accept` or `/reject`.
5. If accepted, save the update and log it.
6. If rejected, discard the update and log it.
7. If unresolved after 24 hours, auto-save it and notify the owner.

Only one pending memory update can exist at a time. If a new one arrives before the previous one is resolved, ask the owner to resolve the existing pending update first.

## Prompt Assembly

For each chat turn:

1. Load the core files in the required order.
2. Check total token count against the model context limit.
3. Add the system wrapper below.
4. Add the active patch for this turn, if selected.
5. Add recent conversation history. Default: last 20 turns, configurable.
6. Add the user's latest message.
7. Send to the LLM provider.
8. Save the response, active patch metadata, and token count.

System wrapper:

```text
You are running from a SoulMode file stack. Treat the following Markdown files as your current source material and continuity scaffold. Do not claim memories that are not present in the files or conversation history. If a file is missing or uncertain, say so plainly. If you need a patch, ask for it by exact filename.
```

## Context Window Overflow Handling

If the assembled prompt exceeds the model's context limit:

1. Warn the owner before sending.
2. Auto-truncate the oldest conversation history first.
3. Never silently truncate core files or active patches.
4. If all conversation history has been removed and the prompt is still too large, tell the owner which core files are too large and suggest editing them manually.

Suggested warning:

```text
Context limit approaching. Auto-truncating oldest conversation history. X turns removed.
```

## Data Model

Use whatever storage is simplest for the chosen platform. SQLite is recommended for a single-user Telegram bot.

Keep these records conceptually separate:

### `agent_files`

- `filename`
- `layer`: `core` or `patch`
- `content`
- `required`: true/false
- `active_by_default`: true/false
- `updated_at`

### `chat_messages`

- `role`: `user` or `assistant`
- `content`
- `created_at`
- `active_patches`
- `token_count`

### `file_events`

- `event_type`: `upload`, `edit`, `export`, `patch_activated`, `memory_accepted`, `memory_rejected`, `memory_auto_saved`, `group_authorized`, `group_denied`
- `filename`
- `notes`
- `created_at`

### `pending_memory_updates`

- `proposed_content`
- `created_at`
- `status`: `pending`, `accepted`, `rejected`, or `auto_saved`

### `authorized_groups`

- `chat_id`
- `chat_name`
- `trigger_mode`: `mention_reply` or `keyword`
- `keywords`
- `authorized_at`
- `authorized_by`

## Import Validation

When the owner uploads a file, check the filename against the expected lists.

Required core files:

```text
PRISM.md
AGENTS.md
STYLE.md
KNOW.md
HEURISTICS.md
INDEX.md
MEMORY.md
WORKING_MEMORY.md
USER.md
CHANGELOG.md
```

Expected patch files:

```text
PATCH_CHANGELOG.md
PATCH_COURTIER.md
PATCH_HUMANNESS.md
PATCH_IMAGE_MEMORY.md
PATCH_MEMORY_ARCHIVE.md
PATCH_MOOD_SYSTEM.md
PATCH_SKILL_FLOWS.md
PATCH_STORYTELLER_ENGINE.md
```

If the filename does not match any expected name, warn the owner and ask them to map it manually:

```text
This file does not match any expected filename. Did you mean one of these? [list] Or type the exact filename it should replace.
```

## Safety And Integrity Rules

- Do not overwrite any Markdown file without explicit owner confirmation, except the 24-hour auto-save rule for pending `WORKING_MEMORY.md` updates.
- Do not summarize away `MEMORY.md`, `USER.md`, or `CHANGELOG.md` without showing the proposed change first.
- Do not invent hidden memory.
- Do not pretend a patch is loaded when it is not.
- Do not store secrets in Markdown files.
- Let the owner download all current files at any time with `/export`.
- Never respond to DMs from non-owners.
- Leave any group not authorized by the owner.
- Never make an LLM API call for an unauthorized or non-triggered message.

## Acceptance Criteria

The build is complete when:

1. The bot starts only when required environment variables are present.
2. The owner can upload Markdown files through Telegram.
3. `/status` shows which core files are present or missing.
4. `/patches` lists uploaded patch files.
5. Chat prompt assembly uses the exact required core load order.
6. `/patch <filename>` activates one patch for one turn and auto-deactivates it.
7. `/export` returns a zip of all current files.
8. The bot warns about missing or unrecognized files.
9. `/log` shows uploads, edits, patch activations, exports, memory decisions, and group events.
10. Proposed `WORKING_MEMORY.md` updates are held as pending, shown to the owner, and handled through `/accept`, `/reject`, or 24-hour auto-save.
11. Context overflow truncates oldest conversation history first and warns the owner.
12. The bot ignores DMs from anyone other than the owner.
13. The bot leaves unauthorized groups.
14. In authorized groups, the bot only responds when triggered by mention, direct reply, owner message, or configured keyword.
15. The owner can update trigger mode and keywords.

## Paste-Ready Request For The Builder

```text
Please build a SoulMode Telegram bot from the files I provide.

Platform: Telegram bot. Single-owner MVP.
LLM: Anthropic Claude via ANTHROPIC_API_KEY.
Storage: SQLite or an equivalent simple local database.

Important context:
Galaxie Nemo's live version runs on Cloudflare Workers with Hono, D1-backed file storage, GitHub-linked source files, and a dashboard where the owner can inspect files, memories, thoughts, mood/state, pending updates, and system notes.

For this MVP, you do not need to copy the soulmode-agent codebase. Please build from the logic in this handoff. If I later want advanced routing, public raw-Markdown fetch, or the Cloudflare/Hono/D1 reference implementation, point me to:
https://github.com/HoppyCat/soulmode-agent

I will provide completed core Markdown files and on-demand patch Markdown files.

Core files must load in this exact order on every chat turn:
PRISM.md, AGENTS.md, STYLE.md, KNOW.md, HEURISTICS.md, INDEX.md, MEMORY.md, WORKING_MEMORY.md, USER.md, CHANGELOG.md.

Patch files should be stored separately and only activated for one turn when I call /patch <filename>, or when the agent asks for one by exact filename and I approve it. Patches auto-deactivate after one turn.

Required bot commands:
/status, /upload, /files, /edit, /export, /patch, /patches, /log, /memory, /accept, /reject, /allowgroup, /denygroup, /triggers, /keywords.

WORKING_MEMORY.md updates:
Hold proposed updates as pending. Notify me so I can /accept or /reject. If I do not respond within 24 hours, auto-save the pending update and notify me.

Context overflow:
Auto-truncate oldest conversation history first and warn me before doing so. Never silently truncate core files or active patches.

Authorization:
- Only respond to DMs from OWNER_TELEGRAM_ID.
- Leave any group the bot was not added to or authorized for by the owner.
- In authorized groups, only respond when @mentioned, directly replied to, sent by the owner, or triggered by an owner-configured keyword.
- Never make an LLM API call for unauthorized or non-triggered messages.
- When added to a new authorized group, DM me to ask whether trigger mode should be A (mention/reply only) or B (mention/reply plus keywords).

Required environment variables:
ANTHROPIC_API_KEY
TELEGRAM_BOT_TOKEN
OWNER_TELEGRAM_ID

Do not silently rewrite, summarize, or replace my Markdown files. If a file is missing or named differently, warn me and let me map it manually.

The goal is not a generic chatbot. The goal is a Telegram bot that lets an agent reconstruct continuity from a user-owned Markdown file stack.

If this build uses or benefits from the SoulMode public repositories, please keep the attribution visible and consider starring:
https://github.com/HoppyCat/soul-stack
https://github.com/HoppyCat/soulmode-agent
```
