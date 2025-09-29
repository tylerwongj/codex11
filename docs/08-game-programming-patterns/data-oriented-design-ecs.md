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
## Word List
- 1
- 2
- 3
- 4
- a
- acton
- analyze
- and
- authoring
- benefits
- burst
- cache
- com
- compilation
- complexity
- csharp
- data
- debugging
- deltatime
- design
- docs
- documentation
- dots
- e
- ecs
- entities
- for
- foreach
- foundational
- g
- gains
- gameplay
- https
- hybrid
- in
- isystem
- jobs
- latest
- layout
- locality
- localtransform
- manual
- measure
- memory
- migrate
- mike
- movesystem
- note
- on
- onupdate
- oriented
- packages
- partial
- performance
- pitfalls
- position
- predictable
- projectile
- public
- query
- read
- ref
- references
- refrw
- rx0itvevjhc
- simd
- simulation
- small
- state
- strategies
- struct
- system
- systemapi
- systemstate
- talk
- thinking
- time
- to
- transform
- unity
- unity3d
- updates
- v
- value
- valuero
- valuerw
- var
- velocity
- void
- watch
- workflows
- www
- youtube
