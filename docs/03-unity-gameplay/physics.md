# Physics Building Blocks

## Key Concepts
- Rigidbodies enable dynamic motion and physics simulation; use kinematic bodies for scripted motion.
- Colliders define shape; combine primitive colliders for performance, mesh colliders for exact geometry.
- Triggers detect overlaps without physical response; subscribe to `OnTriggerEnter` and related events.
- Layers and masks let you filter collisions and raycasts, enabling selective physics interactions.
- Physics materials tweak friction and bounciness to tune gameplay feel.

## Practice Checklist
- Create destructible props using compound colliders and mass distribution.
- Author trigger zones for pickups, damage volumes, and area-based AI behaviors.
- Build raycast-based interaction (e.g., grappling hook) with layer masks to exclude UI or terrain.
- Implement custom gravity or physics forces using `AddForce` and `FixedUpdate` loops.







## References
- [Physics manual](https://docs.unity3d.com/Manual/PhysicsSection.html) - overview of Unity physics.
- [Rigidbody scripting reference](https://docs.unity3d.com/ScriptReference/Rigidbody.html) - API for forces and motion.
- [Colliders overview manual](https://docs.unity3d.com/Manual/CollidersOverview.html) - collider types and trigger setup.
- [Physics best practices](https://docs.unity3d.com/Manual/PhysicsBestPractices.html) - performance and stability tips.
- [Physics profiler tips](https://www.youtube.com/watch?v=Uy0_lvYB2Dg) - session on diagnosing physics bottlenecks.
## Key Terms
- **Rigidbody**: Component that lets Unity's physics engine move an object using forces and collisions.
- **Collider**: Shape definition used for collision detection, available as primitive or mesh types.
- **Trigger**: Collider configured to detect overlaps without responding with physical forces.
- **Layer Mask**: Bitmask that filters which layers participate in physics queries and collisions.
- **Physic Material**: Asset controlling friction and bounciness applied to colliders for gameplay feel.
