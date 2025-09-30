# Entity-Component Principles
1. Read Chapter 7 (Component) from Robert Nystrom's *Game Programming Patterns*.
2. Compare Unity's `MonoBehaviour`-based components with pure data components.
3. Prototype a simple character using composition-only components; avoid inheritance trees.
4. Reflect on composition benefits: reuse, testability, and runtime modularity.

## Entity Assembly
```csharp
var enemy = new GameObject("Enemy");
enemy.AddComponent<HealthComponent>().Initialize(100);
enemy.AddComponent<AIMover>().SetSpeed(3f);
enemy.AddComponent<DropLoot>().Register(lootTable);
```






## References
- [Component pattern chapter](https://gameprogrammingpatterns.com/component.html) - composition-based design for game objects.
- [GameObjects and components manual](https://docs.unity3d.com/Manual/GameObjects.html) - Unity component model reference.
- [Unity ECS tutorial](https://learn.unity.com/tutorial/entity-component-system) - introduction to Unity ECS workflow.
- [Component scripting article](https://www.bitsquid.se/blog/component_scripting.html) - engineering insights into component architectures.
- [Unity DOTS introduction talk](https://www.youtube.com/watch?v=MlK6SIjcjE8) - presentation on ECS motivation and workflow.
## Key Terms
- **Entity**: Game object identity composed from interchangeable components rather than inheritance hierarchies.
- **Component**: Data or behaviour module attached to an entity; in Unity, typically a `MonoBehaviour` or pure data struct.
- **Composition**: Building functionality by assembling components together instead of subclassing.
- **System**: Handler that operates over collections of components to update game logic (e.g., AI movement, health decay).
- **Data-Oriented Component**: Struct-like component containing only state, processed by systems for cache-friendly updates.
- **Component Registry**: Script or service that discovers components on an entity and wires dependencies like loot tables or health values.
