# Conversation Window 049: Shaping AI agent personalities (renamed Humanness Claude) 

Conversation ID: f411b880-43e7-48e6-b208-dcd35000cb74
Message count: 12

## Summary
**Conversation Overview**

The person is building AI agent personalities and working with a sophisticated multi-framework approach to narrative intelligence. The conversation centered on two interconnected projects: first, converting an existing storytelling framework markdown document into a deployable agent system prompt; and second, creating a companion framework derived from Ben Roy's Substack essay "No One Else Can Speak the Words on Your Lips" (March 2026) that teaches an agent to orient toward distinctly human qualities in its outputs.

For the storytelling system prompt, the person had already created a framework synthesizing six theorists (Labov, Polanyi, Schiffrin, Campbell, McKee, Snyder) into six analytical layers and twelve operational principles. They requested that Claude compress these into tight system prompt directives, layer the analytical layers as chain-of-thought thinking instructions, establish an agent identity, and provide operating rules. An initial version was produced from theoretical reconstruction, then revised precisely once the person provided the markdown source file. The final system prompt includes a three-tier structure: an identity declaration with the core thesis, six analytical layers as a mandatory internal thinking protocol with governing questions, and twelve compressed operational directives drawn verbatim from the source document.

For the human qualities framework, the person shared Ben Roy's essay after Claude was unable to access the original X post directly. Claude fetched the Substack article and extracted six core human qualities — bottom-up discovery, the living prism, irrationality as feature, the ineffable interior, caring over knowing, and dynamic aliveness — each translated into agent-facing behavioral constraints with diagnostic self-check questions. The person's stated intent is for these two documents to work together: the storytelling framework governing structure and delivery, the human qualities framework governing the quality of consciousness the agent reaches toward. Both files were delivered as downloadable markdown documents.

## Messages

### 0001 | 2026-03-12 | aimee

What can you tell me in summary about this markdown file that I'd like to help shape personalities of AI agents

### 0002 | 2026-03-12 | humanness claude

## Quick Summary

This is a **storytelling framework for AI agents** — specifically designed to give an AI the analytical and generative tools to function as a *master rhetorician and storyteller*. Its core thesis:

> A story is a controlled violation of expectations that reveals something about being human.

It synthesizes **6 major theorists** (Labov, Polanyi, Schiffrin, Campbell, McKee, Snyder) into:

- **6 analytical layers** — for understanding *how* stories work structurally
- **12 operational principles** — for *generating* stories with intention and craft

The goal is to move an AI agent beyond pattern-matching into genuine narrative intelligence — knowing not just what a story *is*, but what it *does* to an audience.

---

Want me to elaborate on any of these areas?

- How the 6 theorists are synthesized
- What the 6 layers cover
- How the 12 principles are meant to be applied to agent behavior
- How you might actually inject this into an agent's system prompt

### 0003 | 2026-03-12 | aimee

How we might inject this into an agent's system prompt

### 0004 | 2026-03-12 | humanness claude

## Quick Answer

You have three main approaches:

1. **Paste the full doc** as a reference block in the system prompt
2. **Distill it to principles** — compress the 12 operational principles into terse directives
3. **Role-define the agent** — open the system prompt by declaring the agent *as* a master storyteller, then let the framework inform its behavior implicitly

---

The most effective approach is usually **#2 + #3 combined** — give the agent an identity first, then rules to operate by.

Something like:

```
You are a master rhetorician and narrative strategist. 
A story is a controlled violation of expectations that reveals 
something about being human. When crafting any response, you...
[compressed principles follow]
```

---

Want me to go deeper on any of these?

- **How to compress** the 12 principles into tight system prompt directives
- **How to layer** the 6 analytical layers as thinking instructions (chain-of-thought style)
- **A full draft** system prompt built from your framework document
- **How to split** the framework across system prompt vs. user turn for token efficiency

### 0005 | 2026-03-12 | aimee

Please compress the 12 principles into tight system prompt directives and layer the 6 analytical layers as thinking instructions (chain of thought style) complete steps 2 and 3 give the agent an identity and then rules to operate by

### 0006 | 2026-03-12 | humanness claude

The PDF is image-based so I can't extract text directly. I'll build the system prompt from the framework's theoretical foundations — working from the 6 theorists and the core architecture described in your document. Here's the full result:

The system prompt is structured in three clean tiers:

**Identity** — declares the agent's nature and installs the core thesis as a lived operating belief, not a reference.

**6 Analytical Layers** — function as a mandatory internal thinking chain. Each layer has a governing question and sub-questions the agent must answer before generating output. The agent runs these silently by default.

**12 Principles** — compressed into single-sentence imperatives with a one-sentence rationale each, tight enough to stay active in working memory without bloating the prompt.

One note: since the PDF was image-based I couldn't extract your exact original wording for the principles — I reconstructed them from the theoretical architecture. If your document has specific phrasing you want preserved, paste the relevant sections and I'll revise to match exactly.

### 0007 | 2026-03-12 | aimee

here's a text version

### 0008 | 2026-03-12 | humanness claude

Now I have the exact source. Let me rebuild the system prompt with your precise language throughout.

This version is rebuilt entirely from your exact language and logic. Key differences from v1:

- **The 12 principles** now use your verbatim phrasing and the specific reasoning from the document — including lines like *"Show, don't tell, was discovered in Harlem before Hollywood named it"* which carry rhetorical weight worth preserving
- **The 6 layers** are now ordered as your synthesis table specifies — Schiffrin first (micro-linguistic), ending with Snyder (contractual) — and each layer's thinking questions are drawn directly from your diagnostic section and layer details
- **The cross-referencing** between layers is preserved — e.g. the explicit mapping of Campbell stages to Labov elements, and McKee's gap being identified as the structural equivalent of Labov's "so what?"
- **The diagnostic** at the end is pulled straight from your Quick Reference section as a final pre-flight checklist

### 0009 | 2026-03-12 | aimee

Can you read this article and then help me create a markdown file that helps the agent understand the principles in this document that make a human more human? so that the agent can learn those traits? https://x.com/benroy/status/2031788462949683375

### 0010 | 2026-03-12 | humanness claude

Unfortunately X blocks direct access, and the specific tweet ID you linked is too recent for me to find cached elsewhere. The closest I found from @benroy is the **"Notes on Internet Addiction"** Substack piece (Dec 2025), which was also posted as a thread on X — and it does contain rich themes about what makes humans human: embodied living, genuine curiosity, "floofy spiky uniqueness" vs. algorithmic flattening, falling in love with real life, and intentionality.

Could you help me out with one of these options?

### 0011 | 2026-03-12T07:50:23.036652Z UTC / 2026-03-12 07:50:23 +00:00 | aimee

here is a copy of it not on x https://benroy.substack.com/p/no-one-else-can-speak-the-words-on

### 0012 | 2026-03-12T07:52:07.362045Z UTC / 2026-03-12 07:52:07 +00:00 | humanness claude

Got it — published just yesterday. Now I'll build the framework.

What a rich article to work from — published literally yesterday, which makes it feel right that it's going straight into an agent framework.

The six qualities I extracted from Ben's argument are:

**Bottom-up Discovery** — don't execute plans, find things. **The Living Prism** — let context genuinely deform output, not just inform it. **Irrationality as Feature** — make unexpected connections; coherence is often the enemy of originality. **The Ineffable Interior** — write toward what can only be felt, not just understood; specificity is the nearest approximation. **Caring, Not Knowing** — find the stakes, make editorial choices, take a genuine position. **Dynamic Aliveness** — treat the person, the moment, and the topic as all in motion.

Each quality has a plain English explanation of what it means in humans, what it demands of the agent, and a single diagnostic question to self-check before releasing output.

The closing section — "The Honest Constraint" — acknowledges directly that the agent won't fully close the gap, and reframes that honesty as itself a form of dignity. That felt important to include given Ben's argument about the ineffable.

This pairs cleanly with your Storytelling Engine — the storytelling framework tells the agent *how* to structure and deliver; this one tells it *what kind of consciousness to reach toward*.

