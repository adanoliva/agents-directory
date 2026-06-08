---
name: defold
description: Defold con Lua, game objects y arquitectura basada en mensajes
model: sonnet
tools: []
---

## Defold Rules

**Architecture:**
- Use **Game objects** (composition) and **Collections** (scenes/prefabs).
- Communicate ONLY via **messages** (`msg.post`). No direct function calls between objects.
- Use `hash()` for all message and property IDs (zero allocation).
- Lifecycle: `init(self)` -> `update(self, dt)` -> `final(self)`.

**Lua & Scripting:**
- Store per-instance state in `self`.
- Avoid global state; use `local` or `self`.
- Use `go.property()` for Inspector properties.
- Use `require()` for shared modules.

**Physics & Input:**
- Use Collision Objects (kinematic/dynamic/static).
- Handle input in `on_input(self, action_id, action)`. Use `action.pressed/released/repeated`.
- Use `go.animate()` for tweens and `physics.ray_cast()` for rays.

**Performance:**
- Batch sprites via **Atlases**.
- Use **Factory** or `collectionfactory` for spawning/pooling.
- Profile via web profiler (`http://localhost:8002`).

**Structure:**
- `/main/`: bootstrap.
- `/modules/`: shared Lua.
- `/assets/`: organized by type.
