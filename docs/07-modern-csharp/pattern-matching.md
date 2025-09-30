# Pattern Matching Enhancements

## Evolution Since C# 7
- C# introduced pattern matching with `is` expressions and `switch` statements and has expanded each release.
- Patterns reduce boilerplate `if` chains, making business rules declarative and safer.

## `is` Expression Patterns
- Type, constant, and relational patterns simplify null and type checks.

```csharp
if (obj is HttpResponseMessage { IsSuccessStatusCode: true } response)
{
    return await response.Content.ReadAsStringAsync(ct);
}
```

## `switch` Expressions
- Return values directly, focus on expressions, and enforce exhaustiveness for enums and records.

```csharp
public static string DescribeStatus(int code) => code switch
{
    < 0 => "Pending",
    0 => "Ready",
    200 => "OK",
    400 or 404 => "Client error",
    >= 500 => "Server error",
    _ => "Unknown"
};
```

## Property and Positional Patterns
- Match on nested properties or deconstruct types inline.

```csharp
public static bool IsHighValueOrder(Order order) => order switch
{
    { Total: > 1000m, Customer.Tier: CustomerTier.Platinum } => true,
    { Items.Count: > 10 } => true,
    _ => false
};

public readonly record struct Vector(int X, int Y, int Z);

var magnitude = vector switch
{
    Vector(var x, var y, var z) => Math.Sqrt(x * x + y * y + z * z),
    _ => double.NaN
};
```

## `when` Guards and Discard Patterns
- Extend matches with additional conditions using `when`.
- Use `_` to ignore values or discard tuple elements.

```csharp
return state switch
{
    { Attempts: > 3 } when FeatureFlags.LockoutEnabled => State.Locked,
    { Attempts: > 3 } => State.RequiresCaptcha,
    _ => State.Active
};
```

## Best Practices
- Keep patterns readable; nest only when it improves clarity.
- Ensure switch expressions cover all cases to avoid `SwitchExpressionException`.
- Pair with records for ergonomic positional matches.
- Benchmark complex nested patterns; the compiler generates decision DAGs that are fast but not free.

## Further Study
- Docs: "Pattern matching in C#" for full pattern catalog.
- Channel 9 sessions from Anders Hejlsberg on pattern design.
- Roslyn repo issues for upcoming pattern proposals.






## References
- [Pattern matching overview](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/functional/pattern-matching) - motivation and supported pattern forms.
- [Patterns reference](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/patterns) - syntax for each pattern type.
- [Switch expressions documentation](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/switch-expression) - expression-based branching with patterns.
- [Apply pattern matching module](https://learn.microsoft.com/en-us/training/modules/csharp-pattern-matching/) - Microsoft Learn module on advanced patterns.
- [Pattern matching in C# talk](https://www.youtube.com/watch?v=J0z6s4r2VoY) - conference presentation on real-world uses.
## Key Terms
- **Pattern Matching**: Feature set that matches values against shapes (types, constants, properties) to simplify branching logic.
- **`is` Pattern**: Expression that combines type testing and assignment, like `obj is HttpResponseMessage response`.
- **Switch Expression**: Expression-based `switch` that returns a value and enforces exhaustiveness for enums and records.
- **Positional Pattern**: Syntax that deconstructs tuples or records inline, enabling matches like `Vector(var x, var y, var z)`.
- **Property Pattern**: Pattern that inspects nested members, e.g., `{ Total: > 1000m, Customer.Tier: Platinum }`.
- **Guard Clause (`when`)**: Additional condition appended to a pattern to filter matches without extra nesting.
- **Discard (`_`)**: Placeholder used to ignore values while keeping patterns exhaustive and readable.
