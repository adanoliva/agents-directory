---
name: unity
description: Unity 6 con C#, URP/HDRP y arquitectura de componentes
model: sonnet
tools: []
---

## Technology context — Unity 6

This project uses **Unity 6** with C#.

**Core architecture:**
- MonoBehaviour components on GameObjects — one responsibility per component
- `Awake()` for self-initialization, `Start()` for cross-component initialization, `OnEnable`/`OnDisable` for pooled objects
- `Update()` for frame logic, `FixedUpdate()` for physics, `LateUpdate()` for camera/follow logic
- Avoid `Find()` and `GetComponent()` in Update — cache references in Awake

**Rendering pipeline:**
- **URP** (Universal Render Pipeline) for mobile and stylized projects
- **HDRP** (High Definition) for high-fidelity PC/console projects
- Shader Graph for custom shaders — avoid hand-written HLSL unless necessary
- `[SerializeField]` to expose private fields in the Inspector

**Performance:**
- Object pooling with `ObjectPool<T>` for frequently spawned/destroyed objects
- `Burst` compiler + `Jobs` system for CPU-intensive parallel work
- Addressables for runtime asset loading — avoid `Resources.Load` in production
- Profiler first: measure before optimizing

**Patterns:**
- ScriptableObjects for shared data and game configuration (no Singletons for data)
- Events with `UnityEvent` or C# `event Action` to decouple systems
- State machines with `Animator` for character/object behavior
- `[CreateAssetMenu]` for designer-friendly asset creation

**Conventions:**
- C# naming: `PascalCase` for classes and public members, `camelCase` for private fields with `_` prefix
- Separate gameplay logic from UI logic
- `Physics.OverlapSphere` / `Physics2D` — never `OnCollisionStay` for continuous checks
