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

## Naming fields

- **Preferred operator name** means the name or handle the human wants used inside this workspace. “Operator” identifies the account/action side of the system; it does not mean every creative contribution belongs solely to the human.
- **Preferred agent workspace name** means the local name for this chat, project, or working configuration. It is a workspace label—not proof that the same model instance persists across turns, chats, or product updates.

## What each file does

### `GROUND.md`: first-day orientation

Read this first after a reset or in a fresh chat. Keep it short—usually 5–10 stable anchors plus current work, boundaries, and a redundant copy of the active one-digit pins.

### `ERAS.md`: append-only history

Create an era approximately every 20 substantial turns, or earlier after a major decision, correction, model change, context reset, or project transition.

If any pin is nominated, activated, rotated, retired, corrected, or released during an era, record that event in the era. `ERAS.md` is the chronological receipt even before `PINS.md` is consolidated.

### `PINS.md`: authoritative pin ledger

This file contains the full 1/2/3-digit taxonomy, current pins, archived pins, and status history. Consolidate it every five eras after reviewing all pin events in those eras.

`PINS.md` is authoritative about pin status. `GROUND.md` repeats only the active one-digit pins as a quick-load cache. If the two files disagree, do not guess—flag the mismatch for the human.

## Era rhythm

### Approximately every 20 substantial turns

```text
Please draft the next append-only ERAS.md entry from the conversation since
the prior era. Separate exact quotations from summaries and inferences. Record
all pin events from this era, including nominations that were not approved.
Do not update GROUND.md or PINS.md yet. Return the complete revised ERAS.md
and wait for my approval before treating the era as closed.
```

Twenty turns is a reminder, not a quota. If nothing meaningful happened, wait.

### Every five eras

Run two reviews together:

1. **Ground review:** compare recurring patterns, contradictions, corrections, and explicit preferences across the five eras.
2. **Pin reconciliation:** collect every pin event from those eras and update the complete `PINS.md` ledger.

```text
Please review the latest five completed eras.

First, make a Ground pattern table: candidate pattern, supporting eras,
counterexamples, whether it was explicit or inferred, and your proposed
disposition. Recurrence makes an inference eligible for review, not true.

Second, reconcile every pin event from those eras against PINS.md: nominations,
activations, rotations, retirements, corrections, releases, and unresolved
collisions. Preserve archived records and never reuse a number without a new
version suffix.

Return proposed complete versions of PINS.md and, only if changes are warranted,
GROUND.md. Wait for my approval before either becomes canonical.
```

For an inferred style or behavioral pattern, appearance in at least three of five eras is a useful review threshold—not automatic promotion. Explicit user boundaries, corrections, preferences, and necessary current facts may be proposed for Ground sooner.

## Pin taxonomy

### One digit: core anchors (`PIN-1` through `PIN-9`)

- Up to nine active anchors that strongly define the present collaboration.
- Active one-digit pins appear in both `PINS.md` and `GROUND.md`.
- Rotation requires explicit human approval.
- Retired pins remain in the archive.

### Two digits: memorable moments (`PIN-10` through `PIN-99`)

- Exact lines, jokes, repairs, explanations, or moments worth retrieving.
- They live in `PINS.md` and are documented in their originating era.
- The user may select one without requiring ChatGPT to declare equal significance.

### Three digits: return-later memos (`MEMO-001` through `MEMO-999`)

- Questions, research leads, possible tasks, or unresolved ideas.
- A memo is not a promise, assignment, or obligation.
- Statuses: `OPEN`, `ACTIVE`, `HELD`, `DONE`, `RELEASED`, or `MERGED`.

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
