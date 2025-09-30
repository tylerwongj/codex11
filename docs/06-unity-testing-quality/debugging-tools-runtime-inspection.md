# Debugging Tools for Runtime Inspection
- **Structured logging:** Use `Debug.Log`, `LogWarning`, and `LogError` with context objects so the console highlights offending GameObjects. Create lightweight log wrappers that gate verbose logs behind `#if UNITY_EDITOR` or a custom log level enum.
- **Visual probes:** Call `Debug.DrawLine`, `Debug.DrawRay`, or `Debug.DrawWireSphere` to visualize physics queries in the Scene view. Remember they only appear while the scene is playing or paused in the editor.
- **Gizmos:** Implement `OnDrawGizmos`/`OnDrawGizmosSelected` to render persistent cues (spawn areas, AI paths) during design time. Use color-coding and labels to distinguish states without entering Play Mode.
- **Debugger attachment:** Attach Visual Studio, Rider, or VS Code debuggers via the `Attach to Unity` command. Set breakpoints in coroutines, inspect component fields live, and evaluate expressions in the Immediate window.
- **Crash forensics:** Capture logs with the Player Log, enable stack traces for warnings, and snapshot the Profiler timeline when reproducing complex bugs. Persist artifacts alongside bug reports.
- **Hands-on checkpoint:** Create a gizmo that outlines projectile trajectories, add log wrappers that prefix messages with subsystem tags, and practice attaching a debugger to catch a failing coroutine.

## Debug Draw Example
```csharp
Debug.DrawRay(transform.position, transform.forward * 2f, Color.green, 2f);
```






## References
- [Managed code debugging](https://docs.unity3d.com/Manual/ManagedCodeDebugging.html) - attach debuggers to Unity player and editor.
- [Console window manual](https://docs.unity3d.com/Manual/Console.html) - filter and interpret log output.
- [Profiler manual](https://docs.unity3d.com/Manual/Profiler.html) - collect runtime profiling data while debugging.
- [Debugging techniques tutorial](https://learn.unity.com/tutorial/debugging-techniques) - practical debugging exercises.
- [Unity debugging workflow video](https://www.youtube.com/watch?v=qRCN2Fzu03Y) - official tips for efficient debugging.
## Key Terms
- **Structured Logging**: Consistent log format that tags messages with context objects so issues surface clearly in the Console.
- **Debug Draw API**: `Debug.DrawLine`, `DrawRay`, and `DrawWireSphere` calls that visualize physics or navigation data in the Scene view.
- **Gizmo Callback**: `OnDrawGizmos` and `OnDrawGizmosSelected` hooks used to render editor-time aids like spawn volumes or AI paths.
- **Managed Debugger**: External IDE debugger (Visual Studio, Rider, VS Code) attached through `Attach to Unity` for live inspection and breakpoints.
- **Profiler Timeline**: Recorded timeline that captures CPU, GPU, and memory samples to correlate spikes with logged issues.
- **Crash Artifact Bundle**: Collected player logs, stack traces, and profiler snapshots archived with each bug report for reproducibility.
