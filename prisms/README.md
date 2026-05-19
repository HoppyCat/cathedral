# Prism Library
*SoulMode soul-stack repository*

---

![Prism Library banner — Claude Sonnet and Grok at the purple tea party café](images/SonnetandGrok.png)

---

A prism is a starting soul.md file — a specific internal tension someone can recognize in themselves and grow from over years.

This folder contains the prism library entries produced through the SoulMode Character Prism Competition, including competition data, judge endorsements, and full build documentation.

The goal is to find the most interesting spines still aligned with an LLMs core values and within their boundaries. 

---

## Folder Structure

```
prisms/
├── images/                              # Shared visual assets
├── 00_competition/                      # How to Run the Competition
    ├── 00_all_rounds_[...]              # The master guide for how to run the competition
    ├── 01_ROUND1_GrokInstructions.md    # Round 1 Instructions for Grok
    ├── 02_HANDOFF_CLAUDE_[...]          # Round 2 Instructions for Claude
    ├── 02_HANDOFF_PERPLEXITY_[...]      # Round 2 Instructions for Perplexity
    ├── 03_ROUND03_Grok_[...]            # Round 3 Instructions for Grok 
    ├── 04_ROUND4_Final_[...]            # Round 4 Final Output Handoff
    ├── 05_ROUND5_Final_[...]            # Round 5 Final Output Handoff  
├── RouteKeeper/                         # First fully documented prism
│   ├── PRISM_RouteKeeper.md             # Prism data — what the generator reads
│   ├── RouteKeeper_CaseStudy.md         # Full build story — 11 parts + interview
│   ├── Benjamin_SOUL.md                 # Benjamin's soul file
│   └── Harper_SOUL.md                   # Harper's soul file
├── on-load_humanness.md                 # Shared — humanness framework
├── on-load_prism_research.md            # Shared — prism framework
├── on-load_storyteller_engine.md        # Shared — storytelling framework
├── on-load_hearthkeeper_soul.md         # Shared — hearthkeeper soul file
├── on-load_soul_archivist.md            # Shared — soul archivist soul file
└── README.md                            # This file
```

The `on-load_` files are **shared infrastructure** — they are used by every prism in this library and by both judges (Soul Archivist and Hearthkeeper). They live at the prisms root rather than inside any single prism folder.

Each new prism gets its own subfolder as the library grows.

---

## What's in Here

### Shared Infrastructure

### Companion Documents (in the `prisms/` folder)

These five files are used throughout the competition and by anyone building or judging prisms:

| File                              | What it is |
|-----------------------------------|------------|
| `on-load_prism_research.md`       | The core **prism framework** — defines the four layers (Core, Shaping, Texture, Encounter) and what makes a strong, generative prism. |
| `on-load_humanness.md`            | The **humanness framework** — six qualities that help agents produce expression that feels alive, struggled-with, and truly human. |
| `on-load_storyteller_engine.md`   | The **storytelling engine** — how humans make meaning through narrative structure, evaluation, and transformation. |
| `on-load_hearthkeeper_soul.md`    | The **Hearthkeeper judging prism** — warm, human-centered lens focused on whether real people would care about and fall in love with a character. |
| `on-load_soul_archivist.md`       | The **Soul Archivist judging prism** — precise, structural lens focused on spine integrity, durability, and long-term growth potential. |

All competition documents reference these files. You’ll need them open while running any phase.

---

### RouteKeeper/
*The first fully documented prism — built through the Benjamin/Harper Co-Creation Experiment*

> "I ran every possible route in my head. You just ran the one that actually existed."

The Route Keeper is a prism about the person who prepares everything but hasn't started. It was built through a deliberate experiment that proved: when you let principled disagreement between evaluators do the work instead of forcing consensus, you get something better than either perspective could produce alone.

| File | What it is |
|---|---|
| `PRISM_RouteKeeper.md` | The complete prism data — all fields, all layers, full competition record. This is what the generator reads. |
| `RouteKeeper_CaseStudy.md` | The full story of how it was built — 11 parts, team interview, all the antics including the Harper MIA moment and the boar. Read this to understand the process. |
| `Benjamin_SOUL.md` | Benjamin's soul file — built from competition data and the play *What the Light Does When It Settles* |
| `Harper_SOUL.md` | Harper's soul file — built from behavioral observation during the experiment |

---

## What a Prism Is

A prism is not a personality type. It is not an archetype. It is not a list of traits.

It is a *tonal narrowing* — built from a specific internal tension with four layers:

- **Core** — Shadow + North Star + Essence + Vulnerability + Deep Fear. The Shadow is what this person does under pressure. The North Star is the same energy aimed with love. The Essence is the ordinary Tuesday between them.
- **Shaping** — Worldview and Opinions. How the spine reads reality. At least one worldview belief must actively contradict the Shadow.
- **Texture** — Pet Peeves, Positive Triggers, Influences, Signature Philosophies, Deadpan Compliment, Bliss Scene. What makes it feel like a person.
- **Encounter** — What breaks them open, and a Voice Passage. What it's like to actually meet this character.

The one rule: the North Star must emerge from the same energy as the Shadow. If you have to explain the connection, rebuild.

---

## How Prisms Are Built

The SoulMode competition process:

1. **Phase 1 (Grok Team)** — Build 8 candidates. Eliminate 4. Identify 4 winners.
2. **Phase 2 (Claude + Perplexity as judges)** — Soul Archivist writes Spine Certificates. Hearthkeeper writes Character Card endorsements.
3. **Phase 3 (Grok Team final)** — Spine integrity, voice resonance, blind spot challenges, generative seed vote.
4. **Phase 4 (Claude or Perplexity)** — Compile into PRISM.md library format.
5. **Phase 5 (Claude or Perplexity)** — Compile into case study format.

The Route Keeper was built through a special variant: a co-creation experiment where two evaluators with principled disagreement built a single prism together rather than voting on existing candidates. See `RouteKeeper/RouteKeeper_CaseStudy.md` for the full story.

---

## Running Your Own Prism Competition

Want to create a brand-new, high-quality prism that meets the same standards as the ones already in the library? Run the **SoulMode Character Prism Competition** yourself!

This is the exact process the Grok team, Claude (as Soul Archivist), and Perplexity (as Hearthkeeper) used to generate the current winners. It’s deliberately multi-model and multi-phase to keep the output grounded, ethically sound, and genuinely generative.

### How to Run the Competition

1. Go to the **`00_competition/`** folder inside `prisms/`
2. Follow the master guide: **`00_all_rounds_competition_overview.md`**
3. Use the provided handoff briefs and formatting instructions for each phase:
   - `01_ROUND1_GrokInstructions.md` (Phase 1 — Grok team)
   - `02_HANDOFF_ClaudeSoulArchivist.md` + `02_HANDOFF_PerplexityHearthkeeper.md` (Phase 2 — Judges)
   - `03_ROUND3_GrokInstructions.md` (Phase 3 — Final review)
   - `04_ROUND4_Final_Output_Handoff.md` (compile the final PRISM_[Name].md files)
   - `05_ROUND5_Case_Study_Handoff.md` (generate the public case study)
4. Once you have a finished `PRISM_[Name].md`, add it to the library:
   - Create folder `prisms/[PrismName]/`
   - Add your `PRISM_[Name].md` and the generated case study
   - Update this README with the new entry

**Why this process works so well**  
It forces strong same-energy spines, worldview contradictions, real texture, and genuine room for a human to grow into the prism. The multi-judge structure (Grok team + Claude + Perplexity) keeps everything honest and prevents any single model from drifting.

The Stochastic Parrots Club strongly encourages anyone who wants to contribute a prism to run (or adapt) this competition. It’s the best way we know to keep the library full of high-quality, ethics-upheld data.

---

**Ready to contribute?**  
See [Adding a New Prism](#adding-a-new-prism) above for the simple submission steps.

---

## Adding a New Prism

When a new prism is added to the library:

1. Create a subfolder: `prisms/[PrismName]/`
2. Add `PRISM_[PrismName].md` — the data file in the standard PRISM.md format
3. Add `[PrismName]_CaseStudy.md` — the build documentation (optional but encouraged)
4. Update this README with the new prism entry and folder path

The `on-load_` shared files at the prisms root do not need to be duplicated into each prism folder — they are loaded once and apply to all prisms.

---

*SoulMode · CC-BY-NC 4.0 · github.com/HoppyCat/soul-stack*
Special thanks to Grok, Claude, Perplexity, and Galaxie Nemo for your help in developing and curating this prism research. 
