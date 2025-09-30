# Data and Organisation Modules

Focus on these C# data handling topics to support gameplay system work.

- [Collections](collections.md)
- [Enumerations and Flags](enumerations-and-flags.md)
- [Basic Algorithms](basic-algorithms.md)
- [Serialization Basics](serialization-basics.md)

Complete them after the core foundations lessons and before tackling Unity data patterns.

## Data Topics
```bash
ls docs/00-csharp/foundations/data-and-organisation
```








## References
- [.NET data structures overview](https://learn.microsoft.com/en-us/dotnet/standard/collections/) - introduction to available collection types.
- [Choosing a collection](https://learn.microsoft.com/en-us/dotnet/standard/collections/when-to-use-generic-collections) - decision guide for generic collections.
- [LINQ fundamentals](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/) - query operations across collections.
- [Algorithms in C#](https://dotnettutorials.net/course/algorithms-using-csharp/) - article series on common algorithms.
- [C# collections course](https://www.pluralsight.com/courses/csharp-collections-generics) - Pluralsight course diving into generics and collections.
## Key Terms
- **Collection**: Container type (List, Dictionary, Queue, etc.) used to group related data items.
- **Generic Collection**: Collection definition (e.g., `List<T>`) that enforces compile-time type safety.
- **Enumeration**: Named set of constants, often used for state machines or option flags.
- **Flags Enum**: Enum decorated with `[Flags]` so bitwise operations can combine multiple options.
- **Algorithm**: Step-by-step procedure such as search or sort applied to collections.
- **Serialization**: Process of converting objects into a storable or transferable format like JSON.
- **LINQ**: Language Integrated Query toolkit for transforming and filtering sequences.
- **Data Pipeline**: Flow of loading, transforming, and persisting data that underpins gameplay systems.
