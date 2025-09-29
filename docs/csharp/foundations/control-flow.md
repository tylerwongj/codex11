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

## Word List
- 0
- 05m
- 0m
- 15m
- 2
- 25m
- 50m
- 5m
- 60m
- 9
- a
- against
- amount
- analyze
- and
- apply
- argumentoutofrangeexception
- as
- avoids
- behavior
- between
- body
- boilerplate
- bool
- branches
- branching
- break
- build
- c
- calculation
- can
- canada
- case
- casts
- checkpoints
- checks
- clauses
- clearly
- code
- comparing
- conditional
- conditionals
- conditions
- console
- construct
- continue
- control
- core
- count
- country
- csharp
- custom
- data
- decimal
- deconstruct
- descriptive
- destination
- differentiate
- discard
- do
- early
- else
- empty
- encourage
- enhancements
- enumerators
- essentials
- example
- exceptional
- exhaustive
- exit
- exits
- expedited
- experiment
- exploration
- explore
- express
- expression
- expressions
- expressive
- fallback
- false
- flow
- focus
- for
- foreach
- further
- generated
- gracefully
- guard
- handling
- hands
- happy
- how
- ideas
- if
- il
- implement
- in
- index
- inline
- input
- introduced
- isnullorwhitespace
- iso
- iteration
- iterator
- jump
- jumps
- keep
- know
- label
- later
- learning
- length
- leverage
- linear
- lines
- logic
- logical
- loop
- looping
- loops
- management
- manual
- many
- match
- matching
- math
- max
- method
- methods
- more
- moves
- must
- nameof
- nearest
- need
- nested
- new
- next
- null
- objectives
- objects
- obscure
- of
- on
- once
- one
- only
- options
- or
- ordertotal
- path
- pattern
- patterns
- positional
- practice
- pre
- prefer
- property
- provide
- reach
- readable
- reads
- reduce
- relational
- return
- returns
- rewrite
- right
- run
- s
- select
- sequence
- shape
- shine
- shipping
- shippingcost
- signals
- simple
- sparingly
- standard
- statements
- states
- static
- straightforward
- stream
- string
- strings
- switch
- that
- the
- throw
- to
- too
- total
- traversal
- true
- tuples
- type
- types
- understand
- until
- us
- use
- user
- value
- var
- verbose
- via
- when
- while
- whitespace
- with
- without
- work
- writeline
- yield
- you
- your

## References
- [Selection statements](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/selection-statements) — `if`, `else`, and `switch` constructs with examples.
- [Iteration statements](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/iteration-statements) — loops available in C# and when to use them.
- [switch expression guidance](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/switch-expression) — modern pattern-based branching.
- [Microsoft Learn: Create branching and looping structures](https://learn.microsoft.com/en-us/training/modules/csharp-create-branching-loops/) — hands-on practice with control flow.
- [Programming with Mosh: C# Control Flow](https://www.youtube.com/watch?v=5i0rCsWfO1Y) — video introduction to branching and loops.

