# Extension, Partial, and Expression-Bodied Members

## Extension Methods at a Glance
- Add helper functionality to existing types without modifying source or creating subclasses.
- Declared in static classes with static methods whose first parameter uses the `this` modifier.
- Great for fluent APIs, domain-specific helpers, and keeping business logic discoverable.

```csharp
public static class MoneyExtensions
{
    public static Money ConvertTo(this Money amount, Currency target, IExchangeProvider provider)
        => new(provider.Convert(amount.Value, amount.Currency, target), target);
}

// Usage
authorization.Limit.ConvertTo(Currency.Eur, exchangeProvider);
```

## Partial Types and Methods
- Split large classes, structs, or records across multiple files to separate generated and handwritten code.
- Source generators and designers emit `partial` declarations so developers can extend behavior safely.
- Partial methods allow optional implementations; if omitted, the compiler removes the declaration.

```csharp
public partial class InvoiceProcessor
{
    partial void OnProcessingStarted(Invoice invoice);

    public void Process(Invoice invoice)
    {
        OnProcessingStarted(invoice);
        // processing steps
    }
}

public partial class InvoiceProcessor
{
    partial void OnProcessingStarted(Invoice invoice)
        => _logger.LogInformation("Processing {InvoiceId}", invoice.Id);
}
```

## Expression-Bodied Members
- Provide concise syntax for simple property getters, methods, constructors, and operators.
- Use when the body is a single expression; keep readability by avoiding deeply nested expressions.

```csharp
public class Segment
{
    public Segment(Point start, Point end) => (Start, End) = (start, end);

    public Point Start { get; }
    public Point End { get; }

    public double Length => Math.Sqrt(Math.Pow(Start.X - End.X, 2) + Math.Pow(Start.Y - End.Y, 2));

    public override string ToString() => $"{Start} -> {End}";
}
```

## Putting It Together
- Combine extension methods with expression-bodied members for fluent pipelines.
- Organize partial types by responsibility: file-per-feature or generated vs manual sections.
- Document extension namespaces so consumers add the correct `using` directives.

## Further Study
- MSDN: "Extension Methods" and "Partial Classes and Methods".
- Roslyn source generator samples leveraging partial types.
- Coding standards: prefer expression-bodied members where they enhance clarity, not just brevity.






## References
- [Extension methods guide](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/extension-methods) - extend existing types without inheritance.
- [Partial classes and methods](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods) - split type definitions across files.
- [Expression-bodied members](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members) - concise member syntax.
- [Pattern matching fundamentals](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/functional/pattern-matching) - combine modern language features with patterns.
- [Extension methods tutorial](https://www.youtube.com/watch?v=PQmqHo7T0n8) - video exploring extension method scenarios.
## Key Terms
- **Extension Method**: Static method with a `this` parameter that adds helper behaviour to existing types without modifying their source.
- **Partial Type**: Class, struct, or record split across multiple files so generated and handwritten code can coexist safely.
- **Partial Method**: Optional hook declared in a partial type; the compiler removes it when no implementation is provided.
- **Expression-Bodied Member**: Concise syntax using `=>` to implement simple getters, methods, or constructors with a single expression.
- **Source Generator**: Build-time tool emitting extra partial declarations consumed by your handwritten extensions.
- **Fluent API**: Chainable method style often enabled by extension methods to create readable domain-specific pipelines.
