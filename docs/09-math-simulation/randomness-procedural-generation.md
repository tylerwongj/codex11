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
## Key Terms
- **Pseudo-Random Number Generator (PRNG)**: Deterministic algorithm producing random-like sequences from a seed.
- **Seed**: Initial value fed into a PRNG to ensure results are reproducible across runs.
- **Perlin Noise**: Gradient noise function producing smooth, natural-looking variation, ideal for terrain and textures.
- **Blue Noise Sampling**: Distribution strategy that avoids clustering, improving visual uniformity for scatter placement.
- **Poisson Disk Sampling**: Algorithm generating evenly spaced points with minimum distance, commonly used for foliage placement.
- **Procedural Generation**: Automated creation of levels, terrain, or assets using algorithms and randomness instead of manual design.
