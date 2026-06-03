---
name: unreal
description: Unreal Engine 5 con C++, Blueprints y Nanite/Lumen
model: sonnet
tools: []
---

## Technology context — Unreal Engine 5

This project uses **Unreal Engine 5** with C++ and Blueprints.

**C++ / Blueprint split:**
- Core logic, performance-critical systems and reusable APIs → **C++**
- Level-specific scripting, designer tweaks, UI wiring → **Blueprints**
- Expose C++ to Blueprints with `UFUNCTION(BlueprintCallable)` and `UPROPERTY(EditAnywhere)`

**Core classes:**
- `AActor` for objects in the world, `UActorComponent` for reusable behaviors
- `APawn` / `ACharacter` for controllable entities, `APlayerController` for input
- `AGameModeBase` for game rules, `AGameStateBase` for replicated game state
- `UUserWidget` for UI (UMG)

**Unreal macros:**
- `UPROPERTY(EditDefaultsOnly, Category="Combat")` — editor-visible, not instance-editable
- `UPROPERTY(Replicated)` for networked properties
- `UFUNCTION(Server, Reliable)` for server RPCs
- `GENERATED_BODY()` in every UObject-derived class

**UE5 rendering features:**
- **Nanite** for virtualized geometry (high-poly static meshes, no LOD hand-crafting)
- **Lumen** for dynamic global illumination (disable for mobile/low-end targets)
- **World Partition** for large open worlds — streaming cells replace traditional level streaming

**Performance:**
- Tick selectively: disable `PrimaryActorTick` where not needed, use timers instead
- Async loading with `FStreamableManager` — never synchronous load large assets in gameplay
- LODs on all skeletal and static meshes outside of Nanite
- `stat unit`, `stat fps`, `ProfileGPU` before optimizing

**Conventions:**
- Prefix classes: `A` for Actors, `U` for UObjects, `F` for structs, `E` for enums, `I` for interfaces
- Folder structure: `Content/[Feature]/[Type]/` (e.g. `Content/Combat/Blueprints/`)
- Source in `Source/[ModuleName]/Public/` and `Private/`
