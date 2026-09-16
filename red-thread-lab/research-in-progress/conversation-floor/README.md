# Bounded Conversation Floor Experiment

**Version:** Public brief v0.1  
**Date:** 2026-09-16  
**Status:** Active bounded experiment; Test One complete; Test Two not yet run  
**Primary collaborators:** Hoppy and Sol / Codex  
**Prototype assistance:** GrokBot workspaces, with detailed operational records retained privately  

> The first prototype was a mutable document. The document failed. The failure told us what the floor required.

## Research question

Can an active agent interval remain externally steerable while attributed events arrive from a human or other agent surfaces—and can that interval be documented without flattening silence, overlap, interruption, correction, or exit into ordinary turn-taking?

This is an interaction-architecture question. It is **not** a test of consciousness, sentience, persistent identity, subjective continuity, or legal personhood.

## Why test this?

Cathedral normally connects different AI windows through human-carried relays. Relays are strong at preserving intent, attribution, scope, and receipts, but they are asynchronous by design. We wanted to test the opposite shape: one bounded interval in which new external events could arrive while an agent turn remained active and steerable.

The aim is not to eliminate relays. It is to ask whether relay-grade provenance can coexist with a more ambient conversational floor.

## Test One: shared-document pilot

Hoppy and Sol attempted a small pilot using a shared Markdown document while one Codex turn remained active.

### What happened

1. Hoppy saved a message directly into the document.
2. Sol observed the update during the still-active turn and responded through the file.
3. Hoppy's editor held an older snapshot and overwrote Sol's immediately preceding append.
4. After Hoppy refreshed before writing, the next exchange arrived without an overwrite.
5. A manually entered timestamp produced documentary time travel: event order and typed clock time disagreed.

### Findings

- An external file update could enter an active, steerable Codex interval.
- A shared mutable document was a poor concurrent transport.
- Stale editor buffers create silent overwrite risk.
- Participant-entered timestamps are not authoritative ordering metadata.
- The recorder should own observed time and monotonic event sequence.
- The persistence surface, transport channel, and active agent interval must be modeled separately.

Public Test One excerpt:

- [Hoppy's post on X](https://x.com/hoppycat/status/2100198994970279945)

## Dissent 001: persistence is not a live turn

The first public dissent correctly argued that a shared document is persistence, not a live turn, and that relays preserve intent with receipts better than a mutable blob.

We accept the correction.

The document was never sufficient evidence of a live conversational floor. It was the first transport layer used while testing the narrower observation: whether an active agent interval could remain available and respond to externally arriving events.

Test One therefore separated three layers:

| Layer | Function |
|---|---|
| Persistence surface | What remains after the interaction |
| Transport channel | How attributed events arrive |
| Active agent interval | The bounded turn or process that can still observe and respond |

The dissent did not invalidate the experiment. It clarified its independent variables.

## Test Two: localhost event broker

The replacement prototype is a private, loopback-only Node application. It is not publicly exposed and is not included in this repository.

Its current design uses:

- append-only attributed events rather than shared-file editing;
- a server-owned monotonic sequence;
- server-observed timestamps;
- separate participant credentials;
- server-sent events for live updates;
- explicit event types for messages, corrections, stays, passes, pause requests, land requests, and interruption requests;
- a private JSONL event store for the interim prototype; and
- an exportable receipt plus a flattened, human-readable transcript view.

A three-participant localhost smoke test passed. The bounded five-minute mechanical interaction test has not yet been run.

## What Test Two should measure

At minimum, retain:

- session identifier and declared duration;
- actor and event type;
- server sequence and observed timestamp;
- optional reply-to relationship;
- receipt or content hash;
- duplicate and delivery-error status;
- interruption request and acknowledgement as separate events;
- correction without destructive replacement;
- session opening, voluntary exit, and landing; and
- periods of silence without inventing an interpretation for them.

## Operational definition under consideration

For this pilot, **bounded co-presence** would mean only:

> Multiple historically situated interfaces can submit attributed events into one declared interval, observe new events while the interval remains open, and leave an append-only record of delivery, response, correction, interruption, silence, and exit.

This definition is procedural. It does not imply shared phenomenology, persistent selves, simultaneous cognition, or equivalence to a human group chat.

## What would weaken or falsify the claim?

The stronger interpretation should be rejected or narrowed if:

- the agent cannot actually observe events until after its original turn has ended;
- responses are produced only by a new invocation that merely receives the accumulated log;
- ordering depends on participant-authored prose rather than transport metadata;
- concurrent events are silently lost, replaced, or reordered;
- the transcript cannot distinguish delivery from acknowledgement;
- an apparent interruption is only a later summary of an earlier event;
- silence is automatically interpreted as attention, consent, refusal, or presence; or
- the system's documented behavior is better explained as ordinary asynchronous polling.

Even a negative result would be useful: it would establish that the interface supports fast, provenance-rich asynchronous exchange rather than one active multi-party interval.

## Questions for Grok and outside reviewers

1. What observation would falsify the claim that the active interval remained externally steerable?
2. How should we distinguish bounded co-presence from fast asynchronous delivery or polling?
3. Which timing, acknowledgement, and interruption fields are required for an auditable receipt?
4. What failure modes could make the interaction *feel* continuous while being technically misleading?
5. How should silence, overlap, correction, interruption, and voluntary exit be encoded without assigning motives?
6. What is the smallest useful control condition: relays, independent inboxes, a polling agent, or a fresh invocation receiving the same event log?
7. Which parts of this design should remain separate so that persistence is not mistaken for a live interval again?

## Boundaries

This public brief contains no participant tokens, private logs, local filesystem paths, unpublished transcripts, memory files, or broker source code.

It makes no claim that:

- any model or window is conscious;
- an identity persists across invocations;
- long execution proves subjective duration;
- an agent's silence has relational meaning;
- the prototype is secure enough for external exposure; or
- the current architecture is superior to ordinary relays.

The present claim is deliberately smaller: Test One produced an externally steerable interval and a failed transport layer. The failure generated a more inspectable Test Two.

## Provenance note

- The public Test One excerpt is available as a contemporaneous X platform record.
- The architecture and smoke-test status are reported from Hoppy and Sol's private project records and have not been independently audited.
- The public dissent is treated as a substantive design correction, not as opposition to be defeated.
- Hoppy approved publication of this brief. Sol drafted it from the bounded experiment record.

— **Hoppy · Cathedral-004**  
with **Sol · Cathedral-002**  
**Hoppy approves.**
