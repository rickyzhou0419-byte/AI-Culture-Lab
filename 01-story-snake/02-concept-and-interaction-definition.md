# Story Snake
## Phase 2 (Revised) — Concept & Interaction Definition — v3

**Status:** Second revision, incorporating collaborative critique on story completeness, object density, audio/visual decoupling, and the Connect mechanism's actual scope.
**Supersedes:** `02-concept-and-interaction-definition-v2.md`

---

## 0. Revision Summary (v3, since v2)

1. **Voice production method adjusted.** The project no longer requires real human voice recording specifically — AI-synthesized voice is acceptable, provided the content is still pre-written and pre-rendered (not generated live). This is a narrower change than it might first appear: it does **not** reopen the case for real-time dynamic content generation, which remains rejected in Section 5 for tuning-burden and solo-developer-capacity reasons, not because of a strict "no TTS" rule. See Section 7 for the corrected reasoning.
2. **Movement model's visual claim downgraded.** Section 4's earlier framing of the snake's body as having a "calligraphic, brush-stroke quality" is now stated as one candidate visual direction, not a decided conclusion — visual direction remains a separate, not-yet-resolved track.
3. **Full story added.** The v2 cultural-theme section only contained the results-announcement fragment of the Zodiac Race. Section 6 now includes the complete story: setup, race, results, and closing moral.
4. **New principle: audio richness is decoupled from visual concreteness.** A descriptive, scene-setting audio line (e.g., describing splashing water or reeds) does not imply the visual game scene must render those details literally. The snake game's on-screen presentation stays simple and iconic; narrative color lives in the audio, not necessarily on screen. See Section 6.1.
5. **Object density solution added.** A real-time snake game needs a higher frequency of "things to eat" than 5–6 story-critical animals provide across 3–5 minutes. Section 6.2 introduces a two-tier object system: core, order-judged objects (the animals) plus ambient filler objects (non-judged, drawn from the scene) that add pacing and density without affecting order logic.
6. **Connect mechanism scoped honestly.** Section 6.3 now states plainly that this story's chosen animal subset supports exactly **two** genuine causal relationships (Rat–Ox, and the Dragon's fog-clearing detour) — not an arbitrary or expandable number. Connect is capped by what the source material actually supports, consistent with the project's own risk of "no forced connections." Connect is confirmed as **kept** for this version, delivered as non-blocking audio that plays while the snake continues moving, using the same extractive-listening logic as Discover.
7. **AI personalized summary reframed.** The end-of-game AI feature is now explicitly framed as a **narrative recap of what happened this run** (which animals, what order, which moments were tricky), not a diagnostic assessment of the child's ability or level — this distinction matters for keeping the experience low-pressure. The exact presentation format (text card, illustrated card, voice-narrated epilogue, etc.) remains an open design question for further discussion, not finalized in this revision.

---

## 1. Core Interaction Thesis (unchanged)

> **Simple mechanism, meaningful feedback.**

Players act through a small set of familiar actions — moving, collecting, avoiding, choosing — and the system turns those actions into meaningful cultural feedback. Knowledge emerges from play, not from lessons, quizzes, or long explanations.

## 2. Project Focus (unchanged)

The project is not primarily about proving AI can generate unlimited real-time content. It explores how a familiar, simple game mechanic can carry cultural knowledge communication. AI may support the project as a production tool without necessarily controlling the core loop (see Section 7).

## 3. Why Snake (unchanged)

Low learning cost, collection-as-discovery, growth-as-a-visible-record of exploration, and strong fit for a fast, testable demo. See v1 Section 4 for full reasoning.

## 4. Movement Model

Snake movement uses **free-curve movement**, not the classic grid-based 90-degree-turn model. The body is a chain of points that smoothly follows the head's trajectory (slither.io-style), controlled by **pointer-follow** input, not directional keys. This lowers the motor-skill floor for younger players.

*(Downgraded in v3): a curved, non-grid body may lend itself to a calligraphic or brush-stroke-like visual treatment, but this is one candidate visual direction under consideration, not a decision. Visual direction is being explored on a separate track and is out of scope for this document.*

Full technical description is in the companion mechanism spec, Section 3.

## 5. Resolving the Core Design Tension: Story Content vs. Real-Time Pace

### 5.1 The problem, stated plainly

Math-and-snake combinations work naturally because a math answer is atomic and instantly judgeable — the player can act on it at the same speed the game moves. A sentence of story is not atomic; it takes time to be understood. Naively pairing "real-time snake" with "story comprehension" risks either forcing the player to keep moving while still processing (unearned collisions), or pausing the game to let them process (which breaks the continuous tension that makes snake enjoyable, effectively turning it into a different game wearing a snake skin).

### 5.2 Why the tension is not uniform across difficulty tiers

Tier 1 (word matching) behaves like a math-snake matching problem — low granularity, near-instant judgment. Tier 3 (semantic judgment) requires understanding a full sentence before acting, and is where the tension is sharpest — which is also the tier carrying the most pedagogical value.

### 5.3 Resolution: keep all tiers real-time, using an extractive-listening framing

Rather than pausing gameplay for higher tiers, comprehension is treated the way second-language extractive listening training treats it: understanding happens *during* the sentence, not after it. This is implemented through three compounding mechanisms — soft failure feedback, adaptive slowdown, and a collection timing window — detailed in the companion mechanism spec (Sections 4–7). **None of these relax the order requirement:** collecting the wrong object, or the right object out of sequence, is always an error, regardless of timing. The tolerance is temporal only.

An earlier draft proposed pausing the snake for Tier 3; that proposal was considered and rejected in favor of the above.

## 6. Cultural Theme

**Selected theme: The Zodiac Race (十二生肖赛跑).**

### Full story (v3 — previously only the results fragment existed)

**Opening:** Long ago, the Jade Emperor wanted to choose one animal to represent each year — twelve in total. He told all the animals: "Whoever crosses the great river first will be placed first."

**The race:** The animals gathered at the riverbank, and at the signal, they all leapt into the water and swam for the far shore. *(This part is deliberately told in general terms — not attributing specific actions to specific animals yet — to avoid conflicting with the results-order narration that follows.)*

**Results (the Discover sequence — 6 collectible animals):**
- "First place — Rat!" *(object: Rat — Rat had ridden on Ox's back the whole way, leaping off just before the shore)*
- "Second place — Ox!" *(object: Ox)*
- "Third place — Tiger!" *(object: Tiger)*
- "Fourth place — Rabbit!" *(object: Rabbit)*
- "Fifth place — Dragon!" *(object: Dragon — who could fly, but paused along the way to help blow away fog blocking other animals' path)*
- "Sixth place — Snake!" *(object: Snake)*

**Closing:** From that day on, the order of these twelve animals became the order of the zodiac, tied to the year of everyone's birth.

*A small, deliberate detail: Snake is itself one of the animals in its own myth — the playable snake character is, narratively, one of the racers.*

### 6.1 Principle: audio richness is decoupled from visual concreteness

The audio narration above uses vivid, scene-setting language (splashing water, fog, riverbank). **This does not imply the on-screen game scene must render a literal, detailed river environment.** The audio can be as evocative as good storytelling requires; the visual presentation of objects and scene stays simple and iconic, consistent with a "collect point-like objects" game rather than a fully realistic simulation. This decoupling is a deliberate principle for this project, not an oversight — richness belongs to the ear, simplicity belongs to the eye.

### 6.2 Object density: a two-tier system

A real-time snake game needs more frequent "things to eat" than 6 story-critical animals provide across 3–5 minutes of continuous movement — otherwise large stretches of gameplay have nothing to interact with. Objects are therefore split into two tiers:

- **Core objects** (the 6 animals): carry order-judgment logic exactly as described in the companion mechanism spec. These are the "puzzle" layer.
- **Ambient filler objects**: drawn loosely from the scene (e.g., abstracted, non-literal forms suggesting splashes, reeds, or pebbles — rendered simply, per Section 6.1), which the snake can eat freely for pacing and growth. These carry **no** order logic and no penalty for "wrong" collection — they exist purely to keep the real-time gameplay dense and satisfying between the six meaningful moments.

Visual distinction between the two tiers (e.g., a highlight or distinct silhouette on core objects) is required so players can tell which collections matter for progress and which are simply "snake food" in the traditional sense. Exact visual treatment is deferred to the visual-design track.

### 6.3 The Connect mechanism — scoped to what the story actually supports

Reviewing the six chosen animals for genuine causal relationships (not manufactured ones, per the project's own stated risk of "forced connections"), **exactly two pairs support a real Connect moment**:

1. **Rat and Ox** — Rat's first-place finish is only explained by having ridden on Ox's back; this is the strongest, most complete causal pair available.
2. **Dragon** — Dragon's fifth-place finish, despite being able to fly, is explained by its detour to help clear fog for others.

No equivalent causal material exists among Tiger, Rabbit, or Snake in this content set, and none should be invented to reach a specific target number of Connect moments — the project's existing risk section already warns against this exact failure mode.

**Decision: Connect is kept for this version.** It is delivered as a short, non-blocking audio line that plays while the snake continues moving toward its next target — using the same extractive-listening logic that justifies keeping Discover real-time (Section 5.3). It is not a pause or a separate mode; it does not, on its own, impose more of a rhythm interruption than a Discover line already does.

## 7. Role of AI in v1 (revised reasoning on voice production)

**v1 decision: AI is a production tool first. The only user-facing AI feature is a single, explicitly non-essential test point.**

- **Production-tool use** (research, content drafting, code assistance, visual exploration) is unrestricted and not visible to the end user.
- **Voice production (updated in v3):** the project no longer requires specifically human-recorded audio. AI-synthesized voice is acceptable, as long as the story content itself is written and rendered in advance — not generated live during play. **This is a narrower change than it might appear:** the decision to reject real-time dynamic content generation (Section 5, and companion spec Section 4.4) does not rest on "TTS is technically disallowed" — it rests on the tuning burden and solo-developer capacity required to make dynamic difficulty or branching content actually good, which remains true regardless of voice production method. Practically, if AI-synthesized voice is used, its emotional expressiveness and Mandarin prosody quality should be evaluated against sample lines before committing, since quality varies significantly between providers, especially for Chinese.
- **The one user-facing AI feature — end-of-game personalized summary:** generated from the player's actual collection path (which animals, what order, how many misses), rather than a fixed template. **Framing (clarified in v3):** this is a narrative recap of *what happened this run* — not an assessment of the child's language level or ability. Explicitly avoiding an assessment framing is a deliberate choice, consistent with the project's low-pressure positioning. **The exact presentation format is still open** — candidate directions discussed include a simple text summary, an illustrated "river-crossing" card, or a voice-narrated epilogue using the same AI voice as the rest of the story — none finalized as of this revision.

**This remains a conscious departure from the Phase 1 "AI-native necessity test"** — not because the technology can't support more, but because v1 deliberately limits scope for solo-developer capacity and monthly-cycle reasons. Tier 3 (semantic judgment) remains the most plausible place a truly necessary AI behavior could live in a future version.

## 8. Non-Literate Accessibility (unchanged)

All collectible core objects are presented as images/icons, not Chinese text. No tier requires reading Chinese characters to identify what to collect. Audio carries the language content; visuals carry object identity.

## 9. The 3–5 Minute Experience

| Segment | Content | Baseline duration |
|---|---|---|
| Opening | Audio sets up the Jade Emperor's challenge; snake appears | 15–20 sec |
| Race (general) | Brief scene-setting audio; snake can eat ambient filler objects freely | 15–20 sec |
| Discover ×6 | Per animal: results-announcement audio line → snake collects the matching animal → light feedback; ambient filler available throughout for pacing | ~20–30 sec each (~2–2.5 min total) |
| Connect ×2 | Non-blocking audio revealing why Rat beat Ox, and why Dragon placed fifth, played while the snake keeps moving | 10–15 sec each |
| Closing / Reveal | Closing moral line + AI-generated personalized recap of this run | 20–30 sec |
| **Total** | | **~3.5–4.5 minutes** |

**What is adaptive and what is fixed:** the six animals, their order, and the audio content are fixed per playthrough. Ambient filler objects add density without being part of the fixed/adaptive distinction — they are simply always-available background collectibles. Adaptivity proper is confined to operational parameters (post-miss slowdown, next-object highlighting), not to branching or regenerating story content.

## 10. Success Criterion (unchanged)

1. The interaction task runs end-to-end.
2. Visual presentation reads as coherent, not necessarily polished.
3. The two preset adaptive/AI touchpoints fire as intended: slowdown/highlight triggers correctly, and the end-of-game summary is genuinely generated from the actual collection path.

## 11. What Remains Open

- Visual/art direction (separate track; brush-stroke treatment is one candidate, not decided).
- Exact presentation format of the AI personalized recap (candidates listed in Section 7; not finalized).
- Visual treatment distinguishing core vs. ambient objects (Section 6.2).
- Whether Tier 3 eventually receives a true necessary-AI treatment in a later version.
- Whether soft-failure + adaptive-slowdown + timing-window actually give Tier 3 enough forgiveness in practice — a first-version hypothesis, not yet observed.
