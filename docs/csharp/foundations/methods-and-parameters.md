# Methods and Parameters

## Learning objectives
- Design method signatures that express intent and return the right amount of information.
- Choose parameter modifiers (`ref`, `out`, `in`) that accurately describe data flow.
- Employ overloading and optional parameters judiciously to keep APIs approachable.

## Core ideas

### Method signatures and return types
- A signature combines method name, parameter list (types + modifiers), and return type; the signature determines overload resolution.
- Prefer returning meaningful types (tuples, custom structs/classes) over relying solely on side-effects or `out` parameters.

### Parameter passing semantics
- Default parameter passing copies the value (or reference for reference types).
- `ref` enables callers to pass an initialized variable that the method can read and update.
- `out` signals that the method will set the variable before returning; callers do not need to pre-initialize it.
- `in` allows passing large structs by reference while preventing modifications inside the method body.

### Optional, named, and params arguments
- Optional parameters (`void Log(string message, LogLevel level = LogLevel.Info)`) simplify call sites with sensible defaults.
- Named arguments (`Log(level: LogLevel.Warning, message: "Disk space low")`) clarify intent, especially when multiple arguments share the same type.
- Use `params` arrays for variable-length argument lists when the caller count is unknown.

### Overloading best practices
- Keep overload sets small and focused; too many variations create ambiguity.
- Differ only by parameter count or types—changing return type alone is not permitted.
- Provide a single "core" overload and let others delegate to it for maintainability.

## Hands-on example: parsing and scaling dimensions
```csharp
static bool TryParseDimensions(string source, out int width, out int height)
{
    width = height = 0;
    var parts = source.Split('x', StringSplitOptions.TrimEntries);
    return parts.Length == 2
        && int.TryParse(parts[0], out width)
        && int.TryParse(parts[1], out height);
}

static void Scale(ref int value, double factor)
{
    value = (int)Math.Round(value * factor);
}

if (TryParseDimensions("1920 x 1080", out var w, out var h))
{
    Scale(ref w, 0.5);
    Scale(ref h, 0.5);
    Console.WriteLine($"Scaled dimensions: {w}x{h}");
}
```

## Practice checkpoints
- Create overloads of a `Log` method that accept a message only, message + exception, and a generic payload.
- Implement a method that returns a tuple `(bool IsSuccess, string Error)` rather than relying solely on `out` parameters.
- Explore using `in` parameters with large readonly structs to avoid defensive copies while protecting data.

## Further exploration
- Review the language specification rules for overload resolution to understand how the compiler picks a candidate.
- Investigate local functions and lambda expressions as alternatives to private helper methods.
- Examine how `Span<T>` and other ref struct types restrict parameter usage (e.g., they cannot be captured by closures).

## Word List
- 'x'
- 0
- 1
- 1080
- 1920
- 2
- 5
- a
- accept
- accurately
- allows
- alone
- alternatives
- ambiguity
- amount
- an
- and
- apis
- approachable
- argument
- arguments
- arrays
- as
- avoid
- be
- before
- best
- body
- bool
- by
- call
- caller
- callers
- can
- candidate
- cannot
- captured
- changing
- checkpoints
- choose
- clarify
- classes
- closures
- combines
- compiler
- console
- copies
- core
- count
- create
- csharp
- custom
- data
- default
- defaults
- defensive
- delegate
- describe
- design
- determines
- differ
- dimensions
- disk
- do
- double
- e
- effects
- employ
- enables
- error
- especially
- examine
- example
- exception
- exploration
- explore
- express
- expressions
- factor
- flow
- focused
- for
- functions
- further
- g
- generic
- h
- hands
- height
- helper
- how
- ideas
- if
- implement
- in
- info
- information
- initialize
- initialized
- inside
- int
- intent
- investigate
- is
- issuccess
- it
- judiciously
- keep
- lambda
- language
- large
- learning
- length
- let
- level
- list
- lists
- local
- log
- loglevel
- low
- maintainability
- many
- math
- meaningful
- message
- method
- methods
- modifications
- modifiers
- multiple
- name
- named
- need
- not
- objectives
- of
- on
- only
- optional
- or
- other
- others
- out
- over
- overload
- overloading
- overloads
- parameter
- parameters
- params
- parsing
- parts
- pass
- passing
- payload
- permitted
- picks
- practice
- practices
- pre
- prefer
- preventing
- private
- protecting
- provide
- rather
- read
- readonly
- ref
- reference
- relying
- resolution
- restrict
- return
- returning
- returns
- review
- right
- round
- rules
- same
- scale
- scaled
- scaling
- semantics
- sensible
- set
- sets
- share
- side
- signals
- signature
- signatures
- simplify
- single
- sites
- small
- solely
- source
- space
- span
- specification
- split
- static
- string
- stringsplitoptions
- struct
- structs
- t
- than
- that
- the
- they
- to
- too
- trimentries
- tryparse
- tryparsedimensions
- tuple
- tuples
- type
- types
- understand
- unknown
- update
- usage
- use
- using
- value
- var
- variable
- variations
- void
- w
- warning
- when
- while
- width
- will
- with
- writeline
- x

## References
- [Methods (C# Programming Guide)](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/methods) — syntax, lifecycle, and overloading rules.
- [Named and optional arguments](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) — call-site flexibility and readability gains.
- [ref keyword](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/ref) — when to pass arguments by reference.
- [Microsoft Learn: Call methods in your programs with C#](https://learn.microsoft.com/en-us/training/modules/csharp-call-methods/) — interactive module practicing parameters and return values.
- [C# 101 show](https://learn.microsoft.com/en-us/shows/dotnet/csharp-101/) — video series with episodes on methods and parameter passing.
