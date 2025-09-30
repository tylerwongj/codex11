# Unity Test Framework: Edit Mode and Play Mode Suites
- **Edit mode tests:** Execute in the lightweight NUnit runner without booting the player loop. Use them to validate pure C# logic, ScriptableObject configuration, or classes that rely on editor-only APIs. Keep fixtures fast (<100 ms) and deterministic.
- **Play mode tests:** Run inside a stripped-down player that simulates runtime execution. Target behaviours that depend on scene objects, physics steps, or coroutines. Use `UnityTest` attributes to yield across frames and run asynchronous checks.
- **Assembly definitions:** Create `Tests/EditMode` and `Tests/PlayMode` asmdefs referencing the runtime assemblies they exercise. Enable `Test Assemblies` in inspector so the Test Runner discovers the suites automatically.
- **Running suites:** Use the Unity Test Runner window for local workflows and the `-runTests` CLI flag plus an `-testResults` path for CI. Fail builds on any test failure and persist XML output for dashboards.
- **Hands-on checkpoint:** Configure a sample project where pressing `Play` loads a bootstrap scene. Author one edit mode test verifying spawn data from a ScriptableObject and one play mode test that checks a coroutine-driven state machine.

## Edit Mode Test
```csharp
[Test]
public void PlayerStartsWithFullHealth()
{
    var player = new GameObject().AddComponent<PlayerHealth>();
    Assert.AreEqual(100, player.Current);
}
```






## References
- [Unity Test Framework manual](https://docs.unity3d.com/Packages/com.unity.test-framework@latest/manual/index.html) - official documentation.
- [Test Runner workflows](https://docs.unity3d.com/Packages/com.unity.test-framework@latest/manual/workflow-run-test.html) - structure edit and play mode suites.
- [Assertions reference](https://docs.unity3d.com/Packages/com.unity.test-framework@latest/manual/reference-assertions.html) - list of built-in assertions.
- [Introduction to the Unity Test Framework](https://learn.unity.com/tutorial/introduction-to-the-unity-test-framework) - guided overview of writing tests.
- [Testing in Unity session](https://www.youtube.com/watch?v=8M4b9LQ1csE) - live demo of testing workflows.
## Key Terms
- **Unity Test Framework (UTF)**: Unity package built on NUnit that exposes Edit Mode and Play Mode automation inside the editor.
- **Edit Mode Test**: Test fixture that runs in the editor process to validate pure C# logic or asset configuration without loading the player loop.
- **Play Mode Test**: Scenario-driven test that boots a stripped player to exercise scene objects, coroutines, and physics interactions.
- **Assembly Definition (asmdef)**: Asset that scopes compile targets; create dedicated test asmdefs that reference the runtime assemblies they cover.
- **UnityTest Attribute**: Coroutine-friendly attribute that lets Play Mode tests yield across frames while awaiting game state changes.
- **Test Runner CLI (`-runTests`)**: Headless execution path that runs suites in CI and exports XML results with the `-testResults` flag.
- **Assertion Library**: NUnit `Assert` methods plus Unity-specific helpers that fail tests when expected outcomes aren't met.
