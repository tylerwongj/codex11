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
## Word List
- 0
- a
- add
- adjust
- and
- animation
- awake
- being
- between
- callback
- can
- cases
- com
- components
- controls
- coroutine
- coroutines
- csharp
- debug
- default
- dependency
- depends
- design
- details
- diagnostics
- differentiate
- docs
- document
- during
- e
- edit
- execution
- executionorder
- explore
- fade
- fixedupdate
- for
- frame
- framecount
- from
- g
- html
- https
- implement
- in
- initialization
- initialized
- input
- ins
- internal
- issues
- lateupdate
- lifecycle
- like
- limitations
- log
- logic
- lookup
- manual
- mask
- memorize
- methods
- monobehaviour
- movement
- on
- ondestroy
- ondisable
- onenable
- order
- ordering
- other
- pause
- per
- perform
- phases
- physics
- playing
- project
- prototype
- reference
- references
- rendered
- return
- sample
- scene
- scheduling
- script
- sequence
- settings
- setup
- special
- splits
- start
- startcoroutine
- statements
- step
- that
- the
- time
- timed
- timescale
- to
- trace
- unity
- unity3d
- update
- updates
- use
- using
- visual
- void
- vs
- watch
- when
- while
- why
- work
- yield
