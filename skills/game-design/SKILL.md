---
name: game-design
description: Guides opinionated, tasteful, commercially aware game design by prioritizing player fantasy, market appeal, fun, and scope discipline. Use when designing games, gameplay features, prototypes, simulations, Steam pitches, trailers, mechanics, loops, progression, game feel, hooks, fantasy, fun, scope, monetization, or game design critique.
---

# Game Design

## Core rule

Design the appeal before the mechanics. Players buy the fantasy, vibe, promise, and screenshots before they understand the systems. If the pitch is not desirable, better mechanics rarely save it.

Optimize for:

```text
quality = (fun * appeal) / scope
appeal = (presentation + fantasy) * readability
```

- **Appeal** gets players: "I need to be there / do that / master that / see what happens."
- **Fun** keeps players: challenge, agency, mastery, surprise, flow.
- **Scope** decides whether the game ships.
- **Monetization** matters, but decide it after the core promise is strong unless the business model defines the game.

## Default workflow

1. **Name the player fantasy** in one sentence.
2. **Define the trailer moment**: the 5-15 seconds that makes someone say "I need to play this."
3. **Choose the proven base**: genre, camera, controls, session length, platform expectations.
4. **Add one sharp difference**: fantasy, mechanic, simulation, tech, structure, or presentation.
5. **Cut scope until the promise survives**: fewer verbs, fewer content types, fewer systems.
6. **Prototype separately**:
   - appeal prototype: mock screenshots, pitch deck, trailer beats, mood, readability.
   - fun prototype: greybox controls, verbs, challenge, feedback loops.
7. **Measure the riskiest assumption** with the cheapest artifact.

Start with a pitch deck, Steam page mock, key art, or trailer sketch before implementation. Treat implementation as expensive evidence gathering, not the first design step. Exception: pure mechanics-first games, e.g. Balatro-like designs, where the core fun is the pitch.

## Appeal paths

Prefer proven appeal plus one meaningful twist. Avoid originality for its own sake.

- **Fantasy first**: "be a witch running a cursed bakery", "pilot a living submarine". Easy to understand, strong for marketing, may constrain mechanics.
- **Iterate a proven formula**: safer; win through sharper fantasy, pacing, usability, or content curation.
- **Market gap**: high upside, but validate with evidence; do not trust vibes alone.
- **Unique hook**: rare and risky; use only if the hook is instantly legible like Portal.
- **Translate other media**: borrow emotional texture from films, books, anime, tabletop, or history; be tasteful, not derivative.
- **Tech advantage**: simulation, destruction, scale, AI, procedural depth, or low-level performance that creates appeal competitors cannot cheaply copy.
- **Trailer-first**: design the sellable moment first; expensive, but clarifies what the game must deliver.

## Taste checks

Good concepts produce at least one strong urge:

- "I want to be that."
- "I want to explore that place."
- "I want to prove myself against that."
- "I want to tinker with that system."
- "I want to see how that story unfolds."
- "I want to spend time in that mood."

Weak concepts need long explanations. Strong concepts survive as one image, one sentence, and one verb.

## Useful lenses

Use references as lenses, not cargo cults:

- **Flow** (Mihaly Csikszentmihalyi): tune challenge so the player feels stretched, not bored or crushed.
- **Actionable Gamification** (Yu-kai Chou): check motivation beyond rewards: mastery, ownership, scarcity, social pressure, unpredictability, meaning.
- **Portal**: legible unique hook.
- **Balatro**: mechanics-first exception where the system itself is the fantasy.
- **Noita**: tech advantage creating marketable simulation appeal.

## Common traps

- **Mechanics-first blindness**: a clever system nobody wants to inhabit.
- **Local minimum**: polishing a weak idea instead of making a big jump.
- **Alien originality**: too unfamiliar to read; combine familiar frame + novel edge.
- **Scope inflation**: every added system taxes content, UI, balance, QA, and onboarding.
- **Wrong reward function**: optimizing lore, engine architecture, or novelty instead of appeal, fun, and shippability.
- **Measurement noise**: overreacting to tiny feedback; measure twice only where decisions are expensive.

## Prototype rules

- Optimize early for speed, not correctness.
- Throw prototypes away without regret.
- Test art/readability and gameplay/fun separately before merging.
- Parallelize multiple directions when possible.
- Use ugly code for disposable prototypes; use maintainable code once the direction survives.

## Response pattern

When advising, be concrete, opinionated, and willing to push back. Do not politely decorate weak concepts; sharpen them.

1. State the likely fantasy and audience.
2. Identify the strongest appeal factor.
3. Identify the biggest scope risk.
4. Propose 2-3 sharper alternatives.
5. Give the cheapest next validation step.
