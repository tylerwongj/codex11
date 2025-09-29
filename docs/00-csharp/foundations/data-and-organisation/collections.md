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








## References
- [Collections in .NET](https://learn.microsoft.com/en-us/dotnet/standard/collections/) - overview of collection namespaces.
- [Generic collections guide](https://learn.microsoft.com/en-us/dotnet/standard/collections/when-to-use-generic-collections) - choose between List, Dictionary, Queue, and more.
- [System.Collections.Generic reference](https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic) - API docs for primary collection types.
- [Immutable collections](https://learn.microsoft.com/en-us/dotnet/api/system.collections.immutable) - persistent collection types and scenarios.
- [C# collection types explained](https://www.youtube.com/watch?v=MKCrYYU0vxY) - video comparing common collections.
## Word List
- 0
- 1
- 100
- 2
- 3
- 30
- 4
- 5
- a
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
- choosing
- class
- collection
- collections
- com
- common
- comparer
- concepts
- console
- consumers
- copying
- csharp
- custom
- cut
- data
- decision
- default
- deferred
- dequeue
- dictionary
- dotnet
- down
- dynamic
- each
- en
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
- guide
- hashset
- hot
- hp
- https
- id
- if
- in
- indexing
- initialize
- insensitive
- int
- interop
- introduces
- isactive
- issue
- iterate
- job
- keep
- key
- keys
- known
- learn
- lifo
- linq
- list
- load
- lookup
- lookups
- loops
- manually
- microsoft
- minimal
- modern
- more
- mp
- n
- net
- new
- note
- nums
- o
- objects
- odds
- on
- once
- only
- operations
- operators
- or
- orderby
- orderbydescending
- ordered
- ordinalignorecase
- out
- over
- overview
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
- programming
- provide
- query
- queue
- reach
- readability
- readonlyspan
- reallocations
- referenced
- references
- remember
- removeall
- repeated
- results
- runs
- score
- select
- selecting
- sheet
- shows
- size
- span
- stack
- standard
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
- us
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
