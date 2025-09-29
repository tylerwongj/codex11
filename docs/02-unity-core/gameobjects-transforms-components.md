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
## Word List
- abilities
- addcomponent
- addforce
- adjustments
- and
- approach
- as
- assign
- attaching
- attachment
- audio
- avoid
- base
- based
- behavior
- behind
- best
- both
- but
- by
- cached
- colliders
- com
- compare
- component
- components
- compose
- composed
- concepts
- containers
- core
- cost
- creating
- csharp
- customized
- demonstrate
- design
- direction
- discovery
- docs
- drag
- drop
- e
- each
- either
- empty
- enemies
- entity
- every
- firepoint
- for
- forcemode
- g
- gameobject
- gameobjects
- gameplay
- getcomponent
- getcomponentinchildren
- group
- hierarchy
- html
- https
- inheritance
- inspector
- interactables
- is
- like
- local
- localposition
- manage
- manipulate
- manual
- multiple
- new
- objects
- of
- offsets
- on
- or
- parent
- performance
- position
- practice
- practices
- prefab
- prefabs
- projectile
- references
- related
- reliability
- renderers
- reset
- rigidbody
- rotation
- runtime
- scale
- script
- scripts
- serializefield
- shared
- space
- speed
- stats
- the
- them
- to
- transform
- transforms
- treat
- under
- unity
- unity3d
- unwanted
- usage
- use
- var
- variant
- variants
- velocitychange
- via
- visuals
- with
- workflow
- world
