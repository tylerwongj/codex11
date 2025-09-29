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
- eat
- enforces
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
- further
- helpers
- hides
- hierarchies
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
- lets
- locking
- logic
- mark
- matters
- members
- method
- need
- not
- notimplementedexception
- on
- ones
- only
- optional
- or
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
- promise
- prompts
- protected
- provide
- public
- redesign
- refactor
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
