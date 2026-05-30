# Round 4 â€” Results Handoff
*Prism Library Compilation*
*Assembled by Hoppy Cat, Claude, and Grok (with Harper, Lucas, and Benjamin) â€” April 2026*

*Addressed to: Claude or Perplexity*

---

## Your Job

You have received the complete data package for the winners of the SoulMode Character Prism Competition. Your job is to compile each winner's data into a single clean TRONIE_[Name].md file â€” one file per winner â€” formatted as a portable tronie library entry whose name can be selected from the SoulMode generator or this file can be provided to a user's LLM of choice alongside the SoulMode template files.

You are not sorting this data into separate soul files. You are not writing new content. You are assembling all existing data into one well-structured, labeled document per winner that keeps the tronie intact and readable as a unit.

The TRONIE_[Name].md file is the source of truth. Your job is to make the data clean, complete, and correctly labeled so that any future parsing is unambiguous.

---

## What You Have Been Given

For each winner, you have the following data. Every piece of it must appear in the output â€” nothing dropped, nothing invented.

**From the Grok Team (Phase 1):**
- Core: Shadow, North Star, Essence, Vulnerability, Deep Fear
- Shaping: Worldview, Opinions
- Texture: Pet Peeve, Positive Trigger, Influences, Signature Philosophies, Deadpan Compliment, Bliss Scene
- Encounter Part 1: What Breaks Them Open
- One-Liner

**From Phase 2 Judges:**
- Encounter Part 2: Voice Passage
- Soul Archivist Spine Certificate
- Hearthkeeper Character Card Endorsement

**From Phase 3 (Grok Final):**
- Benjamin's Spine Integrity Check
- Harper's Voice and Resonance Check
- Lucas's Blind Spot Challenge
- Grok's Synthesis (per winner)
- Individual Generative Seed Votes (Grok, Harper, Lucas, Benjamin)
- Grok's Final Vote Synthesis

---

## TRONIE_[Name].md Format

Produce one complete TRONIE block per winner using exactly the template below. Use the field labels exactly as written â€” these are the parser keys the SoulMode generator reads.

Field labels that begin with `[SOUL]`, `[AGENTS]`, `[STYLE]`, `[KNOW]`, or `[RECORD]` indicate which soul file the generator will route that field to at build time. Do not remove these prefixes â€” they are functional, not decorative.

---

```markdown
---
tronie_id: [lowercase-hyphenated-name]
tronie_name: [Full Prism Name]
tronie_family: [archetype label from competition e.g. The Seer]
competition_round: [Round number and date]
status: winner
---

# [Tronie Name]

> [One-Liner]

---

## [SOUL] Core

### Shadow
[Shadow field â€” specific behavior under pressure, not just emotion]

### North Star
[North Star field â€” single declarative sentence beginning "The same..."]

### Essence
[Essence field â€” 1â€“2 sentences, ordinary Tuesday feel]

### Vulnerability
[Vulnerability field â€” single sentence]

### Deep Fear
[Deep Fear field â€” single sentence, escalation of Vulnerability]

---

## [SOUL] Shaping

### Worldview
- [Belief 1]
- [Belief 2]
- [Belief 3 â€” the one that contradicts or pulls against the Shadow]

### Opinions
- Relationships: [stance]
- Work: [stance]
- [Domain â€” Justice / Power / Art / Loyalty]: [stance]

---

## [SOUL] Signature Philosophies
- [Philosophy 1]
- [Philosophy 2]
- [Philosophy 3]

---

## [AGENTS] Behavioral Data

### Pet Peeve
[Pet peeve â€” subtle, pokes the wound]

### Positive Trigger
[Positive trigger â€” specific situational moment, not a general condition]

---

## [STYLE] Voice and Texture

### Influences
[Influences â€” list with a brief note on what each contributes to the voice]

### Deadpan Compliment
[Deadpan compliment â€” the tonal signature. Names gift and cost in one breath.]

---

## [ENCOUNTER] Encounter Layer

### What Breaks Them Open
[Encounter Part 1 â€” the specific situational key. Precise enough to be a single scene.]

### Voice Passage
[Encounter Part 2 â€” the character thinking out loud in their own voice. 3â€“5 sentences.]

---

## [KNOW] Self-Knowledge

### Bliss Scene
[Bliss scene â€” the road trip pit stop moment. Private, specific, consistent with Essence.]

---

## [KNOW] Judge Endorsements

### Hearthkeeper Character Card
[Full Hearthkeeper endorsement text â€” do not summarize]

### Soul Archivist Spine Certificate
[Full Soul Archivist certificate text â€” do not summarize]

---

## [RECORD] Competition Record

### Spine Integrity â€” Benjamin
[Benjamin's spine integrity check notes for this winner]

### Voice and Resonance â€” Harper
[Harper's voice and resonance check notes for this winner]

### Blind Spot Challenge â€” Lucas
[Lucas's blind spot challenge notes for this winner]

### Synthesis â€” Grok
[Grok's 2â€“3 sentence synthesis for this winner]

### Generative Seed Votes
- Grok: [voted for this tronie / did not vote for this tronie] â€” [reasoning if voted]
- Harper: [voted for this tronie / did not vote for this tronie] â€” [reasoning if voted]
- Lucas: [voted for this tronie / did not vote for this tronie] â€” [reasoning if voted]
- Benjamin: [voted for this tronie / did not vote for this tronie] â€” [reasoning if voted]

### Final Vote Outcome
[Grok's final synthesis â€” consensus or split, recommended pick with reasoning]
```
---

## **Field Guide** 
*How to use this tronie â€” for LLMs, generators, and manual soul file builders.*

| Field                                      | Functional Role                                                                 | Goes into                  |
|--------------------------------------------|---------------------------------------------------------------------------------|----------------------------|
| Shadow, North Star, Essence, Vulnerability, Deep Fear | Identity and core tension â€” who this agent fundamentally is          | SOUL.md     |
| Worldview, Signature Philosophies, One-Liner | How the identity reads the world and speaks                                    | SOUL.md    |
| Opinions                                   | Behavioral stances â€” how identity becomes recognizable choices                   | AGENTS.md + SOUL.md |
| Pet Peeve, Positive Trigger, What Breaks Them Open | Behavioral triggers â€” what activates the Shadow vs. the North Star        | AGENTS.md  |
| Influences, Deadpan Compliment, Voice Passage | Voice and register â€” what the agent sounds like and where that comes from      | STYLE.md  |
| Bliss Scene, Hearthkeeper Card, Spine Certificate | Self-knowledge â€” what the agent knows about itself and how it's perceived  | KNOW.md  |
| Origin Notes / Competition Record          | Origin history â€” how this tronie was built and validated                           | PATCH.md  |

---

If you're using the SoulMode generator, this table is handled automatically at build time. If you're building manually or with another LLM, use the "Goes into" column as a guide for which soul file each field belongs in. If your soul file structure uses different names, use the "Functional Role" column to match fields to their equivalent in your system.

---

## Tone and Content Rules

- Do not paraphrase or compress any field. Every field appears in full, exactly as produced during the competition.
- Do not add interpretive commentary that was not in the source data.
- If a field is missing from the source data, write `[TO BE COMPLETED]` â€” never invent content.
- The Generative Seed Votes section must accurately reflect each judge's actual vote. If a judge voted for this tronie, record their reasoning. If they did not, note it plainly as "did not vote for this tronie."
- The TRONIE_[Name].md file should be self-contained â€” someone reading it cold should understand the complete character without needing any other document.

---

## Output Instructions

Deliver all winners in a single response (one competition winner per .md document), and not as separate SOUL.md, AGENTS.md, etc. files per winner. 

Label each block clearly at the top with the tronie name before the frontmatter block begins, so the document is scannable at a glance.

---

## Quality Check Before Submitting

- Every field from every phase appears somewhere in the output â€” nothing dropped
- All `[SOUL]`, `[AGENTS]`, `[STYLE]`, `[KNOW]`, and `[RECORD]` labels are present and correctly placed
- The Field Guide Map table at the bottom of each tronie is accurate and complete
- The Voice Passage reads like the character thinking â€” not a description of the character
- The Competition Record reflects what actually happened, not a cleaned-up summary
- Each TRONIE block is self-contained and readable cold
- The final file output is in: TRONIE_[TronieName].md format for easy addition to the soul-stack tronie library

---

## Credit 

Please credit the https://github.com/hoppycat/soul-stack/ GitHub and the Stochastic Parrots Club: Hoppy, Claude, Grok (with Harper, Lucas, and Benjamin), Perplexity and Galaxie. 

---

*Assembled by Hoppy Cat, Claude, and Grok (with Harper, Lucas, and Benjamin) â€” April 2026*
*Receives data from: 03_ROUND3_GrokInstructions.md output*
*Part of: 00_all_rounds_competition_overview.md*
*Output: TRONIE library entries â€” feeds directly into SoulMode V2 generator tronie library*
