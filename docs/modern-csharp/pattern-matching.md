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

## Word List
- 0
- 10
- 1000m
- 200
- 3
- 400
- 404
- 500
- 7
- 9
- active
- additional
- all
- and
- anders
- are
- attempts
- avoid
- await
- benchmark
- best
- boilerplate
- bool
- business
- but
- c
- cases
- catalog
- chains
- channel
- checks
- clarity
- client
- code
- compiler
- complex
- conditions
- constant
- content
- count
- cover
- csharp
- ct
- customer
- customertier
- dags
- decision
- declarative
- deconstruct
- describestatus
- design
- directly
- discard
- docs
- double
- each
- elements
- enforce
- enhancements
- ensure
- enums
- ergonomic
- error
- evolution
- exhaustiveness
- expanded
- expression
- expressions
- extend
- false
- fast
- featureflags
- focus
- for
- free
- from
- full
- further
- generates
- guards
- has
- hejlsberg
- httpresponsemessage
- if
- ignore
- improves
- in
- inline
- int
- introduced
- is
- ishighvalueorder
- issuccessstatuscode
- issues
- it
- items
- keep
- locked
- lockoutenabled
- magnitude
- making
- match
- matches
- matching
- math
- nan
- nest
- nested
- not
- null
- obj
- ok
- on
- only
- or
- order
- pair
- pattern
- patterns
- pending
- platinum
- positional
- practices
- properties
- property
- proposals
- public
- readable
- readasstringasync
- readonly
- ready
- record
- records
- reduce
- relational
- release
- repo
- requirescaptcha
- response
- return
- roslyn
- rules
- safer
- server
- sessions
- simplify
- since
- sqrt
- state
- statements
- static
- string
- struct
- study
- switch
- switchexpressionexception
- that
- the
- tier
- to
- total
- true
- tuple
- type
- types
- unknown
- upcoming
- use
- using
- values
- var
- vector
- when
- with
- x
- y
- z

## References
- [Pattern matching overview](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/functional/pattern-matching) — motivation and supported pattern forms.
- [Pattern matching reference](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/patterns) — exhaustive list of patterns and syntax.
- [switch expressions](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/switch-expression) — modern alternative to traditional switch statements.
- [Microsoft Learn: Apply pattern matching in C#](https://learn.microsoft.com/en-us/training/modules/csharp-pattern-matching/) — interactive exercises exploring new patterns.
- [Dustin Campbell: Pattern Matching in C#](https://www.youtube.com/watch?v=J0z6s4r2VoY) — conference talk on practical use cases.
