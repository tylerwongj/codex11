# ScriptableObject Architecture, Event Channels, and Data-Driven Design
- **Data as assets:** Organize gameplay configuration (stats, loot tables, dialogue) into `ScriptableObject` assets. Prototype a feature where designers tweak balance without code changes.
- **Event channel pattern:** Implement broadcast-only ScriptableObjects that wrap `UnityEvent` or custom delegates. Replace direct scene references with these channels to decouple publishers and listeners.
- **Runtime cloning:** Explore when to duplicate ScriptableObject data at runtime (e.g., per-player inventory) versus keeping shared immutable data.
- **Dependency injection:** Combine ScriptableObjects with `Context` prefabs or frameworks like Zenject to wire dependencies. Document trade-offs between ScriptableObject singletons and DI containers.
- **Exercises:** Refactor an existing MonoBehaviour-heavy system (e.g., quest management) into ScriptableObject-driven architecture with unit tests covering asset loading edge cases.
- **Reference material:**
  - [Unity Manual: ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html)
  - [Unity How-To: ScriptableObject Architecture](https://unity.com/how-to/scriptableobject)
  - [Ryan Hipple — Game Architecture with ScriptableObjects (Unite 2017)](https://www.youtube.com/watch?v=raQ3iHhE_Kk)
  - [Unity Zenject Documentation](https://github.com/modesttree/Zenject/wiki)

## ScriptableObject Channel
```csharp
[CreateAssetMenu(menuName = "Events/HealthChanged")]
public class HealthChangedChannel : ScriptableObject
{
    public UnityAction<int> OnRaised;

    public void Raise(int currentHealth) => OnRaised?.Invoke(currentHealth);
}
```






## References
- [ScriptableObject manual](https://docs.unity3d.com/Manual/class-ScriptableObject.html) - create reusable data assets.
- [Scriptable Objects tutorial](https://learn.unity.com/tutorial/scriptable-objects) - hands-on practice building data assets.
- [Architect with ScriptableObjects](https://unity.com/how-to/architect-with-scriptable-objects) - patterns for decoupled architecture.
- [ScriptableObject architecture sample](https://github.com/roboryantron/Unite2017) - Ryan Hipple Unite sample project.
- [Game architecture with ScriptableObjects talk](https://www.youtube.com/watch?v=raQ3iHhE_Kk) - deep dive into ScriptableObject driven systems.
## Key Terms
- **ScriptableObject**: Asset-based data container that lets designers tweak values without scene dependencies.
- **Event Channel**: ScriptableObject that broadcasts events to decoupled listeners via delegates or UnityEvents.
- **Runtime Clone**: Copy of a ScriptableObject created at runtime when per-player state must diverge from shared data.
- **Dependency Injection**: Technique for supplying references via contexts or frameworks like Zenject instead of singletons.
- **Data-Driven Design**: Architecture where gameplay behaviour reads from assets/configs rather than hard-coded values.
