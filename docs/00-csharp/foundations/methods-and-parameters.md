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








## References
- [Methods programming guide](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/methods) - method declaration syntax and semantics.
- [Named and optional arguments](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) - improve call site readability.
- [ref keyword reference](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/ref) - pass arguments by reference safely.
- [Call methods in your programs](https://learn.microsoft.com/en-us/training/modules/csharp-call-methods/) - practice tasks for parameters and returns.
- [C# 101 methods episodes](https://learn.microsoft.com/en-us/shows/dotnet/csharp-101/) - video lessons on methods and parameter passing.
## Key Terms
- **Method Signature**: Combination of method name, parameter list, and return type that the compiler uses for overload resolution.
- **Return Type**: Type produced by a method; can be `void`, a value, a tuple, or a custom object depending on what callers need.
- **ref Parameter**: Modifier that allows a method to read and update the caller’s initialized variable by reference.
- **out Parameter**: Modifier indicating the method will assign a value before returning, commonly used in Try-patterns.
- **in Parameter**: Read-only reference to a value type, useful for large structs where copying would be expensive.
- **Optional Parameter**: Parameter with a default value that callers may omit to simplify call sites.
- **Named Argument**: Call-site feature letting callers specify parameter names to improve clarity or reorder arguments.
- **params Array**: Parameter modifier that treats a variable-length argument list as an array inside the method.
- **Method Overload**: Multiple method definitions sharing the same name but differing by parameter types or counts.
- **Tuple Return**: Method pattern that returns multiple values as a named tuple instead of relying on `out` parameters.
- **Local Function**: Method declared inside another method for encapsulating helper logic without exposing it publicly.
- **Lambda Expression**: Anonymous function that can be passed as a delegate, often used for inline helpers.
- **Span<T>**: Stack-only ref struct used for high-performance APIs; imposes restrictions on parameter passing.
- **Try-Pattern**: Convention where methods return `bool` success flags and populate `out` parameters (e.g., `int.TryParse`).
- **Overload Resolution**: Compiler process that selects which overload to invoke based on argument types and modifiers.
