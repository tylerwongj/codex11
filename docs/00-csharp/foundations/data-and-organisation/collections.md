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
## Key Terms
- **Array**: Fixed-length sequential storage with O(1) indexing and minimal overhead.
- **List<T>**: Resizable array-backed collection ideal for ordered data and frequent appends.
- **Dictionary<TKey,TValue>**: Hash-based key/value store that offers average O(1) lookups.
- **Queue<T>**: First-in, first-out collection suited for job or message processing.
- **Stack<T>**: Last-in, first-out collection useful for undo stacks or depth-first traversal.
- **HashSet<T>**: Set collection that enforces uniqueness and provides fast membership tests.
- **Equality Comparer**: Object that defines equality and hashing rules for dictionary or set keys.
- **LINQ**: Query API that filters, projects, and aggregates sequences using composable operators.
- **Deferred Execution**: LINQ behaviour where queries run only when enumerated, enabling pipelines but hiding costs.
- **Capacity**: Allocated size of a List or Dictionary; setting it reduces reallocations when growth is predictable.
- **Span<T>**: Stack-only view over contiguous memory, enabling high-performance iteration without allocations.
- **Immutable Collection**: Collection type from `System.Collections.Immutable` that provides structural sharing and thread safety.
