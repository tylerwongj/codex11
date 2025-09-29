# C# Inheritance, Interfaces, Polymorphism, Abstract Classes

## Why it matters
- Reuse logic by building class hierarchies; expose common contracts without locking in implementation details.
- Polymorphism lets you work with base types while deferring to overridden behavior at runtime.
- Abstract classes provide shared state + partial implementation; interfaces describe capabilities without state.

## Key syntax reminders
```csharp
class Base { public virtual void Speak() => Console.WriteLine("Base"); }
class Derived : Base { public override void Speak() => Console.WriteLine("Derived"); }

interface IFlyer { void Fly(); }
abstract class Bird : IFlyer
{
    public abstract void Fly();       // force subclasses to implement
    public virtual void Eat() { }     // optional override
}
```

## Design checkpoints
- Prefer interface-first design when you only need to promise behavior.
- Use abstract classes when you share protected helpers or default behavior.
- Mark overrides with `override`; seal behavior with `sealed override` to stop further changes.
- For base constructors: call with `: base(args)` when the parent expects parameters.
- Replace `if`/`switch` chains on type with polymorphic overrides whenever possible.

## Common patterns
- Template Method: abstract class defines `Execute()` and calls abstract steps.
- Strategy: expose interface, inject concrete implementation at runtime.
- Interface Segregation: split large interfaces into focused ones.
- Default interface members (C# 8+): add implementation without breaking consumers.

## Pitfalls to avoid
- Avoid overusing inheritance when composition works; deep hierarchies become brittle.
- Do not throw `NotImplementedException` in interfaces—supply defaults or redesign.
- Remember explicit interface implementation hides members unless cast to the interface.

## Practice prompts
1. Turn a concrete class into an abstract base that enforces validation before saving.
2. Refactor a type-check `switch` into polymorphic behaviors via an interface.
3. Create two unrelated classes that share an interface and swap them behind a factory.








## References
- [Inheritance fundamentals](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/object-oriented/inheritance) - base and derived class behavior.
- [Interfaces overview](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/types/interfaces) - define contracts for polymorphism.
- [Polymorphism explained](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/object-oriented/polymorphism) - virtual dispatch and overriding examples.
- [Explore object oriented programming in C#](https://learn.microsoft.com/en-us/training/modules/csharp-object-oriented-programming/) - hands-on module tying the concepts together.
- [Object oriented programming in C# video](https://www.youtube.com/watch?v=GhQdlIFylQ8) - long-form course covering OOP patterns.
## Word List
- 1
- 2
- 3
- 8
- a
- abstract
- add
- an
- and
- args
- at
- avoid
- base
- become
- before
- behavior
- behaviors
- behind
- bird
- breaking
- brittle
- building
- by
- c
- call
- calls
- capabilities
- cast
- chains
- changes
- check
- checkpoints
- class
- classes
- com
- common
- composition
- concrete
- console
- constructors
- consumers
- contracts
- create
- csharp
- deep
- default
- defaults
- deferring
- defines
- derived
- describe
- design
- details
- do
- dotnet
- eat
- en
- enforces
- examples
- execute
- expects
- explicit
- expose
- factory
- first
- fly
- focused
- for
- force
- fundamentals
- further
- guide
- helpers
- hides
- hierarchies
- https
- if
- iflyer
- implement
- implementation
- in
- inheritance
- inject
- interface
- interfaces
- into
- it
- key
- large
- learn
- lets
- locking
- logic
- mark
- matters
- members
- method
- microsoft
- need
- not
- notimplementedexception
- object
- of
- on
- ones
- only
- optional
- or
- oriented
- overridden
- override
- overrides
- overusing
- parameters
- parent
- partial
- patterns
- pitfalls
- polymorphic
- polymorphism
- possible
- practice
- prefer
- principles
- programming
- promise
- prompts
- protected
- provide
- public
- redesign
- refactor
- references
- remember
- reminders
- replace
- reuse
- runtime
- saving
- seal
- sealed
- segregation
- share
- shared
- speak
- split
- state
- steps
- stop
- strategy
- subclasses
- supply
- swap
- switch
- syntax
- template
- that
- the
- them
- throw
- to
- turn
- two
- type
- types
- unless
- unrelated
- us
- use
- validation
- via
- virtual
- void
- when
- whenever
- while
- why
- with
- without
- work
- works
- writeline
- you
