---
name: defold
description: Defold con Lua, game objects y arquitectura basada en mensajes
model: sonnet
tools: []
---

## Technology context — Defold

This project uses **Defold** with Lua.

**Core concepts:**
- **Game objects** contain components — no inheritance, pure composition
- **Collections** are scene files; nest collections for reusable prefabs
- **Components**: Script, Sprite, Sound, Collision Object, GUI, Label, Tilemap, Model
- Everything communicates via **messages** — no direct function calls between game objects

**Message passing:**
```lua
-- Send a message to another game object
msg.post("enemy#script", "take_damage", { amount = 10 })

-- Receive messages
function on_message(self, message_id, message, sender)
    if message_id == hash("take_damage") then
        self.health = self.health - message.amount
    end
end
```
- Use `hash()` for all message and property IDs — interned strings, zero allocation
- `msg.post(".", "disable")` to disable the current game object
- `go.property()` for Inspector-editable script properties

**Lua conventions in Defold:**
- `self` table holds per-instance state in script components
- `init(self)` → `update(self, dt)` → `final(self)` lifecycle
- Avoid global state — use `self` or module-level locals with `local`
- Modules in `require("my_module")` for shared logic

**Physics and input:**
- Collision Objects with kinematic/dynamic/static types
- `physics.ray_cast()` for raycasting, `go.animate()` for tweens
- Input in `on_input(self, action_id, action)` — bind in `game.input_binding`
- `action.pressed`, `action.released`, `action.repeated` for input state

**Performance:**
- Defold has a fixed draw call budget — batch sprites with atlases, not individual images
- Use **Factory** components for pooled spawning (`collectionfactory` for complex objects)
- `go.delete()` vs factory return-to-pool pattern for high-frequency objects
- Profile with the built-in web profiler (`http://localhost:8002`)

**Project structure:**
- `/main/` for the main collection and bootstrap
- `/modules/` for shared Lua modules
- `/assets/` organized by type: `/assets/sprites/`, `/assets/sounds/`
