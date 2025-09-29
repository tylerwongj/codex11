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

## Word List
- 0
- 1
- 2
- 3
- a
- and
- as
- avoid
- be
- best
- bit
- bitwise
- burning
- check
- clarity
- clear
- closed
- combinations
- combine
- composite
- constants
- create
- csharp
- decorate
- defaults
- define
- depending
- difficulty
- document
- e
- easy
- enum
- enumerations
- enums
- essentials
- exclusive
- explicit
- flag
- flags
- for
- g
- hard
- hasflag
- integers
- interop
- invert
- isstunned
- keep
- magic
- make
- mask
- member
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
- that
- to
- toggle
- tostring
- two
- types
- use
- value
- values
- var
- via
- when
- with
- without

## References
- [Enumeration types](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/enumeration-types) — defining enums and iterating over members.
- [enum (C# Reference)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/enum) — language rules for underlying types and initialization.
- [System.FlagsAttribute](https://learn.microsoft.com/en-us/dotnet/api/system.flagsattribute) — using bit flags for combinable options.
- [Flags enums guidance](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/enum#flags-enums) — official guidance and examples for flags.
- [C# 101 show](https://learn.microsoft.com/en-us/shows/dotnet/csharp-101/) — episode coverage on enums and pattern matching.
