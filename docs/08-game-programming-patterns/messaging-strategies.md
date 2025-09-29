# Messaging Strategies
1. Build an event bus prototype using C# delegates and compare publish/subscribe flexibility.
2. Contrast with built-in C# events: encapsulation, subscription safety, multicast limitations.
3. Investigate UnityEvents: editor wiring, serialization, and runtime costs.
4. Summarize when to use each approach in a decision table (ownership, performance, tooling).

## Event Bus Snippet
```csharp
public static class GameEvents
{
    public static event Action<string> OnQuestAdvanced;
    public static void RaiseQuestAdvanced(string questId) => OnQuestAdvanced?.Invoke(questId);
}
```






## References
- [Observer pattern chapter](https://gameprogrammingpatterns.com/observer.html) - decouple subjects and observers.
- [Event queue chapter](https://gameprogrammingpatterns.com/event-queue.html) - asynchronous messaging between systems.
- [Observer design pattern in .NET](https://learn.microsoft.com/en-us/dotnet/standard/events/observer-design-pattern) - .NET implementation guidance.
- [Unity messaging system manual](https://docs.unity3d.com/Manual/MessagingSystem.html) - Unity built-in messaging options.
- [Events in Unity tutorial](https://www.youtube.com/watch?v=Ywdr7z4St6M) - Brackeys video on Unity events and delegates.
## Word List
- 1
- 1022461
- 2
- 3
- 4
- a
- action
- an
- and
- approach
- architecting
- build
- built
- bus
- buses
- c
- class
- com
- compare
- comparing
- contrast
- costs
- csharp
- decision
- delegates
- discussing
- each
- editor
- encapsulation
- event
- events
- flexibility
- gameevents
- games
- gdc
- gdcvault
- https
- ii
- in
- investigate
- invoke
- learn
- lesson
- limitations
- messaging
- multicast
- offs
- onquestadvanced
- ownership
- performance
- play
- prototype
- public
- publish
- questid
- raisequestadvanced
- references
- runtime
- safety
- serialization
- snippet
- static
- strategies
- string
- subscribe
- subscription
- summarize
- table
- talk
- to
- tooling
- trade
- tutorial
- unity
- unityevent
- unityevents
- use
- using
- void
- when
- wiring
- with
- www
