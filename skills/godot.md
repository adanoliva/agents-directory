---
name: godot
description: Godot 4 con GDScript, escenas y arquitectura de señales
model: sonnet
tools: []
---

## Technology context — Godot 4

This project uses **Godot 4** with GDScript.

**Scene and node architecture:**
- Everything is a scene — compose complex objects from reusable sub-scenes
- One script per node type, focused on that node's responsibility
- `_ready()` for initialization after the node enters the scene tree
- `_process(delta)` for frame logic, `_physics_process(delta)` for physics (fixed timestep)
- `_input(event)` for input handling at node level, `_unhandled_input` for lower priority

**GDScript conventions:**
- Static typing everywhere: `var speed: float = 5.0`, `func move(dir: Vector2) -> void`
- `@export` to expose variables in the Inspector
- `@onready var player: CharacterBody2D = $Player` for node references
- Constants with `const`, class-level with `static var`
- Snake_case for variables and functions, PascalCase for classes

**Signal system (decouple everything):**
```gdscript
signal health_changed(new_health: int)

func take_damage(amount: int) -> void:
    health -= amount
    health_changed.emit(health)
```
- Define signals in the emitting node, connect in the parent or via editor
- Prefer signals over direct node references for cross-branch communication

**Node types:**
- `CharacterBody2D`/`3D` for player and NPCs with `move_and_slide()`
- `Area2D`/`3D` for trigger zones and hitboxes
- `RigidBody2D`/`3D` for physics-simulated objects
- `AnimationPlayer` for code-driven animations, `AnimationTree` for state machines
- `SubViewport` for render-to-texture effects

**Performance:**
- Object pooling with a custom pool node — `queue_free()` is fine for infrequent spawns
- `Node.set_process(false)` to disable tick on inactive nodes
- Use `PackedScene` and `instantiate()` for frequent spawning
- Profile with the built-in Profiler before optimizing
