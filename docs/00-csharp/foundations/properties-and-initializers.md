# Properties and Initializers

## Learning objectives
- Wrap fields with property accessors that validate and expose state intentionally.
- Use object, collection, and indexer initializers to bootstrap data succinctly.
- Apply init-only setters and calculated properties to communicate mutability guarantees.

## Core ideas

### Property types
- **Auto-properties**: `public string Name { get; set; }` generates a hidden backing field; combine with access modifiers (`private set`) to control mutation.
- **Calculated properties**: Provide logic in the getter or setter to enforce invariants or derive values on demand.
- **Init-only setters**: `public string Environment { get; init; }` allow assignment during initialization but keep objects immutable afterward.

### Indexers
- Indexers (`public string this[string key]`) offer array-like access for custom types.
- Overload indexers by parameter type or count to support multiple lookup shapes.
- Throw meaningful exceptions or return defaults when keys are missing to avoid silent failures.

### Object and collection initializers
- Object initializers set properties immediately after construction, even on anonymous types, without additional constructor overloads.
- Collection initializers populate `ICollection<T>` implementations by calling `Add` for each element.
- Target-typed `new()` reduces repetition when the compiler can infer the type.

### Patterns for immutability
- Combine `readonly` fields, `init` setters, and immutable collections to build types that are safe to share across threads.
- When exposing collections, prefer `IReadOnlyCollection<T>` or defensive copies.

## Hands-on example: configuring settings
```csharp
class Settings
{
    private readonly Dictionary<string, string> _values = new();

    public string Environment { get; init; } = "Production";

    public string this[string key]
    {
        get => _values.TryGetValue(key, out var value) ? value : throw new KeyNotFoundException(key);
        set => _values[key] = value;
    }

    public IReadOnlyCollection<string> Keys => _values.Keys;
}

var settings = new Settings
{
    Environment = "Development",
    ["ConnectionString"] = "Host=localhost;Port=5432;",
    ["LogLevel"] = "Debug"
};

var numbers = new List<int> { 1, 2, 3, 5, 8 };
var lookup = new Dictionary<string, int>
{
    ["answer"] = 42,
    ["dozen"] = 12
};
```

## Practice checkpoints
- Convert field-backed properties into auto-properties where appropriate and enforce invariants in accessors.
- Add validation in a setter that throws when the assigned value is out of range.
- Implement indexers that support both numeric and string keys via overloads.

## Further exploration
- Investigate records with `init` setters for concise immutable types.
- Explore `with` expressions to clone objects with modified properties.
- Review collection initializer requirements to customize your own collection types.








## References
- [Properties programming guide](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/properties) - encapsulation via properties.
- [Auto implemented properties](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) - reduce boilerplate when no extra logic is needed.
- [Object and collection initializers](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers) - concise initialization syntax.
- [init accessors reference](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/init) - configure immutable properties during construction.
- [Auto implemented properties explained](https://www.youtube.com/watch?v=P4v1RByyKaA) - video on property patterns and tips.
## Key Terms
- **Auto-property**: Property with compiler-generated backing field; useful when no extra logic is required.
- **Backing Field**: Private field that stores data exposed through property accessors.
- **Calculated Property**: Property whose getter or setter runs logic to derive or validate values on the fly.
- **Init-only Setter**: `init` accessor that permits assignment during object initialization but enforces immutability afterward.
- **Indexer**: Property-like member (`this[...]`) that provides array-style access to custom collections.
- **Object Initializer**: Syntax that assigns properties immediately after construction without explicit setters in code.
- **Collection Initializer**: Syntax that populates collections by invoking `Add` for each element inside braces.
- **Target-typed new**: C# feature allowing `new()` when the compiler can infer the constructed type.
- **Immutable Collection**: Collection type or pattern that prevents modification once created, often exposed via `IReadOnlyCollection<T>`.
- **with Expression**: Expression that clones a record or init-only object while changing selected properties.
- **Defensive Copy**: Technique of returning copies of collections to prevent external mutation of internal state.
- **KeyNotFoundException**: Exception thrown when an indexer or dictionary lookup fails and no default is provided.
- **Property Accessor**: `get` or `set` block controlling how external callers read or modify a property.
