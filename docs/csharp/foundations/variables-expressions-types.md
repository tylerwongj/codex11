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

## Word List
- 0
- 0b1111
- 0m
- 1
- 10
- 42
- 42l
- 99
- a
- about
- accepts
- against
- aids
- allocated
- an
- and
- applies
- apply
- appropriate
- are
- arrays
- assignment
- assignments
- at
- back
- before
- between
- block
- both
- boxing
- but
- by
- c
- c1
- c2
- call
- caller
- calls
- can
- casts
- changes
- checkpoints
- choose
- clarify
- clarity
- class
- classes
- clearly
- coalescing
- combines
- communicates
- compare
- compile
- console
- conversion
- conversions
- convert
- converts
- copy
- copying
- core
- count
- counter
- creating
- csharp
- currency
- data
- decimal
- declarations
- declare
- default
- defensive
- differentiate
- dotnet
- double
- e
- entire
- enum
- escaping
- every
- example
- experiment
- explicit
- exploration
- explore
- expression
- expressions
- favor
- fields
- fine
- for
- from
- further
- g
- generated
- get
- guard
- hand
- handle
- handling
- hands
- heap
- hello
- help
- helper
- helpers
- how
- ideas
- il
- implicit
- inference
- initialization
- input
- inside
- instance
- int
- intent
- interpolated
- investigate
- it
- language
- learning
- leverages
- lifetime
- literal
- literals
- live
- local
- long
- loss
- lossless
- lossy
- make
- manipulating
- mathematics
- mental
- method
- methods
- mirrors
- models
- multiple
- mutates
- name
- new
- noise
- noting
- null
- nullability
- nullable
- nullreferenceexception
- numeric
- object
- objectives
- observe
- of
- on
- operands
- operator
- operators
- or
- original
- p1
- p2
- parentheses
- pass
- point
- practice
- precedence
- primitives
- produce
- produces
- propagation
- public
- reach
- read
- readability
- readonly
- record
- reduce
- reference
- references
- reinforce
- remains
- remember
- required
- right
- rules
- s
- safely
- safety
- same
- scope
- sections
- selection
- semantics
- set
- sharplab
- side
- specification
- statically
- still
- storing
- strategies
- string
- strings
- struct
- structs
- suffixes
- system
- t
- temp
- that
- the
- their
- them
- time
- to
- tryparse
- tune
- type
- typed
- types
- unboxing
- understand
- understanding
- unexpected
- use
- user
- using
- value
- var
- variable
- variables
- verbatim
- view
- vs
- when
- with
- without
- write
- writeline
- x
- y

## References
- [C# type system and variables](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/types/) — overview of built-in types and semantics.
- [Value types](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/types/value-types) — details on structs, enums, and copy behavior.
- [Casting and type conversions](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/types/casting-and-type-conversions) — implicit vs explicit conversions with examples.
- [Nullable reference types](https://learn.microsoft.com/en-us/dotnet/csharp/nullable-references) — guidance on annotating and enforcing null safety.
- [Programming with Mosh: C# Tutorial for Beginners](https://www.youtube.com/watch?v=gfkTfcpWqAY) — full video course covering types, variables, and expressions.

