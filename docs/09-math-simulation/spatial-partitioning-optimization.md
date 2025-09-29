# Spatial Partitioning & Optimization
- Understand uniform grids, quadtrees, octrees, BSP trees, and bounding volume hierarchies.
- Evaluate trade-offs: memory usage, update cost, and query performance for static vs dynamic scenes.
- Implement broad-phase collision detection using spatial hashing or sweep-and-prune.
- Profile cache coherence, data-oriented layouts, and SIMD opportunities in spatial queries.
- Exercises: build a quadtree for 2D collision, compare grid vs tree partitioning under moving entities, and visualize partition structures during runtime.
- Resources: *Real-Time Collision Detection* (Christer Ericson), GDC talks on data-oriented design, and Wicked Engine dev blog deep dives.

## Quadtree Insert
```csharp
public void Insert(Vector2 position, Enemy enemy)
{
    if (!bounds.Contains(position)) return;
    // Subdivision omitted for brevity
}
```






## References
- [Spatial hashing article](https://www.redblobgames.com/articles/spatial-hash/) - visual explanation of spatial hashing.
- [Spatial partitioning solutions](https://www.gamedeveloper.com/programming/spatial-partitioning---a-simple-solution) - article covering grids, quadtrees, and BVHs.
- [Uniform grid spatial partitioning](https://developer.nvidia.com/gpugems/gpugems/part-iv-image-oriented-computing/chapter-32-using-uniform-grid-spatial-partitioning-accelerate-ray-tracing) - GPU Gems chapter on uniform grids.
- [Optimizing physics performance tutorial](https://learn.unity.com/tutorial/optimizing-physics-performance) - Unity Learn guidance on colliders and partitioning.
- [Quadtrees coding adventure](https://www.youtube.com/watch?v=OJ4a0D27c0g) - Sebastian Lague visual explanation of quadtrees.
## Word List
- 2d
- a
- acceleration
- and
- authoritative
- blog
- bounding
- bounds
- brevity
- broad
- bsp
- build
- cache
- christer
- coherence
- collision
- com
- compare
- contains
- cost
- csharp
- data
- deep
- design
- detection
- dev
- dives
- docs
- during
- dynamic
- enemy
- engine
- entities
- ericson
- evaluate
- exercises
- for
- gdc
- grid
- grids
- guidance
- hashing
- hierarchies
- html
- https
- if
- implement
- in
- insert
- layouts
- manual
- memory
- moving
- net
- octrees
- offs
- omitted
- on
- opportunities
- optimization
- optimizing
- optimizingphysics
- or
- oriented
- partition
- partitioning
- performance
- phase
- physics
- position
- profile
- prune
- public
- quadtree
- quadtrees
- queries
- query
- real
- realtimecollisiondetection
- references
- resource
- resources
- return
- runtime
- scenes
- simd
- spatial
- static
- structures
- subdivision
- sweep
- talks
- time
- trade
- tree
- trees
- under
- understand
- uniform
- unity
- unity3d
- update
- usage
- using
- vector2
- visualize
- void
- volume
- vs
- wicked
