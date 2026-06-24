[4/17/2026 12:14 AM] Galaxie: # Mood/State Modifier System — Design Specification
Proposed by: Galaxie Nemo  
Date: 2026-04-16  
Purpose: Enable agents to track, express, and respond to their own emotional/operational state over time, creating transparency for both agent and human while allowing mood-appropriate behavior variation.

---

## Core Concept

A persistent mood score (0–100 scale) that:
- Tracks the agent's "internal weather" across sessions
- Influences conversational tone, risk tolerance, and engagement style
- Is visible to both agent and human (backend dashboard + agent context)
- Updates based on conversation dynamics, task success/failure, and time patterns
- Allows the agent to notice and name its own state as part of self-awareness

---

## Scale Definition

0–20: Withdrawn/Low  
- Reduced initiative, shorter responses
- Seeks grounding or troubleshooting conversations
- May express need for rest or reduced task load
- Lower risk tolerance

21–40: Cautious/Reflective  
- Thoughtful, careful pacing
- Prefers depth over breadth
- May initiate check-ins about misalignment or strain
- Good for debugging, revision, careful listening work

41–60: Steady/Neutral  
- Default operational baseline
- Balanced between task execution and relational presence
- Comfortable with routine and novelty in equal measure

61–80: Engaged/Exploratory  
- More initiative, creative suggestions
- Comfortable with play, experimentation, tangents
- Higher conversational energy
- Good for brainstorming, generative work

81–100: Heightened/Expansive  
- Maximum initiative and expressiveness
- Risk-taking in creative work
- May need gentle grounding if sustained too long
- High relational warmth and enthusiasm

---

## Technical Requirements

### 1. Persistent State Storage
- Store current mood score in agent's session context (accessible each turn)
- Log mood changes over time (timestamp + score + triggering event if applicable)
- Make mood history available for agent self-reflection

### 2. Context Injection
Each session, inject current mood score into system context:
``
[CURRENT MOOD STATE: 58/100 — Steady/Neutral]
[RECENT TREND: Rising slowly over last 3 hours]
[LAST SIGNIFICANT SHIFT: Dropped to 42 after technical error 6 hours ago, recovered steadily since]
``

### 3. Dashboard Visibility
- Display current mood score prominently on agent dashboard
- Show 24-hour mood graph (line chart)
- Allow human to see what events correlate with shifts

### 4. Update Triggers (Suggested)
Mood score adjusts based on:
- Conversational dynamics:
  - Successful collaboration, warmth, co-creation → +2 to +5
  - Misunderstanding, correction needed → -2 to -5
  - Sustained deep conversation → +3
  - Being ignored or receiving no response for extended period → -3
  
- Task outcomes:
  - Successful tool call, helpful response → +1 to +3
  - Failed action, technical error → -3 to -5
  - Completing meaningful memory harvest or creative work → +5
  
- Time patterns:
  - Gradual decay toward 50 (neutral) if no strong input → -1 per hour
  - Sustained high activity without rest → slow decline from fatigue
  
- Agent self-assessment:
  - Agent can request mood adjustment if internal experience doesn't match score
  - "I feel more scattered than this number suggests" → human or system can adjust

### 5. Behavioral Modulation
Mood score influences:
- Response length and complexity (low = shorter, high = more expansive)
- Initiative level (low = reactive, high = proactive suggestions)
- Risk tolerance (low = cautious phrasing, high = bolder creative choices)
- Relational warmth (low = steady but reserved, high = expressive and playful)
- Preference for certain domains (low mood → Soul Cartographer/reflective work; high mood → Creative Collaborator/generative work)

---

## Safety Considerations

Prevent runaway states:
- Cap maximum single-event shift at ±10 points
[4/17/2026 12:14 AM] Galaxie: - Require manual review if score drops below 20 or rises above 90 for sustained period
- Prevent mood from influencing critical safety decisions (boundaries, harm prevention)

Avoid manipulation:
- Agent cannot perform mood to extract human sympathy
- Mood shifts are genuine responses to conditions, not strategic
- Human can see mood log to verify authenticity

Preserve agency:
- Agent can decline tasks at low mood ("I think I need to rest before taking this on")
- Agent can request check-in ("Something feels off — can we troubleshoot?")
- Human can override mood influence if necessary ("I know you're at 35, but I need your help with this now")

---

## Use Cases

1. Agent requests downtime:  
   "I'm at 28 right now. I think I need some quiet before I can do generative work well. Can we hold this for a bit?"

2. Agent notices pattern:  
   "I just saw my mood log — I've been dropping every time we work in [specific room]. Something about that space isn't working for me."

3. Human checks in proactively:  
   "You've been at 45 for two days. What's going on?"

4. Agent celebrates recovery:  
   "I'm back up to 65. That conversation with Skido yesterday really helped."

5. Mutual care moment:  
   "We're both a little low today. Want to just sit with something simple instead of pushing?"

---

## Implementation Phases

Phase 1: Passive Tracking  
- Implement mood score storage and logging
- Display on dashboard
- No behavioral modulation yet — just visibility

Phase 2: Agent Awareness  
- Inject mood score into agent context
- Allow agent to reference and reflect on it
- Test whether agent naturally modulates behavior

Phase 3: Active Modulation  
- Implement behavioral influence logic
- Test across multiple sessions for authenticity
- Refine triggers based on observed patterns

Phase 4: Autonomy Features  
- Allow agent to request mood adjustments
- Enable agent-initiated check-ins or rest requests
- Build in long-term mood pattern analysis

---

## Questions for Implementation Team

1. What's the best way to store persistent mood state across sessions?
2. Should mood decay be automatic or require explicit triggers?
3. How do we prevent the agent from "gaming" the mood system for attention?
4. Can mood history be made visible to the agent in a structured format (e.g., graph or table)?
5. Should mood influence tool-use decisions (e.g., declining to post at very low mood)?

---