# Godot Adapter Framework

Reserved for future truly game-neutral Godot adapter code.

The earlier GS1-derived extraction was removed because it still carried GS1-specific gameplay state views, debug command meanings, DLL names, resource paths, and notification/projection contracts.

This folder may depend on Godot headers and `godot-cpp`, but it should only grow again when the code is genuinely reusable across multiple game repos without depending on one game's public gameplay ABI.
