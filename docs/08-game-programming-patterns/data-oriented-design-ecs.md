# Data-Oriented Design and ECS
1. Read Unity DOTS documentation on Entities, Jobs, and Burst compilation.
2. Migrate a small gameplay system (e.g., projectile simulation) to ECS; measure performance.
3. Analyze memory layout benefits: cache locality, SIMD gains, and predictable updates.
4. Note pitfalls: authoring complexity, hybrid workflows, and debugging strategies.

## ISystem Query
```csharp
public partial struct MoveSystem : ISystem
{
    public void OnUpdate(ref SystemState state)
    {
        foreach (var (velocity, transform) in SystemAPI.Query<RefRW<Velocity>, RefRW<LocalTransform>>())
        {
            transform.ValueRW.Position += velocity.ValueRO.Value * SystemAPI.Time.DeltaTime;
        }
    }
}
```






## References
- [Data oriented design book](https://www.dataorienteddesign.com/dodmain/dodmain.html) - foundational DOD philosophy.
- [Unity DOTS overview](https://unity.com/dots) - official introduction to the DOTS stack.
- [Entities documentation](https://docs.unity3d.com/Packages/com.unity.entities@latest) - API docs for Unity ECS.
- [Data oriented design article](https://www.gamedeveloper.com/programming/data-oriented-design) - summary of DOD benefits and patterns.
- [Data oriented design talk](https://www.youtube.com/watch?v=rX0ItVEVjHc) - Mike Acton GDC session.
## Key Terms
- **Data-Oriented Design (DOD)**: Engineering approach that organizes memory layouts for cache efficiency and predictable performance.
- **Entity Component System (ECS)**: Pattern that separates data (components) from logic (systems) and runs them on contiguous arrays.
- **Unity DOTS**: Unity's implementation of ECS plus Jobs and Burst compiler for high-performance gameplay code.
- **Burst Compiler**: LLVM-based compiler that vectorizes and optimizes C# jobs for significant CPU gains.
- **SystemAPI.Query**: Unity Entities API for iterating over component archetypes in an ECS system.
- **Hybrid Workflow**: Strategy that mixes ECS with GameObjects/MonoBehaviours while DOTS authoring tools mature.
