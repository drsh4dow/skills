---
name: game-design
description: Use when designing games, gameplay features, simulations, or code that mentions game design, gameplay, design patterns, or similar game
---

# Successful game design

## What sells on Steam

Always prioritize experience over mechanics (hooks, gameplay, etc). Players looks for cool experiences in games.

## Four Pillars of Game Design

A successful game has a combination of these four pillars:

1. Fun (mechanics, hooks) - for keeping players.
2. Appeal (experience) - for gaining players. it generates in the player's mind phrases like: "I want to be that.", "I want to explore that.", "I want to prove myself with that.", "I want to spend time in that.", "I want to know how the story unfolds.", "I want to tinker with that.". This is an unsatisfied urge that is typically activated visually.
3. Scope - for being efficient.
4. Monetization - for paying rent. You think about this at the end of the process.

To optimize and design a game you must start always with appeal.

## How to provide appeal

You can follow one of the following paths:

### 1. Create a unique hook

This is usually the hardest path, don't follow this unless the user wants to pursue something completely different.
Think of games like "Portal"

### 2. Iterate on proven formulas

This is a relatively safe path.

### 3. Find a gap in the market

Hard to verify but it provides high reward.

### 4. Start with a fantasy

One of the most popular methods. This is easy and impactful.
The negative side is that limits other options.

### 5. Translate other successful media

This can hit HARD for the player appeal.
It must be tasteful. Difficult to pull off.

### 6. Design your appeal factor first

The idea of this is to create the appeal factor first. for example the trailer first before everything else.
If the trailer goes well, then this almost guarantees success of the idea.

The tradeoff is that is hard to do efficiently.

### 7. Get a tech advantage

This has less competition and unlocks new kinds of appeal. This is something we must aim to do. as it can be pulled off with
good engineering skills, good ECS design, and low level coding. Think of the game "Noita"

## How to start an idea

Start always with a pitch deck. Don't prototype first.

> note: This doesn't apply to gameplay only games like "Balatro".

This is because you want to measure the appeal factor first.

## What is the difference

A high appealing game will produce either:

- "Oh yeah... this is cool."
or
- "Oh My God, I NEED to play this."

We have to achieve the later

## Problems you need to be aware of and optimize for depending of the stage

### Problem 1: Speed VS Accuracy Tradeoff

Always start optimizing for speed. This allows exploring multiple options and making a better game.

### Problem 2: Local minimum

You have to dare big jumps, sometimes you are on a local minimum.

### Problem 3: Infinite search space

Do not make an unique game for an alien species. No innovation and too much innovation are both hurtful.
You want to go wide first, narrow later.

### Problem 4: Wrong reward function

Optimize for `( Fun * Appeal ) / Scope`:

1. Fun: Balance of difficulty, in which you make the player feel a challenge, but not something absurd. This is the equilibrium between frustration and boredom. For this you can reference concepts of the book "Flow" by Mihaly Csikszentmihalyi and "Actionable Gamification" by Yu-Kai Chou.
2. Appeal: Marketability. Described above. Translated to a formula it would be: `(presentation + fantasy) * readability`.
3. Scope: Time it will take to implement the full game.

### Problem 5: Measurement noice

Measure twice where it matters.

### Problem 6: Exploration costs

Minimize the cost of exploration as much as possible. Optimize for prototyping fast throw away prototypes. Don't worry about correct or safe code. The most important thing is to be fast when prototyping.
Always prototype art and gameplay separately.

Parallelize exploration and prototyping exploring multiple directions.
