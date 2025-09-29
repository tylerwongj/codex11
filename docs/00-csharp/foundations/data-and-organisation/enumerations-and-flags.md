# Enumerations and Flags

## Standard Enums
- Represent a closed set of named constants.
- Store explicit values to stabilize persistence and interop.

```csharp
public enum Difficulty
{
    Easy = 0,
    Normal = 1,
    Hard = 2,
    Nightmare = 3
}
```

## Flags Enums
- Combine options via bitwise OR; values must be powers of two.
- Decorate with `[Flags]` so `ToString()` returns composite names.

```csharp
[Flags]
public enum StatusEffects
{
    None = 0,
    Poisoned = 1 << 0,
    Stunned = 1 << 1,
    Burning = 1 << 2,
    Shielded = 1 << 3
}

var state = StatusEffects.Poisoned | StatusEffects.Stunned;
var isStunned = state.HasFlag(StatusEffects.Stunned);
state &= ~StatusEffects.Poisoned; // remove poison
```

## Bitwise Essentials
- `|` combine flags, `&` check or mask, `~` invert, `^` toggle.
- Prefer `HasFlag` or `(value & Flag) != 0` for clarity.
- Use bit shifting (`1 << n`) to define new flags without magic numbers.

## Best Practices
- Keep a `None = 0` member for clear defaults.
- Avoid mixing flags and sequential enums; create separate types.
- Document combinations that make sense (e.g., mutually exclusive flags).
- When serializing, store as integers or strings depending on readability needs.








## References
- [Enumeration types guide](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/enumeration-types) - defining and iterating enum values.
- [enum keyword reference](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/enum) - language rules for enums.
- [Flags enums guidance](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/enum#flags-enums) - combine values with bit flags.
- [System.FlagsAttribute reference](https://learn.microsoft.com/en-us/dotnet/api/system.flagsattribute) - decorate enums for bitwise support.
- [Enums in C# video](https://www.youtube.com/watch?v=SN1exWlNxuE) - short walkthrough of enum best practices.
## Word List
- 0
- 1
- 2
- 3
- a
- and
- api
- as
- avoid
- be
- best
- bit
- bitwise
- builtin
- burning
- check
- clarity
- clear
- closed
- com
- combinations
- combine
- composite
- constants
- covers
- create
- creating
- csharp
- declaration
- decorate
- defaults
- define
- depending
- difficulty
- document
- dotnet
- e
- easy
- en
- enum
- enumeration
- enumerations
- enums
- essentials
- exclusive
- explicit
- flag
- flags
- flagsattribute
- for
- g
- guidance
- hard
- hasflag
- https
- integers
- interop
- invert
- isstunned
- keep
- language
- learn
- magic
- make
- mask
- member
- microsoft
- mixing
- must
- mutually
- n
- named
- names
- needs
- new
- nightmare
- none
- normal
- numbers
- of
- on
- options
- or
- persistence
- poison
- poisoned
- powers
- practices
- prefer
- public
- readability
- reference
- references
- remove
- represent
- returns
- sense
- separate
- sequential
- serializing
- set
- shielded
- shifting
- so
- stabilize
- standard
- state
- statuseffects
- store
- strings
- stunned
- style
- system
- that
- to
- toggle
- tostring
- two
- types
- us
- usage
- use
- value
- values
- var
- via
- when
- with
- without
