# MonoBehaviour Lifecycle and Script Execution Order
- **Lifecycle phases:** Memorize the default order: `Awake` → `OnEnable` → `Start` → `FixedUpdate` → `Update` → `LateUpdate` → `OnDisable` → `OnDestroy`.
- **Awake vs. Start:** Use `Awake` for internal setup and dependency lookup; `Start` for work that depends on other components being initialized.
- **Frame updates:** Differentiate between `Update` (per rendered frame) and `FixedUpdate` (physics step). Prototype a movement script that splits physics input from animation updates.
- **Coroutines:** Implement a coroutine using `StartCoroutine` and `yield return` to perform timed logic like fade-ins. Explore when coroutines pause (e.g., during `Time.timeScale = 0`).
- **Execution order controls:** Use `Edit > Project Settings > Script Execution Order` to adjust initialization for special cases. Document why manual ordering can mask design issues.
- **Diagnostics:** Add `Debug.Log` statements to lifecycle methods in a sample script to watch the execution sequence while playing the scene.

## Lifecycle Trace
```csharp
void Awake() => Debug.Log("Awake");
void Start() => Debug.Log("Start");
void Update() => Debug.Log("Update " + Time.frameCount);
```






## References
- [Execution order of event functions](https://docs.unity3d.com/Manual/ExecutionOrder.html) - detailed order of MonoBehaviour callbacks.
- [MonoBehaviour scripting reference](https://docs.unity3d.com/ScriptReference/MonoBehaviour.html) - API documentation for lifecycle methods.
- [Lifecycle of a MonoBehaviour tutorial](https://learn.unity.com/tutorial/lifecycle-of-a-mono-behaviour) - interactive tutorial on callback timing.
- [Understanding script execution order](https://blog.unity.com/engine-platform/understanding-script-execution-order) - best practices for managing dependencies.
- [Execution order explained video](https://www.youtube.com/watch?v=Mut_u40Sqz4) - official walkthrough of Update, FixedUpdate, and LateUpdate.
## Key Terms
- **Awake**: Lifecycle callback fired when the MonoBehaviour instance loads, ideal for internal setup.
- **Start**: Callback invoked on the first frame after all Awake calls, used for work that depends on other components.
- **Update vs FixedUpdate**: Update runs every rendered frame while FixedUpdate runs at the physics timestep for deterministic movement.
- **Coroutine**: Method returning IEnumerator that yields over frames, enabling timed or asynchronous flows.
- **Script Execution Order**: Project setting that controls callback priority when dependencies demand deterministic startup.
