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
## Key Terms
- **Inheritance**: Mechanism that lets a derived class reuse and extend behavior defined by a base class.
- **Virtual Method**: Base-class method marked `virtual` so derived classes may override it.
- **override Keyword**: Modifier used in derived classes to replace virtual or abstract base members.
- **sealed override**: Combination that prevents further overrides down the hierarchy.
- **Abstract Class**: Class that cannot be instantiated and may define abstract members to enforce implementation.
- **Interface**: Contract that declares members without providing state, enabling multiple inheritance of behavior.
- **Default Interface Member**: C# 8 feature allowing interfaces to supply optional implementation.
- **Template Method**: Pattern where a base class defines the skeleton of an algorithm and delegates steps to overrides.
- **Strategy Pattern**: Pattern that injects interchangeable implementations via a shared interface.
- **Factory**: Component that creates instances, often hiding which concrete type is returned.
- **Explicit Interface Implementation**: Syntax that hides interface members unless accessed through the interface reference.
- **Composition**: Alternative to inheritance where behavior is built by combining smaller components.
