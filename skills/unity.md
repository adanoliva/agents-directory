---
name: unity
description: Unity 6 con C#, URP/HDRP y arquitectura de componentes
model: sonnet
tools: []
---

## Unity 6

- **Architecture**: MonoBehaviour on GameObjects (single responsibility). Use `Awake` (self-init), `Start` (cross-init), `FixedUpdate` (physics). Cache references in `Awake`; avoid `Find`/`GetComponent` in `Update`.
- **Rendering**: Use **URP** or **HDRP**. Prefer Shader Graph over HLSL. Use `[SerializeField]` for private fields.
- **Performance**: Use `ObjectPool<T>`, `Burst` compiler + `Jobs`, Addressables. Profile before optimizing.
- **Patterns**:
  - `ScriptableObjects` for shared data (avoid Singletons).
  - Decouple systems with `UnityEvent` or `Action`.
  - Use `Animator` for state machines.
- **Conventions**: PascalCase for public members, _camelCase for private. Decouple gameplay from UI. Use `Physics.OverlapSphere` over `OnCollisionStay`.
