# Attributes and Reflection

## Purpose of Attributes
- Attach declarative metadata to types, members, and assemblies.
- Drive cross-cutting behaviors such as serialization, validation, and dependency injection.
- Serve as contracts for tooling (Roslyn analyzers, source generators, custom inspectors).

## Built-in Attribute Essentials
- Apply with `[AttributeName]`; omit the `Attribute` suffix when targeting usage.
- Use constructor parameters for required data and named properties for optional settings.
- Common examples: `Obsolete`, `DataMember`, `Authorize`, `Range`.

```csharp
[Obsolete("Prefer the asynchronous overload", error: false)]
public string LoadConfig(string path) => ...;
```

## Creating Custom Attributes
- Inherit from `System.Attribute`.
- Decorate attribute classes with `[AttributeUsage]` to constrain valid targets and multiplicity.

```csharp
[AttributeUsage(AttributeTargets.Class | AttributeTargets.Struct, AllowMultiple = false)]
public sealed class ApiResourceAttribute : Attribute
{
    public ApiResourceAttribute(string routePrefix) => RoutePrefix = routePrefix;
    public string RoutePrefix { get; }
    public string? Version { get; init; }
}
```

## Reflection Basics
- `Type` metadata enables runtime inspection of members, attributes, and generic parameters.
- `Activator.CreateInstance` instantiates types discovered dynamically; pair with caching to avoid overhead.
- Access attributes via `MemberInfo.GetCustomAttributes()` or `CustomAttributeData` for lightweight analysis.

```csharp
var resourceTypes = Assembly.GetExecutingAssembly()
    .GetTypes()
    .Where(t => t.GetCustomAttribute<ApiResourceAttribute>() is not null);

foreach (var type in resourceTypes)
{
    var attribute = type.GetCustomAttribute<ApiResourceAttribute>()!;
    Console.WriteLine($"{type.Name} maps to /api/{attribute.RoutePrefix}");
}
```

## Performance and Safety
- Reflection incurs boxing and metadata lookups; cache `Type` handles and delegate accessors.
- Prefer source generators or compiled expression trees for hot paths.
- Limit dynamic invocation in AOT contexts (Unity IL2CPP, native AOT) where metadata stripping can remove unused members.

## Advanced Patterns
- Use reflection-driven configuration with guardrails: validate attribute usage at startup and fail fast.
- Combine attributes with `IServiceCollection` extensions to auto-register components.
- Pair with analyzers to catch misuse at compile time, e.g., enforce that `[ApiResource]` types expose parameterless constructors.

## Further Study
- .NET Docs: *Attributes* and *Reflection* sections.
- Roslyn source generator samples for attribute-driven code emission.
- "High-performance reflection in .NET" (Stephen Toub) for micro-optimization strategies.






## References
- [Attributes in C# guide](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/attributes/) - introduction to built-in and custom attributes.
- [Creating custom attributes](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/attributes/creating-custom-attributes) - author metadata by deriving from Attribute.
- [Reflection overview](https://learn.microsoft.com/en-us/dotnet/framework/reflection-and-codedom/reflection) - inspect types at runtime using reflection.
- [System.Reflection namespace](https://learn.microsoft.com/en-us/dotnet/api/system.reflection) - API reference for reflection types.
- [Attributes and reflection episode](https://learn.microsoft.com/en-us/shows/csharp-advanced/attributes-and-reflection/) - video demonstrating real-world usage.
## Key Terms
- **Attribute**: Declarative metadata applied to code elements to drive tooling, validation, or runtime behavior.
- **AttributeUsage**: Meta-attribute that constrains where an attribute can be placed and whether multiple instances are allowed.
- **Reflection**: Runtime API for inspecting types, members, and attributes, enabling dynamic discovery and invocation.
- **CustomAttributeData**: Lightweight reflection view that exposes attribute constructor arguments without instantiating them.
- **Activator.CreateInstance**: Helper that constructs objects discovered via reflection, often paired with caching to reduce overhead.
- **IL2CPP Consideration**: Reminder that Unity's AOT pipeline may strip unused metadata, so reflective code must reference types explicitly.
- **Source Generator**: Roslyn tool that emits code at compile time based on attribute markers, reducing runtime reflection costs.
