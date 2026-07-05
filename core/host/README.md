# Core Host

Engine-free host bridge helpers that are genuinely reusable across games.

Current shared contents:

- `adapter_config_loader.*`: serializes adapter-owned config directories into a runtime bootstrap blob and can recover the embedded project root path later.
- `runtime_bootstrap_dll_loader.*`: loads only the neutral `gs_runtime_*` lifecycle and split-step symbols from a gameplay DLL.

This folder still must not depend on one game's public headers, symbol names, commands, state-view types, or DLL naming conventions.
