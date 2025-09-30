# Unity Testing & Quality Learning Guide

Use these modules to build sustainable testing and QA practices for Unity projects.

- [Unity Test Framework: Edit Mode and Play Mode Suites](unity-test-framework.md)
- [Mocking and Data Isolation for MonoBehaviours](mocking-and-data-isolation.md)
- [Debugging Tools for Runtime Inspection](debugging-tools-runtime-inspection.md)
- [Version Control Workflows for Unity Projects](version-control-workflows.md)

Pair study with hands-on experiments so testing habits stick.

## Quality Topics
```bash
ls docs/06-unity-testing-quality
```






## References
- [Unity Test Framework manual](https://docs.unity3d.com/Packages/com.unity.test-framework@latest/manual/index.html) - official testing documentation.
- [Unity Learn: Introduction to testing](https://learn.unity.com/tutorial/introduction-to-the-unity-test-framework) - guided overview of creating tests.
- [Unity debugging techniques tutorial](https://learn.unity.com/tutorial/debugging-techniques) - course on diagnosing runtime issues.
- [Unity profiler manual](https://docs.unity3d.com/Manual/Profiler.html) - profiling tools for quality assurance.
- [Testing in Unity talk](https://www.youtube.com/watch?v=8M4b9LQ1csE) - session showing automated testing workflows.
## Key Terms
- **Unity Test Framework (UTF)**: Built-in package that lets you author Edit Mode and Play Mode automation inside Unity.
- **Edit Mode Tests**: Fast, editor-hosted tests that exercise plain C# logic without spinning up the Unity runtime loop.
- **Play Mode Tests**: Engine-driven tests that load scenes and behaviours to validate gameplay flows end to end.
- **Mock Component**: Lightweight substitute for a MonoBehaviour that mimics expected behaviour so you can isolate dependencies under test.
- **Runtime Inspection**: Using tools such as the Profiler, Frame Debugger, or custom gizmos to observe live game state while diagnosing issues.
- **Version Control Workflow**: Branching, locking, and merge practices tailored to large binary assets and scene files in Unity projects.
