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
## Key Terms
- **Enumeration**: Type that maps human-readable names to fixed numeric constants.
- **Underlying Type**: Numeric type (`int` by default) that stores the raw enum value.
- **FlagsAttribute**: Attribute that signals an enum represents bit fields and should format composite values.
- **Bitwise OR (`|`)**: Operator used to combine individual flags into a composite value.
- **Bitwise AND (`&`)**: Operator used to test or mask whether a specific flag is present.
- **Bitwise NOT (`~`)**: Operator that inverts bits, often used to clear a flag via `value &= ~Flag`.
- **Bit Shift (`1 << n`)**: Expression that generates power-of-two values for defining new flags.
- **HasFlag**: Convenience method that checks whether a composite enum includes a given flag.
- **None Member**: Zero-valued enum member representing no selection or default state.
- **Mutually Exclusive Flags**: Flags that should not appear together; document or validate these combinations.
- **Serialization Strategy**: Decision to store enum values as integers or strings for persistence/interop.
