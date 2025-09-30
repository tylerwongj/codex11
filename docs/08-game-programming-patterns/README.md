# Game Programming Patterns Study Guide

Use these focused modules to explore architectural patterns for gameplay systems. Review the prerequisites, then work through each topic with weekly sprints or study sessions.

- [Entity-Component Principles](entity-component-principles.md)
- [Behavioral Patterns Toolkit](behavioral-patterns-toolkit.md)
- [Messaging Strategies](messaging-strategies.md)
- [Data-Oriented Design and ECS](data-oriented-design-ecs.md)
- [Scene Architecture and Systems Design](scene-architecture-systems-design.md)

Document experiments and reflections as you progress so the insights feed back into your project architecture.

## Practice Checklist
- [ ] Components remain data-driven; behavior is composed through discrete scripts or systems.
- [ ] State machines are testable via unit tests and do not hardcode Unity callbacks.
- [ ] Messaging solution matches team needs (editor tooling, performance, debuggability).
- [ ] ECS systems operate on contiguous data and schedule jobs without race conditions.
- [ ] Scene flow avoids monolithic managers; responsibilities are documented per system.

## Further Reading and Resources
- Robert Nystrom, *Game Programming Patterns* (free online edition).
- Unity Manual: ScriptableObject-based architecture patterns.
- Ryan Hipple, "Game Architecture with ScriptableObjects" (GDC 2017).
- Unity DOTS Samples repository for practical ECS implementations.
- Sander van Rossen, "Data-Oriented Design" talk for fundamentals on cache-friendly layouts.

## Reflection Prompts
- Where does composition break down, and how can data-driven authoring restore flexibility?
- What criteria determine whether you centralize a system or decouple via events/messages?
- How does DOTS change your approach to debugging compared to MonoBehaviour-centric workflows?
- Which architectural decisions need documenting for future contributors, and where should they live?

## Pattern Index
```bash
ls docs/08-game-programming-patterns
```






## References
- [Game Programming Patterns book](https://gameprogrammingpatterns.com/) - free online reference for classic patterns.
- [Design patterns in Unity](https://learn.unity.com/tutorial/design-patterns-in-unity) - Unity Learn course applying GoF patterns.
- [Unity architecture talks](https://www.youtube.com/playlist?list=PLX2vGYjWbI0Rv_0E8xmPKzW0fvkYl9t7P) - collection of Unity architecture sessions.
- [Refactoring.Guru patterns catalog](https://refactoring.guru/design-patterns) - visual explanations of common patterns.
- [Data oriented design book](https://www.dataorienteddesign.com/dodmain/dodmain.html) - Mike Acton on data oriented mindset.
## Key Terms
- **Entity-Component System (ECS)**: Architecture that separates data (components) from behaviour (systems) to improve cache usage and flexibility.
- **Messaging Pattern**: Decoupled communication style (events, signals) that keeps gameplay systems independent yet coordinated.
- **ScriptableObject Architecture**: Unity-specific approach where configuration assets define behaviours and allow designers to tweak without code changes.
- **Data-Oriented Design (DOD)**: Mindset that organizes data layouts for CPU cache efficiency, often paired with Unity DOTS.
- **State Machine**: Control pattern where discrete states and transitions drive gameplay logic and remain unit testable.
- **Scene Composition**: Strategy of breaking scenes into additive layers or feature-specific systems instead of monolithic managers.
