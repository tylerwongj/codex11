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
## Word List
- 0
- 2f
- a
- acceleration
- and
- angular
- article
- articles
- by
- camera
- catlike
- catlikecoding
- characteristics
- classic
- coding
- coding's
- com
- compare
- cover
- create
- critically
- csharp
- currentvelocity
- curve
- curves
- damp
- damped
- easing
- entries
- equations
- error
- euler
- evaluate
- exercises
- fiedler
- fix
- focused
- follow
- for
- gaffer
- gafferongames
- game
- gameplay
- games
- gems
- glenn
- https
- implement
- implicit
- integration
- interpolation
- jerk
- kinematics
- kutta
- learn
- lerp
- linear
- management
- models
- movement
- numerical
- on
- parameters
- penner's
- position
- post
- programming
- prototype
- ref
- references
- referencing
- resources
- robert
- runge
- schemes
- semi
- slerp
- smooth
- smoothdamp
- smoothing
- smoothstep
- snappy
- snippet
- spring
- stable
- system
- targetvelocity
- techniques
- timestep
- tune
- tutorials
- ui
- unity
- vector3
- velocity
- velocityref
- visualizers
- with
- yet
- your
