# Profiling, Performance Optimization, Memory Usage, and Frame Budget
- **Profiling stack:** Master the Unity Profiler, Profile Analyzer, Memory Profiler, and external tools like RenderDoc. Capture baselines in both Editor and device builds.
- **CPU/GPU budgets:** Set frame budget targets (e.g., 16.6 ms for 60 FPS). Instrument systems with `ProfilerMarker` and `CustomSampler` to track long-running blocks.
- **Allocation hygiene:** Detect managed allocations in hot paths using the Profiler's Timeline view and `UnityEngine.Profiling.Recorder`. Replace `foreach` in tight loops, pool objects, and avoid boxing.
- **Burst and Jobs:** Prototype converting a physics or AI workload to the C# Job System with Burst compilation. Compare timings and document scheduling pitfalls.
- **Platform audits:** Profile on target hardware, not just editor play mode. Capture mobile thermal data or console GPU counters, and record findings alongside this module so the team can act on the insights.
- **Exercises:** Create a performance regression budget spreadsheet. Failing example: intentionally add a per-frame allocation, detect it via automated play mode test, then fix and confirm the delta.
- **Reference material:**
  - [Unity Manual: Profiler](https://docs.unity3d.com/Manual/Profiler.html)
  - [Unity Profile Analyzer Package](https://docs.unity3d.com/Packages/com.unity.performance.profile-analyzer@latest/)
  - [Unity Memory Profiler Package](https://docs.unity3d.com/Packages/com.unity.memoryprofiler@latest/index.html)
  - [Unity Manual: C# Job System and Burst](https://docs.unity3d.com/Manual/JobSystem.html)
  - [Unity Blog: Performance Optimization Tips](https://blog.unity.com/games/performance-optimization-tips-for-unity-games)

## Profiler Marker Example
```csharp
private static readonly ProfilerMarker SimulateMarker = new("CombatSystem.Simulate");

void Simulate(float deltaTime)
{
    using (SimulateMarker.Auto())
    {
        ResolveActions(deltaTime);
    }
}
```






## References
- [Unity profiler manual](https://docs.unity3d.com/Manual/Profiler.html) - capture CPU, GPU, and memory metrics.
- [Frame debugger manual](https://docs.unity3d.com/Manual/FrameDebugger.html) - inspect draw calls and render stages.
- [Performance recommendations](https://docs.unity3d.com/Manual/MobileOptimizationPracticalGuide.html) - optimization tips across platforms.
- [Profiling and optimization tutorial](https://learn.unity.com/tutorial/profiling-and-optimization) - guided workflow for finding bottlenecks.
- [Profiling best practices talk](https://www.youtube.com/watch?v=gx0ltmyq3pI) - Unite presentation on systematic optimization.
## Key Terms
- **Unity Profiler**: Primary tool for capturing CPU, GPU, and memory metrics during play mode.
- **Frame Budget**: Time slice (e.g., 16.6 ms for 60 FPS) allotted to all systems per frame.
- **Managed Allocation**: Heap allocation from C# scripts that can trigger garbage collection if overused.
- **Burst Job**: C# Job compiled by Burst for SIMD-friendly, multithreaded execution.
- **Performance Regression**: Measured slowdown introduced by a change; should be caught by automated tests or benchmarks.
