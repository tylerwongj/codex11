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
## Key Terms
- **Scene Architecture**: Organizational strategy that defines how systems, managers, and content are arranged across scenes.
- **Bootstrapper**: Initial MonoBehaviour or script responsible for registering services and configuring dependencies at startup.
- **Service Locator**: Registry that resolves services like `IAudioService`; useful during bootstrapping but can hide dependencies.
- **Modular System**: Self-contained unit (e.g., `LevelLoader`, `UIFlowController`) with clear lifecycle responsibilities.
- **Multi-Scene Workflow**: Unity feature that splits large scenes into additive sub-scenes to isolate responsibilities and improve collaboration.
- **Lifecycle Guideline**: Documented sequence for initializing, updating, and tearing down systems consistently across scenes.
