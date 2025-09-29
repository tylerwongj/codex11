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

## Word List
- 0
- 2d
- 32
- 5
- 9
- a
- access
- account
- accountnumber
- add
- aggregates
- aggressively
- amount
- an
- and
- api
- are
- area
- argumentexception
- argumentoutofrangeexception
- arguments
- as
- assembly
- assign
- assignment
- balance
- bankaccount
- based
- behaviors
- being
- benchmarkdotnet
- best
- boilerplate
- bool
- caller
- cannot
- celsius
- chaining
- change
- checkpoints
- choose
- class
- classes
- code
- collaboration
- combinations
- compare
- concise
- consolidate
- constructor
- constructors
- convert
- coordinate
- copy
- core
- creation
- csharp
- current
- custom
- data
- debugging
- decide
- decimal
- dependency
- deposit
- design
- details
- double
- during
- encapsulation
- enforce
- entities
- equality
- establish
- every
- example
- exploration
- explore
- expose
- exposing
- exposure
- express
- external
- factory
- fahrenheit
- false
- favor
- field
- fields
- for
- from
- further
- get
- guarding
- hands
- have
- help
- hide
- how
- ideas
- identity
- if
- immutability
- immutable
- implementation
- implicit
- inherit
- inheritance
- inherited
- init
- initialization
- injection
- inside
- instance
- intentions
- internal
- into
- invariants
- investigate
- is
- isnullorwhitespace
- keep
- learning
- like
- limit
- logging
- logic
- members
- methods
- minimal
- model
- modeling
- modification
- modifier
- modifiers
- must
- mutability
- mutable
- nameof
- narrowest
- new
- note
- null
- number
- object
- objectives
- objects
- of
- on
- once
- only
- openingbalance
- or
- other
- over
- parameterless
- patterns
- per
- performance
- place
- plus
- polymorphism
- practice
- prevents
- private
- properties
- protected
- provides
- public
- raw
- readability
- readonly
- record
- reduce
- reference
- references
- required
- restrict
- return
- run
- satisfies
- sealed
- semantics
- setters
- shared
- simple
- single
- small
- state
- string
- struct
- structs
- such
- suit
- support
- surface
- syntax
- temperature
- that
- the
- they
- this
- throw
- to
- trace
- true
- trywithdraw
- types
- use
- using
- valid
- validate
- value
- versus
- via
- void
- vs
- want
- when
- with
- withdraw
- work
- you
- zeroes

## References
- [Classes overview](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/classes) — foundational class design concepts.
- [Structs in C#](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/structs) — value-type semantics and guidance.
- [Records and type choices](https://learn.microsoft.com/en-us/dotnet/csharp/whats-new/tutorials/records) — how records compare to classes and structs.
- [Microsoft Learn: Explore classes, structs, and records](https://learn.microsoft.com/en-us/training/modules/csharp-explore-classes-structs-records/) — practice exercises comparing type options.
- [freeCodeCamp: Object-Oriented Programming in C#](https://www.youtube.com/watch?v=GhQdlIFylQ8) — long-form course covering class design and struct usage.

