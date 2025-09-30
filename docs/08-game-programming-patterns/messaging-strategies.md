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
## Key Terms
- **Event Bus**: Central dispatcher that broadcasts notifications to subscribers via delegates or interfaces.
- **C# Event**: Language construct wrapping a delegate to enforce encapsulation and safe subscription/unsubscription.
- **UnityEvent**: Serializable Unity event type that allows designer-driven wiring in the inspector.
- **Publish/Subscribe**: Messaging pattern where publishers emit messages without knowing which subscribers consume them.
- **Multicast Delegate**: Delegate that maintains an invocation list, enabling multiple listeners per event.
- **Decision Matrix**: Table comparing messaging options across criteria like performance, tooling, and ownership.
