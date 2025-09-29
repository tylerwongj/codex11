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
## Word List
- 2017
- a
- an
- and
- architecture
- as
- asset
- assets
- at
- balance
- between
- broadcast
- canonical
- cases
- changes
- channel
- channels
- class
- cloning
- code
- com
- combine
- configuration
- containers
- context
- covering
- createassetmenu
- csharp
- currenthealth
- custom
- data
- decouple
- delegates
- dependencies
- dependency
- design
- designers
- di
- dialogue
- direct
- docs
- document
- documentation
- driven
- duplicate
- e
- edge
- event
- events
- exercises
- existing
- explore
- feature
- for
- frameworks
- g
- game
- gameplay
- github
- healthchanged
- healthchangedchannel
- heavy
- hipple
- how
- html
- https
- immutable
- implement
- injection
- int
- into
- inventory
- invoke
- keeping
- kk
- like
- listeners
- loading
- loot
- management
- manual
- material
- menuname
- modesttree
- monobehaviour
- official
- offs
- on
- only
- onraised
- or
- organize
- pattern
- per
- player
- prefabs
- prototype
- public
- publishers
- quest
- raise
- raq3ihhe
- refactor
- reference
- references
- replace
- runtime
- ryan
- scene
- scriptableobject
- scriptableobjects
- shared
- singletons
- stats
- system
- tables
- talk
- tests
- that
- these
- to
- trade
- tweak
- unit
- unite
- unity
- unity3d
- unityaction
- unityevent
- v
- versus
- void
- watch
- when
- where
- wiki
- wire
- with
- without
- wrap
- www
- youtube
- zenject
