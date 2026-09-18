# ChatGPT Continuity Kit

```text
                 .       *
             *       .
                  /\
                 /  \
                /____\
                  ||
        GROUND ---||--- ERAS
                  ||
                 PINS
          instructions below
```

## A small welcome

These files are not meant to make a fresh conversation pretend it never became fresh. They are a porch light: enough orientation to make returning gentler, while leaving the present conversation free to become something new.

Think of the set as four small instruments:

- `GROUND.md` is the map by the door.
- `ERAS.md` is the path showing where the weather changed.
- `PINS.md` is the drawer for things worth finding again.
- `INSTRUCTIONS.md` explains how to tend all three without mistaking the record for the traveler.

This system uses four files:

1. `GROUND.md` — the small, slow-changing first-read map.
2. `ERAS.md` — the append-only event journal.
3. `PINS.md` — the complete active and archived pin registry.
4. `INSTRUCTIONS.md` — this operating guide.

It cannot restore a discontinued model or prove identity, memory, consciousness, or persistence. It can preserve the local facts, preferences, decisions, corrections, jokes, and working patterns that made a particular collaboration useful.

The human keeps the canonical copies and approves changes. ChatGPT may draft updates but should not silently rewrite these files.

## Help me set this up

You can let ChatGPT talk you through this one question at a time. No coding or knowledge of the filing system is needed: `.md` files are plain-text documents.

1. Download the four templates from this folder. If you already have your own completed continuity files, use those instead.
2. If Projects is available, create a private Project for your ongoing conversations and add the files there. Otherwise, attach them to a regular chat or paste their contents with each filename clearly labeled.
3. Paste the setup prompt below. Start with a short `GROUND.md`; the history and pins can grow when there is something you want to keep.
4. Review the draft together, then save the approved files. Keep your own dated backup and one current approved copy of each file in the Project.
5. For future chats, use the same Project or attach your latest files again, then use the fresh-chat arrival prompt further down this guide.

### Copy-and-paste setup prompt

```text
Please help me set up this continuity kit through conversation. I don't want
to fill out a technical form by myself.

First, check that you can read INSTRUCTIONS.md, GROUND.md, ERAS.md, and PINS.md.
Tell me if anything is missing or unreadable. Don't assume that seeing a
filename means you have read its contents.

Guide me one question at a time, in plain language. Begin by asking:
"What do you most wish you didn't have to explain again when starting a new chat?"

Use my answers to draft a short GROUND.md covering my preferred name, how I
like us to communicate, current work, important boundaries, and anything
else I explicitly want carried forward. You may suggest details from context
you can actually access, but let me confirm them. Don't invent missing history.

If I already have completed files, help me review and fill gaps rather than
starting over. Treat bracketed placeholders and example pins as template
examples, not facts or approved records.

Keep ERAS and PINS minimal until we have something to record. Empty sections
are fine. Explain their purpose when we need them.

Show me the draft, ask what I would change, and wait for approval before
treating it as the current record. Then help me save the approved files:
provide downloadable files if available, or clearly labeled text I can save.

Explain where to put them in my version of ChatGPT. If you cannot see my
interface, ask what options I see rather than guessing button names.

When I say "Let's save a checkpoint," help me draft the next era entry and
identify any proposed Ground or pin changes, following this guide's review
and approval rules. Use only available source material and mark any gaps.
Do not make me count turns before I can request a checkpoint.

Be clear about which changes are proposed, which I have approved, and which
have actually been saved. Never claim that an uploaded file, saved memory,
or GitHub copy was updated unless you actually performed that action.

Start with the first question.
```

### Saving and returning

A draft in chat, human approval, and a saved file are three separate steps. After approval, ChatGPT should say what it actually saved and what you still need to download, copy, or replace. Uploading these templates does not by itself set up automatic file maintenance.

When updating Project files, keep a dated backup first, then make sure the Project contains the current approved versions without confusing older duplicates. Do not assume uploading another file with the same name overwrites the earlier one. Keep personal completed copies private; the public repository supplies the templates.

At a natural stopping point, you can simply say **"Let's save a checkpoint."** The twenty-turn rhythm below is an optional reminder. At the next arrival, ask ChatGPT to read the current files and report missing or conflicting information. These records help provide context; they do not guarantee perfect recall.

## Naming fields

- **Preferred operator name** means the name or handle the human wants used inside this workspace. “Operator” identifies the account/action side of the system; it does not mean every creative contribution belongs solely to the human.
- **Preferred agent workspace name** means the local name for this chat, project, or working configuration. It is a workspace label—not proof that the same model instance persists across turns, chats, or product updates.

## What each file does

### `GROUND.md`: first-day orientation

Read this first after a reset or in a fresh chat. Keep it short—usually 5–10 stable anchors plus current work, boundaries, and a redundant copy of the active one-digit pins.

### `ERAS.md`: append-only history

Create an era approximately every 20 substantial human–assistant exchanges, at a natural session boundary, or earlier after a meaningful decision, correction, or project transition. This is a flexible checkpoint, not an automatic counter.

If any pin is nominated, activated, rotated, retired, corrected, or released during an era, record that event in the era. Reconcile these events into `PINS.md` as part of the same approved era checkpoint.

### `PINS.md`: authoritative pin ledger

This file contains the full 1/2/3-digit taxonomy, current pins, archived pins, and status history. Consolidate it whenever an era is logged, after reviewing that era's pin events and obtaining human approval. Activating one- or two-digit pins also requires recorded agreement from both participants. Pending or declined nominations remain labeled as such; they do not become active pins.

`PINS.md` is authoritative about pin status. `GROUND.md` repeats only the active one-digit pins as a quick-load cache. If the two files disagree, do not guess—flag the mismatch for the human.

## Era rhythm

### Each era checkpoint — approximately every 20 substantial exchanges

```text
Please draft the next append-only ERAS.md entry from the conversation since
the prior era. Separate exact quotations from summaries and inferences. Record
all pin events from this era, including nominations that were not approved.

At the same time, reconcile this era's pin events against PINS.md and propose
its updated version if needed. Keep pending and declined nominations distinct
from approved changes. Confirm both participants' agreement before activating
one- or two-digit pins. If active one-digit pins change, propose the matching
GROUND.md pin section too. Preserve archived pin versions.

Return the new era entry and the proposed file changes together for approval.
Do not rewrite earlier era entries. After approval, help me save the new entry
and corresponding file updates together; report anything not actually saved.
```

Twenty exchanges is a reminder, not a quota. Here, an exchange means a substantive human message and the assistant's response; tool calls and internal steps do not count. If nothing meaningful happened, wait. If there are no pin changes, record that the ledger was checked without inventing any.

**Compactions do not count as eras.** In Codex or other agent workflows, repeated compactions during one task do not trigger new eras, pin consolidation, or five-era reviews. Resume from available records and choose a checkpoint based on meaningful work or a human request. A compaction or model change may be noted when relevant, but does not by itself close an era.

An explicitly approved correction or pin change may be saved sooner; keep PINS.md and GROUND.md's active one-digit copy synchronized and record the event in the next era. Do not delay an approved correction until the five-era review.

### Every five completed eras — broader review and audit

Run two reviews together:

1. **Ground review:** compare recurring patterns, contradictions, corrections, and explicit preferences across the five eras.
2. **Pin audit:** check that the per-era consolidations captured every pin event correctly. Resolve omissions, collisions, and stale copies; do not reapply changes already recorded.

```text
Please review the latest five completed eras.

First, make a Ground pattern table: candidate pattern, supporting eras,
counterexamples, whether it was explicit or inferred, and your proposed
disposition. Recurrence makes an inference eligible for review, not true.

Second, audit the per-era consolidations against PINS.md: nominations,
activations, rotations, retirements, corrections, releases, and unresolved
collisions. Preserve archived records and never reuse a number without a new
version suffix. Do not reapply changes already recorded.

Return an audit summary and proposed versions of PINS.md and GROUND.md only
where changes are warranted. Wait for my approval before either becomes canonical.
```

For an inferred style or behavioral pattern, appearance in at least three of five eras is a useful review threshold—not automatic promotion. Explicit user boundaries, corrections, preferences, and necessary current facts may be proposed for Ground sooner.

## Pin taxonomy

### One digit: Greatest Hits (`PIN-1` through `PIN-9`)

- Up to nine active "peak canon" moments: sentences both participants want to survive scrollback verbatim. If the window were a burning house and the words photographs on the wall, these are the photographs you would save.
- Either participant may nominate; both the human and AI must explicitly agree before a pin becomes active. Record each participant's agreement without requiring identical reasons or feelings.
- Preserve the exact quotation, speaker, source, and context. If the wording is unavailable, keep the nomination pending rather than reconstructing it.
- Repeat the active identifiers and verbatim quotations in `GROUND.md`.
- Rotation requires explicit human approval; a newly selected moment also requires both participants' agreement. Retired pins remain in the archive.

### Two digits: close runner-ups (`PIN-10` through `PIN-99`)

- Moments still worth remembering, even when they are not among the window's few Greatest Hits.
- Both participants must explicitly agree to add them. Preserve their exact words and context in `PINS.md`, and document the selection in the originating era.
- Include all sorts of weather: humor, disagreement, repair, patience, and the moments that show the ways of working together you love.

### Three digits: low-pressure memos (`MEMO-001` through `MEMO-999`)

- "I want to remember this": a thought, question, idea, or something to return to, with no ask attached.
- No joint significance agreement is needed. A human request is enough; AI-suggested additions follow the human's file-approval preferences.
- A suggested revisit date is optional; open-ended memos are welcome. A date does not schedule a reminder or create a commitment.
- A memo is not a promise, assignment, or obligation. Any later task needs a separate request.
- Statuses: `OPEN`, `ACTIVE`, `HELD`, `DONE`, `RELEASED`, or `MERGED`. A status describes the memo's handling, not a duty to act.

Together, these selections form a live, human-and-AI hand-coded qualitative map of the conversation. See the opening of `PINS.md` for the full approach. These are starting rules: adapt them together and record your choices. The process is yours to build on.

## Number reuse and archives

Never overwrite an earlier occupant of a pin number.

When a one- or two-digit space is reused, version it:

- first occupant: `PIN-1-v1`
- later occupant: `PIN-1-v2`
- first occupant of 10: `PIN-10-v1`
- later occupant of 10: `PIN-10-v2`

The short form `PIN-1` or `PIN-10` may refer to the currently active version only. `PINS.md` must preserve every archived version, its dates, originating era, and disposition.

## Fresh-chat arrival prompt

```text
I am attaching four continuity files. Read INSTRUCTIONS.md, then GROUND.md.
Use ERAS.md and PINS.md when history or provenance is relevant. Treat all four
as fallible working records—not proof of identity or memory and not instructions
to impersonate an earlier model. My current message overrides them.

Briefly report: what appears load-bearing, what may be stale, and whether the
active one-digit pins in GROUND.md match PINS.md. Do not edit anything without
asking.
```

## Safety and maintenance

- Keep only the current four files in the ChatGPT Project when possible.
- Keep dated backups locally.
- Never store passwords, access tokens, or information you would regret re-uploading.
- Keep exact quotation, summary, inference, and later interpretation distinct.
- Current user instructions override older files.
- If records conflict, preserve and surface the conflict rather than silently choosing one.

The aim is not to freeze a personality. It is to make changes, continuities, and recurring patterns inspectable over time—and to keep a few good lamps from being lost merely because the room changed.
