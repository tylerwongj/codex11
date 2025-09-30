# Vector Math Fundamentals
- Master vector operations: addition, subtraction, scalar multiplication.
- Deep-dive dot and cross products; analyze geometric interpretations and practical use cases.
- Practice vector normalization and projection with numerical stability considerations.
- Explore quaternion algebra, conversions to/from Euler angles, and understand gimbal lock pitfalls.
- Exercises: derive view-direction vectors, implement quaternion-based rotations, and debug Euler edge cases in small scripts.
- Resources: *3D Math Primer for Graphics and Game Development* (Dunn/Parberry), Freya Holmer's vector math video series, and the *Quaternion Calculus for Animation* SIGGRAPH course notes.

## Vector Projection Example
```csharp
var projection = Vector3.Project(oncomingVelocity, laneDirection);
```






## References
- [Vector math manual](https://docs.unity3d.com/Manual/UnderstandingVectorArithmetic.html) - Unity guide to vector operations.
- [Vector math chapter](https://gamemath.com/book/vector_math.html) - comprehensive review of vector math.
- [Catlike Coding vector fields tutorial](https://catlikecoding.com/unity/tutorials/basics/vector-fields/) - visualization-heavy vector tutorial.
- [Vectors and spaces course](https://www.khanacademy.org/math/linear-algebra/vectors-and-spaces) - structured lessons on vectors.
- [Essence of linear algebra](https://www.youtube.com/watch?v=fNk_zzaMoSs) - 3Blue1Brown introduction to vectors and linear combinations.
## Key Terms
- **Vector**: Quantity with magnitude and direction used for positions, velocities, and forces.
- **Dot Product**: Scalar result measuring alignment between vectors; used for projections and angle checks.
- **Cross Product**: Vector perpendicular to two input vectors, handy for surface normals and torque calculations.
- **Normalization**: Scaling a vector to length 1, preserving direction for consistent comparisons.
- **Quaternion**: Four-dimensional representation of rotation that avoids gimbal lock and interpolates smoothly.
- **Projection**: Operation that projects one vector onto another to find movement along a lane or axis.
