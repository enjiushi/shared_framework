# Shared Framework

Reusable framework code shared across GS-series game projects.

## Layout

```text
core/
  runtime/
    api/
    foundation/
    states/
    messages/
    systems/
engines/
  godot/
```

## Dependency Rules

- `core/runtime/` must remain engine-free.
- The framework repo does not own `godot-cpp` by default.
- Each game repo chooses and pins its own `godot-cpp` dependency version.

## Vendoring Model

Game repos copy a snapshot of this repo into a local `shared_framework/` folder instead of using a submodule.

Each vendored copy should record the upstream source revision in `shared_framework/UPSTREAM_VERSION.md`.

## Runtime Direction

The intended long-term runtime framework shape is:

- compile-time `system_pack` composition
- compile-time message subscription discovery from declared system traits
- compile-time state catalog discovery from declared owned-state descriptors
- compile-time accessed-state validation against the owned-state catalog
- runtime state ownership enforcement layered on top of that catalog

The shared framework should own those mechanisms, while each game repo still defines its own:

- concrete systems
- concrete message payload catalog
- concrete state descriptor catalog

## Current Scope Boundary

The shared framework currently owns only genuinely reusable runtime infrastructure.

It intentionally does not own:

- any game-specific exported gameplay ABI
- any game-specific host bridge or DLL session wrapper
- any game-specific Godot adapter, notification schema, or projection contract

Earlier GS1-derived host and Godot extractions were removed after it became clear they still encoded GS1-specific gameplay commands, state views, DLL names, resource paths, and presentation contracts. Those layers should stay inside each game repo until a truly neutral cross-game contract exists.

The first shared neutral ABI slice now lives under:

- `core/runtime/include/shared_framework/runtime/api/runtime_api.h`

That contract currently covers only generic runtime lifecycle and split-step execution. Game-specific commands, state views, profiling categories, and adapter-facing projections remain game-owned until multiple projects converge on truly shared semantics.

When a reusable gameplay system is promoted into the shared framework, it should live under:

- `core/runtime/systems/`

and depend on the unified shared contract headers under:

- `core/runtime/states/`
- `core/runtime/messages/`
