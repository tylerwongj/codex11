# Randomness & Procedural Generation
- Study pseudo-random number generators, seeds, and reproducibility strategies.
- Implement white, pink, and Perlin/Simplex noise; compare spectral properties and performance.
- Explore procedural content basics: terrain heightmaps, scatter placement, and modular assembly.
- Review sampling techniques: stratified, Poisson disk, blue noise, and their impact on visual artifacts.
- Exercises: generate noise-driven textures, create procedural level layouts, and benchmark RNG variants for bias.
- Resources: *Texturing & Modeling: A Procedural Approach*, Inigo Quilez's articles, and talks by Ken Perlin.

## Noise Sampling
```csharp
float height = Mathf.PerlinNoise(x * frequency, z * frequency) * amplitude;
```






## References
- [Random class scripting reference](https://docs.unity3d.com/ScriptReference/Random.html) - Unity random number utilities.
- [Procedural generation tutorial](https://learn.unity.com/tutorial/procedural-generation) - Unity Learn guide on noise and content synthesis.
- [Noise-based terrain article](https://www.redblobgames.com/maps/terrain-from-noise/) - interactive article on noise for terrain.
- [Noise chapter](https://thebookofshaders.com/11/) - deep dive into noise functions and randomness.
- [Procedural landmass series](https://www.youtube.com/watch?v=ZQ1_IbFFbzA) - Sebastian Lague video series.
## Word List
- a
- algorithms
- amplitude
- and
- approach
- articles
- artifacts
- assembly
- basics
- benchmark
- bias
- blue
- by
- catalog
- com
- compare
- comprehensive
- content
- create
- csharp
- demystified
- disk
- driven
- exercises
- explore
- float
- for
- frequency
- functions
- generate
- generation
- generators
- guide
- height
- heightmaps
- https
- impact
- implement
- index
- inigo
- iquilezles
- ken
- layouts
- level
- lez
- mathf
- modeling
- modular
- noise
- number
- of
- on
- org
- overview
- pcg
- performance
- perlin
- perlinnoise
- php
- pink
- placement
- poisson
- procedural
- properties
- pseudo
- qu
- quilez's
- random
- randomness
- references
- reproducibility
- resources
- review
- rng
- roguebasin
- sampling
- scatter
- seeds
- simplex
- spectral
- strategies
- stratified
- study
- talks
- techniques
- terrain
- textures
- texturing
- their
- variants
- visual
- white
- www
- x
- z
