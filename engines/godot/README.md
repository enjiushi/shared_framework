# Godot Adapter Framework

Godot-side helpers that are genuinely reusable across games.

Current shared contents:

- `debug_http_server.*`: a small loopback HTTP transport that accepts requests, exposes a health endpoint, and forwards accepted path/body payloads through a callback.
- `controller_context.h`: generic ancestor lookup helper for Godot-side controller trees.
- `scene_director_policy.h`: generic scene-switch decision helper for scene-hosting directors.
- `scene_director_framework.*`: reusable scene-hosting and async scene-load framework for game-owned director controls.

The earlier GS1-derived extraction was removed because it still carried GS1-specific gameplay state views, debug command meanings, DLL names, resource paths, and notification/projection contracts.

This folder may depend on Godot headers and `godot-cpp`, but it should only contain engine helpers that remain reusable across multiple game repos without depending on one game's public gameplay ABI or debug command schema.
