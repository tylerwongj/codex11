# C# Generics: Constraints, Collections, Variance Basics

## Why it matters
- Generics remove casts and runtime boxing while enabling type-safe reuse.
- Constraints let you assume capabilities (`new()`, base class, interface) for generic parameters.
- Variance keywords `in` and `out` control assignment compatibility for delegates and interfaces.

## Constraints cheat sheet
```csharp
T where T : struct                // value type
T where T : class                 // reference type
T where T : unmanaged             // no references inside
T where T : new()                 // parameterless constructor
T where T : BaseClass             // inherits from BaseClass
T where T : IComparable<T>        // must implement interface
```
- Mix multiple constraints with commas; value-type constraints must appear first.

## Using generic collections
- `List<T>` for ordered, indexable sequences.
- `Dictionary<TKey,TValue>` for key-based lookup; prefer `TryGetValue` to avoid double lookup.
- `HashSet<T>` for uniqueness; supply `IEqualityComparer<T>` when custom equality needed.
- `ConcurrentDictionary<TKey,TValue>` for thread-safe access.
- Prefer `IReadOnlyList<T>` or `IReadOnlyCollection<T>` for exposing data.

## Variance snapshot
- `IEnumerable<out T>` is covariant: `IEnumerable<string>` is an `IEnumerable<object>`.
- `IComparer<in T>` is contravariant: `IComparer<object>` works for `IComparer<string>`.
- Variance applies to interfaces and delegates only, never to classes like `List<T>`.

## Sample patterns
```csharp
public T FindOrDefault<T>(IEnumerable<T> source, Func<T, bool> predicate, T fallback = default!)
{
    foreach (var item in source)
    {
        if (predicate(item)) return item;
    }
    return fallback;
}

public TResult Map<TSource, TResult>(TSource value, Func<TSource, TResult> selector) => selector(value);
```

## Practice prompts
1. Create a generic repository with `where T : IEntity` constraint and inject it into a service.
2. Implement a reusable `Cache<TKey,TValue>` that accepts a value factory delegate.
3. Demonstrate covariance with `IEnumerable<Animal>` receiving a `List<Cat>`.








## References
- [Generics in .NET](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/types/generics) - core concepts and syntax.
- [Constraints on type parameters](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters) - enforce requirements on generic arguments.
- [Generic collections overview](https://learn.microsoft.com/en-us/dotnet/standard/generics/collections) - built-in collection types and trade-offs.
- [Explore generics in C#](https://learn.microsoft.com/en-us/training/modules/csharp-generics/) - practice module for generic classes and methods.
- [Generics in C# tutorial](https://www.youtube.com/watch?v=6jM8j7lf7Xc) - pragmatic video walkthrough.
## Word List
- 1
- 2
- 3
- a
- accepts
- access
- an
- and
- animal
- annotations
- appear
- applies
- assignment
- assume
- avoid
- base
- baseclass
- based
- basics
- bool
- boxing
- c
- cache
- capabilities
- casts
- cat
- cheat
- class
- classes
- collections
- com
- commas
- compatibility
- concurrentdictionary
- constraint
- constraints
- constructor
- contravariant
- control
- covariance
- covariant
- covers
- create
- csharp
- custom
- data
- default
- delegate
- delegates
- demonstrate
- dictionary
- dotnet
- double
- en
- enabling
- equality
- explains
- exposing
- factory
- fallback
- findordefault
- first
- for
- foreach
- from
- func
- generic
- generics
- hashset
- here
- https
- icomparable
- icomparer
- ientity
- ienumerable
- iequalitycomparer
- if
- implement
- in
- indexable
- inherits
- inject
- inside
- interface
- interfaces
- into
- ireadonlycollection
- ireadonlylist
- is
- it
- item
- key
- keywords
- learn
- let
- like
- list
- lookup
- map
- matters
- microsoft
- mix
- multiple
- must
- needed
- net
- never
- new
- no
- object
- only
- or
- ordered
- out
- parameterless
- parameters
- patterns
- practice
- predicate
- prefer
- prompts
- public
- receiving
- reference
- referenced
- references
- remove
- repository
- return
- reusable
- reuse
- runtime
- safe
- safety
- sample
- selector
- sequences
- service
- sheet
- snapshot
- source
- standard
- string
- struct
- supply
- t
- that
- the
- thread
- tkey
- to
- tresult
- trygetvalue
- tsource
- tvalue
- type
- uniqueness
- unmanaged
- us
- using
- value
- var
- variance
- when
- where
- while
- why
- with
- works
- you
