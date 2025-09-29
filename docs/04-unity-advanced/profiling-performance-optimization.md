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
## Word List
- 16
- 6
- 60
- a
- act
- add
- ai
- allocation
- allocations
- alongside
- analyzer
- and
- audits
- auto
- automated
- avoid
- baselines
- blocks
- blog
- both
- boxing
- budget
- budgets
- builds
- burst
- c
- can
- capture
- com
- combatsystem
- compare
- compilation
- confirm
- console
- converting
- counters
- course
- cpu
- create
- csharp
- customsampler
- data
- delta
- deltatime
- detect
- device
- docs
- document
- e
- editor
- example
- exercises
- external
- failing
- findings
- fix
- float
- focused
- for
- foreach
- fps
- frame
- g
- games
- gpu
- guide
- hardware
- hot
- html
- https
- hygiene
- in
- index
- insights
- instrument
- intentionally
- it
- job
- jobs
- jobsystem
- just
- latest
- learn
- like
- long
- loops
- managed
- manual
- marker
- master
- material
- memory
- memoryprofiler
- mobile
- mode
- module
- ms
- new
- not
- objects
- on
- optimization
- or
- package
- packages
- paths
- per
- performance
- physics
- pitfalls
- platform
- play
- pool
- private
- profile
- profiler
- profiler's
- profilermarker
- profiling
- prototype
- readonly
- record
- recorder
- reference
- references
- regression
- renderdoc
- replace
- resolveactions
- running
- scheduling
- set
- simulate
- simulatemarker
- so
- spreadsheet
- stack
- static
- system
- systems
- target
- targets
- team
- test
- the
- then
- thermal
- this
- tight
- timeline
- timings
- tips
- to
- tooling
- tools
- track
- training
- tuning
- unity
- unity3d
- unityengine
- usage
- using
- via
- view
- void
- with
- workload
