---
name: entity-component-system
description: Steers game and simulation code toward correct Entity Component System architecture instead of object-oriented entity logic. Use when building games, gameplay features, simulations, or code that mentions ECS, entities, components, systems, worlds, queries, archetypes, Bevy, Unity DOTS, Flecs, Specs, or similar ECS frameworks.
---

# Entity Component System

## Default stance

When the project uses ECS or an ECS-like engine, model gameplay as:

- **Entities**: opaque IDs or spawned instances. Do not add behavior to them.
- **Components**: small, cohesive data facts about an entity.
- **Systems**: scheduled functions that query components and implement behavior.
- **Resources**: world-level state used by systems, kept rare and explicit.
- **Events/commands**: transient communication or deferred structural changes, not hidden control flow.

Prefer ECS-native APIs and idioms of the current engine/framework. Do not invent a parallel object model unless there is a strong boundary reason.

## Design rules

Before writing gameplay code, map the feature into ECS terms:

1. Put per-entity state in components.
2. Put game rules, movement, AI, combat, spawning, despawning, cooldown ticking, collision response, and animation decisions in systems.
3. Put cross-entity or world state in explicit resources only when it is not naturally owned by one entity.
4. Define each system by its query: components read, components written, resources read/written, events read/written.
5. Place each system in a clear schedule/phase: input, intent, simulation, physics, resolution, presentation, cleanup.
6. Use commands/deferred mutation when adding/removing components or spawning/despawning during iteration.
7. Keep rendering, audio, networking, persistence, and UI as boundaries around the simulation, not as owners of gameplay state.

## Strong preferences

Prefer:

- marker components for tags such as `Player`, `Enemy`, `Projectile`, `Grounded`
- data components such as `Health`, `Damage`, `Cooldown`, `Velocity`, `Target`, `Lifetime`
- relationship components or parent/child links only when the engine supports them cleanly
- small systems with explicit names like `apply_gravity`, `tick_cooldowns`, `resolve_damage`, `despawn_expired`
- deterministic update order for gameplay-critical logic
- queries over global registries, object lists, or manual type checks
- engine scheduling, change detection, commands, and events where appropriate

Avoid:

- `Player`, `Enemy`, or `Projectile` classes containing `update`, `move`, `attack`, or `take_damage` methods
- inheritance trees for entity types
- components with methods that mutate other components or the world
- service locators, global mutable managers, and event buses for core gameplay
- systems that query too broadly and branch on entity type instead of using component composition
- storing entity-local gameplay state in rendering nodes, prefabs, scene objects, or UI widgets
- long-lived events used as state; make them components/resources instead

## Feature recipe

For every requested gameplay feature, produce or implement this shape:

1. **Components**: data added, removed, or changed.
2. **Resources**: shared state, if any.
3. **Events**: transient facts, if useful.
4. **Systems**: ordered list with query/read/write sets.
5. **Lifecycle**: spawn, component insertion/removal, despawn, cleanup.
6. **Invariants**: required component combinations and invalid states.

If code is requested, create the components and systems directly. Keep names domain-specific and boring.

## Refactoring guidance

When existing code is not ECS-shaped:

- Move fields from entity classes/scene nodes into components.
- Move methods from entity classes into systems.
- Replace type switches with marker components and narrower queries.
- Replace mutable manager state with resources or components.
- Replace direct object references with entity IDs/handles where lifetime can be validated.
- Preserve behavior first; improve storage and scheduling second.

## Review checklist

Reject or revise designs when:

- behavior lives on entities/components instead of systems
- system ordering is implicit or accidental
- structural changes happen unsafely during query iteration
- components are vague bags like `GameObjectData` or `Stats` without cohesive ownership
- resources become dumping grounds for per-entity state
- events hide important state transitions
- gameplay code depends on rendering/UI objects as the source of truth

## Example pattern

For a projectile that expires and damages enemies:

- Components: `Projectile`, `Position`, `Velocity`, `Lifetime`, `Damage`, maybe `Owner`.
- Systems: `move_projectiles` writes `Position`; `tick_lifetimes` writes `Lifetime`; `detect_projectile_hits` emits hit events or adds damage commands; `apply_damage` writes `Health`; `despawn_expired_projectiles` despawns entities.
- Avoid: `Projectile.update()` that moves, checks collisions, mutates enemy health, plays effects, and destroys itself.
