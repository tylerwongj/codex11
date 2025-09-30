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
## Key Terms
- **Coordinate System**: Defined origin and axes (right-handed or left-handed) used to interpret positions and rotations.
- **Homogeneous Coordinates**: Four-component vector representation that enables translation via matrix multiplication.
- **Transformation Matrix**: 4x4 matrix combining translation, rotation, and scale; chained to move between spaces.
- **Local Space**: Coordinate frame relative to a parent object; conversions to world space use hierarchy matrices.
- **Basis Vector**: Vector representing an axis of a coordinate frame; visualizing basis vectors clarifies orientation.
- **Precision Drift**: Accumulated floating-point error when repeatedly applying transforms, often mitigated via re-normalization.
