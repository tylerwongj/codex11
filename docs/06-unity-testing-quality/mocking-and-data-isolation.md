# Mocking and Data Isolation for MonoBehaviours
- **Separate logic from presentation:** Move decision-making into plain C# classes (POCOs) or ScriptableObjects injected into MonoBehaviours. Test them directly without GameObject plumbing.
- **Interface-driven dependencies:** Wrap engine calls (e.g., `Physics.Raycast`, input handlers) behind interfaces and provide editor-time implementations. Substitute them in tests with frameworks such as NSubstitute, Moq, or hand-rolled fakes.
- **Scene scaffolding utilities:** Use `GameObject` factories in `[SetUp]` methods to instantiate only what a test requires. Tear them down in `[TearDown]` or rely on `UnityEngine.TestTools.TestUtils` helpers like `EnumerableExtensions.WithScene` to keep state isolated.
- **Serialized data snapshots:** Store baseline component configurations in prefab assets or ScriptableObjects. Clone them per test via `Object.Instantiate` so modifications never leak between runs.
- **Hands-on checkpoint:** Build a movement controller MonoBehaviour that depends on an `IInputSource` interface. Provide a fake implementation for edit mode tests and verify that speed capping and animation triggers respect the contract.

## Substitute Example
```csharp
var physics = Substitute.For<IPhysicsService>();
physics.Raycast(Arg.Any<Vector3>(), out Arg.Any<RaycastHit>()).Returns(info => true);
```






## References
- [Unity Test Framework manual](https://docs.unity3d.com/Packages/com.unity.test-framework@latest/manual/index.html) - unit, play, and edit mode testing overview.
- [Testable code guidance](https://docs.unity3d.com/Packages/com.unity.test-framework@latest/manual/reference-testable-code.html) - strategies for isolating dependencies.
- [NSubstitute documentation](https://nsubstitute.github.io/help/getting-started/) - lightweight mocking library for .NET.
- [Unit testing best practices](https://learn.microsoft.com/en-us/dotnet/core/testing/unit-testing-best-practices) - arrange-act-assert and dependency isolation tips.
- [Advanced testing techniques tutorial](https://learn.unity.com/tutorial/advanced-testing-techniques) - course on dependency isolation in Unity tests.
## Key Terms
- **Plain Old C# Object (POCO)**: Behaviour-free class that holds logic you can instantiate and unit-test without Unity engine dependencies.
- **Interface Adapter**: Wrapper around Unity APIs (such as `Physics.Raycast`) that lets you substitute fake implementations during tests.
- **Test Double**: Fake, stub, or mock implementation used to simulate collaborators like input sources or physics services.
- **Scene Scaffold**: Minimal set of GameObjects created in `[SetUp]` to provide only the components a test needs.
- **Prefab Snapshot**: Serialized asset clone taken at runtime with `Object.Instantiate` so each test gets an isolated copy of shared data.
- **Setup/TearDown Hooks**: NUnit lifecycle methods that prepare and clean test state, preventing cross-test contamination.
