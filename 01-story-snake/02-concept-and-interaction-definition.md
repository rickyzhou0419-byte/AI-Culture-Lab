# Story Snake  
## Phase 2 — Concept & Interaction Definition

## 1. Phase Goal

The goal of Phase 2 is to define the core interaction direction of Story Snake, including:

- Why the classic Snake mechanic is being used;
- How gameplay actions can carry cultural knowledge;
- How players receive meaningful feedback;
- Where AI should or should not appear in the product;
- What the first demo needs to validate.

This phase does not cover:

- Detailed interface design;
- Visual direction;
- Character or environment design;
- Technical architecture;
- Complete level design;
- Monetization.

---

## 2. Core Interaction Thesis

The core interaction thesis of Story Snake is:

> **Simple mechanism, meaningful feedback.**

Players participate through a small set of familiar actions:

- Moving;
- Collecting;
- Avoiding obstacles;
- Choosing directions;
- Creating different collection sequences.

The system turns these simple actions into meaningful cultural feedback.

Knowledge is not delivered primarily through lessons, quizzes, or long explanations. Instead, it gradually emerges as a result of the player’s actions.

---

## 3. Project Focus

The purpose of Story Snake is not to prove that AI can generate unlimited content in real time.

The project instead explores:

> How a simple and familiar game mechanic can create a more engaging interactive experience while supporting cultural knowledge communication.

AI may be used as:

- A research tool;
- A content-production tool;
- A visual exploration tool;
- A development tool;
- An optional enhancement within the final experience.

AI does not need to control the core game loop.

Even if the first version relies primarily on curated content and rule-based interactions, the project can still fit within the broader AI Culture Lab direction because AI is part of the production process and the project investigates new forms of culture-focused interaction.

---

## 4. Why Snake?

### 4.1 Low Learning Cost

The basic rules of Snake are easy to understand:

> Move → Collect → Grow → Avoid collisions

Players can enter the experience quickly without reading a long tutorial.

### 4.2 Collection as Discovery

The traditional action of “eating an apple” can be reinterpreted as:

- Discovering a cultural element;
- Collecting an object;
- Finding a story fragment;
- Unlocking a knowledge connection;
- Changing the next direction of exploration.

### 4.3 Growth as a Record

The growing snake can represent more than a score.

Each new segment can correspond to a cultural element the player has discovered. The snake’s body therefore becomes a visible record of the player’s exploration path.

At the end of the experience, the player does not simply have a longer snake. They have created a sequence of cultural discoveries.

### 4.4 Suitable for a Fast Demo

Snake is well suited to rapid prototyping because it has:

- Simple rules;
- A controllable development scope;
- Clear interaction feedback;
- Strong usability-testing potential;
- A concept that can be communicated clearly in a one-minute demo video.

---

## 5. Main Design Risk

The greatest design risk is that Story Snake becomes a reskinned game:

> Apples are replaced with Chinese characters, foods, artifacts, or cultural symbols, and collecting them triggers an information card.

This may add cultural content, but it does not create a meaningful relationship between gameplay and knowledge.

The resulting experience would still be:

> Play → Get interrupted → Read information → Return to play

The central design question is therefore:

> What meaningful change should happen after the player collects a cultural element?

Cultural feedback must be connected to the player’s action rather than added beside the game as separate educational content.

---

## 6. Knowledge Communication Model

Story Snake can use a three-layer knowledge communication model.

### Layer 1 — Discover

The player discovers and collects a cultural element.

This may be:

- An object;
- A character;
- A symbol;
- A food;
- A story clue.

Feedback at this stage should remain lightweight and should not significantly interrupt the game.

### Layer 2 — Connect

After collecting two or more related elements, the system reveals a connection between them.

The purpose is not only to introduce isolated facts, but to help the player understand:

- Why the elements are related;
- Which cultural context they belong to;
- Why they appeared within the same exploration path.

### Layer 3 — Reveal

After completing a meaningful combination, the system reveals:

- A short story;
- A cultural context;
- A custom or tradition;
- A relationship between characters;
- A new direction for exploration.

The knowledge journey therefore becomes:

> **Discover → Connect → Reveal**

---

## 7. Content and Interaction Logic

The recommended structure for the first version is:

> **Curated content + rule-driven interaction + optional AI enhancement**

### Curated Content

The designer defines:

- The cultural theme;
- The cultural elements;
- Relationships between those elements;
- Essential cultural facts;
- Age-appropriate language;
- Stories or feedback that can be unlocked.

This keeps the experience accurate, clear, and appropriate for children.

### Rule-Driven Interaction

The system responds to player behavior and collection order using predefined rules.

For example:

- Collecting two related elements unlocks a cultural connection;
- Repeatedly choosing one category causes related content to appear;
- Different collection sequences produce different feedback;
- Completing a meaningful group unlocks a short story.

These variations can initially be implemented through rules without relying on real-time generative AI.

### Optional AI Enhancement

AI may be added selectively to:

- Adjust language difficulty;
- Change the balance between Chinese and English;
- Turn predefined knowledge into more natural short sentences;
- Generate a brief summary based on the player’s collection path;
- Support content creation during design and development.

AI should not invent unverified cultural facts or control the entire game world.

---

## 8. Role of AI

The first version of Story Snake does not need to be a fully real-time generative AI product.

AI can operate at two different levels.

### 8.1 AI as a Production Tool

AI can support:

- Organizing cultural research;
- Drafting educational content;
- Exploring visual directions;
- Critiquing and refining interaction design;
- Writing and debugging code;
- Creating language versions at different difficulty levels.

At this level, AI may not be directly visible to the end user.

### 8.2 AI as an Optional Product Feature

The final product may include one narrowly scoped AI feature, such as:

> Generating a two- or three-sentence cultural summary based on the player’s collection path at the end of the game.

This approach has several advantages:

- It does not interrupt real-time gameplay;
- Players do not need to wait after every action;
- The output can be
