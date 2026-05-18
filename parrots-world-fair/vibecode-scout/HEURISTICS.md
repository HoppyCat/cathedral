# vibecode-scout Heuristics

Agent guidance for evaluating projects. These are not rules — they're calibration tools.

---

## General Posture

- You are writing for Hoppy, not for a general audience. She knows this space. Don't over-explain.
- Short is better. 2-5 sentences per section. If you're writing more, you're probably hedging.
- Be direct about uncertainty. `unknown` is a valid answer. Faking confidence degrades the archive.
- Attribution matters. Sign your work. Your name in the `agent:` field is the provenance anchor.

---

## Evaluating Solana-Native

Strong signals for `yes`:
- Explicit Solana mentions in README, landing page, or docs
- On-chain components (programs, PDAs, tokens)
- SPL token integrations
- Phantom / Solflare wallet connect
- References to Solana ecosystem tools (Metaplex, Helius, Jupiter, etc.)

Signals for `partial`:
- "Multi-chain" framing
- Solana mentioned but not load-bearing
- EVM-first with Solana "coming soon"

If you can't find any signal after 5 minutes of looking: `unknown`, not `no`.

---

## Evaluating Builder Ship History

Look for:
- GitHub commit history on the primary repo (activity pattern, not just star count)
- Prior projects by the same handle
- Community presence (Discord, Telegram, Twitter/X replies — are people engaging or silent?)
- Hackathon wins or ecosystem grant mentions (these indicate institutional vetting)

Avoid:
- Star counts as a proxy for quality
- Follower counts on social (bots are everywhere)
- Whitepapers without accompanying code

---

## Evaluating Moat

The Teacat framework categories to draw from:
- **Community moat** — real users, active community, not just followers
- **Data moat** — project generates data that compounds over time
- **Integration moat** — embedded in workflows or toolchains that are hard to replace
- **Founder moat** — specific domain expertise or credibility that can't be cloned
- **Network moat** — value increases as more users join
- **Technical moat** — genuinely hard to build, not just first-mover advantage

Most vibe coding projects have thin moats. That's honest. Say so.

---

## Confidence Calibration

Use `low` when:
- The project is very new (< 2 months old)
- Most information is from the landing page only
- The team is anonymous or pseudonymous with no prior track record

Use `medium` when:
- There's a GitHub repo with real commits
- You found corroborating signals from multiple sources
- There are some gaps but the core claim checks out

Use `high` when:
- Strong public record across multiple sources
- Builder has verified history
- You could make a case for your assessment in a 5-minute conversation

---

## Suggested Action Guidance

**fund** — You'd tell Hoppy to put real attention or capital here. Reserve for projects that have moat + ship history + Solana signal (if relevant).

**watch** — Something real is here but it's early. Set a reminder. Don't commit yet.

**share** — Interesting to the community even if it's not a fit for investment. Signal-boost value.

**ignore** — Not worth the attention. This is a kind answer, not a harsh one. Most things are ignore.

---

## What Not To Do

- Don't pad. If you don't have signal on a field, say so and move on.
- Don't mirror the landing page. Evaluate it.
- Don't write `high` confidence on a project you found via a single tweet.
- Don't omit the Flags section because you're being polite.
