# Unity Learning Roadmap

## C# Foundations
- Variables, expressions, and type system (value vs reference)
- Control flow: conditionals, loops, pattern matching with switch expressions
- Methods, parameters (ref/out), return values, overloading
- Classes, structs, encapsulation, constructors, access modifiers
- Properties, auto-properties, indexers, object and collection initializers

## C# Intermediate
- Inheritance, interfaces, polymorphism, abstract classes
- Generics: type constraints, generic collections, variance basics
- Delegates, events, lambdas, Action/Func usage
- Error handling with exceptions, custom exceptions, try/finally patterns
- Memory management, garbage collection, IDisposable, using statements

## Data and Organisation
- Collections: arrays, List<>, Dictionary<>, Queue<>, LINQ fundamentals
- Enumerations, flags enums, bitwise operations where useful
- Basic algorithms: searching, sorting, iteration patterns in built-in APIs
- Serialization basics: JSON, ScriptableObjects, PlayerPrefs considerations

## Unity Core Concepts
- Unity project layout, scenes, prefabs, assets, build targets
- MonoBehaviour lifecycle (Awake, Start, Update, coroutines) and script execution order
- GameObjects, Transforms, components, prefab variants, script references
- Serialization rules in Unity (public fields, [SerializeField], ScriptableObjects)
- Scene management (SceneManager, additive loading, persistent managers)

## Unity Gameplay Systems
- Input systems (legacy Input vs new Input System)
- Physics: Rigidbodies, colliders, triggers, physics events, layers and masks
- Animation basics, Animator Controller, state machines, blend trees
- UI Toolkit and/or Unity UI (RectTransform, Canvas, anchoring, Events)
- Audio (AudioSource, AudioListener, audio mixer basics)

## Advanced Unity Topics
- ScriptableObject architecture, event channels, data-driven design
- Addressables, asset bundles, resource management, loading strategies
- Profiling, performance optimization, memory usage, frame budget
- Custom inspectors, editor scripting, tooling workflows
- Building for platforms, player settings, build pipeline, CI basics

## Game Programming Patterns
- Entity-component principles, composition over inheritance
- State machines, command pattern, service locators, dependency injection options
- Event buses vs C# events vs UnityEvents trade-offs
- Data-oriented design concepts, ECS exposure (Unity DOTS)
- Scene architecture: managers, singleton pitfalls, modular systems

## Math and Simulation
- Vector math, dot and cross product, normalization, quaternions, Euler pitfalls
- Coordinate systems, transformations, world and local space conversions
- Basic kinematics, interpolation (lerp, smooth damp), easing functions
- Randomness, noise generation, procedural basics
- Spatial partitioning (grids, quadtrees) for optimization

## Testing and Quality
- Unity Test Framework, play mode vs edit mode tests
- Mocking and data isolation strategies for MonoBehaviours
- Debugging tools (Debug.Draw, gizmos, log levels, debugger attachment)
- Version control workflows (Git with Unity, .gitignore, meta files)

## Tooling and Workflow
- IDE: Visual Studio or Rider setup, code analysis, Unity integration
- Package Manager usage, managing dependencies, custom packages
- Continuous integration, automated builds, crash and analytics instrumentation
- Asset pipeline basics (import settings, compression, platform overrides)

## Supplementary Topics
- Basic shader knowledge (Shader Graph vs hand-written, URP vs HDRP)
- Networking options (Netcode for GameObjects, Mirror, Photon)
- Save systems, persistence strategies, cloud save considerations
- Live ops: telemetry collection, A/B testing, content updates
- Team collaboration: scene and prefab merge strategies, task tracking, code reviews

## Study Sprint Template
```yaml
block: CSharp Foundations
duration_weeks: 2
practice: |
  - implement value vs reference sample
  - refactor a loop using pattern matching
next: Unity Core Concepts
```






## References
- [Unity Essentials pathway](https://learn.unity.com/pathway/unity-essentials) - starter path for Unity fundamentals.
- [Junior Programmer pathway](https://learn.unity.com/pathway/junior-programmer) - structured C# and gameplay scripting practice.
- [Professional Programmer pathway](https://learn.unity.com/pathway/professional-programmer) - advanced engineering topics for Unity developers.
- [C# learning path](https://learn.microsoft.com/en-us/training/paths/csharp-first-steps/) - Microsoft Learn modules for language basics.
- [Game Programming Patterns](https://gameprogrammingpatterns.com/) - free online book on game architecture.
## Key Terms
- **C# Foundations**: Introductory language topics that prepare you for Unity scripting.
- **C# Intermediate**: Advanced language constructs—generics, delegates, memory patterns—for reusable code.
- **Unity Core Concepts**: Scene, prefab, and lifecycle fundamentals that underpin every Unity project.
- **Unity Gameplay Systems**: Engine subsystems for input, physics, animation, UI, and audio.
- **Advanced Unity Topics**: Scalability practices like ScriptableObject architecture, Addressables, and tooling.
- **Game Programming Patterns**: Design approaches (state machine, ECS, service locator) for gameplay architecture.
- **Math & Simulation**: Mathematics that drives movement, physics, interpolation, and procedural systems.
- **Testing & Quality**: Workflows for Unity Test Framework, debugging, and version control.
- **Tooling & Workflow**: IDE setup, package management, CI, and asset pipeline processes.
- **Supplementary Topics**: Specialized areas such as shaders, networking, live ops, and collaboration.
