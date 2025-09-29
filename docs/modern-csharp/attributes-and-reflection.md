# Attributes and Reflection

## Purpose of Attributes
- Attach declarative metadata to types, members, and assemblies.
- Drive cross-cutting behaviors such as serialization, validation, and dependency injection.
- Serve as contracts for tooling (Roslyn analyzers, source generators, custom inspectors).

## Built-in Attribute Essentials
- Apply with `[AttributeName]`; omit the `Attribute` suffix when targeting usage.
- Use constructor parameters for required data and named properties for optional settings.
- Common examples: `Obsolete`, `DataMember`, `Authorize`, `Range`.

```csharp
[Obsolete("Prefer the asynchronous overload", error: false)]
public string LoadConfig(string path) => ...;
```

## Creating Custom Attributes
- Inherit from `System.Attribute`.
- Decorate attribute classes with `[AttributeUsage]` to constrain valid targets and multiplicity.

```csharp
[AttributeUsage(AttributeTargets.Class | AttributeTargets.Struct, AllowMultiple = false)]
public sealed class ApiResourceAttribute : Attribute
{
    public ApiResourceAttribute(string routePrefix) => RoutePrefix = routePrefix;
    public string RoutePrefix { get; }
    public string? Version { get; init; }
}
```

## Reflection Basics
- `Type` metadata enables runtime inspection of members, attributes, and generic parameters.
- `Activator.CreateInstance` instantiates types discovered dynamically; pair with caching to avoid overhead.
- Access attributes via `MemberInfo.GetCustomAttributes()` or `CustomAttributeData` for lightweight analysis.

```csharp
var resourceTypes = Assembly.GetExecutingAssembly()
    .GetTypes()
    .Where(t => t.GetCustomAttribute<ApiResourceAttribute>() is not null);

foreach (var type in resourceTypes)
{
    var attribute = type.GetCustomAttribute<ApiResourceAttribute>()!;
    Console.WriteLine($"{type.Name} maps to /api/{attribute.RoutePrefix}");
}
```

## Performance and Safety
- Reflection incurs boxing and metadata lookups; cache `Type` handles and delegate accessors.
- Prefer source generators or compiled expression trees for hot paths.
- Limit dynamic invocation in AOT contexts (Unity IL2CPP, native AOT) where metadata stripping can remove unused members.

## Advanced Patterns
- Use reflection-driven configuration with guardrails: validate attribute usage at startup and fail fast.
- Combine attributes with `IServiceCollection` extensions to auto-register components.
- Pair with analyzers to catch misuse at compile time, e.g., enforce that `[ApiResource]` types expose parameterless constructors.

## Further Study
- .NET Docs: *Attributes* and *Reflection* sections.
- Roslyn source generator samples for attribute-driven code emission.
- "High-performance reflection in .NET" (Stephen Toub) for micro-optimization strategies.

## Word List
- access
- accessors
- activator
- advanced
- allowmultiple
- analysis
- analyzers
- and
- aot
- api
- apiresource
- apiresourceattribute
- apply
- as
- assemblies
- assembly
- asynchronous
- at
- attach
- attribute
- attributename
- attributes
- attributetargets
- attributeusage
- authorize
- auto
- avoid
- basics
- behaviors
- boxing
- built
- cache
- caching
- can
- catch
- class
- classes
- code
- combine
- common
- compile
- compiled
- components
- configuration
- console
- constrain
- constructor
- constructors
- contexts
- contracts
- createinstance
- creating
- cross
- csharp
- custom
- customattributedata
- cutting
- data
- datamember
- declarative
- decorate
- delegate
- dependency
- discovered
- docs
- drive
- driven
- dynamic
- dynamically
- e
- emission
- enables
- enforce
- error
- essentials
- examples
- expose
- expression
- extensions
- fail
- false
- fast
- for
- foreach
- from
- further
- g
- generator
- generators
- generic
- get
- getcustomattribute
- getcustomattributes
- getexecutingassembly
- gettypes
- guardrails
- handles
- high
- hot
- il2cpp
- in
- incurs
- inherit
- init
- injection
- inspection
- inspectors
- instantiates
- invocation
- is
- iservicecollection
- lightweight
- limit
- loadconfig
- lookups
- maps
- memberinfo
- members
- metadata
- micro
- misuse
- multiplicity
- name
- named
- native
- net
- not
- null
- obsolete
- of
- omit
- optimization
- optional
- or
- overhead
- overload
- pair
- parameterless
- parameters
- path
- paths
- patterns
- performance
- prefer
- properties
- public
- purpose
- range
- reflection
- register
- remove
- required
- resourcetypes
- roslyn
- routeprefix
- runtime
- safety
- samples
- sealed
- sections
- serialization
- serve
- settings
- source
- startup
- stephen
- strategies
- string
- stripping
- struct
- study
- such
- suffix
- system
- t
- targeting
- targets
- that
- the
- time
- to
- tooling
- toub
- trees
- type
- types
- unity
- unused
- usage
- use
- valid
- validate
- validation
- var
- version
- via
- when
- where
- with
- writeline

## References
- [Attributes in C#](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/attributes/) — introduction to built-in and custom attributes.
- [Creating custom attributes](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/attributes/creating-custom-attributes) — how to author and apply metadata.
- [Reflection overview](https://learn.microsoft.com/en-us/dotnet/framework/reflection-and-codedom/reflection) — runtime type inspection fundamentals.
- [System.Reflection namespace](https://learn.microsoft.com/en-us/dotnet/api/system.reflection) — API reference for reflective operations.
- [C# Advanced: Attributes and Reflection](https://learn.microsoft.com/en-us/shows/csharp-advanced/attributes-and-reflection/) — video episode demonstrating practical usage.
