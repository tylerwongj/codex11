# Control Flow Essentials

## Learning objectives
- Select the right conditional construct to express branching logic clearly.
- Apply looping patterns that match the shape of your data and exit conditions.
- Leverage pattern matching and switch expressions to reduce boilerplate.

## Core ideas

### Conditionals
- Use `if`/`else if`/`else` for straightforward, readable branches.
- Reach for `switch` when comparing one value against many options or patterns.
- Guard clauses (early `return`, `throw`) keep happy-path logic more linear.

### Loops
- `for` loops shine when you know the iteration count or need the index.
- `while` and `do`-`while` focus on conditions; prefer `while` for pre-checks and `do` when the body must run once.
- `foreach` reads clearly for sequence traversal and avoids manual index management.

### Pattern matching and switch expressions
- Type patterns (`case Stream s`) and relational patterns (`case > 0`) provide expressive branching without verbose casts.
- Positional patterns and property patterns deconstruct tuples or objects inline.
- Switch expressions return a value and encourage exhaustive handling via the `_` discard.

### Jump statements
- `break` exits the nearest loop or switch; `continue` moves to the next iteration.
- `return` exits the method; `throw` signals exceptional states.
- Use jumps sparingly—too many can obscure control flow.

## Hands-on example: shipping calculation
```csharp
static decimal ShippingCost(decimal orderTotal, string destination, bool expedited) =>
    (orderTotal, destination, expedited) switch
    {
        ( <= 0m, _, _) => throw new ArgumentOutOfRangeException(nameof(orderTotal)),
        (var total, "US", false) when total >= 50m => 0m,
        (var total, "US", true) => Math.Max(5m, total * 0.05m),
        (_, "Canada", _) => 15m,
        (_, { Length: 2 }, _) => 25m, // ISO country code fallback
        _ => 50m
    };

foreach (var amount in new[] { 25m, 60m })
{
    Console.WriteLine($"Standard US shipping for {amount:C} = {ShippingCost(amount, "US", false):C}");
}
```

## Practice checkpoints
- Rewrite nested `if` statements as a switch expression that returns a descriptive label.
- Implement a `while` loop that reads console input until the user types `exit`, handling empty lines gracefully.
- Use property patterns to differentiate between `null`, empty, and whitespace-only strings (`string.IsNullOrWhiteSpace`).

## Further exploration
- Explore pattern matching enhancements introduced in C# 9 and later (relational, logical, and simple type patterns).
- Experiment with iterator methods (`yield return`) to build custom looping behavior.
- Analyze the generated IL for `foreach` to understand how enumerators work.








## References
- [Selection statements](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/selection-statements) - syntax for if, else, switch, and switch expressions.
- [Iteration statements](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/iteration-statements) - loops available in C# and usage tips.
- [Switch expression reference](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/switch-expression) - pattern-based branching features.
- [Create branching and looping structures](https://learn.microsoft.com/en-us/training/modules/csharp-create-branching-loops/) - Microsoft Learn practice module.
- [C# control flow basics](https://www.youtube.com/watch?v=5i0rCsWfO1Y) - video covering decisions and loops.
## Key Terms
- **Conditional Statement**: Branching construct like `if`/`else` or `switch` that chooses code paths based on a predicate.
- **Guard Clause**: Early `return` or `throw` that exits when preconditions fail, keeping the happy path uncluttered.
- **Switch Expression**: Expression-based `switch` introduced in modern C# that returns a value and supports pattern matching.
- **Pattern Matching**: Feature that matches values against type, relational, or property patterns for concise branching.
- **for Loop**: Counter-driven loop ideal when you need an index or a fixed iteration count.
- **while Loop**: Condition-checked loop that continues while the predicate remains true.
- **do-while Loop**: Loop that executes the body at least once before re-checking the condition.
- **foreach Loop**: Sequence traversal construct that works with any type exposing `GetEnumerator()`.
- **break Statement**: Terminates the nearest loop or switch block immediately.
- **continue Statement**: Skips the rest of the current loop iteration and proceeds to the next.
- **return Statement**: Ends method execution and optionally provides a value to the caller.
- **throw Statement**: Signals an exceptional condition by raising an exception instance.
- **Relational Pattern**: Pattern matching clause such as `case > 0` evaluated against numeric or comparable values.
- **Property Pattern**: Pattern that inspects object members inline (e.g., `case { Length: 2 }`).
- **Tuple Pattern**: Pattern that matches on tuple or deconstructed values inside a switch expression.
- **Iterator Method**: Method using `yield return`/`yield break` to produce custom sequences lazily.
