# Unity Core Concepts Learning Guide

This guide covers the fundamentals you should master before building production-grade projects in Unity.
Each module below links to a focused topic so you can tackle one concept at a time.

- [Unity Project Layout, Scenes, Prefabs, and Build Targets](project-layout-scenes-prefabs-build-targets.md)
- [MonoBehaviour Lifecycle and Script Execution Order](monobehaviour-lifecycle-execution-order.md)
- [GameObjects, Transforms, Components, Prefab Variants, and Script References](gameobjects-transforms-components.md)
- [Serialization Rules in Unity](unity-serialization-rules.md)
- [Scene Management (SceneManager, Additive Loading, Persistent Managers)](scene-management.md)

Work through the modules in order, pairing each with a small in-editor experiment to solidify the ideas.

## Core Topics
```bash
ls docs/02-unity-core
```






## References
- [Unity manual](https://docs.unity3d.com/Manual/index.html) - official documentation for engine systems.
- [Unity Essentials pathway](https://learn.unity.com/pathway/unity-essentials) - foundation course for engine basics.
- [Unity scripting manual](https://docs.unity3d.com/Manual/ScriptingSection.html) - scripting concepts and API references.
- [Unity asset workflow manual](https://docs.unity3d.com/Manual/AssetWorkflow.html) - import pipeline and best practices.
- [Unity platform development manual](https://docs.unity3d.com/Manual/PlatformSpecific.html) - platform-specific considerations.
## Key Terms
- **Project Layout**: Structure of Assets, Packages, and ProjectSettings folders that determine how Unity discovers content.
- **MonoBehaviour Lifecycle**: Order of Unity callbacks such as Awake, Start, Update, and OnDestroy that govern script execution.
- **GameObject Composition**: Concept of building behaviours by stacking components on GameObjects instead of relying on inheritance.
- **Unity Serialization**: Rules that decide which fields persist in scenes, prefabs, and ScriptableObjects.
- **Scene Management**: APIs and workflows for loading, unloading, and coordinating multiple Unity scenes.
