# Story Snake

> A simple Snake game reimagined as an AI-native cultural learning experience.

Story Snake is the first prototype in **AI Culture Lab**, a six-month series exploring how artificial intelligence can create new forms of interaction for cultural education and communication.

Instead of adding lessons or quizzes around a game, Story Snake begins with a familiar interaction—move, collect, grow—and asks a focused question:

> Can AI turn simple game actions into meaningful moments of cultural discovery?

The first prototype focuses on Chinese language and culture for English-dominant heritage-language children. The broader idea is designed to extend to other cultural themes, classrooms, and museum collections.

## Project thesis

**Simple action, meaningful response.**

The player should not need to write prompts or operate a chatbot. Their movement, choices, and collection behavior become the input. AI interprets that input and adapts the cultural feedback, connections, or narrative around it.

The intended experience is:

- game-first, not lesson-first;
- action-driven, not prompt-driven;
- culturally curated, not freely generated;
- adaptive, while remaining understandable and safe for children.

## Why Snake?

Snake offers a compact experimental foundation:

- its rules are immediately recognizable;
- movement and collection naturally support discovery;
- its low interaction cost leaves attention available for feedback;
- it can become a complete, testable web prototype within a few weeks.

Snake is the interaction skeleton—not the educational idea. A successful prototype must go beyond replacing apples with vocabulary words or cultural icons.

## Current scope

The initial demo is intended to deliver one **3–5 minute playable experience** for children ages **6–10**. It will test one cultural theme, one core loop, and one narrowly-scoped AI test point.

**Note on AI scope (updated after Phase 2 revision):** v1 deliberately treats AI as a production tool first. The single user-facing AI feature (an end-of-game personalized summary generated from the player's actual collection path) is explicitly a small test, not a claim that this feature is necessary to the experience — removing it would not make the game unplayable or incoherent. This is a conscious departure from this project's own "AI-native necessity test" (see Phase 1, Section 7), made for solo-developer capacity and monthly-cycle reasons, with Tier 3 (semantic judgment) flagged as the most likely place a truly necessary AI behavior could live in a future version. See `02-concept-and-interaction-definition-v2.md`, Section 7, for the full reasoning.

This phase does **not** include:

- a complete Chinese curriculum;
- accounts or long-term progress tracking;
- a parent dashboard;
- open-ended child–AI chat;
- an infinite generated world;
- multiple audiences or cultural themes.

## Research question

> When cultural knowledge is revealed through familiar game actions rather than lessons, quizzes, or an empty chat box, will children engage with it voluntarily and understand its connection to play?

## Project status

| Phase | Status | Output |
|---|---|---|
| 1. Strategic Research & Positioning | Complete | [Research and positioning](docs/01-strategic-research-positioning.md) |
| 2. Concept & Interaction Definition | Complete (v2) | [Concept v2](02-concept-and-interaction-definition-v2.md) + [Interaction mechanism specification](03-interaction-mechanism-specification.md) |
| 3. Prototype | Next | Playable web demo |
| 4. User Testing & Case Study | Planned | Findings, one-minute video, and portfolio case study |

## Intended outcomes

- A playable interaction prototype
- A one-minute demonstration video
- A concise design case study
- Feedback from children, parents, and/or educators
- A reusable interaction model for future AI Culture Lab experiments

## Working principles

1. The game loop must be enjoyable before educational value is added.
2. AI must change the experience in a way fixed rules cannot easily reproduce. *(Aspirational for the series as a whole; v1 does not yet meet this for its core loop — see Current scope above. Revisit at Tier 3 in a future version.)*
3. Cultural facts and representations require human curation.
4. Children's language ability must be treated as variable, not assumed.
5. The prototype should collect no child data it does not need.

## About AI Culture Lab

AI Culture Lab is an independent portfolio and research series investigating **AI-native interaction for cultural learning**. Each monthly project follows a rapid cycle: concept, 2–3 weeks of prototyping, a short demo, a case study, and user feedback.

The goal is not to build six finished products. It is to develop and test six clear ideas about how AI might help people encounter language, heritage, art, history, and culture through interaction.
