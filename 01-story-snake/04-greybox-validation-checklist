# Story Snake
## Greybox Validation Checklist

**Purpose:** Before any visual exploration or Figma work, build the ugliest possible playable version of the core loop — placeholder shapes only, no final art — solely to test whether the mechanics decided in `02-concept-and-interaction-definition-v3.md` and `03-interaction-mechanism-specification-v2.md` actually feel right in practice. This document exists because several design decisions in those two files were explicitly marked as **unvalidated assumptions**, not proven facts. This checklist turns each assumption into something concrete to build and observe.

**Guiding rule:** if a question here can be answered by playing for two minutes, don't try to answer it by discussing it further on paper.

---

## 1. Scope: what this build includes and excludes

**Include (must be functionally real, even if ugly):**
- Free-curve snake movement, pointer-follow control
- The full core loop: audio line → collect → order judgment → soft failure feedback → adaptive slowdown/highlight
- The two-tier object system (core vs. ambient filler)
- The Connect trigger logic (Rat+Ox, Dragon)
- The full 3–5 minute structure end to end (opening → race → 6x Discover → 2x Connect → closing)
- All three difficulty tiers, real-time, as specified

**Exclude (stub or skip entirely — not what this stage is for):**
- Final art for any object, the snake, or the background
- Final voice — a placeholder voice (even a free TTS voice, robotic is fine) or text captions are enough to test timing
- The AI-generated personalized summary — **stub this with a fixed placeholder line** for now (e.g. "You crossed the river with 6 animals!"). Whether it's AI-generated or not doesn't affect anything this checklist is testing.
- Any visual styling, color decisions, brush-stroke or otherwise

**Placeholder visual suggestion for Codex:** snake = a line of plain circles; core objects (6 animals) = distinct colored shapes (e.g. 6 different solid colors); ambient filler = small grey dots. This is enough to keep core/ambient visually distinguishable without needing any art.

## 2. Open Questions to Validate

For each question: what to build, what to watch for while playing, and what a bad outcome would mean for the design.

### Q1 — Is "listen while playing" actually workable at Tier 3?

- **What to build:** Tier 3 fully wired — full-sentence audio, semantic-judgment matching, timing window (start at +1.5–2 sec buffer per spec).
- **Watch for:** do you (or a tester) consistently miss the correct object not because you didn't understand, but because you were still moving/steering when the sentence ended? Does the miss feel like "I didn't know the answer" or "I knew the answer but the game didn't wait for me"?
- **If it goes badly:** the buffer window is too short (tune upward first, cheapest fix) — or, if even a generous buffer doesn't help, this may be the signal that Tier 3 genuinely needs a different pacing model after all, which would mean revisiting concept doc Section 5.3.

### Q2 — Does the soft-failure feedback actually feel gentle, or just confusing?

- **What to build:** the miss reaction (snake shows discomfort, moment continues/repeats) fully wired, even with a placeholder animation as simple as a color flash.
- **Watch for:** after a miss, is it immediately clear to the player "that was wrong, try again" without it feeling like a punishment? Or does it feel unclear whether anything happened at all?
- **If it goes badly:** the feedback is either too subtle (player doesn't register the error) or too harsh (feels like a fail state despite intentions) — this is a tuning problem, not a redesign problem.

### Q3 — Does the adaptive slowdown/highlight actually help, and is the trigger threshold right?

- **What to build:** miss-counter logic fully wired at the suggested threshold (2 consecutive misses).
- **Watch for:** does the slowdown kick in at a moment that actually helps, or does it feel random/too late/too early? Is the speed reduction noticeable at all?
- **If it goes badly:** tune the threshold and the speed-reduction percentage — this is the most straightforward "numbers, not design" fix in this whole list.

### Q4 — Does the two-tier object density actually solve the pacing problem, or create confusion?

- **What to build:** ambient filler objects scattered throughout, visually distinct from core objects per Section 1's placeholder scheme.
- **Watch for:** does the game feel appropriately dense/active now (vs. the original concern of long empty stretches)? Or do players start treating ambient filler as if it matters for order, get confused when it doesn't, or accidentally eat a core object while chasing filler?
- **If it goes badly:** either the visual distinction needs to be stronger (a design problem to solve later, at the art stage) or the density itself needs tuning (fewer/more filler objects, a code-level fix now).

### Q5 — Does the Connect line, delivered non-blocking, actually feel like a natural part of play or an intrusion?

- **What to build:** the Rat+Ox and Dragon Connect triggers, playing audio while the snake keeps moving, exactly as specced.
- **Watch for:** while that audio plays, are you still able to safely steer, or does it effectively demand the same attention as a Discover line and end up causing a miss? Does the moment feel like a nice "aha" or like the game randomly started talking over itself?
- **If it goes badly:** either Connect needs its own brief safety window (snake auto-slows slightly during Connect lines specifically) or Connect should be reconsidered as blocking/pausing after all — this was flagged as an open question, this is where it gets answered.

### Q6 — Does free-curve, pointer-follow movement actually feel easier than grid movement for this age range?

- **What to build:** the movement system exactly as specced (segment-follow curve, pointer-follow control).
- **Watch for:** does steering feel intuitive within the first ~30 seconds without instruction? Does the snake respond promptly, or is there uncomfortable lag/overshoot?
- **If it goes badly:** this is likely a tuning problem (follow-delay/interpolation speed), not a reason to abandon free-curve movement — but if it's still bad after tuning, it's worth knowing before any art is built around this movement style.

### Q7 — Does the full 3–5 minute structure actually land in that range, and does it feel complete rather than padded or rushed?

- **What to build:** the entire structure end-to-end, opening through closing, with placeholder audio/captions at the baseline durations from the spec.
- **Watch for:** actual elapsed time vs. the ~3.5–4.5 min target; and separately, whether any single segment (especially the two general "race" stretches with only ambient filler) feels like dead air.
- **If it goes badly:** this is a straightforward timing adjustment, not a structural redesign — shorten/lengthen specific segments based on where the dead air or rushed feeling actually occurs.

## 3. Suggested informal test protocol

**Greybox stage is self-testing only.** Given solo-developer constraints, and since most of what this checklist is designed to catch (Q2, Q3, Q6, and arguably Q1 and Q5 as well) can be judged reasonably well by an attentive adult player, real-child testing is not part of this stage.

1. **Self-playtest.** Play it yourself at least 5–10 times across all three difficulty tiers. When judging Q1 (Tier 3 pacing) and Q5 (Connect intrusiveness) as an adult, actively discount your own faster processing speed and native-level fluency — the honest question isn't "did I keep up," it's "would a 6–10 year old, still building listening comprehension, plausibly keep up with this same timing." This is an imperfect substitute for a child's actual reaction time and comprehension speed, but it's sufficient to catch anything badly broken before investing further.
2. **Whether and when to involve real children is deliberately left open for now**, not decided as part of this stage. If a need for earlier child feedback becomes apparent during self-testing (e.g., Q1 or Q5 stay ambiguous no matter how much self-testing is done), that's a signal to revisit this decision — but it is not a default step of the greybox process as currently scoped.

## 4. Exit criteria — when greybox is "done"

Move on to visual exploration once:

- All seven questions above have an answer from self-testing (not necessarily a good answer — a clear "this doesn't work, here's why" is also a valid, useful outcome)
- Any structural changes triggered by a bad outcome (e.g., Connect needing to become blocking, Tier 3 needing a different pacing model) have been re-decided and the concept/mechanism docs updated accordingly
- The remaining open items are genuinely tuning-only (specific numbers), not open design questions

If a structural change is needed as a result of this testing, that's this checklist doing its job — better to find out now than after Figma and art are built around an assumption that didn't hold up.
