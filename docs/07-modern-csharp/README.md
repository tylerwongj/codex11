# Modern C# Features

These modules cover language features that complement Unity development.

- [Async/Await and Task Patterns](async-await-task-patterns.md)
- [Attributes and Reflection](attributes-and-reflection.md)
- [Extension, Partial, and Expression Members](extension-partial-expression-members.md)
- [Pattern Matching Enhancements](pattern-matching.md)
- [Struct vs Class Trade-offs](struct-vs-class.md)

Use them as reference after the intermediate C# topics.

## Module Quick Glance
```bash
ls docs/07-modern-csharp
```






## References
- [C# language reference](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/) - detailed syntax reference for modern features.
- [What is new in C#](https://learn.microsoft.com/en-us/dotnet/csharp/whats-new/) - release-by-release feature summaries.
- [Functional programming in C#](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/functional/) - modern C# functional style guidance.
- [C# in Depth](https://csharpindepth.com/) - deep explanations of advanced language topics.
- [dotNET Conf sessions](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oU_Prec7F2sS8aPguM9wRCU) - conference talks on new C# capabilities.
## Key Terms
- **Modern C# Feature**: Language capability introduced after C# 6 (e.g., pattern matching, records) that improves expressiveness in Unity projects.
- **Async/Await Pattern**: Task-based asynchronous model that keeps Unity tooling and editor extensions responsive during I/O.
- **Attribute Metadata**: Declarative annotations that drive reflection-based systems, editor tooling, and serialization hooks.
- **Extension Method**: Static method that adds fluent APIs to existing types without modifying their source.
- **Pattern Matching**: `is`, `switch`, and relational patterns that simplify branching logic when inspecting complex types.
- **Struct vs Class Trade-off**: Decision between value and reference semantics that impacts GC pressure and copying costs in Unity.
