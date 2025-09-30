# Serialization Rules in Unity
- **Serialized fields:** Public fields and private fields marked with `[SerializeField]` persist in scenes and prefabs. Avoid serializing types Unity cannot handle (e.g., raw dictionaries without helper classes).
- **Supported types:** Review which built-in types serialize by default (primitive types, `Vector3`, `Color`, `AnimationCurve`). For custom classes, annotate with `[System.Serializable]`.
- **ScriptableObjects:** Create data assets for configuration (e.g., weapon stats). Learn how to create instances from the Assets menu and reference them from MonoBehaviours.
- **Serialization pitfalls:** Understand that references break when scripts move namespaces, that serialized data updates only when values change in the inspector, and that polymorphic fields require `[SerializeReference]` and custom drawers.
- **Version control considerations:** Track `.meta` files to preserve GUIDs. Use `Force Text` serialization in editor settings for diff-friendly YAML assets.
- **Practice exercise:** Build a `ScriptableObject` for game difficulty settings, expose it in a manager MonoBehaviour, and observe how changes propagate across scenes.

## Serialized Field Example
```csharp
[SerializeField] private List<ItemConfig> startingItems = new();
public ItemConfig ActiveItem => startingItems.FirstOrDefault();
```






## References
- [Script serialization manual](https://docs.unity3d.com/Manual/script-Serialization.html) - rules for serializing fields.
- [Custom serialization manual](https://docs.unity3d.com/Manual/script-Serialization-Custom.html) - extend serialization with custom logic.
- [Serialization in Unity blog](https://blog.unity.com/engine-platform/serialization-in-unity) - deep dive into Unity serialization internals.
- [Serialization tutorial](https://learn.unity.com/tutorial/scriptable-objects-and-serialization) - practice using ScriptableObjects and serialized data.
- [Serialization pitfalls talk](https://www.youtube.com/watch?v=8-ZH0BzozsE) - Unite presentation on serialization gotchas.
## Key Terms
- **Serialized Field**: Public or `[SerializeField]` member Unity saves into scenes, prefabs, and ScriptableObjects.
- **System.Serializable**: Attribute applied to plain classes/structs so Unity can persist their fields.
- **ScriptableObject**: Asset-based data container used to author reusable configuration outside scenes.
- **SerializeReference**: Attribute allowing polymorphic fields by storing managed reference metadata.
- **Meta File**: `.meta` companion Unity uses to store GUIDs; required for stable references in version control.
