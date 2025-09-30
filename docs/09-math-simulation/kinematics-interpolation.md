# Kinematics & Interpolation
- Cover linear and angular kinematics: position, velocity, acceleration, and jerk.
- Implement numerical integration schemes (Euler, semi-implicit, Runge-Kutta) and compare error characteristics.
- Learn interpolation techniques: lerp, slerp, smoothstep, smooth damp, and critically damped spring models.
- Evaluate easing curves for UI/gameplay, referencing Robert Penner's easing equations.
- Exercises: prototype a camera follow system with smooth damp, create easing curve visualizers, and tune spring parameters for snappy yet stable movement.
- Resources: Gaffer on Games articles by Glenn Fiedler, *Game Programming Gems* kinematics entries, and Catlike Coding's smoothing tutorials.

## SmoothDamp Snippet
```csharp
currentVelocity = Vector3.SmoothDamp(currentVelocity, targetVelocity, ref velocityRef, 0.2f);
```






## References
- [Interpolation manual](https://docs.unity3d.com/Manual/Interpolation.html) - official guidance on smoothing motion.
- [Fix your timestep article](https://gafferongames.com/post/fix_your_timestep/) - stable integration and interpolation strategies.
- [Interpolation chapter](https://gamemath.com/book/interpolation.html) - mathematical background for lerp and easing.
- [Catlike Coding movement tutorial](https://catlikecoding.com/unity/tutorials/basics/movement/) - practical interpolation patterns in Unity.
- [Smooth movement video](https://www.youtube.com/watch?v=_1nzEFMjkI4) - Sebastian Lague demonstration.
## Key Terms
- **Kinematics**: Study of motion variables (position, velocity, acceleration, jerk) independent of forces.
- **Euler Integration**: Simple numerical method that updates velocity and position using current derivatives; prone to accumulated error.
- **Runge-Kutta (RK4)**: Higher-order integration scheme that samples multiple times per step for better accuracy.
- **Lerp / Slerp**: Linear and spherical interpolation functions used to blend between positions or rotations.
- **Smooth Damp**: Critically damped spring interpolation provided by Unity (`Vector3.SmoothDamp`) that eases toward targets without overshoot.
- **Easing Curve**: Mathematical function shaping interpolation speed over time, often used in UI animations.
