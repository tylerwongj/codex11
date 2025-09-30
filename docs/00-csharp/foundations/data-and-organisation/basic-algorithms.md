# Basic Algorithms With Built-in APIs

## Searching
- `List<T>.Find`/`FindIndex` grab the first match without a manual loop.
- `FirstOrDefault`, `SingleOrDefault` in LINQ return the element or a default value.
- `BinarySearch` on sorted lists gives O(log n) lookups—remember to sort first.

```csharp
var found = enemies.FirstOrDefault(e => e.HP <= 0);
if (found != null)
{
    HandleDefeat(found);
}
```

## Sorting
- `List<T>.Sort()` sorts in place; pass an `IComparer<T>` or comparison lambda.
- `OrderBy`/`ThenBy` create a sorted copy without mutating the source.
- Use `Array.Sort(keys, items)` to keep parallel arrays in sync.

```csharp
scores.Sort((a, b) => b.Value.CompareTo(a.Value));
var topThree = scores.Take(3).ToList();
```

## Iteration Patterns
- `foreach` is the safest default; it cannot modify the collection but is concise.
- `for` loops offer index access for arrays/lists when you need manual control.
- `Select` + `ToList()` transforms data while encouraging immutability.
- `Aggregate` folds a sequence into a single value; great for totals or string joins.

```csharp
var totalDamage = attacks.Aggregate(0, (sum, hit) => sum + hit.Damage);
```

## When to Drop to Manual Loops
- Profiling shows hot paths with high allocation counts.
- You need early exits that do not fit `First()` or `Any()` cleanly.
- Complex state machines where a `while` loop keeps intent clearer.

Always measure: readability first, micro-optimizations after evidence from profiling tools.








## References
- [LINQ programming guide](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/) - core operators for querying in-memory data.
- [List.Find API reference](https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1.find) - search helpers on List<T>.
- [Array.Sort documentation](https://learn.microsoft.com/en-us/dotnet/api/system.array.sort) - sorting overloads and comparer usage.
- [Enumerable.Aggregate reference](https://learn.microsoft.com/en-us/dotnet/api/system.linq.enumerable.aggregate) - fold sequences into single values.
- [LINQ crash course](https://www.youtube.com/watch?v=8pTEmbeENF4) - video overview of practical LINQ patterns.
## Key Terms
- **Linear Search**: Sequential scan through a collection until a match is found.
- **Binary Search**: O(log n) search algorithm that operates on sorted sequences.
- **Comparer**: Object or lambda that defines ordering rules for `Sort` and other algorithms.
- **In-place Sort**: Sorting approach like `List<T>.Sort()` that reorders the existing collection.
- **Projection**: Transformation of elements via `Select`, often paired with `ToList()` to materialize results.
- **Aggregation**: Operation that folds a sequence into a single value, e.g., sums or concatenations.
- **Deferred Execution**: LINQ behaviour where queries run on enumeration, enabling optimized pipelines.
- **Hot Path**: Performance-critical section of code identified through profiling.
- **Early Exit**: Pattern of breaking or returning once a result is known to avoid extra work.
- **Complexity**: Big-O characterization of algorithm cost relative to input size.
- **Profiling**: Measuring runtime behaviour to determine when manual loops outweigh LINQ readability.
