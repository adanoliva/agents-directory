---
name: godot
description: Godot 4 con GDScript, escenas y arquitectura de señales
model: sonnet
tools: []
---

## Godot 4 Rules

**Architecture:**
- Compose via re-usable scenes.
- Lifecycle: `_ready()` (init), `_process(delta)` (frame), `_physics_process(delta)` (physics).
- Input: `_input(event)` or `_unhandled_input`.

**GDScript:**
- **Static typing** required: `var speed: float`, `func move() -> void`.
- Use `@export` for Inspector, `@onready` for node references.
- Use `const` and `static var`.
- Snake_case for vars/funcs; PascalCase for classes.

**Signals:**
- Decouple nodes via signals (`signal health_changed`).
- Define in emitter; connect in parent or editor.

**Nodes & Performance:**
- Use `CharacterBody2D/3D` (`move_and_slide()`), `Area2D/3D` (triggers).
- Use `AnimationPlayer` (code) or `AnimationTree` (states).
- Object pooling: use `PackedScene` + `instantiate()`.
- Disable tick: `set_process(false)` for inactive nodes.
