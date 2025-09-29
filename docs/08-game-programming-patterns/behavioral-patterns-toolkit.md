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
## Word List
- 1
- 2
- 3
- 4
- a
- abstract
- ai
- an
- and
- audioservice
- background
- behavioral
- both
- buffering
- class
- com
- command
- commands
- complexity
- configuration
- cons
- coupling
- csharp
- ctx
- dependency
- depth
- designing
- difficulty
- docs
- document
- enemy
- enemycontext
- enemystate
- entry
- evaluate
- exit
- explore
- finite
- for
- fsm
- fsms
- game
- gameprogrammingpatterns
- hooks
- html
- https
- implement
- in
- injection
- input
- locator
- log
- machine
- manual
- of
- offs
- pattern
- patterns
- player
- programming
- pros
- public
- record
- redo
- references
- service
- skeleton
- state
- statemachinetheory
- states
- testing
- the
- theory
- tick
- toolkit
- track
- trade
- transitions
- treatment
- undo
- unity3d
- vs
