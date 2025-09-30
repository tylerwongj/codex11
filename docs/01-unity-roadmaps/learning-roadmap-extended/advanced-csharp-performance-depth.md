# Advanced C# and Performance Depth

## Timeline
- Week 1: Review async/await patterns, convert an existing loading flow, and measure impact.
- Week 2: Prototype a Job System/Burst-enabled task, compare against baseline execution times.
- Week 3: Conduct profiling deep dive across representative scenes, documenting hotspots.
- Quarterly: Re-run benchmarks and regression tests to ensure optimizations hold.

## Suggested Resources
- Unity DOTS samples and official ECS documentation for job-oriented architectures.
- Catlike Coding tutorials on coroutines, async, and performance optimization.
- Microsoft async best practices (ConfigureAwait, exception handling) adapted for Unity contexts.
- Unity Profiler, Memory Profiler, and Frame Debugger documentation and related talks.

## Deliverables
- Async guidelines doc covering do/don'ts, exception strategy, and synchronization contexts.
- Job System template scripts and utility wrappers ready for reuse.
- Benchmark report with charts, methodology notes, and acceptance thresholds.
- Profiling playbook that lists target metrics, tool workflow, and remediation strategies.

## Tracking & Reflection
- Store benchmark projects and data files under `tests/performance/` with version tags.
- Automate performance regression checks in CI where feasible (e.g., playmode tests with profiling hooks).
- Keep a changelog of optimization experiments, results, and follow-up tasks.
- Schedule cross-discipline share-outs to propagate lessons to the broader team.

## Burst Job Snippet
```csharp
[BurstCompile]
public struct SpinJob : IJobParallelFor
{
    public NativeArray<float> Speeds;

    public void Execute(int index)
    {
        Speeds[index] = math.sin(Speeds[index]);
    }
}
```






## References
- [Unity DOTS documentation](https://docs.unity3d.com/Packages/com.unity.entities@latest) - entities, jobs, and burst reference.
- [Unity DOTS samples](https://github.com/Unity-Technologies/EntityComponentSystemSamples) - example projects using the ECS stack.
- [Understanding async in Unity](https://blog.unity.com/engine-platform/understanding-async-await-in-unity) - guidance for async workflows inside Unity.
- [Unity profiler manual](https://docs.unity3d.com/Manual/Profiler.html) - capture and analyse performance data.
- [Performance optimization talk](https://www.youtube.com/watch?v=gx0ltmyq3pI) - Unite session on profiling best practices.
## Key Terms
- **Async Guideline**: Documented rules for using async/await safely inside Unity projects.
- **Job System**: Unity's multithreaded framework for scheduling work on worker threads.
- **Burst Compiler**: LLVM-based compiler that optimizes jobs for SIMD and cache efficiency.
- **Benchmark Report**: Structured measurement results comparing optimization experiments against baselines.
- **Profiling Playbook**: Checklist describing which tools to run, target metrics, and remediation steps.
- **Performance Regression Test**: Automated check ensuring future changes do not degrade measured metrics.
