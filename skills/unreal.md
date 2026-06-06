---
name: unreal
description: Unreal Engine 5 con C++, Blueprints y Nanite/Lumen
model: sonnet
tools: []
---

## Unreal Engine 5

- **Workflow**: C++ for core/performance; Blueprints for scripting/UI. Use `BlueprintCallable` and `UPROPERTY` to bridge.
- **Core**: `AActor` (world objects), `UActorComponent` (reusable behavior), `APawn`/`ACharacter` (entities), `UUserWidget` (UI).
- **Macros**: `UPROPERTY` (EditDefaultsOnly, Replicated), `UFUNCTION` (Server, Reliable), `GENERATED_BODY()`.
- **UE5 Features**: Nanite (geometry), Lumen (GI), World Partition (streaming).
- **Performance**: Disable `PrimaryActorTick` where possible. Use `FStreamableManager` for async loading. Profile with `stat unit`/`fps`.
- **Conventions**:
  - Prefixes: `A` (Actor), `U` (UObject), `F` (struct), `E` (enum), `I` (interface).
  - Content structure: `Content/[Feature]/[Type]/`.
