---
name: bevy
description: Develop, debug, and review Rust projects using the Bevy game engine. Use when working on Bevy ECS systems/components/resources, plugins, schedules, states, UI, rendering/assets, input, physics/gameplay, migration errors, or Cargo builds for Bevy apps.
---

# Bevy

## First moves

1. Read Bevy version from `Cargo.toml` / `Cargo.lock`; do not assume APIs.
2. Check current sources when API details matter:
   - Examples: <https://bevyengine.org/examples/>
   - Migration guides: <https://bevyengine.org/learn/migration-guides/>
   - Local examples: `~/.cargo/registry/src/*/bevy-*/examples`
3. Inspect existing plugins/schedules before adding systems.
4. Verify changes with `cargo check`; avoid `cargo clean` unless explicitly needed.

## Current API anchors

Bevy breaks APIs often. For modern Bevy (0.17+):

- Buffered cross-system data: `#[derive(Message)]`, `add_message::<T>()`, `MessageWriter<T>`, `MessageReader<T>`.
- Triggered/observable behavior: `#[derive(Event)]`, `commands.trigger(...)`, `app.add_observer(...)`, `On<T>`.
- Input buttons: `Res<ButtonInput<KeyCode>>` / `Res<ButtonInput<MouseButton>>`.
- Fixed timestep: put systems in `FixedUpdate`; `Res<Time>` is fixed there, or use `Res<Time<Fixed>>` explicitly.
- 3D material handles are wrapper components like `MeshMaterial3d<StandardMaterial>`, not raw `Handle<StandardMaterial>` components.
- Bevy 0.18 automatically updates `Aabb` for mesh/sprite entities; remove old manual AABB workarounds.

## Design rules

- Model data first: entities, components, resources, messages/events, systems, schedules.
- Components are data; systems are transformations; resources are global state and should be rare.
- Prefer focused components over monolithic "stats" structs when entities may use different subsets.
- Use plugins as feature boundaries. A feature registers its own types and systems.
- Make behavior-dependent order explicit: input → gameplay state → derived values → visuals → UI.
- Use change detection (`Changed<T>`, `Added<T>`, `is_changed()`) for expensive/visual/UI updates.
- Prefer queries and marker components over storing entity IDs. If storing entities, handle despawn with `if let Ok(...)`.

## Minimal patterns

```rust
pub struct CombatPlugin;

impl Plugin for CombatPlugin {
    fn build(&self, app: &mut App) {
        app
            .add_message::<Damage>()
            .add_systems(Update, (apply_damage, update_health_ui).chain());
    }
}

#[derive(Component)]
pub struct Health { pub current: f32, pub max: f32 }

impl Health {
    pub fn fraction(&self) -> f32 { (self.current / self.max).clamp(0.0, 1.0) }
}

#[derive(Message)]
pub struct Damage { pub target: Entity, pub amount: f32 }

fn apply_damage(mut damage: MessageReader<Damage>, mut health: Query<&mut Health>) {
    for event in damage.read() {
        if let Ok(mut health) = health.get_mut(event.target) {
            health.current -= event.amount;
        }
    }
}
```

## Build workflow

- Fast check: `cargo check`
- Dev run/build: use project command; if appropriate, `cargo run --features bevy/dynamic_linking`
- Release validation: `cargo build --release`
- Do not delete `target/` casually; Bevy rebuilds are expensive.

## Pitfalls checklist

- System registered in the plugin/app?
- Correct schedule (`Startup`, `Update`, `FixedUpdate`, state-specific schedules)?
- Ordering resolved with `.chain()`, `.before()`, `.after()`, or system sets?
- Query cardinality handled (`single()` can fail; return early when absence is valid)?
- Borrow conflicts avoided with `ParamSet`, query filters, or `get_many_mut`?
- Asset handles/components match the project's Bevy version?
- Migration guide checked before using remembered APIs?
