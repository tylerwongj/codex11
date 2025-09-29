# Coordinate Systems & Transformations
- Review right-handed vs left-handed systems and the impact on cross products and rendering.
- Study homogeneous coordinates, transformation matrices, and chain composition.
- Implement world↔local space conversions, including parent-child hierarchy transforms.
- Analyze common pitfalls: precision drift, incorrect order of operations, and scale shearing.
- Exercises: build a simple transform stack, convert between engine coordinate conventions, and author gizmos that visualize basis vectors.
- Resources: *Game Engine Architecture* (Gregory) chapter on math, Unity and Unreal docs on transforms, and Jamis Buck's matrix visualization posts.

## Transform Direction
```csharp
Vector3 worldForward = playerTransform.TransformDirection(Vector3.forward);
```






## References
- [Transform component manual](https://docs.unity3d.com/Manual/class-Transform.html) - Unity coordinate systems and transforms.
- [Coordinate systems article](https://learnopengl.com/Getting-started/Coordinate-Systems) - model, view, and projection spaces explained.
- [Catlike Coding transforms tutorial](https://catlikecoding.com/unity/tutorials/basics/transforms/) - visual walkthrough of local versus global transforms.
- [Matrix transforms chapter](https://gamemath.com/book/matrix_transform.html) - derive transform matrices for games.
- [Linear transformations video](https://www.youtube.com/watch?v=kYB8IZa5AuE) - 3Blue1Brown visualizing matrix transforms.
## Word List
- a
- analyze
- and
- architecture
- author
- basis
- between
- buck's
- build
- chain
- chapter
- child
- com
- common
- composition
- conventions
- conversions
- convert
- coordinate
- coordinates
- cross
- csharp
- deep
- direction
- dive
- docs
- drift
- engine
- exercises
- forward
- game
- gameenginebook
- gizmos
- gregory
- handed
- handles
- hierarchy
- homogeneous
- how
- html
- https
- impact
- implement
- including
- incorrect
- into
- jamis
- left
- local
- manual
- math
- matrices
- matrix
- of
- on
- operations
- order
- parent
- pitfalls
- playertransform
- posts
- precision
- products
- references
- rendering
- resources
- review
- right
- scale
- shearing
- simple
- space
- spaces
- stack
- study
- systems
- that
- the
- transform
- transformation
- transformations
- transformdirection
- transforms
- unity
- unity3d
- unreal
- vector3
- vectors
- visualization
- visualize
- vs
- world
- worldforward
- www
