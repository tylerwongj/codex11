# Classes, Structs, and Encapsulation

## Learning objectives
- Decide when to model data with classes versus structs based on semantics and performance.
- Use constructors and access modifiers to enforce invariants and hide implementation details.
- Design types that balance mutability, readability, and encapsulation.

## Core ideas

### Classes vs structs
- Classes are reference types that support inheritance, polymorphism, and `null` references; they suit entities with identity or shared mutable state.
- Structs are value types that copy on assignment, cannot inherit from other structs, and work best for small, immutable aggregates.
- Use `record`/`record struct` when you want value-based equality with concise syntax.

### Encapsulation and invariants
- Keep fields private and expose state via methods or properties; this provides a single place to validate invariants.
- Favor behaviors (`Deposit`, `Withdraw`) over exposing raw fields for external modification.
- `readonly` members and `init`-only setters help express immutability intentions.

### Constructors and initialization
- Constructors run once per instance to establish valid state—validate arguments aggressively.
- Structs have an implicit parameterless constructor that zeroes fields; custom constructors must assign every field.
- Use constructor chaining (`: this(...)`) to consolidate initialization logic.

### Access modifiers
- Choose the narrowest modifier that satisfies collaboration (`private`, `protected`, `internal`, `public`, plus combinations like `protected internal`).
- Internal types limit exposure to the current assembly; `sealed` prevents classes from being inherited further.

## Hands-on example: guarding invariants
```csharp
class BankAccount
{
    private decimal _balance;

    public BankAccount(string accountNumber, decimal openingBalance)
    {
        if (string.IsNullOrWhiteSpace(accountNumber))
            throw new ArgumentException("Account number is required", nameof(accountNumber));
        if (openingBalance < 0)
            throw new ArgumentOutOfRangeException(nameof(openingBalance));

        AccountNumber = accountNumber;
        _balance = openingBalance;
    }

    public string AccountNumber { get; }
    public decimal Balance => _balance;

    public void Deposit(decimal amount)
    {
        if (amount <= 0) throw new ArgumentOutOfRangeException(nameof(amount));
        _balance += amount;
    }

    public bool TryWithdraw(decimal amount)
    {
        if (amount <= 0 || amount > _balance) return false;
        _balance -= amount;
        return true;
    }
}

readonly struct Temperature
{
    public Temperature(double celsius) => Celsius = celsius;
    public double Celsius { get; }
    public double Fahrenheit => Celsius * 9 / 5 + 32;
}
```

## Practice checkpoints
- Convert a simple 2D coordinate class into a struct and note how assignment semantics change inside caller code.
- Add logging to constructors to trace object creation during debugging.
- Restrict setters with `internal` or `protected` to reduce the public API surface area.

## Further exploration
- Compare performance of classes versus structs using BenchmarkDotNet when modeling small data objects.
- Investigate `record` types for value-based equality with minimal boilerplate.
- Explore encapsulation patterns such as factory methods, private constructors, and dependency injection.








## References
- [Classes overview](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/classes) - fundamentals of class design and members.
- [Structs in C#](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/structs) - value type behavior and guidelines.
- [Records tutorial](https://learn.microsoft.com/en-us/dotnet/csharp/whats-new/tutorials/records) - comparison between records and classes.
- [Explore classes, structs, and records](https://learn.microsoft.com/en-us/training/modules/csharp-explore-classes-structs-records/) - interactive module reinforcing type choices.
- [Object oriented programming in C#](https://www.youtube.com/watch?v=GhQdlIFylQ8) - video walkthrough of OOP concepts.
## Key Terms
- **Class**: Reference type that supports inheritance, polymorphism, and identity semantics.
- **Struct**: Value type that copies on assignment and excels at small, immutable aggregates.
- **Record**: C# type offering concise value-based equality; available as `record class` or `record struct`.
- **Encapsulation**: Practice of hiding implementation details and exposing controlled operations or properties.
- **Invariant**: Rule that must hold for an object’s state; validated in constructors or property setters.
- **Constructor**: Method that initializes a new instance and enforces required arguments.
- **Constructor Chaining**: Use of `: this(...)` or `: base(...)` to reuse initialization logic across overloads.
- **Access Modifier**: Keyword such as `private`, `protected`, `internal`, or `public` that controls visibility.
- **readonly Field**: Field that can only be assigned during declaration or in a constructor, signaling immutability.
- **init-only Setter**: Property setter modifier that allows assignment during object initialization but not afterward.
- **Identity**: Concept that two references can point to the same class instance even if field values match.
- **Value Equality**: Equality semantics where two instances compare equal when their contained data matches.
- **Sealed Class**: Class declared with `sealed` to prevent further inheritance.
- **Private Field**: Implementation detail stored on the type and hidden from consumers to enforce encapsulation.
- **Try Pattern**: Method style (e.g., `TryWithdraw`) that returns `bool` and leaves state unchanged on failure.
- **readonly struct**: Struct modifier indicating fields are immutable, preventing accidental copies inside members.
