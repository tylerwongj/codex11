# Variables, Expressions, and the Type System

## Learning objectives
- Differentiate between value and reference semantics when storing and manipulating data.
- Choose appropriate variable declarations and initialization strategies for clarity and safety.
- Apply conversion rules and expression operators without unexpected data loss.

## Core ideas

### Variable declarations and scope
- Favor explicit types (`int count = 0;`) when it aids readability; reach for `var` when the right-hand side clearly communicates the type.
- Remember that local variables live for the lifetime of their block; fields live with the object/struct instance.

### Expressions and operators
- An expression combines operands (literals, variables) with operators or method calls to produce a value.
- Operator precedence mirrors mathematics (`*` before `+`), and parentheses clarify intent.
- Null-propagation (`?.`) and null-coalescing (`??`) operators help guard against `NullReferenceException`.

### Value vs reference semantics
- Value types (`struct`, `enum`, numeric primitives) copy the entire value with every assignment or pass-by-value call.
- Reference types (`class`, `string`, arrays, `record class`) copy the reference; multiple variables can point to the same object instance.
- Boxing converts a value type to `object`, creating a heap-allocated copy; unboxing casts back to the original type.

### Type inference and literals
- Literal suffixes (`1.0m`, `42L`, `0b1111`) fine-tune type selection at compile time.
- `var` leverages local type inference but still produces a statically typed variable.
- Interpolated strings (`$"Hello {name}"`) and verbatim strings (`@"C:\\temp"`) reduce escaping noise.

### Conversions and nullability
- Implicit conversions are lossless (e.g., `int` to `long`); explicit casts or helper methods are required for lossy conversions.
- Use `int.TryParse`/`Convert` helpers to handle user input safely.
- Nullable reference types (`string?`) and `Nullable<T>` (`int?`) make intent about null-handling explicit.

## Hands-on example: understanding semantics
```csharp
using System;

// Structs are value types: assignments copy data
struct Point
{
    public int X;
    public int Y;
}

// Classes are reference types: assignments copy references
class Counter
{
    public int Value { get; set; }
}

var p1 = new Point { X = 1, Y = 1 };
var p2 = p1;         // Value copy
p2.X = 99;
Console.WriteLine($"p1.X = {p1.X}, p2.X = {p2.X}"); // p1.X remains 1

var c1 = new Counter { Value = 10 };
var c2 = c1;         // Reference copy
c2.Value = 42;
Console.WriteLine($"c1.Value = {c1.Value}, c2.Value = {c2.Value}"); // Both read 42
```

## Practice checkpoints
- Declare a `decimal` variable for currency and experiment with implicit vs explicit conversions from `int` and `double`.
- Write a helper that accepts both a `struct` and a `class`, mutates them inside the method, and observe the caller’s view.
- Compare `default(T)` for a value type (`default(int)`) and a reference type (`default(string)`), noting how nullability applies.

## Further exploration
- Explore the IL generated for value vs reference types using `dotnet il` or SharpLab to reinforce mental models.
- Investigate how `readonly struct` changes copy semantics and defensive copying.
- Read the C# language specification sections on conversions to understand implicit vs explicit rules.








## References
- [C# type system overview](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/types/) - built-in types and semantics.
- [Value types guide](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/types/value-types) - structs, enums, and copy behavior.
- [Casting and type conversions](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/types/casting-and-type-conversions) - implicit and explicit conversions with examples.
- [Nullable reference types](https://learn.microsoft.com/en-us/dotnet/csharp/nullable-references) - annotate and enforce null safety.
- [C# tutorial for beginners](https://www.youtube.com/watch?v=gfkTfcpWqAY) - full length video covering types and expressions.
## Key Terms
- **Value Type**: Struct or primitive copied by value; assignments duplicate the entire data payload.
- **Reference Type**: Class, string, array, or record class that copies references so multiple variables share the same object.
- **Boxing**: Operation that wraps a value type in an `object`, moving the copy onto the heap.
- **Type Inference**: Compiler deduction of a variable’s type from the right-hand expression when `var` is used.
- **Literal Suffix**: Token such as `m`, `f`, or `L` appended to literals to force a specific numeric type.
- **Null-conditional Operator**: The `?.` operator that safely navigates members only when the reference is non-null.
- **Null-coalescing Operator**: The `??` operator that falls back to a default value when the left operand is null.
- **Implicit Conversion**: Lossless automatic conversion (e.g., `int` to `long`) that requires no cast.
- **Explicit Conversion**: Potentially lossy conversion enforced via cast syntax or helper methods like `Convert.ToInt32`.
- **Nullable Value Type**: Wrapper `Nullable<T>` or `T?` that allows value types to represent absence.
- **Nullable Reference Type**: `string?` style annotations that help the compiler enforce null-safety contracts.
- **Interpolated String**: String literal prefixed with `$` that embeds expressions inside `{}` placeholders.
- **Scope**: Region of code (block, method, type) that determines variable lifetime and visibility.
- **Expression**: Combination of operands and operators that produces a value and may trigger side effects.
- **Operator Precedence**: Rules that determine evaluation order, ensuring `*` executes before `+` unless parentheses change it.
- **default(T)**: C# expression that yields the default value for a given type (zero for value types, null for references).
