# Structs, Classes, and Records

## Mental Model
- Classes are reference types: allocated on the heap, passed by reference, garbage collected.
- Structs are value types: stack or inline allocation, copied on assignment, need explicit boxing to treat as object.
- Records (class or struct) favor immutable data models with value-based equality out of the box.

## Performance Trade-offs
- Structs avoid GC pressure for small, short-lived data but copying large structs increases cost.
- Reference types enable polymorphism and sharing state but require GC tracking and pointer indirection.
- Measure first: modern .NET GC is fast; premature structification can hurt readability and allocation locality.

```csharp
public readonly struct Point2D
{
    public Point2D(float x, float y) => (X, Y) = (x, y);
    public float X { get; }
    public float Y { get; }
}
```

## Guidelines for Structs
- Keep size ≤ 16 bytes where possible; large structs multiply copy cost.
- Mark as `readonly struct` when fields never change to prevent defensive copies.
- Implement `IEquatable<T>` and override `GetHashCode` for dictionary usage.
- Avoid parameterless constructors before C# 10; prefer static factories for clarity.

## Records and Immutability
- `record class` favors reference semantics with built-in cloning (`with` expressions) and value equality.
- `record struct` combines value semantics with record features, ideal for lightweight DTOs.
- Leverage `init` accessors to set properties during object initialization while preserving immutability.

```csharp
public record class Customer(string Id, string Name)
{
    public string Email { get; init; } = string.Empty;
}
```

## Choosing the Right Type
- Use `record class` for domain models that need equality, pattern matching, and DDD behaviors.
- Stick with `class` when mutability, inheritance hierarchies, or large object graphs dominate.
- Reach for `struct` only when profiling reveals allocation pressure or tight CPU loops.
- For interop with native code, `struct` with `[StructLayout]` ensures predictable layout.

## Immutable Patterns Beyond Records
- Encapsulate state via constructors and `init` setters; expose behavior through methods.
- Combine with `with` expressions to produce copies with modified fields (`var updated = customer with { Email = newEmail };`).
- Guard invariants inside constructors or factory methods to keep immutable instances valid from creation.

## Further Study
- .NET Runtime docs: Value types, records, and memory fundamentals.
- BenchmarkDotNet for measuring struct vs class behavior.
- Eric Lippert's "Don't use mutable structs" for historical context.






## References
- [Choosing between class and struct](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/choosing-between-class-and-struct) - design guidelines for selecting a type.
- [Design guidelines for structs](https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/struct) - framework guidance on struct design.
- [Value types versus reference types](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/types/) - compare semantics and storage.
- [Write safe and efficient C# code](https://learn.microsoft.com/en-us/dotnet/csharp/write-safe-efficient-code) - performance considerations for structs.
- [Struct vs class video](https://www.youtube.com/watch?v=WVobZ4D9F94) - Tim Corey explanation of trade-offs.
## Key Terms
- **Reference Type**: Class-based type stored on the managed heap and accessed via references, enabling polymorphism and shared state.
- **Value Type**: Struct or primitive stored inline; copying passes data by value, which can reduce GC pressure for small structs.
- **Record**: C# type with synthesized value equality and `with` expressions, available as `record class` or `record struct`.
- **Readonly Struct**: Struct whose fields never mutate, preventing defensive copies and signalling immutability to callers.
- **IEquatable<T>**: Interface that lets structs and records define value equality, critical for dictionary and set lookups.
- **`with` Expression**: Syntax that clones a record while overriding selected properties, preserving immutability.
- **StructLayout Attribute**: Interop directive controlling field layout when passing structs to native code.
