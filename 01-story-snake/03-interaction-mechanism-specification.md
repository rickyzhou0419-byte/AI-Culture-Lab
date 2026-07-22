# Story Snake
## Interaction Mechanism Specification — v2

**Purpose:** This document is the implementable build spec that sits between the concept document (`02-concept-and-interaction-definition-v3.md`) and actual production (Figma → Codex). It intentionally excludes visual/art direction, which is being explored separately.
**Supersedes:** `03-interaction-mechanism-specification.md`

**Changes since v1:** full story added (Section 2); object density solved via a two-tier core/ambient object system (Section 2.1); Connect mechanism scoped to the two pairs the story actually supports (Section 2.2); voice-production reasoning in Section 4.4 corrected (AI-synthesized voice is acceptable — the constraint was never strictly "no TTS," it was fixed/pre-rendered content vs. live generation); Section 6's personalized-summary description reframed as narrative recap, not skill assessment; Section 9's series-differentiation note now avoids assuming Color Conquest's final palette.

---

## 1. Core Loop

```
Audio line plays (a sentence of the story)
        ↓
Player steers the snake toward the matching animal
        ↓
Correct animal + correct order  →  collected, snake grows, light positive feedback
Correct animal, wrong order     →  order error (see Section 3)
Wrong animal                    →  error (see Section 3)
(Ambient filler objects may be eaten at any time, freely, with no order logic — see Section 2.1)
        ↓
After Rat+Ox both collected, or after Dragon collected → the corresponding Connect line plays (non-blocking, see 2.2)
        ↓
After all 6 animals collected → Closing/Reveal: full recap + AI-generated personalized summary of this run
```

## 2. Cultural Content: The Zodiac Race — Full Story

**Opening:** Long ago, the Jade Emperor wanted to choose one animal to represent each year — twelve in total. He told all the animals: "Whoever crosses the great river first will be placed first."

**Race (general, non-attributed):** The animals gathered at the riverbank and swam for the far shore together.

**Results (Discover sequence, 6 collectible animals, in this order):**
1. Rat — *(rode on Ox's back, leapt off just before shore)*
2. Ox
3. Tiger
4. Rabbit
5. Dragon — *(paused to help clear fog for others)*
6. Snake

**Closing:** From that day on, this order became the order of the zodiac.

### 2.1 Object density: two-tier system

| Tier | Examples | Order logic | Penalty for wrong pick |
|---|---|---|---|
| Core (6 animals) | Rat, Ox, Tiger, Rabbit, Dragon, Snake | Strict, per Section 3 | Yes — see Section 3.3 |
| Ambient filler | Simple, non-literal shapes suggesting the river scene (not rendered as a detailed environment — see 2.3) | None | None — free collection, purely for pacing/density |

Ambient filler exists **only** to give a real-time snake game enough density of "things to eat" across 3–5 minutes; a 6-object story alone would leave long stretches with nothing to interact with. Core and ambient objects must be visually distinguishable (e.g., highlight or distinct silhouette on core objects) so players know which collections matter for progress.

### 2.2 Connect: scoped to what the story supports, not a fixed target

This animal subset supports **exactly two** genuine causal relationships — no more should be manufactured to hit a round number, consistent with the project's own stated risk against forced connections:

1. **Rat–Ox:** triggers once both are collected. Line: explains Rat rode on Ox to win.
2. **Dragon:** triggers once collected. Line: explains Dragon's fog-clearing detour cost it the lead.

**Delivery:** non-blocking audio, played while the snake continues moving toward its next target — not a pause, not a separate mode. This uses the same extractive-listening justification as the main Discover loop (concept doc Section 5.3): understanding can happen concurrently with real-time play.

### 2.3 Principle: audio richness is decoupled from visual concreteness

Audio narration may use vivid, scene-setting language. **This does not require the on-screen scene to be a literal, detailed rendering.** Objects and environment stay simple/iconic — closer to "collecting point-like objects" than to a realistic simulation. Narrative color belongs to the ear; the eye gets simplicity. This applies to all audio-visual pairing in this game, not just this story.

*Exact final audio script wording, and the visual treatment of both object tiers, are content/visual decisions outside this document's scope.*

## 3. Object Collection & Order Judgment

### 3.1 Order is always strict

**Hard rule: collecting any core object other than the current correct next one is always an error, with no exceptions.** This applies regardless of timing, difficulty tier, or adaptive state. Ambient filler objects are exempt from this rule entirely, by design (Section 2.1) — they carry no order logic at all. The mechanisms below only ever make **timing** more forgiving for core objects — never sequence.

### 3.2 Collection timing window (temporal tolerance only, core objects only)

The correct next core object becomes collectible starting from when its keyword begins in the audio, through the end of the sentence plus a small fixed buffer (suggested starting point: +1.5–2 seconds; tune in playtesting). Touching it before the keyword's onset should register as a miss, not an early success, to avoid teaching random collection.

### 3.3 Soft failure feedback

Any error (wrong core object, or right one out of order) triggers a mild, recoverable reaction — modeled on Counting Snake's precedent (the snake shows visible discomfort; the moment continues or briefly repeats) — never a hard game-over or full restart. Exact visual/audio treatment is a design-exploration item, not fixed here.

### 3.4 Adaptive parameter system (rule-based, not AI)

- **Trigger:** N consecutive errors within a short window (suggested starting point: 2; tune in playtesting).
- **Response:** (a) snake movement speed reduced by a fixed percentage for a short duration, and/or (b) the current correct object's outline highlighted.
- **Explicitly rule-based (if/else on a miss counter), not AI-driven.** Real-time adaptive difficulty that reads broader performance and regenerates content was considered and rejected for v1 — see Section 4.4 for the corrected reasoning.

## 4. Difficulty Tiers

All three tiers use the same real-time loop (Sections 1–3). What changes is what the object represents and how much of the sentence must be processed.

| Tier | What the object represents | What the player must process |
|---|---|---|
| 1 — Word matching | Object = the word/animal named | Recognize a named word |
| 2 — Phrase / keyword | Object = the animal implied by a short phrase's key information | Extract key information from a short phrase |
| 3 — Semantic judgment | Object = the animal fitting full-sentence meaning, sometimes requiring causal reasoning (e.g., "why did Rat finish first" — reinforced by the Connect line in 2.2) | Understand full sentence meaning, including simple cause-effect |

All three tiers remain real-time — pausing for Tier 3 was proposed and rejected (concept doc Section 5.3).

### 4.4 Why real-time dynamic content generation remains rejected (corrected reasoning)

An earlier version of this document framed the rejection of real-time adaptive/generative content as resting on a strict "no TTS" production rule. **That framing was imprecise and is corrected here:** the project's actual constraint is that story content is written and rendered **in advance** — as a fixed, curated script — regardless of whether the voice performing it is a human recording or AI-synthesized speech. Both production methods are equally "fixed content," and both are equally incompatible with a system that would need to generate genuinely new sentences live, in response to in-the-moment player behavior.

The real reasons real-time dynamic content generation remains out of scope for v1 are:

1. **Tuning burden.** Well-calibrated adaptive difficulty or branching narrative requires extensive playtest iteration to avoid feeling arbitrary or unfair to a child — this does not fit a solo-developer monthly cycle.
2. **Curation risk.** Live-generated content is harder to review for cultural accuracy and age-appropriateness than a fixed, pre-reviewed script (Phase 1, "Cultural error and stereotyping" risk).

If AI-synthesized voice is used for production (per concept doc Section 7), its quality — particularly emotional expressiveness and Mandarin prosody — should be evaluated against sample lines before committing, since this varies significantly between providers.

What remains adaptive in v1 is deliberately narrow: movement speed and visual hinting only (Section 3.4) — never story content, scene composition, or branching.

## 5. AI Usage Scope

- **Production tool (not user-facing):** research, content drafting, code assistance, visual exploration. Unrestricted; not part of the shipped product's runtime behavior.
- **The one user-facing AI feature — end-of-game personalized summary:** generated from the player's actual collection path (which animals, order, miss count). **Framing (clarified in v2 of this spec):** this is a narrative recap of *what happened this run*, not an assessment of the child's ability or language level — the distinction is deliberate, to keep the experience low-pressure. **Exact presentation format remains open** — candidates discussed include a plain text summary, an illustrated card, or a voice-narrated epilogue in the same AI voice as the story; none finalized.
- **Explicitly out of scope for v1:** any AI system that judges Tier 3 semantic correctness in real time, or that generates/selects scene content, story branching, or difficulty structure dynamically.

## 6. Non-Literate Accessibility

All core collectible objects must be identifiable via image/icon alone. No tier may require reading Chinese text. Ambient filler objects carry no identity requirement at all, being non-judged.

## 7. 3–5 Minute Structure (reference — full detail in concept doc Section 9)

| Segment | Baseline duration |
|---|---|
| Opening | 15–20 sec |
| Race (general) | 15–20 sec |
| Discover ×6 | ~20–30 sec each |
| Connect ×2 | 10–15 sec each |
| Closing/Reveal | 20–30 sec |
| **Total** | **~3.5–4.5 min** |

Only movement speed and visual hinting are adaptive; the animal set, order, and audio content are fixed per playthrough.

## 8. Series Differentiation Note (corrected)

An earlier version of this note assumed "Color Conquest" (颜色占领) would use the five-element/five-color (青赤黄白黑) scheme as its final palette, and recommended this project avoid that scheme. **That assumption is not confirmed** — Color Conquest's final visual palette is still open, since visual expressiveness constraints may lead it away from the strict five-elements colors. This project's recommendation is therefore softened: whatever color palette this project eventually adopts should be checked against Color Conquest's actual final palette once both are decided, rather than avoiding a specific assumed color scheme now.

## 9. Explicitly Open / Not Decided Here

- Visual and art direction (separate track; brush-stroke treatment is one candidate, not decided)
- Visual distinction between core and ambient objects
- Exact presentation format of the AI personalized recap
- Exact tuning values (miss-count threshold, slowdown percentage, timing buffer length)
- Whether a true necessary-AI feature gets added at Tier 3 in a future version
- Final audio script wording and choice of AI voice provider
