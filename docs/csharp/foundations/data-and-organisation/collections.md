# Collections Cheat Sheet

## When to Reach for Each Type
- **Arrays (`T[]`)**: fixed-size, fastest indexing, minimal allocations. Prefer for known-size buffers or interop.
- **`List<T>`**: dynamic arrays, cheap append, great default choice for ordered data. Use `Capacity` to avoid repeated reallocations.
- **`Dictionary<TKey,TValue>`**: key/value lookups in O(1) average time. Provide an equality comparer when keys are case-insensitive or custom structs.
- **`Queue<T>`**: FIFO workflow processing. `Enqueue` producers, `Dequeue` consumers; use `TryDequeue` pattern to avoid exceptions.
- Bonus: `Stack<T>` for LIFO, `HashSet<T>` to enforce uniqueness.

## Common Operations
```csharp
var nums = new List<int> { 1, 2, 3 };
nums.AddRange(new[] { 4, 5 });
nums.RemoveAll(n => n % 2 == 0); // keep odds only

var lookup = new Dictionary<string, int>(StringComparer.OrdinalIgnoreCase)
{
    ["hp"] = 100,
    ["mp"] = 30
};
if (lookup.TryGetValue("HP", out var hp))
{
    Console.WriteLine($"HP: {hp}");
}

var queue = new Queue<string>();
queue.Enqueue("load assets");
if (queue.TryDequeue(out var job))
{
    Process(job);
}
```

## LINQ Fundamentals
- `Where`, `Select`, `OrderBy`, `GroupBy` transform or filter without copying collections manually.
- Use LINQ for readability, but cache results with `ToList()` when you enumerate more than once.
- Remember deferred execution: the query runs when you iterate (`foreach`, `ToArray`, etc.).

```csharp
var activeIds = players
    .Where(p => p.IsActive)
    .OrderByDescending(p => p.Score)
    .Select(p => p.Id)
    .ToList();
```

## Performance Tips
- Prefer `Span<T>`/`ReadOnlySpan<T>` for tight loops over arrays in modern .NET.
- Initialize `List<T>(expectedCount)` and `Dictionary<TKey,TValue>(expectedCount)` to cut down on reallocations.
- Avoid LINQ in hot paths; use loops when profiling shows allocations are an issue.

## Word List
- 0
- 1
- 100
- 2
- 3
- 30
- 4
- 5
- activeids
- addrange
- allocations
- an
- and
- append
- are
- arrays
- assets
- average
- avoid
- bonus
- buffers
- but
- cache
- capacity
- case
- cheap
- cheat
- choice
- collections
- common
- comparer
- console
- consumers
- copying
- csharp
- custom
- cut
- data
- default
- deferred
- dequeue
- dictionary
- down
- dynamic
- each
- enforce
- enqueue
- enumerate
- equality
- etc
- exceptions
- execution
- expectedcount
- fastest
- fifo
- filter
- fixed
- for
- foreach
- fundamentals
- great
- groupby
- hashset
- hot
- hp
- id
- if
- in
- indexing
- initialize
- insensitive
- int
- interop
- isactive
- issue
- iterate
- job
- keep
- key
- keys
- known
- lifo
- linq
- list
- load
- lookup
- lookups
- loops
- manually
- minimal
- modern
- more
- mp
- n
- net
- new
- nums
- o
- odds
- on
- once
- only
- operations
- or
- orderby
- orderbydescending
- ordered
- ordinalignorecase
- out
- over
- p
- paths
- pattern
- performance
- players
- prefer
- process
- processing
- producers
- profiling
- provide
- query
- queue
- reach
- readability
- readonlyspan
- reallocations
- remember
- removeall
- repeated
- results
- runs
- score
- select
- sheet
- shows
- size
- span
- stack
- string
- stringcomparer
- structs
- t
- than
- the
- tight
- time
- tips
- tkey
- to
- toarray
- tolist
- transform
- trydequeue
- trygetvalue
- tvalue
- type
- uniqueness
- use
- value
- var
- when
- where
- with
- without
- workflow
- writeline
- you

## References
- [Collections in .NET](https://learn.microsoft.com/en-us/dotnet/standard/collections/) — guide to the collection namespaces.
- [Choosing a collection](https://learn.microsoft.com/en-us/dotnet/standard/collections/when-to-use-generic-collections) — decision matrix for generic types.
- [System.Collections.Generic overview](https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic) — reference for primary collection types.
- [Immutable collections](https://learn.microsoft.com/en-us/dotnet/api/system.collections.immutable) — when to reach for persistent collection types.
- [IAmTimCorey: C# Collection Types](https://www.youtube.com/watch?v=MKCrYYU0vxY) — video comparing lists, dictionaries, queues, and stacks.
