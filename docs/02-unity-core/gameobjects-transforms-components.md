# GameObjects, Transforms, Components, Prefab Variants, and Script References
- **GameObjects:** Treat them as containers; every gameplay entity is composed of multiple components.
- **Transforms:** Manipulate position, rotation, and scale. Practice both local (`transform.localPosition`) and world (`transform.position`) space adjustments.
- **Component-based design:** Compose behavior by attaching scripts, renderers, colliders, and audio components. Use `GetComponent`, `GetComponentInChildren`, and cached references to manage performance.
- **Prefab variants:** Demonstrate inheritance-like behavior by creating variants for enemies with shared base stats but customized visuals or abilities.
- **Script references:** Assign references either via inspector drag-and-drop, `SerializeField`, or runtime discovery. Compare the cost and reliability of each approach.
- **Hierarchy best practices:** Group related objects under empty GameObjects (e.g., `Enemies`, `Interactables`). Reset transforms on parent containers to avoid unwanted offsets.

## Component Attachment
```csharp
var projectile = new GameObject("Projectile");
projectile.transform.position = firePoint.position;
projectile.AddComponent<Rigidbody>().AddForce(direction * speed, ForceMode.VelocityChange);
```






## References
- [Unity manual: GameObjects](https://docs.unity3d.com/Manual/GameObjects.html) - core concepts for building scene hierarchies.
- [Transform component reference](https://docs.unity3d.com/Manual/class-Transform.html) - position, rotation, and scale management.
- [Prefab workflow manual](https://docs.unity3d.com/Manual/Prefabs.html) - create and manage reusable hierarchies.
- [GameObjects and components tutorial](https://learn.unity.com/tutorial/gameobjects-and-components) - hands-on introduction to component composition.
- [Understanding transforms lesson](https://learn.unity.com/tutorial/understanding-transforms) - visual explanation of local versus world space.
## Key Terms
- **GameObject**: Unity scene node that acts as a container for components.
- **Transform**: Built-in component storing position, rotation, and scale in local and world space.
- **Component**: Script or built-in behaviour attached to a GameObject to add functionality.
- **Prefab Variant**: Prefab derived from a base prefab that overrides specific values while inheriting structure.
- **Serialized Reference**: Field exposed through the inspector (`[SerializeField]`) so references persist across play sessions.
