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
## Word List
- 1
- 100
- 2
- 3
- 3f
- 4
- 7
- a
- addcomponent
- aimover
- and
- approach
- architecture
- assembly
- at
- avoid
- based
- behaviour
- benefits
- case
- chapter
- character
- com
- compare
- component
- components
- composition
- csharp
- data
- design
- docs
- droploot
- enemy
- entity
- focused
- from
- game
- gameobject
- gameplay
- gdc
- healthcomponent
- html
- https
- inheritance
- initialize
- loottable
- manual
- modularity
- monobehaviour
- new
- nystrom's
- on
- only
- overwatch
- patterns
- principles
- programming
- prototype
- pure
- read
- references
- reflect
- register
- reuse
- robert
- runtime
- scale
- setspeed
- simple
- study
- testability
- to
- trees
- unity
- unity's
- unity3d
- using
- v
- var
- w3aiehjynvw
- watch
- with
- www
- youtube
