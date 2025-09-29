# Scene Architecture and Systems Design
1. Audit a Unity scene for manager singletons; identify responsibilities and coupling.
2. Refactor into modular systems (e.g., `LevelLoader`, `GameStateSystem`, `UIFlowController`).
3. Use ScriptableObjects or dependency injection to share state instead of global singletons.
4. Establish lifecycle guidelines: bootstrapping, teardown, and cross-scene communication.

## Bootstrap Pattern
```csharp
public class Bootstrapper : MonoBehaviour
{
    [SerializeField] private ServiceLocator locator;

    void Awake()
    {
        locator.Register<IAudioService>(new AudioService());
    }
}
```






## References
- [ScriptableObject manual](https://docs.unity3d.com/Manual/class-ScriptableObject.html) - share data without singletons.
- [Multi-scene editing manual](https://docs.unity3d.com/Manual/MultiSceneEditing.html) - structure large scenes across additive loads.
- [Architect with ScriptableObjects article](https://unity.com/how-to/architect-with-scriptable-objects) - official guidance on modular architecture.
- [Architecting Unity projects tutorial](https://learn.unity.com/tutorial/architecting-unity-projects) - course on building maintainable project structure.
- [Game architecture with ScriptableObjects talk](https://www.youtube.com/watch?v=raQ3iHhE_Kk) - Ryan Hipple Unite presentation.
## Word List
- 1
- 2
- 3
- 4
- 5
- a
- and
- architecting
- architecture
- audioservice
- audit
- awake
- blog
- bootstrap
- bootstrapper
- bootstrapping
- class
- code
- com
- communication
- composition
- coupling
- cross
- csharp
- dependency
- design
- docs
- e
- editing
- establish
- for
- g
- games
- gamestatesystem
- global
- guidance
- guidelines
- html
- https
- iaudioservice
- identify
- injection
- instead
- into
- levelloader
- lifecycle
- locator
- manager
- manual
- modular
- monobehaviour
- multi
- multisceneediting
- new
- of
- on
- or
- pattern
- practical
- private
- public
- refactor
- references
- register
- responsibilities
- scene
- scriptableobjects
- serializefield
- servicelocator
- share
- singletons
- state
- system
- systems
- teardown
- techniques
- tips
- to
- uiflowcontroller
- unity
- unity3d
- use
- void
- your
