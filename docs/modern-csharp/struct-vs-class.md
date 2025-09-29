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

## Word List
- 10
- 16
- accessors
- allocated
- allocation
- and
- are
- as
- assignment
- avoid
- based
- before
- behavior
- behaviors
- benchmarkdotnet
- beyond
- box
- boxing
- built
- but
- by
- bytes
- c
- can
- change
- choosing
- clarity
- class
- classes
- cloning
- code
- collected
- combine
- combines
- constructors
- context
- copied
- copies
- copy
- copying
- cost
- cpu
- creation
- csharp
- customer
- data
- ddd
- defensive
- dictionary
- docs
- domain
- dominate
- don't
- dtos
- during
- email
- empty
- enable
- encapsulate
- ensures
- equality
- eric
- explicit
- expose
- expressions
- factories
- factory
- fast
- favor
- favors
- features
- fields
- first
- float
- for
- from
- fundamentals
- further
- garbage
- gc
- get
- gethashcode
- graphs
- guard
- guidelines
- heap
- hierarchies
- historical
- hurt
- id
- ideal
- iequatable
- immutability
- immutable
- implement
- in
- increases
- indirection
- inheritance
- init
- initialization
- inline
- inside
- instances
- interop
- invariants
- is
- keep
- large
- layout
- leverage
- lightweight
- lippert's
- lived
- locality
- loops
- mark
- matching
- measure
- measuring
- memory
- mental
- methods
- model
- models
- modern
- modified
- multiply
- mutability
- mutable
- name
- native
- need
- net
- never
- newemail
- object
- of
- offs
- on
- only
- or
- out
- override
- parameterless
- passed
- pattern
- patterns
- performance
- point2d
- pointer
- polymorphism
- possible
- predictable
- prefer
- premature
- preserving
- pressure
- prevent
- produce
- profiling
- properties
- public
- reach
- readability
- readonly
- record
- records
- reference
- require
- reveals
- right
- runtime
- semantics
- set
- setters
- sharing
- short
- size
- small
- stack
- state
- static
- stick
- string
- struct
- structification
- structlayout
- structs
- study
- t
- that
- the
- through
- tight
- to
- tracking
- trade
- treat
- type
- types
- updated
- usage
- use
- valid
- value
- var
- via
- vs
- when
- where
- while
- with
- x
- y

## References
- [Choosing between class and struct](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/choosing-between-class-and-struct) — design guidelines for selecting a type.
- [Design guidelines for structs](https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/struct) — framework design rules.
- [Value types vs reference types](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/types/) — comparison of semantics and storage.
- [Write safe and efficient C# code](https://learn.microsoft.com/en-us/dotnet/csharp/write-safe-efficient-code) — performance considerations for structs.
- [Tim Corey: Struct vs Class](https://www.youtube.com/watch?v=WVobZ4D9F94) — video guide on when to favor structs.
