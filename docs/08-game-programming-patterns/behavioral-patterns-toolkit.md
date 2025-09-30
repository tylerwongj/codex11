# Behavioral Patterns Toolkit
1. Implement a finite state machine (FSM) for enemy AI. Track states, transitions, and entry/exit hooks.
2. Explore the Command pattern for player input buffering; log commands for undo/redo.
3. Evaluate service locator vs dependency injection: implement both for an `AudioService` and record pros/cons.
4. Document trade-offs: testing difficulty, coupling, and configuration complexity.

## State Machine Skeleton
```csharp
public abstract class EnemyState
{
    public abstract EnemyState Tick(EnemyContext ctx);
}
```






## References
- [State pattern chapter](https://gameprogrammingpatterns.com/state.html) - finite state machine pattern for games.
- [Command pattern chapter](https://gameprogrammingpatterns.com/command.html) - command queues and undo systems.
- [Service locator chapter](https://gameprogrammingpatterns.com/service-locator.html) - trade-offs of locator versus dependency injection.
- [Behavioral patterns catalog](https://refactoring.guru/design-patterns/behavioral-patterns) - reference list of behavioral patterns.
- [Finite state machines tutorial](https://www.youtube.com/watch?v=-E4YBS4zOgg) - video building FSM-driven AI.
## Key Terms
- **Finite State Machine (FSM)**: Behaviour model where AI or gameplay logic transitions between discrete states with entry/exit hooks.
- **Command Pattern**: Encapsulates player inputs or actions as objects so they can be queued, replayed, or undone.
- **Service Locator**: Global registry that resolves services like `AudioService` at runtime, trading convenience for hidden dependencies.
- **Dependency Injection (DI)**: Technique that supplies dependencies explicitly (constructor parameters, factories) to improve testability.
- **Transition Table**: Mapping of FSM states and triggers that clarifies how behaviour flows and simplifies debugging.
- **Undo Stack**: History of executed commands that enables redo/undo functionality in tools or gameplay systems.
