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
## Word List
- 100
- a
- across
- addcomponent
- an
- and
- any
- apis
- areequal
- asmdefs
- assemblies
- assembly
- assert
- asynchronous
- attributes
- author
- automatically
- automation
- behaviours
- booting
- bootstrap
- builds
- c
- checkpoint
- checks
- ci
- classes
- cli
- com
- configuration
- configure
- coroutine
- coroutines
- create
- csharp
- current
- dashboards
- data
- definitions
- depend
- deterministic
- discovers
- docs
- down
- driven
- edit
- editmode
- editor
- editortestsrunner
- enable
- execute
- execution
- exercise
- fail
- failure
- fast
- fixtures
- flag
- for
- frames
- framework
- from
- gameobject
- hands
- headlessly
- html
- https
- in
- inside
- inspector
- keep
- lightweight
- loads
- local
- logic
- loop
- machine
- manual
- mode
- ms
- new
- nunit
- objects
- on
- one
- only
- or
- output
- path
- persist
- physics
- play
- player
- playerhealth
- playerstartswithfullhealth
- playmode
- plus
- pressing
- project
- public
- pure
- references
- referencing
- rely
- run
- runner
- running
- runtests
- runtime
- sample
- scene
- scriptableobject
- simulates
- so
- spawn
- state
- steps
- stripped
- suites
- target
- test
- testing
- testresults
- tests
- that
- the
- them
- they
- to
- unity
- unity3d
- unitytest
- unitytestrunner
- use
- using
- validate
- var
- verifying
- void
- where
- window
- without
- workflows
- xml
- yield
